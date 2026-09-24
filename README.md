# Sistema de Gerenciamento para Pit Dog

Projeto da disciplina de Engenharia de Software.

Sistema web para controle operacional e gerencial de lanchonetes de rua (pit dogs), cobrindo o ciclo do pedido, o caixa e o estoque. Hoje esses negócios trabalham com cardápio impresso, pedido verbal e anotação em papel, o que gera erro de pedido, perda de controle do caixa e falta de visibilidade sobre o que está acabando.

O objetivo da disciplina é aplicar o processo de engenharia de software: levantamento de requisitos, modelagem e projeto seguindo o modelo cascata, com prototipação na etapa de desenvolvimento.

## Escopo

**Dentro do escopo**

- Registro e acompanhamento de pedidos
- Pagamento e fechamento de caixa por turno
- Baixa automática de insumo por ficha técnica
- Cadastros de apoio e relatórios gerenciais

**Fora do escopo**

- Delivery e cardápio online para o cliente final
- Emissão de documento fiscal
- Operação com mais de uma unidade

## Organização sugerida do repositório

```
/docs          requisitos.md, glossario.md, regras-negocio.md,
               casos-de-uso.md, rastreabilidade.md
/diagramas     arquivos .drawio e os PNG exportados
/prototipo     telas exportadas e link da ferramenta
/relatorio     documento final
README.md      este arquivo
```

As pastas são criadas conforme os artefatos ficam prontos. Não crie pasta vazia.

## Como trabalhamos

As issues estão organizadas por milestone e cada uma traz um checklist de critérios de aceitação. Os artefatos nascem dessas issues.

Cada milestone tem uma issue de revisão cruzada, atribuída a quem não produziu o artefato. É nessas issues que a integração entre as etapas acontece. Ou seja, as entregas são revisadas por outros membros além do que fez o artefato.

`docs/glossario.md` define o nome oficial de cada termo do domínio. Requisitos, diagramas e telas usam esses nomes, sem sinônimos. Divergência de vocabulário entre artefatos é um erro que podemos evitar para manter coerência nas etapas.

Os três casos de uso críticos são os mesmos nos três artefatos. Descrição tabular, diagrama de atividades e diagrama de sequência tratam do mesmo trio de casos de uso.

Mudança de requisito depois do congelamento entra por issue nova, com justificativa.

## Convenções

Diagramas são commitados em dois formatos: `.drawio` para edição e `.png` para leitura. O PNG é o que entra no relatório e o que permite revisar o diagrama direto pelo navegador, sem baixar arquivo.

| Membro | Responsabilidade |
| :--- | :--- |
| Vinicius | Slides da apresentação |
| Jordana | Diagrama de casos de uso |
| Wesly | Diagramas de atividades |
| J. Victor | Diagramas de sequência |
| Raika | Requisitos, regras de negócio, DER e diagrama de classes |
| Esdras | Protótipo |
| Erick | Organização, dinâmica de apresentação e revisão final |

## Artefatos

| Artefato | Arquivo | Situação |
| :--- | :--- | :--- |
| Glossário | `docs/glossario.md` | a fazer |
| Requisitos funcionais e não funcionais | `docs/requisitos.md` | a fazer |
| Regras de negócio | `docs/regras-negocio.md` | a fazer |
| Diagrama de casos de uso | `diagramas/casos-de-uso.drawio` | a fazer |
| Descrição dos casos de uso | `docs/casos-de-uso.md` | a fazer |
| Diagramas de atividades | `diagramas/atividades-*.drawio` | a fazer |
| Diagramas de sequência | `diagramas/sequencia-*.drawio` | a fazer |
| Diagrama entidade-relacionamento | `diagramas/der.drawio` | a fazer |
| Diagrama de classes | `diagramas/classes.drawio` | a fazer |
| Protótipo | `prototipo/` | a fazer |
| Matriz de rastreabilidade | `docs/rastreabilidade.md` | a fazer |
| Relatório final | `relatorio/` | a fazer |

Atualize a situação ao fechar a issue correspondente.
