# agents2.me — Skill de Implantação

Skill que entrevista você, gera o system prompt do seu bot e configura o agents2.me (tags, filas, mensagens rápidas, campos, funcionalidades, papéis, usuários, funil e relatórios).

## Pré-requisito: MCP do agents2.me

Conecte o MCP do agents2.me no seu agente com um usuário **Administrador** da empresa. Sem o MCP a skill funciona em modo manual: entrega uma lista de tarefas para fazer na tela.

## Instalação

- **Qualquer agente compatível com Agent Skills:** `npx skills add Soublox/agents2me-onboarding-skills`
- **Claude Code (manual):** copie `agents2me-onboarding/` para `~/.claude/skills/`
- **Codex (manual):** copie `agents2me-onboarding/` para `~/.codex/skills/`
- **OpenCode (manual):** copie `agents2me-onboarding/` para `~/.config/opencode/skills/`
- **Cursor (manual):** copie `agents2me-onboarding/` para `.cursor/skills/` do projeto

## Uso

Peça: "quero implantar o agents2.me". Os arquivos ficam em `onboarding/<empresa>/`; rode de novo para retomar.

## Testes (manuais)

1. **Modo manual:** sem MCP, responda com `tests/cenario-loja.md`. Confira: `plano.md` com todos os itens `[M]` e caminho na tela; `system-prompt.md` ≤ 5000 caracteres (`wc -m`) e sem regras genéricas de segurança.
2. **Modo MCP:** empresa nova em dev (hub conectado, com um workspace), mesmo cenário. Confira na tela, incluindo "Configurar Workspace" do canal: Instruções = `system-prompt.md` sem a linha de contagem, nome do workspace intacto. Rode de novo — tudo deve sair `[-]`.
3. **Retomada:** interrompa no meio da Etapa 2, abra nova sessão, peça para continuar.
4. **Portabilidade:** instale no Claude Code e no Codex ou OpenCode; a skill deve aparecer e iniciar.
