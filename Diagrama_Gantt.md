# 📅 Diagrama de Gantt — Edu HelpDesk

**Equipa EduHelp:** Pedro Fernandes e Rafael Silveira
**Disciplina:** Programação e Sistemas de Informação — 12.º Ano (Turma I-24-27)
**Ano letivo:** 2026/2027

O planeamento está dividido em 5 fases. As fases de **Análise** e **Modelação** correspondem às Tarefas 1 a 6 já entregues. O **Desenvolvimento** está organizado em *sprints* de 2 semanas, seguindo a prioridade MoSCoW do [Backlog Priorizado (Tarefa 4)](./Informações/Ficha%20M18-T4-Backlog%20priorizado.pdf): primeiro as *Must*, depois as *Should* e no fim as *Could*.

```mermaid
gantt
    title Edu HelpDesk — Planeamento do Projeto
    dateFormat  YYYY-MM-DD
    axisFormat  %d/%m

    section 1. Análise e Planeamento
    T1 - Visão do produto                 :done,    t1, 2026-09-21, 7d
    T2 - Contrato de equipa e processo    :done,    t2, after t1, 7d
    T3 - Registo de requisitos            :done,    t3, after t2, 8d
    T4 - Backlog priorizado               :done,    t4, 2026-10-12, 3d

    section 2. Modelação (UML / E-R)
    T5 - Diagrama de casos de uso         :done,    t5, 2026-10-15, 7d
    T6 - Diagramas de classes e atividades:done,    t6, 2026-10-21, 9d
    Modelo E-R da base de dados           :done,    er, 2026-10-21, 9d
    Diagrama de Gantt                     :active,  gantt, 2026-11-02, 5d

    section 3. Preparação
    Protótipo das interfaces (mockups)    :         ui, 2026-11-09, 10d
    Configurar ambiente e base de dados   :         env, 2026-11-16, 5d

    section 4. Desenvolvimento
    Sprint 1 - US01 Submeter ticket, US02 Lista, US03 Estado (Must)        :s1, 2026-11-23, 12d
    Sprint 2 - US04 Comentários/anexos, US05 Email, US06 Prioridade (Must) :s2, after s1, 12d
    Férias de Natal                                                        :crit, natal, 2026-12-19, 2027-01-04
    Sprint 3 - US07 Filtrar, US08 Recuperar password, US09 Contas (Must)   :s3, 2027-01-04, 12d
    Sprint 4 - US10 Reencaminhar, US11 Avaliar, US12 Pesquisar (Should)    :s4, after s3, 14d
    Sprint 5 - US13 FAQ, US14 Relatórios (Should)                          :s5, after s4, 14d
    Sprint 6 - US15 Templates, US16 Exportar CSV (Could)                   :s6, after s5, 14d

    section 5. Testes e Entrega
    Testes e correção de erros            :         test, after s6, 10d
    Documentação e manual de utilizador   :         doc, after s6, 12d
    Apresentação final do projeto         :milestone, apres, after doc, 0d
```

## Resumo das fases

| Fase | Período | Conteúdo | Estado |
| :--- | :--- | :--- | :--- |
| 1. Análise e Planeamento | 21/09 – 15/10/2026 | Tarefas 1 a 4 | ✅ Concluído |
| 2. Modelação | 15/10 – 06/11/2026 | Tarefas 5 e 6, E-R, Gantt | 🔄 A terminar |
| 3. Preparação | 09/11 – 20/11/2026 | Mockups, ambiente, base de dados | ⏳ Por fazer |
| 4. Desenvolvimento | 23/11/2026 – 26/02/2027 | 6 sprints com as 16 user stories | ⏳ Por fazer |
| 5. Testes e Entrega | 01/03 – 16/03/2027 | Testes, documentação, apresentação | ⏳ Por fazer |

## Distribuição das user stories por sprint

| Sprint | User Stories | MoSCoW | Esforço (pontos) |
| :--- | :--- | :--- | :---: |
| Sprint 1 | US01, US02, US03 | Must | 8 |
| Sprint 2 | US04, US05, US06 | Must | 8 |
| Sprint 3 | US07, US08, US09 | Must | 10 |
| Sprint 4 | US10, US11, US12 | Should | 7 |
| Sprint 5 | US13, US14 | Should | 8 |
| Sprint 6 | US15, US16 | Could | 4 |
| **Total** | **16 user stories** | | **45** |

> As datas das fases futuras são uma estimativa e podem ser ajustadas ao calendário escolar.
