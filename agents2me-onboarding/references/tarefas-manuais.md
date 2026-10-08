# Modo manual — lista de tarefas

Use o mesmo `plano.md`, com todos os itens `[M]`, na ordem de `aplicacao.md`. Cada item diz **onde** e **o quê**.

| Item | Onde no agents2.me |
|---|---|
| Funcionalidades (Contas, Oportunidades, CX Score, Conversa interna) | Configurações → Geral |
| Etapas do funil | Com Oportunidades: Configurações → Geral → Oportunidades → Etapas. Sem: Configurações → Campos de contatos → Novo → tipo combobox "Etapa do funil" com as etapas como opções |
| Campos de contatos / contas / oportunidades | Configurações → Campos de contatos (`/settings/contacts-custom-fields`), de contas (`/settings/accounts-custom-fields`), de oportunidades (`/settings/opportunities-custom-fields`) |
| Papéis | Configurações → Papéis (`/settings/roles/new`) — marque as permissões da matriz |
| Usuários | Configurações → Usuários (`/settings/users/new`) — cada um recebe convite por e-mail |
| Tags | Configurações → Tags (`/settings/tags/new`) |
| Filas | Configurações → Filas (`/settings/queues/new`) |
| Mensagens rápidas | Configurações → Mensagens rápidas (`/settings/quick-replies/new`) |
| Relatórios | Relatórios (`/reports`) → Novo → escolha o tipo e siga a receita |
| System prompt | Configurações → Integrações → Chatt2me Hub → canal → configurações do agente |

Formato de cada item:

```
- [M] Criar tag "Troca" — cor #2E86DE — usada por: todos
      Onde: Configurações → Tags → Nova
- [M] Relatório "Motivos de contato"
      Onde: Relatórios → Novo → tipo Conversas
      Agrupar por: Tag · Medida: contagem · Gráfico: rosca · Compartilhar com: Ana, João
```
