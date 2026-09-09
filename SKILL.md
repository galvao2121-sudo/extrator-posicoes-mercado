---
name: extrator-posicoes-mercado
description: Extrai de vídeos, transcrições, textos e relatórios financeiros recomendações, mudanças de preço-alvo, movimentações institucionais e programas de recompra, organizando os ativos por compra, venda, neutro ou recompra. Use quando o usuário pedir posições ou recomendações de mercado mencionadas em um conteúdo.
license: MIT
metadata:
  version: "1.0.1"
  language: "pt-BR"
  author: "LVM Tech"
  compatibility: "Agent Skills; links exigem acesso à web ou transcrição fornecida"
---

# Extrator de Posições e Recomendações de Mercado

Produza uma síntese fiel, rápida e verificável das posições de mercado mencionadas na fonte fornecida.

## Obter a fonte

- Se o usuário fornecer texto ou transcrição, analise esse conteúdo diretamente.
- Se fornecer um link, obtenha o conteúdo acessível e, para vídeos, priorize a transcrição. Informe brevemente se a fonte ou a transcrição não puder ser acessada e peça o texto; não simule a análise.
- Quando houver mais de uma fonte, diferencie claramente o que cada uma atribui a cada instituição.

## Extrair

Para cada ativo citado, identifique somente quando houver evidência na fonte:

- ticker e nome da empresa ou do ativo;
- instituição, fundo, banco, corretora, gestor, analista ou empresa responsável;
- direção do movimento: compra, venda, neutro/manutenção ou recompra;
- natureza da informação: recomendação, elevação/rebaixamento, mudança de preço-alvo, entrada/saída de posição ou recompra corporativa;
- motivo ou contexto principal, em uma linha curta;
- data ou período, quando declarado e relevante.
- minuto, página ou trecho de origem, quando estiver disponível e ajudar na verificação.

Normalize o ticker apenas quando a equivalência for inequívoca. Não invente ticker, preço-alvo, instituição, motivo ou direção. Se o conteúdo citar a empresa sem ticker e não for possível confirmá-lo com segurança, use `Ticker não informado`.

Não trate comentário genérico, opinião do apresentador, notícia operacional ou simples menção a uma ação como recomendação institucional. Diferencie fato consumado, anúncio, intenção e especulação.

## Classificar

- **Compra:** recomendação de compra, elevação de recomendação, aumento de posição, entrada de grande investidor ou aumento de preço-alvo com viés positivo explícito.
- **Venda:** recomendação de venda, rebaixamento, redução/saída de posição ou corte de preço-alvo com viés negativo explícito.
- **Neutro / manter:** recomendação neutra, manutenção de posição ou ausência de mudança direcional explícita.
- **Recompra:** programa anunciado, aprovado ou executado pela própria companhia.

Mudança de preço-alvo isolada não equivale automaticamente a compra ou venda. Preserve a recomendação declarada e explique a mudança no contexto.

Quando houver visões divergentes sobre o mesmo ativo, coloque-o no bloco que melhor represente o destaque principal da fonte e registre a divergência na mesma linha. Se as visões tiverem peso semelhante, prefira **Posições neutras / manter** e explicite ambos os lados.

## Formato de saída

Comece diretamente pelas categorias aplicáveis e omita qualquer categoria vazia.

### 🟢 RECOMENDAÇÕES E MOVIMENTOS DE COMPRA

* `[TICKER] — [Empresa]: [Quem recomendou/comprou] — [motivo ou contexto].`

### 🔴 RECOMENDAÇÕES E MOVIMENTOS DE VENDA

* `[TICKER] — [Empresa]: [Quem recomendou/vendeu] — [motivo ou contexto].`

### 🟡 POSIÇÕES NEUTRAS / MANTER

* `[TICKER] — [Empresa]: [Quem recomendou] — [motivo, contexto ou divergência].`

### 🔄 PROGRAMAS DE RECOMPRA DE AÇÕES

* `[TICKER] — [Empresa]: [situação e detalhes relevantes do programa].`

Se nenhum ativo ou movimento elegível for identificado, diga objetivamente: `Nenhuma recomendação, movimentação institucional ou recompra foi identificada no conteúdo analisado.`

## Regras de qualidade

- Seja extremamente direto e evite introduções longas.
- Preserve qualificadores como “pode”, “pretende”, “segundo o analista” e “ainda não executado”.
- Não apresente a síntese como aconselhamento financeiro nem acrescente recomendações próprias.
- Quando a fonte for pública e tiver sido consultada, cite ou vincule a fonte de forma próxima às informações extraídas.
- Se houver ambiguidade material, sinalize-a em vez de preencher lacunas por suposição.
- Se a fonte trouxer apenas a visão do apresentador ou autor, identifique-a como opinião própria e não como recomendação institucional.
