# Modo manual — lista de tarefas

Use o mesmo `plano.md`, com todos os itens `[M]`, na ordem de `aplicacao.md`. Cada item diz **onde** e **o quê**.

| Item | Onde no agents2.me |
|---|---|
| Funcionalidades (Contas, Oportunidades, Tarefas, Compromissos, CX Score, Conversa interna) | Configurações → Geral (`/settings/general`) — cada recurso tem seu cartão com um interruptor; Salvar |
| Google Agenda (opcional, por usuário) | Cada usuário, na própria conta: Configurações → Aplicativos conectados → cartão **Google Agenda** → Conectar conta do Google → ligue **Sincronizar** nas agendas que devem aparecer. A sincronização é nos dois sentidos: o que muda no Google aparece no agents2.me. Não é configuração da empresa: a conexão é pessoal. Se o cartão não aparecer, a instância ainda não tem o Google configurado |
| Nomes das entidades (Conta, Contato, Oportunidade, Tarefa, Compromisso) | Configurações → Nomes das entidades (`/settings/entity-names`) — escolha o idioma, preencha singular e plural, Salvar |
| Etapas do funil | Com Oportunidades: Configurações → Geral → cartão Oportunidades → "Configurar etapas" (aparece depois de salvar Oportunidades ligado). Sem: Configurações → Campos Personalizados → Campos de Contato → Novo → tipo combobox "Etapa do funil" com as etapas como opções |
| Campos customizados | Configurações → seção **Campos Personalizados**: Campos de Contato (`/settings/contacts-custom-fields`), de Contas (se ligado) (`/settings/accounts-custom-fields`), de Oportunidades (`/settings/opportunities-custom-fields`), de Tarefas (`/settings/tasks-custom-fields`), de Compromissos (`/settings/events-custom-fields`) |
| Papéis | Configurações → Papéis (`/settings/roles/new`) — marque as permissões da matriz. Compromissos não tem "ver todos": para o gestor ver a agenda da equipe, torne a agenda pública ou compartilhe (Calendário → lateral → menu da agenda → Configurações e compartilhamento) |
| Usuários | Configurações → Usuários (`/settings/users/new`) — cada um recebe convite por e-mail |
| Tags | Configurações → Tags (`/settings/tags/new`) |
| Filas | Configurações → Filas (`/settings/queues/new`) |
| Mensagens rápidas | Configurações → Mensagens rápidas (`/settings/quick-replies/new`) |
| Relatórios | Relatórios (`/reports`) → Novo → escolha o tipo e siga a receita |
| System prompt | Configurações → Integrações → chatt2.me Hub → canal → link "Configurar Workspace" (acima de "Workspace de conhecimento") → cole em **Instruções** (máx. 5000) → Salvar. Confira se o canal usa esse workspace no dropdown |

Formato de cada item:

```
- [M] Criar tag "Troca" — cor #2E86DE — usada por: todos
      Onde: Configurações → Tags → Nova
- [M] Relatório "Motivos de contato"
      Onde: Relatórios → Novo → tipo Conversas
      Agrupar por: Tag · Medida: contagem · Gráfico: rosca · Compartilhar com: Ana, João
```
