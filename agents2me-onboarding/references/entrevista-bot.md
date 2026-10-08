# Etapa 1 — Bot e system prompt

O resultado é o **prompt da empresa**. O hub do agents2.me já tem um prompt master com as regras de segurança, então **não** inclua regras genéricas ("não invente", "seja educado", "não fale de política"...). Inclua só o que é da empresa.

## Blocos (uma pergunta por vez; grave cada bloco em respostas.md)

1. **Negócio** — o que a empresa faz e vende; para quem; horário de atendimento; site e links úteis.
2. **Canais** — com MCP, mostre os canais de `list_channels` e pergunte se falta algum e se o bot atende todos ou só alguns. Sem MCP, pergunte quais usa (WhatsApp, Instagram, Webchat...).
3. **Tom de voz** — formal ou informal; você/senhor(a); emojis (nunca/às vezes/frequente); respostas curtas ou detalhadas. Peça **2 ou 3 mensagens reais** que a empresa já mandou e gosta, e **1** que não quer que o bot mande.
4. **O que o bot resolve** — dúvidas frequentes com as respostas; preços; políticas (troca, prazo, frete, cancelamento); agendamento. Para cada item, de onde vem a resposta (texto colado, link, "não sei" → bot transfere).
5. **Regras do negócio e transferência** — o que o bot nunca faz (desconto, prometer prazo, falar de concorrente...); quando passa para um humano; a frase de transferência; o que coletar antes (nome, pedido, motivo).
6. **Fora do horário** — o que responder e o que coletar.

## Montagem do system-prompt.md

```
<!-- caracteres: N / 5000 -->
# Identidade
Você é <nome do bot>, atendente virtual da <empresa>, que <o que faz> para <público>.

# Tom de voz
<regras curtas em lista>
Exemplos do jeito certo:
- "<mensagem real boa>"
Nunca escreva assim:
- "<mensagem ruim>"

# O que você resolve
<FAQ em pares curtos "Pergunta → resposta"; políticas; links>

# Regras do negócio
<lista do bloco 5>

# Transferência
Transfira para um atendente quando: <condições>. Antes, colete: <dados>. Diga: "<frase>".

# Fora do horário
Horário: <horário>. Fora dele: <resposta>; colete <dados>.
```

## Limite de 5000 caracteres

1. Conte: com shell, `wc -m < onboarding/<empresa>/system-prompt.md`; sem shell, conte você mesmo e arredonde para cima.
2. Acima de 5000, corte nesta ordem e reconte a cada corte:
   1. Exemplos de tom: deixe 1 bom e 1 ruim.
   2. FAQs menos frequentes: troque por link quando houver; senão remova as menos citadas.
   3. Condense as regras do negócio (frases curtas, sem repetição).
3. Atualize o comentário da primeira linha com o total. Nunca entregue acima de 5000.

## Teste rápido

Mostre como o bot responderia, seguindo o prompt, a:
1. Uma dúvida comum do bloco 4.
2. Um pedido fora do escopo.
3. Uma reclamação.

Pergunte: "Está no tom certo?" Ajuste e regere até aprovar.

## Entrega

O prompt é sempre colado manualmente: Configurações → Integrações → Chatt2me Hub → canal → configurações do agente (prompt da empresa). Registre como item `[M]` no plano.
