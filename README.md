# Sistema de Gestão para Pit Dogs

Projeto acadêmico desenvolvido na disciplina de Engenharia de Software I do curso de Sistemas de Informação do Instituto Federal de Goiás, Câmpus Goiânia.

O projeto especifica e demonstra um sistema web para integrar a operação de um pit dog. A solução cobre o ciclo completo do pedido, desde o atendimento e o envio para a cozinha até o pagamento, a movimentação de estoque e a geração de informações gerenciais.

O estabelecimento Jão Burguer foi utilizado como referência para o levantamento do domínio. A visita técnica e a entrevista realizadas pela equipe ajudaram a confirmar problemas relacionados a controles manuais, concentração de atividades e dependência dos sistemas utilizados na operação.

## Escopo

### Dentro do escopo

- Autenticação de usuários e controle de permissões por perfil
- Registro e acompanhamento de pedidos de balcão e mesa ou comanda
- Personalização de produtos, adicionais, remoções e observações
- Acompanhamento da produção por painel de cozinha KDS
- Fechamento do consumo de mesas e comandas
- Pagamentos simples, mistos e parciais
- Abertura, movimentação e fechamento de caixa
- Controle de estoque e baixa de insumos por ficha técnica
- Compras, fornecedores, inventário, perdas e consumo interno
- Planejamento de produção e tirada de demanda
- Pedidos externos recebidos do iFood e da 99Food
- Relatórios de vendas, estoque e desempenho operacional
- Auditoria de operações críticas

### Fora do escopo

- Entrega própria, cadastro de endereço, roteirização e gestão de entregadores
- Cardápio online próprio para pedidos realizados diretamente pelo cliente
- Emissão de documentos fiscais
- Operação de múltiplas unidades ou filiais
- Implantação de uma versão de produção com servidor e banco de dados persistente

O delivery contemplado no projeto corresponde apenas à integração conceitual com iFood e 99Food. A logística e a entrega continuam sob responsabilidade dessas plataformas.

## Processo de desenvolvimento

O trabalho foi organizado em milestones que representam requisitos e escopo, modelagem funcional, modelagem comportamental e estrutural, prototipação, relatório e apresentação. A sequência foi inspirada no modelo cascata utilizado na disciplina, com revisões e refinamentos entre as etapas quando foram identificadas divergências entre os artefatos.

As issues e seus critérios de aceite foram utilizadas para organizar as entregas. A integração final incluiu revisão de vocabulário, regras de negócio, permissões, rastreabilidade e correspondência entre os casos de uso críticos, seus diagramas de atividades, diagramas de sequência e o protótipo.

## Casos de uso críticos

Foram selecionados três casos de uso para detalhamento:

1. **UC-01 Registrar pedido** — conecta atendimento, produtos, personalizações, preços, cozinha e consumo de estoque.
2. **UC-02 Registrar ajuste de estoque** — envolve autorização, justificativa, histórico, auditoria e estoque mínimo.
3. **UC-03 Registrar pagamento** — reúne pagamento simples, misto e parcial, troco, caixa e quitação de mesas.

Cada caso crítico possui descrição textual, diagrama de atividade e diagrama de sequência correspondente.

## Estrutura do repositório

```text
docs/
  Relatório-visita-J-Burguers.pdf
  casos-de-uso.md
  melhorias-visita-tecnica.md
  regras_de_negocio.md
  requisitos_funcionais_e_nao_funcionais.md

diagramas/
  DER.drawio
  diagrama_casos_uso.drawio
  diagrama_classes.drawio
  diagramas_atividades_01.drawio
  diagramas_atividades_02.drawio
  diagramas_atividades_03.drawio
  sequencia_registrar_pedido.drawio
  sequencia_ajustar_estoque.drawio
  sequencia_registrar_pagamento.drawio
  matriz_rastreabilidade.md

prototipo/
  index.html
```

Os arquivos `.drawio` são as fontes editáveis dos diagramas. Quando necessário, eles podem ser exportados para PDF ou PNG para uso no relatório, na apresentação ou em ferramentas como o NotebookLM.

## Artefatos

| Artefato | Arquivo | Situação |
| :--- | :--- | :---: |
| Requisitos funcionais e não funcionais | `docs/requisitos_funcionais_e_nao_funcionais.md` | Concluído |
| Regras de negócio | `docs/regras_de_negocio.md` | Concluído |
| Relatório da visita técnica | `docs/Relatório-visita-J-Burguers.pdf` | Concluído |
| Melhorias identificadas na visita | `docs/melhorias-visita-tecnica.md` | Concluído |
| Descrição dos casos de uso críticos | `docs/casos-de-uso.md` | Concluído |
| Diagrama geral de casos de uso | `diagramas/diagrama_casos_uso.drawio` | Concluído |
| Diagramas de atividades dos casos críticos | `diagramas/diagramas_atividades_01.drawio` a `03.drawio` | Concluído |
| Diagramas de sequência dos casos críticos | `diagramas/sequencia_*.drawio` | Concluído |
| Diagrama entidade relacionamento | `diagramas/DER.drawio` | Concluído |
| Diagrama de classes | `diagramas/diagrama_classes.drawio` | Concluído |
| Matriz de rastreabilidade | `diagramas/matriz_rastreabilidade.md` | Concluído |
| Protótipo navegável | `prototipo/index.html` | Concluído |
| Relatório técnico final | Documento em elaboração | Em elaboração |

## Protótipo

O protótipo é uma aplicação web de página única, navegável e parcialmente funcional. Ele utiliza dados fictícios mantidos durante a execução no navegador e não depende de instalação, servidor ou banco de dados.

Para executar:

1. Abra `prototipo/index.html` em um navegador atual.
2. Escolha um dos usuários apresentados na tela inicial.
3. Digite qualquer PIN com quatro números.

Os perfis disponíveis são Atendente, Cozinha, Caixa e Administrador. Cada perfil apresenta apenas os módulos e ações associados às suas responsabilidades.

## Decisões principais do domínio

- Fechar a conta de uma mesa significa encerrar o consumo, impedir novos lançamentos e consolidar o valor devido.
- Registrar pagamento é uma operação posterior, realizada pelo Caixa.
- A mesa somente volta ao estado livre após a quitação integral da conta.
- O estado operacional do pedido e sua situação financeira são controlados separadamente.
- Uma venda deve produzir no máximo uma baixa de estoque, considerando sua ficha técnica e as personalizações realizadas.
- Pedidos pagos pelo iFood ou pela 99Food não podem ser cobrados novamente no caixa.
- A cozinha encerra sua participação ao marcar a produção como pronta; a entrega ou retirada é registrada no fluxo de atendimento.

## Equipe

| Integrante | Responsabilidade principal |
| :--- | :--- |
| Esdras | Liderança técnica, integração dos artefatos, rastreabilidade e protótipo |
| Erick | Visita técnica, entrevista e levantamento do contexto operacional |
| João Victor | Diagramas de sequência |
| Jordana | Diagrama de casos de uso |
| Raphaela Raika | Requisitos, regras de negócio, DER e diagrama de classes |
| Vinícius | Revisões e apresentação |
| Wesly | Diagramas de atividades |

## Estado atual

Os artefatos centrais de requisitos, modelagem e prototipação estão concluídos. Os diagramas de atividades foram revisados e separados em três arquivos independentes, cada um com uma única página e correspondência direta com um caso de uso crítico. O relatório técnico e a apresentação constituem a etapa final do trabalho.
