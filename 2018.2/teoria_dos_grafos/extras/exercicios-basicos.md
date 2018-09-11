---
title: Exercícios - Conceitos básicos
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


## 1.1

Tal demonstração é proporcional a demonstrar que em qualquer grafo com $n \geq 6$ ou existe um $K_3$ ou um $I_3$ induzido.

  Suponha por absurdo que $G$ não possui nem $K_3$ ou $I_3$ induzidos. Observe que se $G$ é bipartido ele necessariamente possui um $I_3$ , para que não exista é necessário um ciclo ímpar.

  Porém ele não pode possuir um $K_3$ e portanto deve possuir um ciclo de tamanho 5, pois ciclos de tamanho maior que 5 possuem $I_3$.

  Como sabemos que $G$ não possuí um ciclo induzido de tamanho 3 todo ciclo de tamanho cinco é da seguinte forma

  ```{.dot scale="0.3" caption="$C_5$"}
  graph G {
    node[shape=circle]
    edge[len=5]
    A -- B;
    A -- C;

    { rank=same B; C };
    { rank=same D -- E };

    C -- E ;
    D -- B ;
  }
  ```

  Observe que neste $C_5$ sempre é possível obter um $I_2$. Sabemos que $G$ possui pelo menos seis vértices, suponha sem perda de generalidade um $I_2 = \{D,C\}$, suponha um vértice $v \in V(G)- V(C_5)$ para que não exista um $I_3$ em $G$ é necessário que $v$ seja vizinho de pelo menos 3 dos seguintes vértices $B,C,D,E$, porém qualquer composição dessa nos dá um $K_3$ e é portanto absurda .

  Logo todo $G$ com $n > 5$ possui ou um $K_3$ ou um $I_3$. \qed

## 1.2

Suponha que $G$ é um grafo conexo que possui 2 caminhos distintos de forma que $|p_1| = |p_2|$ onde ambos são os maiores caminhos. Como $G$ é conexo existe pelo menos um caminho entre quaisquer vértices de $p_1$ e $p_2$, porém tal caminho é absurdo pois se o mesmo existir $p_1$ e $p_2$ não são os maiores caminhos, já que o caminho necessário teria uma soma dos vértices de $p_1$ e $p_2$.

## 1.3

Suponha $u,v \in V(G)$ os vértices de grau ímpar. Sem perda de generalidade considere $u$, como $u$ possui grau ímpar ele precisa possuir necessariamente pelo menos um vizinho. Se tal vizinho $w_1$ não é $v$ então $w_1$ é par e precisa de mais um vizinho, e assim sucessivamente.

```{.dot scale="0.3" caption="Construção"}
graph G {
  node[shape=circle]
  rankdir=LR
  u -- w_1 -- w_2
  w_2 -- w_n[style="dotted"]

}
```

Observe que tal recursão só para quando ou existe um ciclo ou se atinge um vértice de grau ímpar (i.e $v$). Porém para que qualquer $w_i$ seja o fecho de um ciclo e não seja necessário a adição de mais um vértice ele precisa ser $v$ e portanto $\exists P[u,v]$
