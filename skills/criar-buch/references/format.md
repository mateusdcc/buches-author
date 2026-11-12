# Contrato de arquivos do Bücher

O Bücher lê o Markdown do vault. Para criar o Buch, não gere JavaScript, páginas HTML, índices de exercícios ou arquivos de controle próprios.

## Árvore de diretórios

```text
<Vault>/
└── Buches/
    └── Álgebra Linear/
        ├── _index.md
        └── concepts/
            ├── Espaços Vetoriais.md
            ├── Espaços Vetoriais/
            │   ├── Subespaços.md
            │   └── Subespaços/
            │       └── Interseções.md
            └── Transformações Lineares.md
```

- O plugin reconhece pastas filhas diretas de `Buches/` que contêm `_index.md`. O índice recebe `title`, `description` (opcional) e `icon` (opcional, por exemplo `lucide:sigma`). O nome de exibição pode diferir da pasta. O app gera currículo, progresso, árvore e folha de exercícios.
- Cada conceito é um arquivo `.md` em `concepts/`. Para ter filhos, mantenha o arquivo do pai e uma pasta irmã com **o mesmo nome do arquivo sem `.md`**, inclusive acentos e espaços. A regra vale para qualquer profundidade. Não crie uma pasta pai sem a nota correspondente.
- Em cada nota use `name` (título exibido), `description` (uma frase), `order` (número comparado entre irmãos), `category` (omitida no filho se herdada) e `depends_on` (lista YAML de pré-requisitos; use `[]` quando vazia). O leitor percorre pai, descendentes e próximo irmão. Atribua ordens distintas, com espaço para inserções. O primeiro H1 também é usado como título da página, então alinhe-o a `name`. Ícones `lucide:<nome>` são opcionais.
- Para novo conteúdo, use nomes de arquivo legíveis e caracteres compatíveis com o sistema de arquivos. Em um Buch existente, não renomeie capítulos apenas para mudar o título; altere `name` e o H1. Uma mudança estrutural de caminho exige atualizar todos os links e preservar as chaves de progresso.
- `_progress.md` e `_solutions/` ficam junto ao índice e são administrados pelo plugin. Um documento de trabalho sobre cobertura pode ficar na raiz do Buch, com nome distinto; ele não faz parte do currículo.

## Blocos e pré-requisitos

Tipos indexados: `definition`, `theorem`, `lemma`, `proposition`, `corollary`, `example`, `exercise`. O título e corpo podem estar em qualquer idioma; os identificadores de tipo ficam em inglês. Escreva cada linha do corpo com `>`, inclusive linhas vazias internas. Após o callout, deixe uma linha vazia e coloque a âncora em uma linha própria, por exemplo `^criterio-subespaco`. Use IDs únicos na nota, com letras ASCII, dígitos e hífens. Preserve esses IDs em revisões.

Use `depends_on` para pré-requisitos do capítulo e `block_depends_on` para pré-requisitos de um bloco ou exercício. As chaves do mapa são IDs sem `^`; os destinos são wiki links entre aspas no YAML. No mesmo arquivo, use `"[[#^id]]"`; para outro arquivo, use o caminho completo no vault sem `.md`, por exemplo `"[[Buches/Álgebra Linear/concepts/Espaços Vetoriais/Subespaços#^criterio-subespaco]]"`. Para apontar à página, omita `#^id`. Declare dependência só quando o resultado for necessário. Um wiki link no corpo é uma referência comum e não cria aresta de pré-requisito.

## Exercícios, dicas e soluções

- Um `[!exercise]` por problema ou grupo deliberado de subitens. Declare as hipóteses dentro do enunciado, pois a folha pode ser lida sem a página. Evite “como no exemplo acima”. O enunciado precede a âncora e fica visível.
- Logo após a âncora e antes da solução, escreva um ou mais callouts `[!hint]-`. A ordem no arquivo é a ordem das lâmpadas. Coloque pistas de estratégia nas dicas, não no enunciado. Não insira um título Markdown entre a pergunta e a solução.
- Delimite a solução com **duas linhas** isoladas contendo `---`. Para deixar espaço de trabalho em branco, mantenha o par com uma linha vazia entre ele. Use `***` se precisar de uma régua horizontal fora de soluções.
- Para uma demonstração pronta em LaTeX, comece o corpo com `<!-- buches-math: mathjax -->`. Para Typst, use `<!-- buches-math: typst -->` e a sintaxe que o vault usa. O leitor aceita matemática inline com `$...$` e em bloco com `$$...$$`; dentro de callouts, prefixe as linhas com `>`. O plugin pode materializar a solução em nota separada e deixar um embed `![[…]]`. Não apague nem substitua esse embed para atualizar a teoria.
- O botão **Mark solved** pertence ao usuário. Não marque exercícios novos como resolvidos ao gerar uma resposta ou solução.

Antes de entregar, siga a leitura em profundidade e confira órfãos, referências que não resolvem, pré-requisitos posteriores, ciclos, âncoras repetidas, dicas sem exercício e divisores sem par.
