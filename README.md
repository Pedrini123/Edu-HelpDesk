# Edu HelpDesk - Sistema de Gestão de Suporte Técnico

Projeto desenvolvido no âmbito do curso **Técnico de Gestão e Programação de Sistemas Informáticos (TGPSI)** — 12.º Ano, disciplina de **Programação e Sistemas de Informação (PSI / MADS)**.

---

## 📁 Ficheiros de Modelação (.drawio)

Conforme as instruções do **Guião de Diagramas no Draw.io** (para a **Tarefa 5** e **Tarefa 6**), todos os ficheiros-fonte editáveis encontram-se na raiz do repositório:

1. **[`casos_uso_helpdesk.drawio`](./casos_uso_helpdesk.drawio)** — **Tarefa 5: Diagrama de Casos de Uso (UML)**
   - **Atores:** Utilizador (Requisitante), Técnico de Suporte, Administrador e Servidor de Email (*sistema externo*).
   - **Fronteira do Sistema:** *Edu HelpDesk*.
   - **Relações:** Ligações de associação, setas tracejadas `«include»` (ex.: disparo automático de notificações por email ao criar ticket ou alterar estado) e `«extend»` (ex.: modelos de resposta pré-definidos).

2. **[`classes_helpdesk.drawio`](./classes_helpdesk.drawio)** — **Tarefa 6: Diagrama de Classes (UML)**
   - Classes estruturadas com os **3 compartimentos** (Nome, Atributos com visibilidade/tipos e Métodos).
   - **Herança / Generalização:** `Utilizador` (classe base) especializada em `Requisitante`, `Tecnico` e `Administrador`.
   - **Entidades de Domínio:** `Ticket`, `Categoria`, `Comentario`, `Anexo`, `Avaliacao`, `FAQ`, `TemplateResposta`, `NotificacaoEmail`.
   - **Enumerações:** `EnumEstadoTicket` (`ABERTO`, `EM_RESOLUCAO`, `RESOLVIDO`, `FECHADO`) e `EnumPrioridade` (`BAIXA`, `MEDIA`, `ALTA`).
   - **Multiplicidades explícitas:** `1`, `0..1`, `0..*` / `*` e relações de Composição (losango preenchido para Comentários e Anexos pertencentes ao Ticket).

3. **[`atividades_ticket.drawio`](./atividades_ticket.drawio)** — **Tarefa 6: Diagrama de Atividades (UML)**
   - Representação detalhada do **Ciclo de Vida do Ticket** (desde a abertura até à resolução e avaliação).
   - Organizado em **Raiais (Swimlanes)**: *Utilizador (Requisitante)*, *Sistema Edu HelpDesk* e *Técnico de Suporte*.
   - Elementos UML: Ponto de início, ações/atividades, nós de decisão (losangos com guardas `[Sim]`/`[Não]`), transições e ponto final.

4. **[`er_helpdesk.drawio`](./er_helpdesk.drawio)** — **Diagrama Entidade-Relacionamento (E-R)**
   - Modelo relacional da base de dados com tabelas, chaves primárias (`PK`), chaves estrangeiras (`FK`) e cardinalidades `1:N` / `1:1`.

---

## 📋 Mapeamento das User Stories (Backlog Priorizado - Tarefa 4)

| ID | User Story | Ator | Diagramas Onde Consta |
|---|---|---|---|
| **US01** | Submeter ticket de suporte | Utilizador | Casos de Uso, Classes, Atividades, E-R |
| **US02** | Ver lista de tickets abertos | Técnico | Casos de Uso, Classes, Atividades, E-R |
| **US03** | Mudar estado do ticket (Em Resolução, Resolvido) | Técnico | Casos de Uso, Classes, Atividades, E-R |
| **US04** | Adicionar comentários e ficheiros anexos | Utilizador / Técnico | Casos de Uso, Classes, Atividades, E-R |
| **US05** | Receber notificação por email ao atualizar ticket | Utilizador | Casos de Uso (`«include»`), Classes, Atividades |
| **US06** | Definir prioridade (Baixa, Média, Alta) | Técnico | Casos de Uso, Classes, Atividades, E-R |
| **US07** | Filtrar os tickets por estado | Utilizador | Casos de Uso, Classes |
| **US08** | Recuperar palavra-passe via email | Utilizador | Casos de Uso, Classes |
| **US09** | Gerir contas de utilizadores e técnicos | Administrador | Casos de Uso, Classes, E-R |
| **US10** | Reencaminhar ticket para outro colega | Técnico | Casos de Uso, Classes, Atividades |
| **US11** | Avaliar suporte após resolução (1 a 5 estrelas) | Utilizador | Casos de Uso, Classes, Atividades, E-R |
| **US12** | Pesquisar tickets por palavras-chave | Técnico | Casos de Uso, Classes |
| **US13** | Consultar Perguntas Frequentes (FAQ) | Utilizador | Casos de Uso, Classes, E-R |
| **US14** | Ver relatórios com tempos e desempenho | Administrador | Casos de Uso, Classes |
| **US15** | Usar respostas pré-definidas (templates) | Técnico | Casos de Uso (`«extend»`), Classes, Atividades, E-R |
| **US16** | Exportar lista de tickets para Excel/CSV | Administrador | Casos de Uso, Classes |

---

## 🛠️ Como Abrir e Editar no Draw.io / Diagrams.net

1. Aceder a **[https://app.diagrams.net/](https://app.diagrams.net/)** (já aberto no navegador).
2. No ecrã inicial:
   - Clicar em **"Open Existing Diagram"** (ou *Abrir Diagrama Existente*).
   - Escolher **"Device"** (Computador) e navegar até à pasta do projeto: `C:\Edu HelpDesk`.
   - Selecionar o ficheiro pretendido:
     - `casos_uso_helpdesk.drawio`
     - `classes_helpdesk.drawio`
     - `atividades_ticket.drawio`
     - `er_helpdesk.drawio`
3. Para exportar a imagem para o relatório/dossiê:
   - Menu **File** (Ficheiro) → **Export as** (Exportar como) → **PNG** (ou **SVG**).