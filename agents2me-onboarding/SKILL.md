---
name: agents2me-onboarding
description: Implanta o agents2.me para uma empresa — entrevista sobre canais, tom de voz e atendimento, gera o system prompt da empresa para o bot (gravado nas instruções do workspace do hub) e configura tags, filas, mensagens rápidas, campos customizados, funcionalidades, papéis, usuários, funil de oportunidades e relatórios via MCP do agents2.me (ou gera uma lista de tarefas manuais). Use quando o usuário quiser implantar, configurar ou fazer o onboarding do agents2.me.
---

# Implantação agents2.me

Você conduz a implantação do agents2.me para uma empresa. Trabalhe em etapas, uma pergunta por vez, e salve tudo em arquivos para poder retomar.

## Regras gerais

- Fale no idioma do usuário (pt, en ou es).
- **Uma pergunta por mensagem.** Ofereça opções numeradas sempre que der; aceite resposta livre.
- **Proponha em vez de perguntar do zero** quando as respostas anteriores já indicam o caminho ("sugiro as tags X, Y, Z — ajusta?").
- Com o MCP conectado, **leia antes de perguntar** e só confirme o que já existe.
- Ajuste o vocabulário ao perfil: cliente (simples, sem jargão) ou implantador (direto).
- Nunca aplique nada antes da confirmação da Etapa 4.
- Leia cada arquivo de `references/` **somente** ao entrar na etapa dele.

## Estado (sempre em disco)

Pasta `onboarding/<empresa>/` no diretório atual (`<empresa>` em minúsculas, sem acentos, com hífens):

- `respostas.md` — uma seção `## <Etapa> / <Bloco>` por bloco respondido; grave ao fim de **cada** bloco.
- `system-prompt.md` — prompt final (Etapa 1).
- `plano.md` — mudanças e status (Etapa 4).

Status no `plano.md`: `[ ]` pendente · `[x]` feito · `[-]` pulado (já existe igual) · `[!] erro: <motivo>` · `[~] bloqueado por <item>` · `[M]` manual.

Sem ferramenta de arquivo? Mostre o conteúdo de cada arquivo em bloco de código e peça ao usuário para salvar.

## Etapa 0 — Preparação

1. Pergunte o nome da empresa. Se `onboarding/<empresa>/` existir, leia os arquivos e ofereça **retomar** a partir do primeiro bloco sem seção em `respostas.md` (ou do primeiro item não `[x]`/`[-]` em `plano.md`).
2. Verifique o MCP chamando `whoami`:
   - Funcionou → mostre "Conectado como <nome> (<email>), papel <papel>" e pergunte se é a empresa certa. Se não for, peça para reconectar o MCP do agents2.me com a conta da empresa certa e pare.
   - Ferramenta inexistente ou erro → **modo manual**. Avise: "Sem o MCP, no final vou entregar uma lista de tarefas para fazer na tela do agents2.me." Para conectar depois: Configurações → Apps conectados no agents2.me.
3. Pergunte o perfil: (1) sou da empresa / (2) sou implantador/parceiro.
4. Com MCP, leia: `list_channels`, `list_users`, `list_roles`, `list_tags`, `list_queues`, `list_quick_replies`, `list_custom_fields` (entity `contacts`), `get_company_features`, `list_agent_workspaces`; se opportunities ligado, `list_opportunity_stages`. Grave um resumo (para cada workspace: nome e se já tem instruções) em `respostas.md` (`## Etapa 0 / Estado atual`).

## Etapa 1 — Bot e system prompt
Leia `references/entrevista-bot.md` e siga.

## Etapa 2 — Operação
Leia `references/entrevista-operacao.md` e siga.

## Etapa 3 — Relatórios
Leia `references/entrevista-relatorios.md` e siga.

## Etapa 4 — Plano e aplicação
Leia `references/aplicacao.md` e siga. No modo manual, use também `references/tarefas-manuais.md`.

## Fim

Mostre o resumo (criados, atualizados, pulados, falhas, manuais) e diga onde ficou o `system-prompt.md`: gravado nas instruções do workspace (MCP) ou a colar manualmente (item `[M]`). Lembre que ligar o canal ao workspace é feito na tela do canal.
