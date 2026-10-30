# Etapa 4 — Plano e aplicação

## 1. Gerar plano.md

Agrupe por tipo, na ordem de aplicação abaixo. Cada linha: status, ação, alvo, detalhes.

```
## 1. Funcionalidades
- [ ] ligar Oportunidades
## 2. Nomes das entidades (pt)
- [ ] Oportunidade → Pedido / Pedidos
## 6. Usuários  ⚠️ cada um recebe convite por e-mail
- [ ] criar Ana Souza <ana@loja.com> — papel Atendente
- [-] João <joao@loja.com> — já existe
```

Contas, Oportunidades, Tarefas e Compromissos são independentes: cada um vira linha própria, só se escolhido (ex.: `ligar Compromissos`). Ligar um não liga outro. A conexão com o Google Agenda não é passo da implantação: cada usuário faz a própria conexão em Aplicativos conectados, e nenhuma ferramenta MCP conecta a conta.

Ações: **criar**, **atualizar** (existe com diferença — diga qual), **pular** `[-]` (existe igual), **remover** (só etapas do funil), **manual** `[M]`.

Idempotência — antes de propor "criar", procure o item existente:
- tags, filas, papéis, etapas, relatórios, campos: mesmo nome sem diferenciar maiúsculas/acentos;
- nomes das entidades: mesmo singular e plural em `get_entity_labels.configured` para o idioma;
- mensagens rápidas: mesmo atalho;
- usuários: mesmo e-mail.

Nunca proponha apagar nada além de etapas do funil.

## 2. Confirmar

Mostre o plano inteiro e pergunte uma vez: "Posso aplicar? Os N usuários novos vão receber um convite por e-mail agora." Só siga com um sim explícito. No modo manual, pule para `tarefas-manuais.md`.

## 3. Aplicar (nesta ordem)

Atualize a linha no `plano.md` logo após cada chamada. Se um item falhar: `[!] erro: <mensagem da ferramenta>` e continue com os independentes; quem depende dele vira `[~] bloqueado por <item>`.

| # | Item | Ferramentas | Observações |
|---|---|---|---|
| 1 | Funcionalidades | `update_company_features` | uma chamada com todas (`accounts`, `opportunities`, `tasks`, `events`, `cxScore`, `agentsChat`); confira o estado retornado |
| 2 | Nomes das entidades | `get_entity_labels`, `update_entity_labels` | uma chamada por idioma, só com as entidades que mudam (`account`, `contact`, `opportunity`, `task`, `event`, cada uma `{ singular, plural }`); `null` volta ao padrão; confira `configured` retornado |
| 3 | Etapas do funil | `list_opportunity_stages`, `update_opportunity_stage`, `create_opportunity_stage`, `delete_opportunity_stage`, `reorder_opportunity_stages` | só com Oportunidades ligado: renomeie/reaproveite padrão → crie → remova → reordene com todos os ids |
| 4 | Campos customizados | `create_custom_field` / `update_custom_field` | entity `contacts`, `accounts` (só com Contas ligada), `opportunities`, `tasks` (só com Tarefas), `events` (só com Compromissos); sem Oportunidades, o funil entra aqui: entity `contacts`, `fieldType: "combobox"`, `options` = etapas em ordem (já existe com outras opções → atualizar `options`) |
| 5 | Papéis | `list_roles`, `create_role` / `update_role` | copie a matriz de um papel existente e ajuste; `tasks` (com `viewAllTasks`) só depois do passo 1 ligar os recursos; Compromissos não tem permissão de ver tudo — para gestores, a visão de equipe vem de agendas públicas ou compartilhadas |
| 6 | Usuários | `create_user` | `roleId` do passo 5 |
| 7 | Tags | `create_tag` / `update_tag` | `userIds` de `list_users` |
| 8 | Filas | `create_queue` / `update_queue`, `add_queue_member` | `memberIds`, `tagIds`, `channelIds`; `hubQueueSyncError` → anote `[x] (aviso: sync hub)` |
| 9 | Mensagens rápidas | `create_quick_reply` / `update_quick_reply` | |
| 10 | Relatórios | `create_report` (folder "Gestão"), `describe_report_type`, `create_report` (report, `parentId` da pasta), `save_report_config`, `share_report` | veja abaixo |
| 11 | Instruções do bot | `update_agent_workspace` | `workspaceId` + `instructions` = `system-prompt.md` **sem** a linha `<!-- caracteres: … -->`; não passe `name` nem `description` (ficam como estão); confira o tamanho de `instructions` retornado |
| 12 | Manuais | — | itens `[M]` (criar workspace, ligar canal ao workspace) e `[!]` |

### Relatórios
Para cada receita: `describe_report_type` do tipo → escolha os campos reais que correspondem a "agrupar por" e "medida" → `save_report_config` com groups, columns e `chart` → confira a amostra retornada. Se nenhum campo corresponder, marque `[!] campo não encontrado` e deixe a receita para o manual. Compartilhe com `share_report` passando os `userIds` de quem deve ver (usuários com papel Supervisor/Administrador em `list_users` + `list_roles`) — `role: true` compartilha apenas com o papel de quem está conectado.

## 4. Resumo
Conte criados, atualizados, pulados, falhas e manuais. Liste os `[!]` com o motivo e o que fazer. Reexecutar a skill retoma pelos status do `plano.md`.
