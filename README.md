# Bücher Author

Duas skills para [Bücher no Obsidian](https://github.com/mateusdcc/obsidian-buches). O pacote escreve Markdown no vault indicado pelo usuário; a extensão Obsidian renderiza o livro.

| Skill | O que faz |
| --- | --- |
| [Criar Buch](skills/criar-buch/SKILL.md) | Pergunta pelo objetivo, nível e materiais de referência. Constrói um currículo, conceitos, subconceitos e exercícios de prova com dicas. |
| [Extender Buch](skills/extender-buch/SKILL.md) | Compara uma lista ou prova com o conteúdo real de um Buch, indica o que estudar e, quando solicitado, escreve a teoria e os exercícios que faltam. |

O [guia de formato](skills/criar-buch/references/format.md) descreve diretórios, frontmatter, âncoras, dependências e soluções. Os [templates](skills/criar-buch/assets/templates/) incluem índice, conceito, subconceito, exercício e um [capítulo completo de matemática axiomática](skills/criar-buch/assets/templates/mathematics-axiomatic.md). As duas skills compartilham esse guia; instale o pacote inteiro.

## Hermes Agent

```sh
hermes plugins install mateusdcc/buches-author --enable
```

Abra uma sessão no diretório do vault. No Hermes CLI, TUI ou Desktop, use **`/buches-author:criar-buch`** ou **`/buches-author:extender-buch`**. No gateway de mensagens, peça a skill pelo nome em linguagem natural. Se a versão instalada não reconhecer plugins portáveis `plugin.json`, atualize o Hermes.

## Codex

```sh
codex plugin marketplace add mateusdcc/buches-author
codex plugin add buches-author@buches-tools
```

No app Codex, o marketplace **Bücher Tools** oferece o plugin **buches-author**. Abra o vault como projeto e invoque **`$criar-buch`** ou **`$extender-buch`** pelo seletor de skills. Veja a [documentação do OpenAI sobre marketplaces de plugins](https://developers.openai.com/plugins/build/plugins).

## Claude Code

```text
/plugin marketplace add mateusdcc/buches-author
/plugin install buches-author@buches-tools
```

No diretório do vault, use **`/buches-author:criar-buch`** ou **`/buches-author:extender-buch`**. Veja a [documentação de marketplaces do Claude Code](https://code.claude.com/docs/en/plugin-marketplaces).

## Exemplos de uso

> Crie um Buch de álgebra linear avançada para minha prova. Quero uma abordagem algébrica e axiomática. Pergunte o que precisar e use as duas provas anteriores e a lista que anexei.

> Extenda meu Buch de Álgebra Linear para a lista 4. Minha prova é na próxima semana. Compare os subitens com as notas e me diga o que estudar primeiro. Escreva as lacunas e exercícios de transferência sem mudar meu progresso.

Para uma primeira passagem sem editar o vault, peça **só um diagnóstico**.
