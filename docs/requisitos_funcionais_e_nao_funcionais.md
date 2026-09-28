# Requisitos Funcionais e Nao Funcionais

Sistema de Gestao para Pit Dog - Projeto Academico

Escopo: sistema inspirado na operacao de um pit dog, cobrindo atendimento, pedidos, cozinha, caixa, estoque, compras, demanda, inventario, relatorios e delivery exclusivamente por iFood e 99Food. Nao havera entrega propria; por isso o sistema nao contempla cadastro de endereco de entrega, roteirizacao ou gestao de entregadores.

## Requisitos Funcionais

### 1. Cadastro e configuracao do estabelecimento

RF-001 - O sistema deve permitir cadastrar os dados basicos do estabelecimento.

RF-002 - O sistema deve permitir configurar dias e horarios de funcionamento.

RF-003 - O sistema deve permitir cadastrar categorias de produtos, como sanduiches, bebidas, porcoes e adicionais.

RF-004 - O sistema deve permitir cadastrar produtos com nome, descricao, categoria, preco e status.

RF-005 - O sistema deve permitir ativar, desativar e marcar temporariamente produtos como indisponiveis.

RF-006 - O sistema deve permitir cadastrar adicionais e complementos.

RF-007 - O sistema deve permitir definir adicionais obrigatorios ou opcionais.

RF-008 - O sistema deve permitir definir quantidade minima e maxima de adicionais.

RF-009 - O sistema deve permitir definir preco adicional para complementos.

RF-010 - O sistema deve permitir cadastrar combos.

RF-011 - O sistema deve permitir alterar precos de produtos.

RF-012 - O sistema deve registrar em cada item do pedido o preco praticado no momento de sua inclusao, permitindo sua consulta posterior independentemente de alteracoes realizadas no cadastro do produto.

### 2. Usuarios e permissoes

RF-013 - O sistema deve permitir cadastrar usuarios.

RF-014 - O sistema deve permitir autenticacao por usuario e senha ou PIN.

RF-015 - O sistema deve possuir perfis de acesso, como atendente, caixa, cozinha e administrador.

RF-016 - O sistema deve restringir funcionalidades de acordo com o perfil do usuario.

RF-017 - O sistema deve permitir restringir cancelamentos de pedidos.

RF-018 - O sistema deve permitir restringir concessao de descontos.

RF-019 - O sistema deve permitir restringir ajustes manuais de estoque.

RF-020 - O sistema deve registrar o usuario responsavel por operacoes relevantes.

### 3. Frente de loja / PDV

RF-021 - O sistema deve permitir criar pedidos diretamente no balcao.

RF-022 - O sistema deve permitir selecionar produtos por categoria.

RF-023 - O sistema deve permitir pesquisar produtos.

RF-024 - O sistema deve permitir informar a quantidade de cada produto.

RF-025 - O sistema deve permitir adicionar complementos ao produto.

RF-026 - O sistema deve permitir remover ingredientes quando essa opcao estiver disponivel.

RF-027 - O sistema deve permitir inserir observacoes no item do pedido.

RF-028 - O sistema deve calcular automaticamente o valor do item considerando os adicionais.

RF-029 - O sistema deve calcular automaticamente o valor total do pedido.

RF-030 - O sistema deve permitir alterar itens enquanto o pedido estiver aberto.

RF-031 - O sistema deve permitir excluir itens antes da finalizacao.

RF-032 - O sistema deve gerar um identificador unico para cada pedido.

RF-033 - O sistema deve identificar a origem do pedido como balcao, mesa/comanda, iFood ou 99Food.

RF-034 - O sistema deve registrar data e horario da criacao do pedido.

RF-035 - O sistema deve permitir consultar pedidos em andamento.

RF-036 - O sistema deve permitir consultar pedidos concluidos.

RF-037 - O sistema deve permitir cancelar pedidos de acordo com as permissoes do usuario.

RF-038 - O sistema deve exigir um motivo para o cancelamento.

### 4. Mesas e comandas

RF-039 - O sistema deve permitir cadastrar mesas.

RF-040 - O sistema deve apresentar o status das mesas, diferenciando livres e ocupadas.

RF-041 - O sistema deve permitir abrir uma mesa ou comanda.

RF-042 - O sistema deve permitir adicionar novos itens a uma mesa ou comanda ja aberta.

RF-043 - O sistema deve apresentar todos os itens consumidos na mesa ou comanda.

RF-044 - O sistema deve permitir transferir itens entre mesas ou comandas.

RF-045 - O sistema deve permitir emitir pre-conta.

RF-046 - O sistema deve permitir fechar a conta da mesa ou comanda apos a quitacao do valor devido.

RF-047 - O sistema deve permitir dividir o pagamento da conta.

RF-048 - O sistema deve liberar a mesa apos o fechamento da conta.

### 5. Fluxo do pedido

RF-049 - O sistema deve permitir acompanhar e atualizar o status operacional de cada pedido.

RF-050 - O sistema deve apresentar os pedidos de acordo com os estados Recebido, Em preparacao, Pronto, Finalizado e Cancelado.

RF-051 - O sistema deve registrar data e horario de cada alteracao de status.

RF-052 - O sistema deve permitir enviar pedidos de balcao e mesa para a producao.

RF-053 - Pedidos recebidos de iFood e 99Food devem entrar no mesmo fluxo operacional dos demais pedidos.

RF-054 - O sistema deve manter registrada a origem externa do pedido.

RF-055 - O sistema deve impedir o cadastro duplicado do mesmo pedido externo.

RF-056 - O sistema deve manter historico das alteracoes realizadas no pedido.

### 6. Cozinha e producao

RF-057 - O sistema deve possuir uma tela de pedidos para a cozinha.

RF-058 - Novos pedidos confirmados devem aparecer automaticamente na tela da cozinha.

RF-059 - A cozinha deve visualizar o numero do pedido e sua origem.

RF-060 - A cozinha deve visualizar os produtos do pedido.

RF-061 - A cozinha deve visualizar adicionais, remocoes e observacoes.

RF-062 - O sistema deve apresentar o horario em que o pedido foi recebido.

RF-063 - O sistema deve permitir marcar o inicio do preparo.

RF-064 - O sistema deve permitir marcar o pedido como pronto.

RF-065 - O sistema deve indicar ha quanto tempo cada pedido esta aguardando.

RF-066 - O sistema deve destacar pedidos que ultrapassarem o tempo esperado de preparo.

RF-067 - O sistema deve registrar o tempo total de preparacao.

### 7. Retirada e expedicao

RF-068 - O sistema deve permitir identificar pedidos prontos.

RF-069 - O sistema deve apresentar o numero do pedido pronto para retirada.

RF-070 - O sistema deve permitir registrar a entrega ou retirada de pedidos de balcao e retirada, considerando as regras de pagamento aplicaveis ao pedido.

RF-071 - O sistema deve registrar o horario da retirada ou finalizacao operacional.

### 8. Delivery por iFood e 99Food

RF-072 - O sistema deve permitir receber pedidos originados no iFood.

RF-073 - O sistema deve permitir receber pedidos originados na 99Food.

RF-074 - O sistema deve identificar claramente de qual plataforma veio o pedido.

RF-075 - O sistema deve armazenar o identificador externo do pedido.

RF-076 - O sistema deve importar os produtos do pedido externo.

RF-077 - O sistema deve importar adicionais e complementos do pedido externo.

RF-078 - O sistema deve importar observacoes relacionadas aos itens quando fornecidas pela plataforma.

RF-079 - O sistema deve importar os valores do pedido.

RF-080 - O sistema deve identificar pedidos ja pagos pela plataforma.

RF-081 - O sistema deve permitir mapear produtos externos para produtos cadastrados internamente.

RF-082 - O sistema deve sinalizar produtos externos sem correspondencia interna cadastrada.

RF-083 - O sistema deve impedir que um produto sem correspondencia gere baixa incorreta de estoque.

RF-084 - O sistema deve registrar cancelamentos recebidos das plataformas quando disponibilizados pela integracao.

RF-085 - O sistema deve atualizar os estados do pedido que forem suportados pela integracao.

RF-086 - O sistema deve registrar falhas de integracao.

RF-087 - O sistema deve permitir reprocessar uma falha de integracao sem duplicar o pedido.

RF-088 - O sistema nao deve exigir cadastro de endereco de entrega, pois a logistica sera de responsabilidade das plataformas externas.

RF-089 - O sistema nao deve realizar roteirizacao, calculo de distancia ou gestao de entregadores proprios.

### 9. Pagamentos

RF-090 - O sistema deve permitir pagamento em dinheiro.

RF-091 - O sistema deve permitir pagamento por cartao.

RF-092 - O sistema deve permitir pagamento via Pix.

RF-093 - O sistema deve permitir utilizar mais de uma forma de pagamento no mesmo pedido.

RF-094 - O sistema deve calcular troco em pagamentos em dinheiro.

RF-095 - O sistema deve registrar a forma de pagamento utilizada.

RF-096 - O sistema deve identificar como pagos externamente os pedidos do iFood ou 99Food cujo pagamento tenha sido confirmado pela respectiva plataforma.

RF-097 - O sistema deve impedir cobranca duplicada de pedidos identificados como ja pagos externamente.

RF-097A - O sistema deve permitir registrar o pagamento de pedidos presenciais antes ou depois do preparo, de acordo com o tipo de atendimento adotado para o pedido.

RF-097B - O sistema deve permitir manter pedidos de mesa ou comanda com pagamento pendente enquanto a conta permanecer aberta.

RF-097C - O sistema deve apresentar a situacao de pagamento do pedido, diferenciando pelo menos Pendente e Pago.

### 10. Caixa

RF-098 - O sistema deve permitir abertura de caixa.

RF-099 - O sistema deve registrar o operador responsavel pelo caixa.

RF-100 - O sistema deve permitir informar o valor inicial do caixa.

RF-101 - O sistema deve registrar os recebimentos realizados no caixa.

RF-102 - O sistema deve permitir registrar sangrias.

RF-103 - O sistema deve permitir registrar suprimentos.

RF-104 - O sistema deve permitir fechamento de caixa.

RF-105 - O sistema deve calcular o valor esperado por forma de pagamento.

RF-106 - O sistema deve comparar o valor esperado com o valor informado no fechamento.

RF-107 - O sistema deve apresentar diferencas de caixa.

### 11. Estoque

RF-108 - O sistema deve permitir cadastrar itens de estoque.

RF-109 - O sistema deve armazenar a unidade de medida do item.

RF-110 - O sistema deve permitir registrar entradas de estoque.

RF-111 - O sistema deve permitir registrar saidas de estoque.

RF-112 - O sistema deve apresentar o saldo atual de cada item.

RF-113 - O sistema deve manter historico das movimentacoes de estoque.

RF-114 - O sistema deve permitir definir estoque minimo.

RF-115 - O sistema deve alertar quando um item atingir o estoque minimo.

RF-116 - O sistema deve permitir realizar ajustes manuais de estoque.

RF-117 - Ajustes manuais de estoque devem possuir justificativa.

### 12. Ficha tecnica e consumo teorico

RF-118 - O sistema deve permitir criar ficha tecnica para os produtos vendidos.

RF-119 - A ficha tecnica deve relacionar o produto aos ingredientes utilizados.

RF-120 - Cada ingrediente da ficha tecnica deve possuir quantidade definida.

RF-121 - O sistema deve utilizar a ficha tecnica para calcular o consumo teorico.

RF-122 - A venda de um produto deve gerar baixa dos ingredientes correspondentes.

RF-123 - Adicionais devem gerar consumo adicional quando possuirem itens de estoque associados.

RF-124 - O sistema deve calcular o custo estimado do produto com base na ficha tecnica.

RF-125 - O sistema deve permitir atualizar fichas tecnicas preservando o historico das vendas ja realizadas.

### 13. Tirada de demanda

RF-126 - O sistema deve calcular a necessidade de producao de itens.

RF-127 - O calculo deve considerar o estoque disponivel.

RF-128 - O sistema deve permitir utilizar vendas anteriores como referencia para a demanda.

RF-129 - O sistema deve apresentar os itens que precisam ser preparados.

RF-130 - O sistema deve apresentar as quantidades sugeridas para producao.

RF-131 - O sistema deve permitir ajuste manual da quantidade sugerida.

RF-132 - O sistema deve gerar uma lista de producao.

RF-133 - O sistema deve permitir comparar a quantidade planejada com a quantidade efetivamente produzida.

### 14. Compras e fornecedores

RF-134 - O sistema deve permitir cadastrar fornecedores.

RF-135 - O sistema deve permitir associar produtos aos fornecedores.

RF-136 - O sistema deve registrar compras.

RF-137 - O recebimento de uma compra deve gerar entrada no estoque.

RF-138 - O sistema deve armazenar o preco de compra.

RF-139 - O sistema deve manter historico dos precos de compra.

RF-140 - O sistema deve permitir gerar sugestao de compra considerando o estoque atual e o estoque minimo.

### 15. Inventario

RF-141 - O sistema deve permitir iniciar uma contagem de estoque.

RF-142 - O sistema deve apresentar o saldo teorico durante o processo de inventario.

RF-143 - O usuario deve poder informar a quantidade fisica encontrada.

RF-144 - O sistema deve calcular a diferenca entre estoque fisico e teorico.

RF-145 - O sistema deve permitir concluir o inventario.

RF-146 - O sistema deve gerar ajustes correspondentes as diferencas aprovadas.

RF-147 - O sistema deve manter historico dos inventarios realizados.

### 16. Perdas e consumo interno

RF-148 - O sistema deve permitir registrar perdas.

RF-149 - O usuario deve informar o motivo da perda.

RF-150 - Uma perda registrada deve gerar saida de estoque.

RF-151 - O sistema deve permitir registrar consumo interno.

RF-152 - O sistema deve permitir consultar perdas por periodo.

### 17. Relatorios e indicadores

RF-153 - O sistema deve apresentar relatorio de vendas por periodo.

RF-154 - O sistema deve apresentar vendas por produto.

RF-155 - O sistema deve apresentar vendas por categoria.

RF-156 - O sistema deve apresentar vendas por origem do pedido: balcao, mesa/comanda, iFood e 99Food.

RF-157 - O sistema deve apresentar as formas de pagamento utilizadas.

RF-158 - O sistema deve apresentar os produtos mais vendidos.

RF-159 - O sistema deve calcular o ticket medio.

RF-160 - O sistema deve apresentar a quantidade total de pedidos.

RF-161 - O sistema deve apresentar o tempo medio de preparo.

RF-162 - O sistema deve apresentar cancelamentos realizados.

RF-163 - O sistema deve apresentar perdas de estoque.

RF-164 - O sistema deve apresentar a posicao atual do estoque.

RF-165 - O sistema deve permitir comparar estoque fisico e estoque teorico.

### 18. Auditoria basica

RF-166 - O sistema deve registrar o usuario responsavel por cancelamentos.

RF-167 - O sistema deve registrar alteracoes manuais de estoque.

RF-168 - O sistema deve registrar sangrias.

RF-169 - O sistema deve registrar alteracoes de preco.

RF-170 - O sistema deve registrar data e horario das operacoes auditadas.

RF-171 - O administrador deve poder consultar o historico de auditoria.

## Requisitos Nao Funcionais

### 1. Desempenho

RNF-001 - As operacoes de inclusao, alteracao e remocao de itens no PDV devem apresentar resposta ao usuario em ate 2 segundos, em condicoes normais de operacao.

RNF-002 - Apos a confirmacao de um pedido, sua disponibilizacao para a cozinha deve ocorrer em ate 3 segundos, quando os componentes envolvidos estiverem disponiveis.

RNF-003 - Alteracoes de status dos pedidos devem ser refletidas nos demais terminais em ate 3 segundos, em condicoes normais de comunicacao.

RNF-004 - A geracao de relatorios nao deve impedir a realizacao de vendas.

### 2. Disponibilidade

RNF-005 - Falhas na integracao com iFood nao devem impedir vendas presenciais.

RNF-006 - Falhas na integracao com 99Food nao devem impedir vendas presenciais.

RNF-007 - A indisponibilidade de uma integracao externa nao deve interromper os demais modulos do sistema.

RNF-008 - O sistema deve informar ao usuario quando uma integracao estiver indisponivel.

RNF-009 - Falhas temporarias devem permitir nova tentativa de processamento.

### 3. Integridade dos dados

RNF-010 - O sistema nao deve registrar duas vezes o mesmo pedido externo.

RNF-011 - Uma venda nao deve produzir duas baixas de estoque.

RNF-012 - Um pagamento nao deve ser registrado duas vezes.

RNF-013 - Cada movimentacao de estoque deve possuir uma origem identificavel.

RNF-014 - Cancelamentos e ajustes nao devem apagar o historico anterior.

### 4. Seguranca

RNF-015 - O acesso ao sistema deve exigir autenticacao.

RNF-016 - Senhas nao devem ser armazenadas em texto puro.

RNF-017 - Funcionalidades devem respeitar as permissoes do usuario.

RNF-018 - Credenciais utilizadas nas integracoes externas devem ser protegidas.

RNF-019 - Operacoes criticas devem ser registradas para auditoria.

### 5. Privacidade

RNF-020 - O sistema deve armazenar apenas os dados pessoais necessarios a operacao.

RNF-021 - O sistema nao deve exigir cadastro de endereco residencial de clientes, pois a entrega sera gerenciada pelas plataformas.

RNF-022 - Dados pessoais eventualmente recebidos de integracoes nao devem ser exibidos a usuarios que nao necessitem deles.

### 6. Usabilidade

RNF-023 - A tela do PDV deve priorizar a visualizacao dos produtos, itens do pedido, valor total e acoes principais de atendimento sem exigir navegacao por modulos administrativos.

RNF-024 - As operacoes frequentes de selecao de produto, alteracao de quantidade e inclusao de adicionais devem poder ser realizadas diretamente durante a montagem do pedido, sem necessidade de sair da tela de atendimento.

RNF-025 - Botoes utilizados durante o atendimento devem ser adequados para telas sensiveis ao toque, quando aplicavel.

RNF-026 - A interface da cozinha deve exibir, sem necessidade de abrir telas adicionais, o identificador do pedido, seus itens, personalizacoes, origem, horario de recebimento e estado atual.

RNF-027 - Pedidos atrasados devem possuir destaque visual.

RNF-028 - Mensagens de erro devem ser compreensiveis para usuarios nao tecnicos.

### 7. Compatibilidade

RNF-029 - O sistema deve funcionar nos dispositivos definidos para o projeto.

RNF-030 - A interface administrativa deve funcionar nos principais navegadores atuais.

RNF-031 - O sistema deve suportar a impressora de pedidos definida para o prototipo, caso a impressao faca parte da implementacao.

### 8. Integracoes

RNF-032 - As integracoes externas devem possuir tratamento de falha e timeout.

RNF-033 - Uma nova tentativa de comunicacao nao deve criar um pedido duplicado.

RNF-034 - O sistema deve registrar erros das integracoes para diagnostico.

RNF-035 - A integracao com cada plataforma deve ser independente, de forma que falha em uma nao interrompa a outra.

### 9. Backup e recuperacao

RNF-036 - O sistema deve permitir realizar backup periodico dos dados.

RNF-037 - O sistema deve permitir restaurar os dados a partir de um backup valido.

RNF-038 - O processo de restauracao deve preservar vendas, movimentacoes de estoque e registros de caixa.

### 10. Manutenibilidade

RNF-039 - Os modulos de vendas, producao, estoque e integracoes devem possuir separacao logica.

RNF-040 - Alteracoes em uma integracao externa nao devem exigir reescrever todo o sistema.

RNF-041 - O banco de dados deve manter integridade entre pedidos, itens, pagamentos e movimentacoes de estoque.

RNF-042 - As principais regras de negocio devem ser passiveis de teste.

Total: 174 requisitos funcionais e 42 requisitos nao funcionais.
