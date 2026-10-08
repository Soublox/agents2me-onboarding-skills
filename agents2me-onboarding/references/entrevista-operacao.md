# Etapa 2 — Operação

Proponha a partir da Etapa 1 e do estado atual; o usuário ajusta. Itens que já existem (mesmo nome, sem diferenciar maiúsculas; usuários pelo e-mail) aparecem como "já existe" e não são perguntados de novo.

## 1. Equipe e usuários
Para cada pessoa: nome, e-mail, função (que vira o papel). Pule e-mails que já estão em `list_users`. Avise: cada usuário novo recebe um convite por e-mail para criar a senha.

## 2. Papéis
Ofereça os modelos e deixe ajustar em linguagem natural ("atendente também vê relatórios"). Não altere o papel protegido (Administrador).

Montagem da matriz: copie as `permissions` de um papel de `list_roles` e ajuste. Toda seção tem `create/read/update/delete`; seção não listada abaixo = tudo `false`. Flags extras ficam `false` salvo indicação.

| Modelo | Seções (todas as ações) | Seções só leitura | Flags `true` |
|---|---|---|---|
| Supervisor | dashboard, inbox, contacts, queues, tags, quickReplies | queuesLive, reports, users | inbox.viewAllSessions, inbox.viewPrivateMessages, contacts.viewAllContacts |
| Atendente | dashboard, inbox, contacts | quickReplies, tags | — |
| Vendedor | dashboard, inbox, contacts, accounts, opportunities | quickReplies, tags | — |

Só ofereça Vendedor se Oportunidades for ligado. Se `create_role` responder `role_exceeds_caller`, remova o excesso ou peça para um Administrador rodar.

## 3. Funcionalidades
Uma por vez, com uma frase e uma recomendação:
- **Contas** — agrupar contatos por empresa cliente (B2B). Recomende se vende para empresas.
- **Oportunidades** — funil de vendas com etapas e valores; liga Contas junto. Recomende se há venda consultiva.
- **CX Score** — nota de experiência dada por IA a cada conversa finalizada. Recomende se quer medir qualidade.
- **Conversa interna** — chat entre atendentes dentro do agents2.me. Recomende se a equipe tem mais de 2 pessoas.

## 4. Etapas do funil
Pergunte se a empresa acompanha o cliente por etapas (ex.: contato → orçamento → fechado). Se não, pule.
Pergunte: "o que acontece entre o primeiro contato e o fechamento?"

**Oportunidades ligado** — padrão do sistema: Prospecção (open, 10%), Qualificação (open, 25%), Proposta (open, 50%), Negociação (open, 75%), Ganha (won, 100%), Perdida (lost, 0%).
Proponha a lista ordenada com nome, categoria (`open`/`won`/`lost`) e probabilidade (%). Mantenha pelo menos uma `open`, uma `won` e uma `lost`. Marque cada etapa padrão como manter / renomear / remover.

**Oportunidades desligado** — o funil vira um campo de **contato** do tipo `combobox`, nome sugerido "Etapa do funil", com as etapas como `options` na ordem do processo (sem categoria nem probabilidade). Explique: "dá para ver os contatos em Kanban agrupados por esse campo". Grave junto com os campos customizados (bloco 8).

## 5. Filas
Setores ou assuntos (ex.: Vendas, Suporte, Financeiro); canais de cada fila; membros. Sugira a partir dos motivos de contato da Etapa 1.

## 6. Tags
Derive dos motivos de contato e do FAQ (ex.: Orçamento, Troca, Rastreio, Reclamação). Para cada: cor (hex) e quem usa (todos, ou uma lista).

## 7. Mensagens rápidas
Proponha: saudação, pedido de dados, horário de atendimento, encerramento e uma por FAQ importante. Para cada: atalho (`/saudacao`), tipo (`text`, `button`, `list`, `cta`, `payment`), texto. Use variáveis onde fizer sentido: `{{first_name}}`, `{{full_name}}`, `{{contact.<campo>}}`.

## 8. Campos customizados
O que a equipe precisa registrar sobre contatos (CPF, plano, cidade...). Tipo de cada um (texto, número, data, combobox com opções...). Se Contas/Oportunidades ligados, pergunte também para essas entidades.

## Fora do escopo
Campanhas, listas (views), templates de WhatsApp e conexão de canais: se o usuário pedir, registre como item `[M]` no plano.
