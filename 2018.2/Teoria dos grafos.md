---
title: Teoria dos Grafos
author: Matheus Souza D'Andrea Alves
date: 2018.2
lang: pt-br
header-includes: |
 \usepackage{mathtools}
---

\tableofcontents
\pagebreak
# Introdução

[site do protti](http://www2.ic.uff.br/~fabio/teografos.html)

## Conceitos básicos

Um _grafo simples_ $G$ é denotado por um conjunto de vértices $V(G)$ e um conjunto de arestas $E(G)$.

Cada aresta é um par não ordenado $(u,v)$ | ($\{u,v\} \subseteq V(G)$). Dois vértices $u$ e $v$ são vizinhos/adjacentes se existe uma aresta $(u,v) \in E(G)$.

A ordem de um grafo é o numero de vértices de $G$

> $n = |V(G)|$ & $m = |E(G)|$

Um grafo é _trivial_ se possuí apenas um vértice e _nulo_ se não possuí vértice.
Um _multigrafo_ são grafos simples extendidos com:

- **Arestas paralelas**: Arestas que conectam os mesmos dois vértices.
- **Laços**: arestas em que ambos os extremos são o mesmo vértice.

## Vizinhança

A vizinhança aberta de um vértice $v$ é denominada $N(v)$; Tal conjunto possuí todo vértice que seja um extremo de arestas que tenham $v$ como outro extremo.

A vizinhança fechada de um vértice é denominada $N[v]$ onde $N[v]=N(v)+v$.

## Grau

O grau de um vértice, denominado $d(v)$ é igual ao número de vezes em que $v$ aparece como algum terminal em qualquer $e \in E(G)$.

Um grafo é dito regular quando todos seus vértices tem o mesmo grau, e $k$-regular se todos os vértices tem $d(v)=k$.

O grau máximo de $G$  é definido como:

> $\Delta(G) = max\{d(v) | v \in V(G)\}$

Dado um grafo $G$, sua sequência de graus é a sequencia formada pelos graus de seus vértices ordenados de forma não decrescente.

Se um vértice possui grau zero, então ele não possui vizinhos e é chamado de vértice _isolado_. Em contrapartida se um vértice é vizinho de todos os outros vértices em um grafo ele é chamado de vértice _universal_.

## Estruturas relacionadas

O complemento de $G$ é chamado de \emph{Gê barra} e denominado por $\overline{G}$.

Um grafo $H$ é um subgrafo de $G$ se $V(H) \subseteq V(G)$ e $E(H) \subseteq E(G)$, e o grafo "faça sentido", isso é seja possível criar um grafo com todos os vértices e arestas de tais subconjuntos.

Um subgrafo _gerador_ de $G$ é um subgrafo $H$ de $G$ onde $V(H) \subseteq V(G)$

$H$ é um subgrafo induzido por um conjunto de vértices $X \subseteq G$ se toda aresta nesse conjunto existente em $G$, também existe em $H$, sua notação é: $H=G[X]$. Um subgrafo $H$ é o subgrafo formado por um conjunto de arestas $E'[ \in E(G)$ com seus respectivos extremos, sua notação é $H=G[E']$.

Seja $S \subset V(G)$:

> $G - S = G[V(G) \backslash S]$

Isso é, O Grafo $G$ sem os vértices em $S$ é o subgrafo induzido pelo conjunto de todos os vértices de $G$ tirando os vértices de $S$

Um passeio é uma sequencia de vértices $v_1,v_1,v_1,v_1$ ligadas sequencialmente por arestas.

Uma trilha é um passeio onde arestas não se repete; Um caminho é uma trilha onde nenhum vértice se repete.
É chamado de comprimento do caminho o número de arestas no mesmo, um caminho é chamado fechado se ...

Um ciclo é um passeio onde nenhum vértice exceto o inicial se repete, e apenas repetindo o inicial no final do passeio, seu número de vértices é igual ao seu númeor de arestas.

Uma corda é uma aresta que liga dois vértices não consecutivos do ciclo

## Propagação de propriedades.

Dado um grafo $G$ uma propriedade é hereditária por subgrafos, e quando ela vale para $G$ ela também vale para seus subgrafos.

Se uma propriedade é hereditária para subgrafos, ela é para subgrafos induzidos.

## Operações

A união de dois grafos é a união de seus vértices e suas arestas, a operação de interseção é semelhante.

teorema do aperto de mão:

> $2m = \sum\limits_{v \in V(G)} d(v)$

Dois grafos são isomorfos se existe uma bijeção $f$ dos vértices de $G$ para vértices de um $G_{iso}$ tal que $\forall (u,v) \in E(G) \implies (f(u),f(v)) \in E(G_{iso})$

## Características

Um grafo é dito completo, se quaisquer dois vértices de $G$ são vizinhos.
O número de arestar de um grafo completo é $n(n-1)/2$.

Um grafo é conexo se para todo par de vértices dado, existe um caminho entre os dois vértices. Uma componente conexa de $G$ é um subgrafo conexo maximal de $G$. $\omega(G)$ é o númeor de componentes conexas de $G$.

A distância entre dois vértices é o comprimento do menor caminho entre eles.

A excentricidade de um vértice $v \in V(G)$ é definida como:

> $exc(v) = max \{ dist(v,x) | x \in V(G)\}$

O diâmetro de um grafo $G$ é definido como:

> $diam(G) = max \{exc(x) | x \in V(G)\}$

O centro $C \subseteq V(G)$ é o subconjunto de vértices com excentricidade mínima, em contrapartida a periferia de um grafo $G$ é o subconjunto de vértices com excentricidade máxima.

## Partições

Uma clique $K$ em um grafo $G$ é um conjunto de vértices $K \subseteq V(G)$ tal que $G[K]$ é completo.
Por outro lado se o conjunto de vértices $S \subseteq V(G)$ induz um grafo sem arestas, então $S$ é um conjunto independente.

Notação: $K_n$ _grafo completo com $n$ vértices_, $S_n$ _conjunto independente com $n$ vértices_.

## Maximalidade e minimalidade

Um conjunto $S$ é maximal em relação a uma propriedade $P$, se:

- $S$ satisfaz $P$
- $\nexists S' \supset S$ tq $S'$ satisfaz $P$.

Um conjunto $S$ é minimal em relação a uma propriedade $P$ se:

- $S$ satisfaz $P$
- $\nexists S' \subset S$ tq $S'$ satisfaz $P$.

## Representações.

Representação gráfica.
Matriz de adjacências


# Primeiro módulo

## Árvores

## Conectividade

# Segundo módulo

## Grafos eurelianos e hamiltonianos

## Emparelhamento

## Coloração de Arestas

# Terceiro módulo

## Coloração de vértices

## Planaridade

## Grafos direcionados
