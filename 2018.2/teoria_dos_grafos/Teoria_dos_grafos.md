---
title: Teoria dos Grafos
author: Matheus Souza D'Andrea Alves
date: 2018.2
lang: pt-br
header-includes: |
  \usepackage{tikz}
  \usetikzlibrary{shapes,arrows}
  \usepackage{mathtools}
  \usepackage{amsmath}
  \usepackage{amsthm}
  \usepackage{tcolorbox}
  \usepackage{pgfplots}
  \usetikzlibrary{intersections}
  \usetikzlibrary{patterns}
  \usepackage{multicol}
  \usepackage{graphicx}
  \tcbuselibrary{theorems}
  \newtcbtheorem{theorem}{Teorema}{colback=green!5,colframe=green!45!black,fonttitle=\bfseries}{th}
  \newtcbtheorem{coro}{Corolario}{colback=blue!5,colframe=blue!45!black,fonttitle=\bfseries}{cr}
  \newtcbtheorem{lemma}{Lema}{colback=orange!5,colframe=orange!35!black,fonttitle=\bfseries}{lm}
  \newtcbtheorem{define}{Definição}{colback=black!5,colframe=black,fonttitle=\bfseries}{lm}
  \newtcbtheorem{problem}{Problema}{colback=gray!5,colframe=gray!45!black,fonttitle=\bfseries}{lm}
---

\newcommand{\teorema}[2]{\begin{theorem}{#1}{th} \textbf{Demonstração.}\\ #2 \qed \end{theorem}}
\newcommand{\corolario}[2]{\begin{coro}{#1}{cr} \textbf{Demonstração.}\\ #2 \qed \end{coro}}
\newcommand{\lema}[2]{\begin{lemma}{#1}{lm} \textbf{Demonstração.}\\ #2 \qed \end{lemma}}
\newcommand{\definicao}[2]{\begin{define}{#1}{lm}  #2 \end{define}}
\newcommand{\problema}[3]{\begin{problem}{#1}{lm} \textbf{Entrada:}  \textit{#2} \\ \textbf{Questão:} #3  \end{problem}}

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

Um grafo é bipartido quando é possível particionar seu conjunto de vértices em dois conjuntos $S_1$ e $S_2$ tal que $S_1 \cup S_2 = V(G)$ e $S_1 \cap S_2 = \emptyset$ onde ambos $S_1$ e $S_2$ são conjuntos independentes.


\teorema{Um grafo $G$ é bipartido, se e somente se, $G$ não contém ciclos ímpares.}{
  Suponha por absurdo que $G$ seja bipartido e contenha um ciclo ímpar  $C = v_1,v_2,\ldots,v_{2k+1}, v_1$ seja $S_1 \cup S_2$ seja uma bipartição de $V(G$, suponha portanto sem perda de generalidade que $v_1 \in S_1$, dessa forma, $v_2 \in S_2, v_3 \in S_1, \ldots, v_{2k} \in S_2, v_{2k+1} \in S_1$. Porém dessa existe a aresta $()$
}


## Maximalidade e minimalidade

Um conjunto $S$ é maximal em relação a uma propriedade $P$, se:

- $S$ satisfaz $P$
- $\nexists S' \supset S$ tq $S'$ satisfaz $P$.

Um conjunto $S$ é minimal em relação a uma propriedade $P$ se:

- $S$ satisfaz $P$
- $\nexists S' \subset S$ tq $S'$ satisfaz $P$.

## Representações.

Representação gráfica.

![fig](./extras/Teoria dos grafos/repre.png){width=100px }

Matriz de adjacências


# Primeiro módulo

## Árvores

### Conceito

Dizemos que um grafo é uma árvore se não possui ciclos e é conexo, uma floresta é um grafo cuja cada componente conexa é uma árvore.

O centro de uma árvore são um ou dois vértices:

**Algoritmo**
\newpage


```ruby
def center(t Tree)
  m = t
  while m.vertices.size >= 3 do
    leafs = m.leafs
    m = m[m.vertices - leafs]
  end
  return m
end
```

## Conectividade

Articulações são vértices cuja a remoção aumenta o número de componentes conexas do grafo.

Teorema:
$v$ é articulação $\iff$ $\exists x,y$ tal que todo caminho entre $x$ e $y$ contém $v$

Demonstração:
Como $v$ é articulação, após sua remoção a componente conexa que continha $v$ não mais existe. São criadas duas componentes conexas $C_1$ e $C_2$. Tome $x \in V(C_1)$ e $y \in V(C_2)$ seja $P$ um caminho de $x$ a $y$ em $G$. Em $G-v$, o caminho $P$ não existe. Logo, $v \in V(P)$.

Em $G-v$ não pode haver nenhum caminho entre $x$ e $y$, pois de acordo com a premissa, a remoção de $v$ remove todos os possíveis caminhos entre os mesmos, isso significa que a remoção de $v$ aumentou o número de componentes conexas, logo $v$ é uma articulação.

\teorema{Em uma árvore $T$ não trivial, $v$ é articulação se e somente se $v$ não é folha.}{

  Suponha por absurdo que $v$ é uma folha, como visto anteriormente existe então dois vértices $x$ e $y$ cujo o caminho entre eles passa por $v$, tal afirmação é contraditória pois $v$ é uma folha e tem $d(v)=1$, sendo impossível fazer parte de um caminho não sendo extremidade.\\

  Seja $u$ um vértice não folha, portanto existe um caminho entre dois vértices $x$ e $y$ que contém $v$, suponha por absurdo que a remoção de tal vértice não aumente o número de componentes conexas, tal afirmação é absurda, pois isso implicaria em um caminho entre $x$ e $y$ que não contém $v$, o que implica em um ciclo e $T$ é uma árvore.}


\corolario{Todo grafo $G$ conexo não trivial possui pelo menos 2 vértices que não são articulações}{

  Seja $T$ a árvore geradora de $G$ e $x$ e $y$ folhas de $T$. Usando o teorema anterior, $x$ e $y$ não são articulações em $T$.

  Portanto, como $T-x$ é árvore geradora de $G-x$, sem perda de generalidade $x$ e $y$ não são articulações em $G$.
}

\teorema{Seja $G$ um grafo com pelo menos 3 vértices. G é biconexo se e somente se para cada par de vértices em $V(G)$ existem dois caminhos disjuntos entre eles.}{
  Seja $\kappa(G)$ o menor número de vértices tal que sua remoção desconecta G $\omega(G-\kappa(G)) > \omega(G)$.\\

  $G$ é $p$-conexo quando $p \leq \kappa(G)$.\\

  Portanto observe que se $G$ é biconexo e existe um par de vértices $u$ e $v$ tal que só existe um caminho em $G$, por definição algum vértice de tal caminho é articulação e sua remoção desconecta $G$ e portanto $\kappa(G) = 1 \implies 2 \leq 1$ que é absurdo. Assumindo portanto que para todo par de vértices em $G$ existem dois caminhos, é impossível tornar o grafo desconexo removendo apenas um vértice, logo $\kappa(G) \geq 2$ e $G$ é biconexo.

}

\teorema{ Seja $G$ um grafo com $k+1$ vértices. $G$ é $k$-conexo se e somente se para quaisquer dois vértices de $G$ existem $k$ caminhos internamente disjuntos entre eles.}{
  
}

# Segundo módulo

## Grafos eurelianos e hamiltonianos

## Emparelhamento

## Coloração de Arestas

# Terceiro módulo

## Coloração de vértices

## Planaridade

## Grafos direcionados
