# Etapa 2 — Operação

Proponha a partir da Etapa 1 e do estado atual; o usuário ajusta. Itens que já existem (mesmo nome, sem diferenciar maiúsculas; usuários pelo e-mail) aparecem como "já existe" e não são perguntados de novo.

## 1. Equipe e usuários
Para cada pessoa: nome, e-mail, função (que vira o papel). Pule e-mails que já estão em `list_users`. Avise: cada usuário novo recebe um convite por e-mail para criar a senha.

## 2. Papéis
Ofereça os modelos e deixe ajustar em linguagem natural ("atendente também vê relatórios"). Não altere o papel protegido (Administrador).

Montagem da matriz: copie as `permissions` de um papel de `list_roles` e ajuste. Toda seção tem `create/read/update/delete`; seção não listada abaixo = tudo `false`. Flags extras ficam `false` salvo indicação.

| Modelo | Seções (todas as ações) | Seções só leitura | Flags `true` |
|---|---|---|---|
| Supervisor | dashboard, inbox, contacts, queues, tags, quickReplies, tasks, events | queuesLive, reports, users | inbox.viewAllSessions, inbox.viewPrivateMessages, contacts.viewAllContacts, tasks.viewAllTasks |
| Atendente | dashboard, inbox, contacts, tasks, events | quickReplies, tags | — |
| Vendedor | dashboard, inbox, contacts, accounts, opportunities, tasks, events | quickReplies, tags | — |

Só ofereça Vendedor se Oportunidades for ligado. `accounts` só entra se Contas estiver ligada; `tasks` só se Tarefas estiver ligado; `events` só se Compromissos estiver ligado. Compromissos não tem permissão de ver todos: cada compromisso pertence a uma agenda do dono, e a pessoa só vê as agendas dela, as públicas e as compartilhadas com ela. Para gestores que precisam ver a agenda da equipe, a resposta é agenda pública (ou compartilhada), não permissão. Sem `tasks.viewAllTasks`, a pessoa vê só as tarefas dela (ou as ligadas a registros que ela vê) e não passa tarefas para outra pessoa. Se `create_role` responder `role_exceeds_caller`, remova o excesso ou peça para um Administrador rodar.

## 3. Funcionalidades
Uma por vez, com uma frase e uma recomendação:
- **Contas** — agrupar contatos por empresa cliente (B2B). Recomende se vende para empresas.
- **Oportunidades** — funil de vendas com etapas e valores. Funciona com ou sem Contas: sem Contas (B2C), cada oportunidade fica ligada a um contato. Recomende se há venda consultiva.
- **CX Score** — nota de experiência dada por IA a cada conversa finalizada. Recomende se quer medir qualidade.
- **Conversa interna** — chat entre atendentes dentro do agents2.me. Recomende se a equipe tem mais de 2 pessoas.
- **Tarefas** — pendências com vencimento, prioridade e lembrete (retornar ligação, enviar proposta, cobrar documento), com listas Minhas/Hoje/Vencidas/Concluídas e Kanban. Recomende se a equipe faz follow-up.
- **Compromissos** — agenda com calendário (dia, semana, mês), convidados, lembretes e repetição (diária, semanal, a cada 2 semanas, mensal). Cada compromisso tem Mostrar como (Ocupado fecha o horário: criar ou mover outro para cima dele pede confirmação; Disponível não) e tipo (normal, Fora do escritório, Tempo de foco). Recomende para quem marca reuniões, visitas ou consultas; para clínicas e consultórios, recomende sempre (sessões semanais viram uma série). Se a equipe usa o Google Agenda, explique que a conexão é **por pessoa**: cada usuário conecta a própria conta em Configurações → Aplicativos conectados → Google Agenda e escolhe as agendas a sincronizar; convidados e Meet só valem nessas agendas do Google.

Tarefas e Compromissos são independentes entre si e de Contas/Oportunidades.

Linha de recomendação: "Vende para pessoas com venda consultiva → Oportunidades ligado, Contas desligado."

## 4. Nomes das entidades
Pergunte se a equipe chama **Conta**, **Contato**, **Oportunidade**, **Tarefa** ou **Compromisso** de outro jeito e proponha a partir da Etapa 1 (ex.: clínica → Conta = Paciente, Oportunidade = Contrato, Compromisso = Sessão ou Consulta; escola → Conta = Aluno, Compromisso = Aula; vendas externas → Compromisso = Visita). Só pergunte pelas entidades ligadas no bloco 3; Contato sempre aparece. "Contato" aqui é o cadastro do CRM, não a pessoa que conversa no chat.
Para cada nome novo: **singular e plural**, até 40 caracteres, sem `{` `}`. Nome padrão é mantido — não grave nada para ele.
Idioma: o da empresa. Pergunte por en/es só se a equipe usa o agents2.me nesses idiomas.
Explique: "o nome muda para toda a empresa: menu, telas, relatórios e exportações". Daqui em diante, use os nomes escolhidos nas perguntas (ex.: "etapas do funil de Contratos").

## 5. Etapas do funil
Pergunte se a empresa acompanha o cliente por etapas (ex.: contato → orçamento → fechado). Se não, pule.
Pergunte: "o que acontece entre o primeiro contato e o fechamento?"

**Oportunidades ligado** — padrão do sistema: Prospecção (open, 10%), Qualificação (open, 25%), Proposta (open, 50%), Negociação (open, 75%), Ganha (won, 100%), Perdida (lost, 0%).
Proponha a lista ordenada com nome, categoria (`open`/`won`/`lost`) e probabilidade (%). Mantenha pelo menos uma `open`, uma `won` e uma `lost`. Marque cada etapa padrão como manter / renomear / remover.

**Oportunidades desligado** — o funil vira um campo de **contato** do tipo `combobox`, nome sugerido "Etapa do funil", com as etapas como `options` na ordem do processo (sem categoria nem probabilidade). Explique: "dá para ver os contatos em Kanban agrupados por esse campo". Grave junto com os campos customizados (bloco 9).

## 6. Filas
Setores ou assuntos (ex.: Vendas, Suporte, Financeiro); canais de cada fila; membros. Sugira a partir dos motivos de contato da Etapa 1.

## 7. Tags
Derive dos motivos de contato e do FAQ (ex.: Orçamento, Troca, Rastreio, Reclamação). Para cada: cor (hex) e quem usa (todos, ou uma lista).

## 8. Mensagens rápidas
Proponha: saudação, pedido de dados, horário de atendimento, encerramento e uma por FAQ importante. Para cada: atalho (`/saudacao`), tipo (`text`, `button`, `list`, `cta`, `payment`), texto. Use variáveis onde fizer sentido: `{{first_name}}`, `{{full_name}}`, `{{contact.<campo>}}`.

## 9. Campos customizados
O que a equipe precisa registrar sobre contatos (CPF, plano, cidade...). Tipo de cada um (texto, número, data, combobox com opções...). Se Contas estiver ligada, pergunte também pelos campos de conta; se Oportunidades estiver ligado, pelos campos de oportunidade; se Tarefas, pelos de tarefa (ex.: "Tipo de tarefa" combobox Ligação/Retorno/Documentação); se Compromissos, pelos de compromisso (ex.: "Link da reunião", "Motivo da consulta"). Cada entidade só se ligada. Não proponha campos que já são nativos: tarefa já tem vencimento, prioridade, lembrete e contato/conta/oportunidade; compromisso já tem início/fim, dia inteiro, local, mostrar como (Ocupado fecha o horário e avisa em caso de sobreposição; Disponível só reserva), tipo (normal, Fora do escritório ou Tempo de foco — estes dois sempre Ocupados e sem convidados nem Meet), convidados, status (agendado, realizado, cancelado, não compareceu), lembrete e repetição. Não proponha campo customizado para disponibilidade/ocupação nem para tipo de evento.

## Fora do escopo
Campanhas, listas (views), templates de WhatsApp e conexão de canais: se o usuário pedir, registre como item `[M]` no plano.
