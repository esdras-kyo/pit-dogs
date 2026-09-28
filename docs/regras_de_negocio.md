# Regras de Negócio

## 1. Produtos, adicionais e preços

RN-001 - Somente produtos ativos e disponíveis podem ser incluídos em novos pedidos.

RN-002 - Um produto marcado como temporariamente indisponível deve permanecer cadastrado, mas não pode ser vendido enquanto durar a indisponibilidade.

RN-003 - Todo produto vendido deve pertencer a uma categoria cadastrada.

RN-004 - Adicionais classificados como obrigatórios devem respeitar a quantidade mínima definida antes da confirmação do item.

RN-005 - A quantidade de adicionais selecionados não pode ultrapassar o limite máximo definido para o grupo.

RN-006 - Adicionais com preço devem compor o valor final do item.

RN-007 - A retirada de ingrediente somente pode ser realizada quando o produto permitir essa personalização.

RN-008 - Combos devem respeitar a composição e as opções definidas em seu cadastro.

RN-009 - O preço utilizado em uma venda deve ser o preço vigente no momento em que o item foi incluído no pedido.

RN-010 - Alterações posteriores de preço não podem modificar o valor de pedidos já registrados.

## 2. Usuários e permissões

RN-011 - Toda operação realizada por usuário identificado deve respeitar as permissões atribuídas ao seu perfil.

RN-012 - Cancelamentos somente podem ser realizados por usuários com permissão para essa operação.

RN-013 - Descontos somente podem ser concedidos por usuários autorizados.

RN-014 - Ajustes manuais de estoque somente podem ser realizados por usuários autorizados.

RN-015 - Operações críticas devem permanecer associadas ao usuário que as realizou.

## 3. Pedidos

RN-016 - Todo pedido deve possuir um identificador único no sistema.

RN-017 - Todo pedido deve possuir uma única origem principal: balcão, mesa/comanda, iFood ou 99Food.

RN-018 - Itens de um pedido podem ser alterados ou excluídos enquanto o pedido estiver aberto e ainda permitir edição.

RN-019 - O valor total do pedido deve corresponder à soma dos itens, adicionais, descontos e demais valores aplicáveis ao pedido.

RN-020 - Todo pedido deve registrar a data e o horário de sua criação.

RN-021 - Todo cancelamento de pedido deve possuir um motivo informado.

RN-022 - O cancelamento de um pedido não pode apagar seu histórico nem as operações já registradas.

RN-023 - Um pedido cancelado não deve ser considerado como venda concluída nos indicadores de faturamento.

RN-024 - Alterações de status do pedido devem permanecer registradas com data e horário.

RN-025 - O fluxo operacional padrão do pedido deve seguir os estados Recebido, Em preparação, Pronto e Finalizado.

RN-026 - Cancelado é um estado de encerramento alternativo do pedido e deve permanecer distinguível de Finalizado.

RN-027 - Um pedido não pode ser marcado como Pronto antes de ter sido colocado Em preparação.

RN-028 - Um pedido não pode ser Finalizado antes de estar Pronto, exceto quando o fluxo específico de balcão definido pela operação não exigir etapa de preparação.

RN-028A - Para pedidos de mesa ou comanda, o estado Pronto representa a conclusão da produção, mas não implica o encerramento da conta.

RN-028B - Pedidos vinculados a mesa ou comanda somente podem ser encerrados financeiramente após a quitação integral do valor devido.

RN-028C - Para pedidos de balcão ou retirada, o pagamento pode ocorrer antes ou depois da preparação, conforme o fluxo de atendimento adotado pelo estabelecimento.

RN-028D - A situação operacional do pedido e sua situação de pagamento devem ser controladas independentemente.

## 4. Mesas e comandas

RN-029 - Uma mesa livre pode ser aberta para iniciar consumo.

RN-030 - Uma mesa ocupada deve permanecer vinculada à conta aberta até seu fechamento.

RN-031 - Novos itens lançados em uma mesa ou comanda aberta devem compor a mesma conta até que sejam transferidos ou fechados.

RN-032 - A transferência de um item entre mesas ou comandas deve remover o item da origem e adicioná-lo ao destino, sem duplicar seu valor.

RN-033 - A emissão de pré-conta não encerra a mesa ou comanda.

RN-034 - A mesa somente deve voltar ao estado livre após o fechamento de sua conta.

RN-035 - A divisão de pagamento não altera o valor total devido pela mesa ou comanda.

RN-035A - Uma mesa ou comanda pode possuir um ou mais pedidos enquanto sua conta permanecer aberta.

RN-035B - O pagamento parcial de uma mesa ou comanda não encerra sua conta enquanto existir valor pendente.

RN-035C - O valor devido pela mesa ou comanda deve corresponder ao saldo dos pedidos e itens ainda não quitados associados à conta.

## 5. Cozinha e produção dos pedidos

RN-036 - Pedidos confirmados para produção devem ser disponibilizados para a cozinha.

RN-037 - A cozinha deve receber as personalizações do item, incluindo adicionais, remoções e observações registradas no pedido.

RN-038 - O tempo de preparo deve ser calculado a partir dos registros de entrada e mudança de status do pedido.

RN-039 - Pedidos que ultrapassarem o tempo esperado de preparo devem ser identificados como atrasados para fins operacionais.

RN-040 - A marcação de pedido como Pronto deve representar que a produção necessária para aquele pedido foi concluída.

RN-041 - A finalização operacional de pedidos de balcão ou retirada deve registrar o horário em que o pedido foi entregue ou retirado.

## 6. Delivery por iFood e 99Food

RN-042 - O sistema não realizará entrega própria; os únicos canais de delivery previstos no projeto são iFood e 99Food.

RN-043 - O endereço do cliente, a roteirização, o cálculo de distância e a gestão de entregadores não fazem parte da operação interna do sistema.

RN-044 - Todo pedido recebido de plataforma externa deve manter o identificador fornecido pela plataforma e a identificação de sua origem.

RN-045 - A combinação entre plataforma de origem e identificador externo deve ser única para impedir pedidos duplicados.

RN-046 - Um pedido externo já processado não pode ser criado novamente em razão de reenvio ou nova tentativa de integração.

RN-047 - Produtos recebidos de iFood ou 99Food devem possuir correspondência com produtos internos para que possam gerar movimentação correta de estoque.

RN-048 - Produto externo sem correspondência interna deve ser sinalizado e não pode gerar baixa automática de estoque até que o vínculo seja resolvido.

RN-049 - Adicionais e complementos recebidos das plataformas devem ser vinculados aos respectivos itens do pedido.

RN-050 - Cancelamentos recebidos das plataformas devem preservar o histórico do pedido e sua origem.

RN-051 - Falhas de integração podem ser reprocessadas, mas o reprocessamento não pode gerar duplicidade de pedido, pagamento ou movimentação de estoque.

RN-052 - A responsabilidade logística do sistema termina na preparação e disponibilização do pedido para coleta pela plataforma, quando aplicável.

## 7. Pagamentos e caixa

RN-053 - O valor total registrado como pagamento de um pedido deve corresponder ao valor devido, considerando todas as formas de pagamento utilizadas.

RN-054 - Um pedido pode utilizar mais de uma forma de pagamento, desde que a soma dos pagamentos corresponda ao valor devido.

RN-055 - Em pagamento em dinheiro, o troco deve corresponder à diferença entre o valor recebido e o valor devido.

RN-056 - Pedidos identificados como pagos pelo iFood ou 99Food não podem ser cobrados novamente no caixa do estabelecimento.

RN-056A - Um pedido presencial pode possuir pagamento pendente durante sua preparação ou consumo.

RN-056B - O registro integral do valor devido deve alterar a situação de pagamento do pedido ou conta para Pago.

RN-056C - Pagamentos parciais ou divididos devem permanecer associados ao mesmo pedido ou conta até que o valor devido seja integralmente quitado.

RN-056D - O fato de um pedido estar pago não altera automaticamente seu estado operacional de preparação.

RN-056E - O fato de um pedido estar Pronto não significa que ele esteja necessariamente pago.

RN-057 - Toda abertura de caixa deve estar vinculada a um operador responsável e a um valor inicial informado.

RN-058 - Sangrias e suprimentos devem compor a movimentação do caixa e permanecer registrados no histórico.

RN-059 - No fechamento, o valor esperado deve ser calculado separadamente por forma de pagamento.

RN-060 - Diferenças entre o valor esperado e o valor informado no fechamento devem ser apresentadas como sobra ou falta de caixa.

## 8. Estoque

RN-061 - Todo item controlado em estoque deve possuir unidade de medida definida.

RN-062 - O saldo de estoque deve resultar das entradas, saídas e ajustes registrados para o item.

RN-063 - Toda movimentação de estoque deve possuir origem identificável e permanecer registrada no histórico.

RN-064 - Ajustes manuais de estoque devem exigir justificativa.

RN-065 - O estoque mínimo deve ser utilizado como referência para alertas de reposição e sugestão de compra.

RN-066 - Uma mesma venda não pode gerar mais de uma baixa para o mesmo consumo previsto.

## 9. Ficha técnica e consumo teórico

RN-067 - Produtos que controlam consumo de ingredientes devem possuir ficha técnica com os respectivos insumos e quantidades.

RN-068 - A venda de um produto deve gerar consumo teórico conforme sua ficha técnica vigente no momento da venda.

RN-069 - Adicionais vinculados a itens de estoque devem acrescentar seu consumo ao consumo teórico do pedido.

RN-070 - A atualização de uma ficha técnica deve afetar vendas futuras e não deve reescrever o consumo histórico de vendas anteriores.

RN-071 - O custo estimado do produto deve ser calculado com base nos ingredientes e quantidades definidos em sua ficha técnica.

RN-071A - Quando uma personalização permitida do produto alterar o consumo de um ingrediente controlado em estoque, o consumo teórico deve considerar essa alteração.

## 10. Tirada de demanda

RN-072 - A necessidade de produção deve considerar o estoque disponível dos itens envolvidos.

RN-073 - Vendas anteriores podem ser utilizadas como referência para calcular a quantidade sugerida de produção.

RN-074 - A quantidade sugerida pela tirada de demanda pode ser ajustada manualmente pelo usuário responsável.

RN-075 - A lista de produção deve refletir a quantidade definida após eventual ajuste manual da sugestão.

RN-076 - A quantidade efetivamente produzida deve poder ser comparada à quantidade planejada para identificar diferenças de produção.

## 11. Compras e fornecedores

RN-077 - Compras devem estar associadas aos fornecedores correspondentes.

RN-078 - O recebimento de uma compra deve gerar entrada dos itens recebidos no estoque.

RN-079 - O preço de compra registrado deve permanecer disponível no histórico, mesmo após novas compras com preços diferentes.

RN-080 - A sugestão de compra deve considerar, no mínimo, o saldo atual e o estoque mínimo cadastrado.

## 12. Inventário

RN-081 - O inventário deve comparar o saldo teórico do sistema com a quantidade física informada pelo usuário.

RN-082 - A diferença de inventário deve corresponder à diferença entre a quantidade física e a quantidade teórica.

RN-083 - O encerramento do inventário somente deve gerar ajuste de estoque para diferenças aprovadas.

RN-084 - Ajustes decorrentes de inventário não devem apagar as movimentações anteriores do item.

RN-085 - Inventários concluídos devem permanecer disponíveis para consulta histórica.

## 13. Perdas e consumo interno

RN-086 - Toda perda deve possuir um motivo informado.

RN-087 - Uma perda registrada deve gerar saída correspondente do estoque.

RN-088 - Consumo interno deve ser registrado separadamente das vendas a clientes.

RN-089 - Perdas e consumo interno não devem ser contabilizados como faturamento de vendas.

## 14. Relatórios, indicadores e auditoria

RN-090 - Relatórios de vendas devem considerar como venda efetiva os pedidos concluídos conforme as regras de fechamento da operação.

RN-091 - Pedidos cancelados devem permanecer disponíveis em relatórios de cancelamento, mas não devem compor o faturamento líquido de vendas concluídas.

RN-092 - A origem do pedido deve permanecer disponível para permitir comparação entre balcão, mesa/comanda, iFood e 99Food.

RN-093 - O ticket médio deve ser calculado a partir do valor das vendas consideradas concluídas dividido pela quantidade correspondente de pedidos concluídos.

RN-094 - O tempo médio de preparo deve considerar os registros de tempo dos pedidos que passaram pelo fluxo de produção.

RN-095 - Alterações manuais de estoque, cancelamentos, sangrias e alterações de preço devem registrar usuário, data e horário.

RN-096 - Registros de auditoria devem preservar o histórico da operação e não devem ser substituídos por alterações posteriores nos cadastros.
