# Etapa 3 — Relatórios gerenciais

1. Pergunte: "O que você quer saber toda segunda de manhã sobre o atendimento?"
2. Mostre o catálogo (só os itens cuja condição vale) para marcar; mapeie a resposta livre para itens do catálogo ou para um item novo no mesmo formato.

| # | Pergunta de gestão | Tipo | Agrupar por | Medida | Gráfico | Condição |
|---|---|---|---|---|---|---|
| 1 | Volume de conversas por canal | channels | canal | contagem | column | — |
| 2 | Volume de conversas por dia | chat_contacts | data de criação (dia) | contagem | line | — |
| 3 | Conversas por fila e por atendente | chat_contacts | fila, atendente | contagem | bar | — |
| 4 | Motivos de contato | chat_contacts | tag | contagem | donut | — |
| 5 | CX Score por atendente | chat_contacts | atendente | média do CX Score | bar | CX Score ligado |
| 6 | Novos contatos por origem | contacts | origem/canal | contagem | column | — |
| 7 | Funil de oportunidades | opportunities | etapa | soma do valor | funnel | Oportunidades ligado |
| 8 | Ganho x perdido por vendedor | opportunities | dono, categoria da etapa | soma do valor | bar | Oportunidades ligado |
| 9 | Mensagens enviadas por atendente | messages | atendente | contagem | bar | — |

3. Pergunte quem vê os relatórios (padrão: Supervisores e Administradores).
4. Grave em `respostas.md` (`## Etapa 3 / Relatórios`) cada relatório como receita: nome, tipo, agrupar por, medida, filtro, gráfico, quem vê.

Os nomes de campo acima são **de negócio**; os ids reais são resolvidos na Etapa 4 com `describe_report_type`.
