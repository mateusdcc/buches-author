# Livros de idiomas no Bücher

Ao criar um Buch para aquisição de idioma, combine **input compreensível** (diálogos e textos curtos), **vocabulário contextualizado** (com frase-exemplo e morfologia), **gramática orientada a padrões**, **flashcards FSRS integrados** e **exercícios ativos de produção**.

## Metadados em `_index.md`

Configure no frontmatter de `_index.md`:

```yaml
title: "Alemão A1–A2"
description: "Estruturas centrais, diálogos reais e prática guiada para conversar e ler em alemão."
icon: lucide:languages
language: German         # Idioma alvo (ex.: German, Japanese, Spanish, French, ja-JP, de-DE)
native_language: Portuguese
mode: language
grading:
  - id: naturalness
    label: Naturalidade e registro
    weight: 3
    criteria: "Avalie se a resposta soa natural no registro pedido, com escolha lexical adequada."
  - id: grammar
    label: Correção gramatical
    weight: 4
    criteria: "Verifique conjugação, ordem das palavras, casos, concordância e preposições."
  - id: completion
    label: Cumprimento da tarefa
    weight: 3
    criteria: "Confira se a resposta atende integralmente ao enunciado e usa a estrutura visada."
```

Declarar `language` ativa a síntese de voz (TTS) do leitor para flashcards e blocos de idioma e ajusta o tutor do Claudian para explicar lema, pronúncia/AFI, registro e papel gramatical.

## Blocos recomendados

- `[!dialogue]`: diálogo ou texto curto no nível do capítulo. Use `==expressão;;dica==` em pontos-chave para permitir o modo **Cloze quiz** durante a leitura.
- `[!vocab]` e `[!phrase]`: palavras, colocações e expressões fixas com gênero/classe/lema, pronúncia quando útil, frase de exemplo e cartões inline (`:::`).
- `[!grammar]` e `[!conjugation]`: regras e tabelas resumidas ligadas ao diálogo e aos capítulos anteriores via `depends_on` / `block_depends_on`.
- `[!usage]` e `[!culture]`: falsos cognatos, nuances de registro (formal/informal) e armadilhas frequentes de tradução.
- `[!exercise]`: prática de produção ativa (tradução contextual, transformação de tempo/modo, resposta a uma situação ou escrita guiada), seguida de `[!hint]-` e resposta-modelo entre `---`.

## Flashcards e mineração de sentenças

O Bücher extrai flashcards automaticamente dos capítulos, de `_cards.md` e de `_notes.md` e agenda revisões por FSRS em `_progress.md` (`cards:`):

1. **Vocabulário bidirecional (`:::`):** ideal para pares palavra/expressão ↔ significado. Coloque na linha imediatamente seguinte `Example: ...` para mostrar a frase de contexto durante a revisão.
   ```markdown
   - der Alltag ::: o cotidiano *(m., pl. die Alltage)* #vocab #A2
     - Example: Das gehört inzwischen zu meinem Alltag.
   ```
2. **Reconhecimento ou regra (`::`) e blocos multilinhas (`?` / `??`):** úteis para tradução de frases curtas, perguntas de gramática e regência verbal.
3. **Clozes em contexto (`==resposta;;dica==`):** dentro de `[!vocab]`, `[!phrase]`, `[!card]`, `#flashcards` ou `_cards.md` (ou em qualquer lugar quando houver `;;dica`), viram cartões de preenchimento automático. Evite `;;` em destaques meramente visuais.
4. **Áudio:** embeds padrão `![[audio.mp3]]` funcionam junto aos cartões e exemplos.

Mantenha os capítulos enxutos: apresente cada ponto gramatical uma vez, retome-o com wiki links e concentre cartões extras específicos do leitor em `_cards.md` ou deixe que ele capture palavras no fluxo de leitura via `_notes.md`.
