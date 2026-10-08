# Cenário de teste — Loja Bella Moda

Use estas respostas ao rodar a skill.

- **Empresa:** Bella Moda — loja de roupas femininas online e uma loja física em Campinas. Público: mulheres 25-45. Horário: seg-sex 9h-18h, sáb 9h-13h. Site: bellamoda.com.br
- **Canais:** WhatsApp e Instagram; o bot atende os dois.
- **Tom:** informal, "você", emojis às vezes, respostas curtas.
  - Boa: "Oi, Ju! 💛 Seu pedido saiu hoje, o código de rastreio é BR123. Qualquer coisa me chama!"
  - Boa: "Temos sim no P e no M! Quer que eu separe pra você?"
  - Ruim: "Prezada cliente, informamos que sua solicitação foi recebida e será analisada."
- **Resolve:** rastreio (link bellamoda.com.br/rastreio), trocas em até 30 dias com etiqueta, frete grátis acima de R$ 299, tabela de medidas (link), formas de pagamento (PIX, cartão até 6x).
- **Regras:** nunca dar desconto; nunca prometer data de entrega; transferir reclamação e pedido de troca com defeito. Coletar nome e número do pedido. Frase: "Vou te passar para alguém da equipe, só um minutinho!"
- **Fora do horário:** "Estamos fora do horário, mas já anotei! Amanhã cedo a equipe te responde." Coletar nome e motivo.
- **Equipe:** Carla (carla@bellamoda.test, supervisora), Ju (ju@bellamoda.test, atendente), Rafa (rafa@bellamoda.test, atendente e vendas).
- **Funcionalidades:** Contas não; Oportunidades sim (vendas para atacado); CX Score sim; conversa interna sim.
- **Funil:** Contato → Catálogo enviado → Pedido montado → Pagamento → Ganha / Perdida.
- **Variante sem Oportunidades** (rodar uma vez no modo manual): responda "Oportunidades não" — o funil deve virar o campo combobox "Etapa do funil" nos contatos.
- **Filas:** Vendas (WhatsApp + Instagram; Rafa, Carla), Pós-venda (WhatsApp; Ju, Carla).
- **Tags:** Rastreio, Troca, Tamanho, Atacado, Reclamação.
- **Campos:** CPF (texto), Tamanho preferido (combobox P/M/G/GG), Cliente atacado (sim/não).
- **Relatórios:** volume por canal, motivos de contato, CX Score por atendente, funil de oportunidades. Ver: Carla.
