# Matriz de Rastreabilidade

Esta matriz relaciona as principais necessidades do negócio com os requisitos já definidos e com os casos de uso presentes no diagrama final de casos de uso

> **Observação:** os itens marcados como **A adicionar** são melhorias identificadas após a visita técnica e ainda não fazem parte do diagrama atual.

| Necessidade / objetivo | Requisitos relacionados | Caso(s) de uso no diagrama | Ator principal | Relação com outros artefatos |
|---|---|---|---|---|
| Controlar acesso ao sistema | RF-013–020; RN-011–015; RNF-015–019 | **Autenticar usuário (login/senha ou PIN)**; **Cadastrar usuários e definir perfis de acesso** | Atendente, Cozinha, Caixa, Administrador | Classes/DER: Usuário, Perfil; Protótipo: login e gestão de usuários |
| Registrar pedidos presenciais | RF-021–038; RN-016–028D | **Registrar pedido** | Atendente | Atividade/Sequência recomendada; DER: Pedido, ItemPedido, Produto |
| Personalizar itens do pedido | RF-025–028; RN-004–008; RN-071A | **Personalizar item (adicionais, remoções, obs.)** `<<extend>> Registrar pedido` | Atendente | DER: ItemPedido, Adicional, Ficha Técnica |
| Aplicar desconto | RF-018; RN-013 | **Aplicar desconto** `<<extend>> Registrar pedido` | Atendente autorizado | Auditoria e permissões |
| Consultar e cancelar pedidos | RF-035–038; RN-021–024 | **Consultar pedidos**; **Cancelar pedido** | Atendente | Histórico do pedido e auditoria |
| Encaminhar pedido para produção | RF-052; RN-036–041 | **Enviar pedido para produção**; **Produzir pedido** | Atendente / Cozinha | Atividade/Sequência de Registrar Pedido |
| Acompanhar preparo | RF-057–067; RN-036–041 | **Produzir pedido**; **Atualizar status do preparo (Em preparação ou Pronto)** | Cozinha | Status e tempos do pedido |
| Registrar entrega ou retirada | RF-068–071; RN-028A–028D; RN-041 | **Registrar entrega/retirada** | Atendente | Fluxo operacional do pedido |
| Controlar mesas e comandas | RF-039–048; RN-029–035C | **Gerenciar mesa/comanda (abrir, lançar, transferir, pré-conta)**; **Fechar conta da mesa** | Atendente | DER: Mesa/Comanda, Conta, Pedido |
| Dividir pagamento de mesa/comanda | RF-047; RN-035–035C | **Dividir pagamento** `<<extend>> Fechar conta da mesa` | Atendente / Caixa | Pagamentos e fechamento da conta |
| Registrar pagamentos | RF-090–097C; RN-053–056E | **Registrar pagamento** | Caixa | Atividade/Sequência recomendada; DER: Pagamento, FormaPagamento |
| Combinar formas de pagamento | RF-093; RN-054; RN-056C | **Combinar formas de pagamento** `<<extend>> Registrar pagamento` | Caixa | Pagamento misto |
| Abrir e movimentar caixa | RF-098–103; RN-057–058 | **Abrir caixa**; **Registrar sangria**; **Registrar suprimento** | Caixa | DER: Caixa, MovimentacaoCaixa |
| Fechar caixa | RF-104–107; RN-059–060 | **Fechar caixa** | Caixa | Atividade/Sequência recomendada; cálculo de sobra/falta |
| Receber pedidos de delivery | RF-072–083; RN-042–049 | **Receber pedido da plataforma** `<<include>> Registrar pedido` | app de delivery | Integração iFood/99Food; id externo e mapeamento de produtos |
| Atualizar/cancelar pedido externo | RF-084–087; RN-050–051 | **Atualizar status do pedido na plataforma**; **Receber cancelamento da plataforma** `<<include>> Cancelar pedido` | app de delivery | Integração e prevenção de duplicidade |
| Controlar estoque | RF-108–117; RN-061–066 | **Cadastrar item de estoque**; **Definir estoque mínimo**; **Consultar saldo e histórico de movimentações**; **Registrar ajuste de estoque** | Administrador | DER: ItemEstoque, MovimentacaoEstoque |
| Controlar consumo por ficha técnica | RF-118–125; RN-067–071A | **Criar / atualizar ficha técnica** | Administrador | DER: Produto, FichaTecnica, Ingrediente; baixa automática pós-venda |
| Registrar compras e fornecedores | RF-134–140; RN-077–080 | **Cadastrar fornecedor**; **Registrar compra**; **Gerar sugestão de compra** | Administrador | DER: Fornecedor, Compra, ItemCompra |
| Planejar produção | RF-126–133; RN-072–076 | **Tirar demanda (calcular necessidade de produção)** | Administrador | Estoque + histórico de vendas |
| Realizar inventário | RF-141–147; RN-081–085 | **Realizar inventário**; **Consultar histórico de inventários** | Administrador | DER: Inventario, ItemInventario, MovimentacaoEstoque |
| Registrar perdas e consumo interno | RF-148–152; RN-086–089 | **Registrar perda**; **Registrar consumo interno** | Administrador | Ambos incluem ajuste/movimentação de estoque |
| Gerar informações gerenciais | RF-153–165; RN-090–094 | **Gerar relatório de vendas**; **Gerar relatório de estoque** | Administrador | Protótipo de relatórios; dados de Pedido, Pagamento e Estoque |
| Consultar operações críticas | RF-166–171; RN-095–096 | **Consultar histórico de auditoria** | Administrador | DER/Classes: Auditoria/Log |
| Preservar operação durante falha de integração | RNF-005–009; RNF-032–035 | Relacionado a **Receber pedido da plataforma**, mas não exige novo UC | Sistema / app de delivery | **Reforçar RNF**: falha externa não deve interromper PDV, cozinha, caixa ou estoque |
| Usar impressão térmica no fluxo operacional | RNF-031 | **A adicionar:** impressão de pedido/comanda como comportamento de Registrar pedido / Gerenciar mesa-comanda | Atendente | **Novo RF sugerido**; Protótipo e componente de impressão |
| Configurar tempo esperado por modalidade/origem | RF-065–066; RN-039 | **A adicionar:** configuração associada ao preparo/pedidos | Administrador | **Novo RF/RN sugerido**; melhora a identificação de atraso |
| Identificar horários de maior movimento | RF-153–165 | **A adicionar:** consulta dentro de Gerar relatório de vendas | Administrador | **Novo RF sugerido**; relatório agrupado por faixa de horário |
| Suportar múltiplas filiais | — | **Evolução futura — fora do escopo atual** | Administrador | Impactaria quase todos os artefatos; não recomendado para esta versão |

## Observação sobre rastreabilidade

Nem todo requisito funcional precisa se transformar em um caso de uso separado. Vários RFs descrevem passos, validações ou comportamentos internos de um mesmo caso de uso. A matriz serve justamente para mostrar onde cada conjunto de requisitos é atendido sem inflar artificialmente o diagrama.
