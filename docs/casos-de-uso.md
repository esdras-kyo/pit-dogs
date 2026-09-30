# Descrição dos Casos de Uso Críticos

Este documento detalha apenas os casos de uso considerados mais críticos para o sistema. A seleção prioriza os fluxos que concentram maior valor para a operação, maior quantidade de regras de negócio e maior risco de inconsistência entre os artefatos.

| ID | Caso de uso | Ator principal | Justificativa da seleção |
|---|---|---|---|
| UC-01 | Registrar pedido | Atendente | É o ponto de entrada da venda e conecta produtos, personalizações, preços, mesas, cozinha, impressão e consumo de estoque. |
| UC-02 | Registrar ajuste de estoque | Administrador | Altera diretamente o saldo de insumos e exige autorização, justificativa, movimentação histórica, auditoria e alerta de estoque mínimo. |
| UC-03 | Registrar pagamento | Caixa | Concentra pagamento simples, misto e parcial, troco, prevenção de cobrança duplicada, caixa e independência entre situação financeira e preparo. |

Os três casos correspondem aos fluxos escolhidos para os diagramas de atividade. Os demais casos de uso permanecem representados no diagrama geral e na matriz de rastreabilidade, sem necessidade de descrição expandida nesta etapa.

## Decisões de domínio aplicadas

1. **Fechar a conta da mesa não significa registrar o pagamento.** Fechar a conta encerra o consumo, impede novos lançamentos e consolida o valor devido. Registrar o pagamento quita esse valor posteriormente.
2. **A conta de mesa deve estar fechada antes de qualquer recebimento.** A quitação integral libera a mesa, enquanto pagamentos parciais mantêm a conta fechada e pendente.
3. **Situação operacional e situação financeira são independentes.** Um pedido pode estar em preparação e já estar pago, ou estar pronto e ainda possuir pagamento pendente.
4. **Uma venda deve gerar no máximo uma baixa de estoque.** Cancelamentos e correções não podem apagar o histórico; devem produzir movimentações compensatórias quando aplicável.
5. **Pedidos pagos pelas plataformas externas não podem ser cobrados novamente no caixa.**

> **Pendência de alinhamento:** o RF-046 atualmente afirma que a conta é fechada após a quitação, enquanto a decisão de domínio adotada e o protótipo tratam o fechamento como consolidação anterior ao pagamento. O RF-046, o RF-048, a RN-030 e a RN-034 devem ser revisados para usar os termos `conta aberta`, `conta fechada`, `pagamento pendente`, `conta quitada` e `mesa livre` de maneira inequívoca.

---

## UC-01 - Registrar pedido

### Objetivo

Registrar um pedido presencial de balcão ou de mesa/comanda, com seus itens, quantidades, personalizações, preços e origem, encaminhando-o para a produção quando necessário.

### Atores

- **Ator principal:** Atendente.
- **Atores relacionados:** Caixa, quando houver pagamento antes do preparo; Cozinha, que recebe o pedido confirmado para produção.

### Gatilho

O cliente solicita produtos no balcão ou durante o atendimento de uma mesa/comanda.

### Pré-condições

1. O atendente está autenticado e possui permissão para registrar pedidos.
2. Os produtos, categorias, adicionais e preços necessários estão cadastrados.
3. Para pedido de mesa/comanda, a mesa está livre para abertura ou possui conta aberta que permite novos lançamentos.
4. A conta da mesa não está fechada.

### Pós-condições de sucesso

1. O pedido é registrado com identificador único, origem, data, horário e usuário responsável.
2. Cada item mantém o preço praticado no momento de sua inclusão.
3. O valor total corresponde aos itens, adicionais e descontos autorizados.
4. Quando o pedido exigir produção, ele é disponibilizado para a cozinha com status `Recebido`.
5. O consumo teórico é registrado uma única vez conforme a ficha técnica e as personalizações aplicáveis.
6. Quando configurada, a comanda é enviada para impressão térmica.

### Fluxo principal

1. O atendente inicia um novo pedido.
2. O sistema solicita a origem do pedido: balcão ou mesa/comanda.
3. Para mesa/comanda, o atendente seleciona uma mesa livre ou uma conta aberta.
4. O sistema apresenta os produtos ativos e disponíveis, organizados por categoria, com opção de pesquisa.
5. O atendente seleciona um produto e informa a quantidade.
6. Quando o produto for personalizável, o sistema apresenta adicionais, remoções permitidas e campo de observação.
7. O atendente informa as personalizações solicitadas pelo cliente.
8. O sistema valida as quantidades mínimas e máximas dos grupos de adicionais e calcula o valor do item.
9. O atendente confirma o item e repete os passos de seleção enquanto houver produtos a incluir.
10. O sistema apresenta os itens, o subtotal e o valor total atualizado.
11. Se solicitado, o atendente aplica desconto, desde que possua autorização, informando o motivo.
12. O atendente confirma o pedido.
13. O sistema verifica disponibilidade, personalizações obrigatórias, origem e, quando aplicável, a situação da mesa.
14. O sistema gera o identificador do pedido, fixa os preços dos itens e registra data, horário, origem e usuário responsável.
15. Para mesa/comanda, o sistema vincula o pedido à conta aberta correspondente.
16. Quando houver pagamento imediato de pedido de balcão, o fluxo UC-03 - Registrar pagamento é executado pelo Caixa.
17. Quando o pedido exigir produção, o sistema o encaminha para a cozinha com itens, quantidades, adicionais, remoções e observações.
18. O sistema registra o consumo teórico previsto, sem permitir baixa duplicada para a mesma venda.
19. Se a impressão térmica estiver habilitada, o sistema envia a comanda para a impressora da cozinha.
20. O sistema confirma o registro do pedido ao atendente.

### Fluxos alternativos e exceções

#### A1 - Produto indisponível

1. No passo 5, o sistema identifica que o produto está inativo, indisponível ou sem estoque suficiente para a produção.
2. O sistema impede sua inclusão e informa o motivo ao atendente.
3. O atendente pode escolher outro produto ou encerrar a montagem.

#### A2 - Personalização inválida

1. No passo 8, a quantidade de opções selecionadas não atende ao mínimo obrigatório ou ultrapassa o máximo permitido.
2. O sistema não confirma o item e destaca o grupo que precisa ser corrigido.
3. O fluxo retorna ao passo 7.

#### A3 - Desconto não autorizado

1. No passo 11, o usuário não possui permissão para conceder desconto.
2. O sistema bloqueia a operação e mantém o preço original.
3. O atendente pode solicitar a atuação de um usuário autorizado ou prosseguir sem desconto.

#### A4 - Mesa com conta fechada

1. No passo 3 ou no passo 13, o sistema identifica que a conta da mesa está fechada.
2. O sistema impede o lançamento de novos itens.
3. O atendente deve selecionar outra mesa ou aguardar a quitação e liberação da mesa.

#### A5 - Pedido alterado antes da confirmação

1. Antes do passo 12, o atendente altera quantidade, personalização ou remove um item.
2. O sistema recalcula os valores.
3. O fluxo retorna ao passo 10.

#### A6 - Cancelamento da montagem

1. Antes da confirmação, o atendente descarta o pedido.
2. O sistema encerra a montagem sem registrar venda, pagamento ou movimentação de estoque.

#### A7 - Falha de impressão

1. No passo 19, a impressora não responde.
2. O sistema mantém o pedido digital já registrado e informa a falha.
3. O atendente pode solicitar nova impressão sem duplicar o pedido ou a baixa de estoque.

#### A8 - Falha ao enviar para a cozinha

1. No passo 17, o pedido não pode ser disponibilizado no terminal da cozinha.
2. O sistema mantém o pedido registrado, sinaliza a pendência e permite nova tentativa.
3. A nova tentativa não pode criar outro pedido nem repetir a baixa de estoque.

### Regras de negócio relacionadas

RN-001, RN-002, RN-004 a RN-010, RN-011, RN-013, RN-015 a RN-020, RN-024, RN-029 a RN-033, RN-036, RN-037, RN-066 a RN-071A.

### Requisitos relacionados

RF-012, RF-016, RF-018, RF-020 a RF-034, RF-041, RF-042, RF-052, RF-118 a RF-125; RNF-001, RNF-002, RNF-011, RNF-017, RNF-019 e RNF-023 a RNF-028.

---

## UC-02 - Registrar ajuste de estoque

### Objetivo

Corrigir o saldo de um item de estoque a partir de uma contagem ou divergência identificada, preservando o histórico da movimentação e a responsabilidade pela alteração.

### Atores

- **Ator principal:** Administrador ou usuário com permissão específica para ajuste de estoque.

### Gatilho

O usuário identifica que o saldo físico de um insumo difere do saldo registrado no sistema.

### Pré-condições

1. O usuário está autenticado e possui permissão para realizar ajustes manuais.
2. O item de estoque está cadastrado e ativo.
3. O item possui unidade de medida definida.

### Pós-condições de sucesso

1. O saldo do item passa a corresponder ao novo saldo informado.
2. A diferença entre o saldo anterior e o novo saldo é registrada como movimentação de ajuste.
3. A justificativa, o usuário, a data e o horário permanecem no histórico e na auditoria.
4. As movimentações anteriores são preservadas.
5. Se o saldo resultante atingir o estoque mínimo, um alerta de reposição é gerado ou mantido ativo.

### Fluxo principal

1. O administrador acessa o módulo de estoque.
2. O sistema apresenta os itens cadastrados, seus saldos, unidades e indicadores de estoque mínimo.
3. O administrador seleciona o item que precisa ser corrigido.
4. O sistema apresenta o saldo atual e o histórico de movimentações do item.
5. O administrador escolhe a operação `Ajuste`.
6. O sistema solicita o novo saldo físico contado e uma justificativa obrigatória.
7. O administrador informa o novo saldo e descreve o motivo da correção.
8. O sistema valida a permissão, o valor informado e a presença da justificativa.
9. O sistema calcula a diferença entre o novo saldo e o saldo anterior.
10. O administrador confirma o ajuste.
11. O sistema registra uma movimentação do tipo `Ajuste`, contendo saldo anterior, diferença, saldo resultante, justificativa, usuário, data e horário.
12. O sistema atualiza o saldo do item sem excluir ou reescrever movimentações anteriores.
13. O sistema registra a operação no histórico de auditoria.
14. O sistema verifica o estoque mínimo e, quando necessário, gera um alerta de reposição.
15. O sistema confirma a conclusão do ajuste.

### Fluxos alternativos e exceções

#### A1 - Usuário sem permissão

1. No passo 1 ou no passo 8, o sistema identifica que o usuário não possui autorização para ajustar estoque.
2. O sistema bloqueia a operação e não modifica o saldo.

#### A2 - Justificativa não informada

1. No passo 8, a justificativa está vazia.
2. O sistema informa que a justificativa é obrigatória.
3. O fluxo retorna ao passo 7.

#### A3 - Valor inválido

1. No passo 8, o novo saldo não é numérico, utiliza unidade incompatível ou representa valor não permitido.
2. O sistema informa o problema e não registra a movimentação.
3. O fluxo retorna ao passo 7.

#### A4 - Nenhuma diferença encontrada

1. No passo 9, o novo saldo é igual ao saldo atual.
2. O sistema informa que não existe diferença a ajustar.
3. O administrador pode cancelar a operação ou revisar a contagem.

#### A5 - Saldo resultante no estoque mínimo

1. No passo 14, o saldo resultante é menor ou igual ao estoque mínimo.
2. O sistema conclui o ajuste normalmente e gera ou mantém o alerta de reposição.

#### A6 - Saldo alterado durante a operação

1. Antes do passo 11, outra movimentação modifica o saldo do item.
2. O sistema não utiliza silenciosamente o saldo antigo apresentado ao usuário.
3. O sistema atualiza o saldo de referência e solicita nova confirmação do ajuste.

### Regras de negócio relacionadas

RN-011, RN-014, RN-015, RN-061 a RN-065, RN-081 a RN-085, RN-095 e RN-096.

### Requisitos relacionados

RF-016, RF-019, RF-020, RF-108, RF-109, RF-112 a RF-117, RF-141 a RF-147, RF-167, RF-170 e RF-171; RNF-013, RNF-014, RNF-017, RNF-019 e RNF-041.

---

## UC-03 - Registrar pagamento

### Objetivo

Registrar o recebimento de um pedido presencial ou de uma conta de mesa/comanda, utilizando uma ou mais formas de pagamento, mantendo a situação financeira independente do estado de preparação.

### Atores

- **Ator principal:** Caixa.
- **Ator relacionado:** Atendente, que pode solicitar o fechamento da conta e encaminhar o cliente ao caixa.

### Gatilho

O cliente solicita o pagamento de um pedido de balcão ou de uma conta de mesa/comanda.

### Pré-condições

1. O Caixa está autenticado e possui permissão para registrar pagamentos.
2. O caixa do turno está aberto.
3. O pedido ou a conta existe, não está cancelado e possui saldo devido.
4. Para mesa/comanda, a conta foi previamente fechada para novos lançamentos e seu valor está consolidado.
5. O pedido não está identificado como integralmente pago pela plataforma externa.

### Pós-condições de sucesso

1. Cada parcela ou forma utilizada é registrada com valor, data, horário e operador.
2. Os recebimentos são associados ao caixa aberto.
3. Quando o saldo chega a zero, o pedido ou a conta passa para a situação `Pago`.
4. Pagamento parcial mantém a situação `Pendente` e preserva o saldo restante.
5. Uma conta de mesa integralmente quitada passa à situação `Quitada` e a mesa é liberada.
6. O pagamento não altera automaticamente o estado operacional do pedido.

### Fluxo principal

1. O Caixa acessa a função de registro de pagamento.
2. O sistema apresenta pedidos presenciais pendentes e contas de mesa fechadas aguardando pagamento.
3. O Caixa seleciona o pedido ou a conta.
4. O sistema apresenta o valor total, os pagamentos já registrados e o saldo devido.
5. O sistema verifica se o pedido não está pago e se não foi confirmado como pago por plataforma externa.
6. O Caixa seleciona a forma de pagamento: dinheiro, cartão ou Pix.
7. O Caixa informa o valor destinado à forma escolhida.
8. Se houver outra forma de pagamento, o Caixa adiciona uma nova parcela e repete os passos 6 e 7.
9. Para pagamento em dinheiro, o Caixa informa o valor recebido do cliente.
10. O sistema calcula o troco, quando houver.
11. O sistema valida os valores informados e apresenta o saldo restante.
12. O Caixa confirma o recebimento.
13. O sistema registra cada pagamento e o associa ao pedido ou à conta e ao caixa aberto.
14. O sistema atualiza o saldo devido.
15. Quando o saldo chega a zero, o sistema altera a situação financeira para `Pago`.
16. Para conta de mesa integralmente quitada, o sistema registra a quitação e libera a mesa.
17. O sistema mantém inalterado o estado operacional de preparação do pedido.
18. O sistema apresenta a confirmação do pagamento e o troco, quando aplicável.

### Fluxos alternativos e exceções

#### A1 - Pagamento misto

1. No passo 8, o cliente escolhe mais de uma forma de pagamento.
2. O sistema mantém todas as parcelas vinculadas ao mesmo pedido ou conta.
3. A soma das parcelas deve corresponder ao valor que será quitado na operação.
4. O fluxo prossegue no passo 9 ou no passo 11, conforme as formas selecionadas.

#### A2 - Pagamento parcial de mesa/comanda

1. No passo 11, o valor informado é menor que o saldo total da conta.
2. O sistema registra o pagamento e calcula o saldo restante.
3. A conta permanece com pagamento pendente e a mesa não é liberada.
4. Um novo pagamento pode ser registrado posteriormente para a mesma conta.

#### A3 - Divisão entre pessoas

1. Após o passo 4, o cliente solicita a divisão do valor entre pessoas.
2. O Caixa informa a quantidade de partes ou os valores individuais.
3. O sistema distribui o saldo, ajustando eventuais centavos sem modificar o total devido.
4. Cada parte pode utilizar uma forma de pagamento distinta.
5. O fluxo retorna ao passo 6 para registrar as parcelas.

#### A4 - Valor em dinheiro insuficiente

1. No passo 10, o valor recebido em dinheiro é menor que o valor atribuído àquela parcela.
2. O sistema informa que o valor é insuficiente e não permite a confirmação.
3. O fluxo retorna ao passo 9.

#### A5 - Soma incompatível

1. No passo 11, a soma informada excede o valor devido ou não corresponde ao valor que o Caixa pretende quitar.
2. O sistema apresenta a diferença e solicita correção.
3. O fluxo retorna ao passo 6.

#### A6 - Conta de mesa ainda aberta

1. No passo 3 ou no passo 5, o sistema identifica que a conta ainda permite novos lançamentos.
2. O sistema bloqueia o pagamento e orienta que a conta seja fechada antes do recebimento.
3. Nenhum pagamento é registrado nesse fluxo até a consolidação da conta.

#### A7 - Pedido pago pela plataforma

1. No passo 5, o pedido está identificado como pago pelo iFood ou pela 99Food.
2. O sistema informa que o pagamento já foi realizado externamente.
3. O sistema bloqueia nova cobrança e encerra o caso de uso sem alterar o caixa.

#### A8 - Caixa fechado

1. Na pré-condição ou no passo 13, o sistema identifica que não existe caixa aberto.
2. O sistema impede o recebimento e orienta a abertura do caixa.

#### A9 - Tentativa de pagamento duplicado

1. Antes da gravação, o sistema identifica que a mesma operação já foi registrada.
2. O sistema não cria novo pagamento e apresenta o registro existente para conferência.

#### A10 - Falha durante o registro

1. Ocorre uma falha antes da conclusão do passo 13.
2. O sistema não deve deixar parcelas, caixa e saldo do pedido em estados divergentes.
3. A operação é desfeita ou mantida como pendente para recuperação segura, sem cobrança duplicada.

### Regras de negócio relacionadas

RN-011, RN-015, RN-028A a RN-028D, RN-034, RN-035 a RN-035C e RN-053 a RN-060.

### Requisitos relacionados

RF-016, RF-020, RF-046 a RF-048, RF-090 a RF-107, RF-168 e RF-170; RNF-012, RNF-014, RNF-017, RNF-019 e RNF-041.

## Rastreabilidade com os demais artefatos

| Caso de uso | Diagrama de casos de uso | Diagrama de atividade atual | Protótipo |
|---|---|---|---|
| UC-01 - Registrar pedido | Registrar pedido; Personalizar item; Aplicar desconto; Enviar pedido para produção | Página `UC-01 - Registrar Pedido` | PDV, personalização, mesas e envio à cozinha |
| UC-02 - Registrar ajuste de estoque | Registrar ajuste de estoque | Página `UC-02 - Ajuste de Estoque` | Estoque, movimentação manual, justificativa, histórico e alerta |
| UC-03 - Registrar pagamento | Registrar pagamento; Combinar formas de pagamento; Dividir pagamento | Página `UC-03 - Registrar Pagamento` | Caixa, pagamento misto, divisão, troco e quitação de mesa |

> Para padronizar o vocabulário, recomenda-se renomear a página `UC-02 - Ajuste de Estoque` do diagrama de atividade para `UC-02 - Registrar ajuste de estoque`, igual ao caso de uso do diagrama geral e a este documento.
