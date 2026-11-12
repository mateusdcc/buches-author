---
name: "Soma direta de subespaços"
description: "Caracterizar a unicidade da decomposição e testar a necessidade das hipóteses."
category: "Espaços vetoriais"
order: 20
depends_on: []
block_depends_on:
  criterio-soma-direta:
    - "[[#^soma-direta]]"
  provar-criterio:
    - "[[#^criterio-soma-direta]]"
  tres-subespacos:
    - "[[#^criterio-soma-direta]]"
---

# Soma direta de subespaços

Fixe um corpo $F$ e um espaço vetorial $V$ sobre $F$. Suponha conhecidas as operações herdadas por um subespaço. Ao inserir esta página num livro, declare em `depends_on` o link para a definição canônica de subespaço desse livro.

> [!definition] Soma direta
> Para subespaços $U,W\le V$, a soma é $U+W=\{u+w:u\in U,\ w\in W\}$. Ela é direta, denotada $U\oplus W$, se cada vetor de $U+W$ admite uma única decomposição dessa forma.

^soma-direta

> [!theorem] Critério para dois subespaços
> A soma $U+W$ é direta se e somente se $U\cap W=\{0\}$.

^criterio-soma-direta

> [!exercise] Provar as duas direções
> Prove o critério de soma direta. Justifique por que a existência de uma decomposição e sua unicidade são questões distintas.

^provar-criterio

> [!hint]- Comparar decomposições
> Subtraia duas decomposições do mesmo vetor e verifique a que subespaços pertence a diferença.

> [!hint]- Testar o zero
> Para a direção inversa, escreva zero usando um elemento de $U\cap W$ e seu oposto.

---
<!-- buches-math: mathjax -->
A existência vem da definição de $U+W$. Se $u+w=u'+w'$, então $u-u'=w'-w\in U\cap W$; quando a interseção é trivial, as parcelas coincidem. Na outra direção, se $x\in U\cap W$, então $0=x+(-x)=0+0$. A unicidade força $x=0$.
---

> [!exercise] A hipótese muda com três subespaços
> Em $F^2$, encontre três subespaços com interseções dois a dois triviais cuja soma não é direta. Formule um critério correto para $U+W+Z$ ser direta e prove-o.

^tres-subespacos

> [!hint]- Procure uma relação
> Experimente os espaços gerados por $e_1$, $e_2$ e $e_1+e_2$. Para o critério, agrupe $U+W$ antes de comparar com $Z$.

---

---
