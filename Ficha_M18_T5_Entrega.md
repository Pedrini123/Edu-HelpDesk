# ESCOLA SECUNDÁRIA DA BOA NOVA – LEÇA DA PALMEIRA
**Cursos Profissionais - Ano Letivo 2026/2027**  
**Curso Profissional Técnico de Gestão e Programação de Sistemas Informáticos**  
**Disciplina:** Programação e Sistemas de Informação – 12º Ano | **Turma:** I-24-27  
**Professor:** Cristina Paes Moreira  

---

# Tarefa nº 5 – Diagramas de casos de uso
## Parte A — Casos de uso do sistema de helpdesk (em equipa)

**Nome da equipa:** Equipa EduHelp  
**Elementos:** Pedro Fernandes e Rafael Silveira  

---

### Tabela de Entrega da Ficha

| Campo | Conteúdo |
| :--- | :--- |
| **Diagrama de casos de uso** | Ficheiro-fonte: **[`casos_uso_helpdesk.drawio`](./casos_uso_helpdesk.drawio)**<br>Imagem vetorial exportada: **[`casos_uso_helpdesk.svg`](./casos_uso_helpdesk.svg)**<br><br>*(Contém os 3 atores identificados na FT1: Utilizador comum, Técnico de TI e Administrador + Serviço de Email externo; fronteira do sistema Edu HelpDesk; 21 casos de uso com relações de associação, «include» e «extend»).* |
| **Caso de uso crítico 1 — identificação** | **Nome:** Submeter ticket de suporte<br>**Ator principal:** Utilizador (professor / aluno)<br>**Objetivo:** Reportar uma avaria num equipamento da escola (computador, projetor, teclado, rato, rede) ou problema na sala, para que seja intervencionado pelo suporte técnico sem interrupção das aulas. |
| **Pré-condições** | O utilizador possui conta ativa e sessão iniciada no sistema Edu HelpDesk (relação «include» com *Autenticar*). |
| **Fluxo principal** | **1.** O utilizador acede à opção «Submeter ticket de suporte».<br>**2.** O sistema apresenta o formulário de abertura de pedido com campos de sala/localização, categoria de equipamento, título e descrição.<br>**3.** O utilizador seleciona a sala e a categoria do equipamento afetado (ex.: Projetor, Computador, Rede).<br>**4.** O utilizador preenche o título resumido e a descrição detalhada da avaria observada.<br>**5.** O utilizador opcionalmente adiciona uma fotografia ou captura de ecrã demonstrativa do erro («extend» *Anexar ficheiro*).<br>**6.** O utilizador confirma clicando em «Submeter».<br>**7.** O sistema valida o preenchimento de todos os campos obrigatórios e a conformidade do anexo.<br>**8.** O sistema cria o ticket com o estado inicial «Não Atribuído» (Aberto), atribui um número sequencial único (#ID) e regista a data e hora do pedido.<br>**9.** O sistema apresenta uma notificação de sucesso no ecrã com o #ID gerado e disponibiliza o atalho para a página de acompanhamento do ticket. |
| **Fluxos alternativos e de exceção** | **FA1 — Sugestão de resolução imediata via FAQ:** No passo 3 ou 4, ao selecionar a categoria ou introduzir o título (ex.: *"Projetor sem sinal"*), o sistema apresenta no rodapé artigos relacionados da FAQ. O utilizador consulta a dica de auto-ajuda, verifica a ligação do cabo HDMI na parede, o equipamento volta a funcionar e o utilizador cancela a submissão, concluindo o processo sem gerar ticket desnecessário.<br><br>**FE1 — Campos obrigatórios em branco:** No passo 7, se a sala, categoria ou descrição estiverem em falta, o sistema não submete o formulário, preserva o texto já digitado e assinala a vermelho os campos que requerem preenchimento.<br><br>**FE2 — Ficheiro anexo com formato ou tamanho inválido:** No passo 7, se o anexo exceder o tamanho máximo permitido (ex.: 10 MB) ou formato não autorizado, o sistema alerta o utilizador com uma mensagem explicativa e permite substituir o ficheiro antes de concluir.<br><br>**FE3 — Duplicação de avaria na mesma sala:** No passo 3, caso já exista um ticket aberto com intervenção em curso para o mesmo equipamento na mesma sala (ex.: *"Projetor da Sala 14"*), o sistema avisa o utilizador. O utilizador pode optar por associar-se ao ticket existente para receber notificações em vez de criar duplicados. |
| **Pós-condições** | O ticket fica gravado na base de dados no estado «Não Atribuído», visível na área pessoal do utilizador (*Consultar e filtrar os meus tickets*) e na fila geral dos técnicos de TI (*Ver tickets abertos*). |

---

| Campo | Conteúdo |
| :--- | :--- |
| **Caso de uso crítico 2 — identificação** | **Nome:** Alterar estado do ticket<br>**Ator principal:** Técnico de TI (gestor de equipamentos)<br>**Objetivo:** Atualizar o ciclo de vida operacional do pedido de suporte (Não Atribuído $\rightarrow$ Em Resolução $\rightarrow$ Resolvido / Em Espera) e registar a intervenção efetuada no equipamento. |
| **Pré-condições** | O técnico possui perfil com privilégios de suporte de TI, sessão iniciada no sistema e o ticket selecionado encontra-se acessível para edição. |
| **Fluxo principal** | **1.** O técnico consulta a lista de tickets pendentes através da opção *Ver tickets abertos*.<br>**2.** O técnico seleciona o ticket pretendido e assume a responsabilidade pelo atendimento.<br>**3.** O técnico ajusta a prioridade do pedido caso necessário (*Definir prioridade do ticket*).<br>**4.** O técnico altera o estado do ticket para «Em Resolução».<br>**5.** O técnico desloca-se à sala, diagnostica o equipamento e executa os procedimentos de reparação/configuração.<br>**6.** O técnico introduz no histórico do ticket as notas técnicas da intervenção (podendo usar modelos via «extend» *Usar resposta pré-definida*).<br>**7.** O técnico seleciona a opção de alteração de estado para «Resolvido» e confirma.<br>**8.** O sistema regista a data/hora da conclusão, calcula o tempo de resposta e guarda o novo estado na base de dados.<br>**9.** O sistema aciona automaticamente a notificação («include» *Enviar notificação por email*) comunicando ao utilizador que o equipamento está reparado e solicitando a respetiva avaliação de suporte. |
| **Fluxos alternativos e de exceção** | **FA1 — Avaria requer esclarecimentos ou confirmação do utilizador:** No passo 5, caso a avaria seja intermitente e o técnico não consiga reproduzir o erro, altera o estado para «Em Espera», adiciona uma mensagem explicativa solicitando mais pormenores («extend» *Comentar ticket*). O ticket aguarda a resposta do utilizador antes de prosseguir.<br><br>**FA2 — Necessidade de peça de substituição / equipamento fora de serviço:** No passo 5, verificando-se que a lâmpada do projetor ou periférico está inoperacional e necessita de substituição de stock, o técnico coloca o ticket no estado «Em Espera (Peça)», regista o motivo nas notas e notifica o Administrador para autorização de material.<br><br>**FA3 — Reencaminhamento para colega especializado:** No passo 2 ou 5, se o problema for de infraestrutura de rede central em vez de avaria física local, o técnico aciona o caso de uso *Reencaminhar ticket*, escolhe o técnico especialista da área e transfere a responsabilidade com uma nota justificativa.<br><br>**FE1 — Reabertura por persistência do problema pelo utilizador:** Após o passo 9, se o professor/aluno voltar à sala e constatar que a avaria continua ativa, pode acionar o caso de uso *Reabrir ticket resolvido*. O sistema reverte o estado do ticket para «Em Resolução» e notifica com prioridade o técnico com o comentário de reabertura. |
| **Pós-condições** | O ticket transita para o estado «Resolvido», o histórico de auditoria fica completo com as intervenções registadas e o utilizador é convidado a avaliar o serviço de 1 a 5 estrelas (*Avaliar o suporte*). |

---

### Resumo dos Critérios de Aceitação da Tarefa 5:

- [x] **Atores da FT1:** Todos os atores identificados na Ficha 1 constam do diagrama (`Utilizador comum: professores/alunos`, `Técnico de TI: gestor de equipamentos` e `Administrador: gestor de salas`, além do ator secundário `Serviço de email`).
- [x] **Relações UML:** Fronteira do sistema bem delimitada, casos de uso no infinitivo, relações simples entre atores e casos de uso, setas tracejadas `«include»` no sentido correto (do caso base para o incluído) e `«extend»` com pontos de extensão pertinentes.
- [x] **Fluxos alternativos:** Descritos de forma detalhada e não trivial (inclui sugestão pela FAQ, duplicação na mesma sala, reencaminhamento, estado em espera e reabertura de tickets).
- [x] **Ficheiros no repositório:** Ficheiro-fonte `.drawio` e imagem vetorial `.svg` disponibilizados e prontos para submissão no GitHub e Google Classroom.
