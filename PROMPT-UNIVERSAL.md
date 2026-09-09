# Prompt universal

Copie o bloco abaixo para qualquer IA. Substitua `[FONTE]` por um link, uma transcrição, um texto ou um relatório.

```text
Atue como analista especializado em extração fiel de informações financeiras. Analise a fonte abaixo e produza um resumo direto das posições, recomendações e movimentações de mercado citadas.

FONTE:
[FONTE]

Para cada ativo, extraia apenas o que estiver sustentado pela fonte:
- ticker e nome da empresa ou ativo;
- banco, fundo, corretora, empresa, gestor, analista ou apresentador responsável;
- direção: compra, venda, neutro/manter ou recompra;
- natureza: recomendação, elevação/rebaixamento, preço-alvo, entrada/saída de posição ou recompra;
- motivo ou contexto principal em uma linha;
- data, período, minuto ou página, quando disponível e relevante.

Não invente ticker, empresa, instituição, preço-alvo, motivo ou direção. Se a empresa for citada sem ticker e não for possível confirmá-lo com segurança, escreva “Ticker não informado”. Não transforme opinião do apresentador em recomendação institucional. Não classifique simples menção, notícia operacional ou mudança isolada de preço-alvo como compra ou venda sem viés explícito.

Use somente as categorias que tiverem itens:

🟢 RECOMENDAÇÕES E MOVIMENTOS DE COMPRA
* [TICKER] — [Empresa]: [responsável] — [motivo/contexto].

🔴 RECOMENDAÇÕES E MOVIMENTOS DE VENDA
* [TICKER] — [Empresa]: [responsável] — [motivo/contexto].

🟡 POSIÇÕES NEUTRAS / MANTER
* [TICKER] — [Empresa]: [responsável] — [motivo/contexto ou divergência].

🔄 PROGRAMAS DE RECOMPRA DE AÇÕES
* [TICKER] — [Empresa]: [situação e detalhes relevantes].

Se houver visões divergentes com peso semelhante, coloque o ativo em “Neutras / Manter” e explique os dois lados. Se nenhuma informação elegível existir, responda: “Nenhuma recomendação, movimentação institucional ou recompra foi identificada no conteúdo analisado.”

Se você não conseguir acessar um link ou extrair sua transcrição, informe isso claramente e solicite o texto. Não simule a análise. Seja extremamente direto, preserve incertezas e não acrescente recomendação financeira própria.
```
