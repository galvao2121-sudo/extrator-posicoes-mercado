# Extrator de Posições e Recomendações de Mercado

Skill em português para transformar vídeos, transcrições, textos e relatórios financeiros em um resumo objetivo de compras, vendas, posições neutras e programas de recompra.

O núcleo segue o padrão aberto [Agent Skills](https://agentskills.io/specification). A mesma pasta pode ser instalada em agentes compatíveis sem alterar o `SKILL.md`.

## O que a skill faz

- identifica ticker, empresa ou ativo, responsável pelo movimento e contexto;
- separa compra, venda, neutro/manter e recompra;
- distingue recomendação institucional de opinião do apresentador;
- preserva divergências entre instituições;
- não inventa tickers, preços-alvo, responsáveis ou justificativas;
- pede a transcrição quando o agente não consegue acessar o link.

## Compatibilidade

| Plataforma | Forma de uso |
| --- | --- |
| ChatGPT Work e Codex | Instale ou importe a pasta/ZIP como skill. No Codex local, copie-a para `~/.codex/skills/`. |
| OpenAI API | Envie o ZIP pelo endpoint de Skills. |
| Claude Code | Copie a pasta para `~/.claude/skills/` ou `.claude/skills/` no projeto. |
| Gemini CLI | Copie a pasta para `~/.gemini/skills/`, `~/.agents/skills/`, `.gemini/skills/` ou `.agents/skills/`. |
| GitHub Copilot | Use `~/.copilot/skills/` ou `.github/skills/` dentro do repositório. |
| Hermes Agent | Copie a pasta para `~/.hermes/skills/`. |
| Outros chats e agentes | Use o arquivo `PROMPT-UNIVERSAL.md` por cópia e cola. |

O acesso direto a vídeos depende das ferramentas disponíveis em cada plataforma. Sem navegação ou extração de legendas, forneça a transcrição junto ao pedido.

## Uso

Depois de instalada, invoque a skill pelo nome ou faça um pedido natural:

```text
Use a skill extrator-posicoes-mercado para analisar:
https://exemplo.com/video
```

```text
Extraia as posições e recomendações de mercado desta transcrição:
[cole a transcrição]
```

## Estrutura

```text
extrator-posicoes-mercado/
├── SKILL.md
├── PROMPT-UNIVERSAL.md
├── README.md
├── LICENSE
├── agents/
│   └── openai.yaml
└── examples/
    └── teste-brsr6.md
```

`SKILL.md` é a definição principal. `PROMPT-UNIVERSAL.md` atende ferramentas que ainda não implementam Agent Skills. O exemplo documenta um teste real feito com uma transcrição automática em português.

## Limites

- A skill resume o conteúdo fornecido; ela não substitui confirmação em documentos oficiais.
- Uma mudança de preço-alvo isolada não é automaticamente classificada como compra ou venda.
- Menção a uma ação não é tratada como recomendação.
- O relatório não constitui aconselhamento financeiro.

## Estado da versão

Versão `1.0.1`, validada estruturalmente e testada com um vídeo público sobre BRSR6.

## Autoria e licença

Desenvolvida por **LVM Tech** e distribuída sob a [licença MIT](LICENSE).
