---
title: Exercícios - Teoria dos Grafos
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

Suponha que $G$ é um grafo conexo que possui 2 caminhos distintos de forma que $|p_1| = |p_2|$ onde ambos são os maiores caminhos. Como $G$ é conexo existe pelo menos um caminho entre quaisquer vértices de $p_1$ e $p_2$, porém tal caminho é absurdo pois se o mesmo existir $p_1$ e $p_2$ não são os maiores caminhos, já que o caminho necessário teria uma soma dos vértices de $p_1$ e $p_2$. \qed

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

Observe que tal recursão só para quando ou existe um ciclo ou se atinge um vértice de grau ímpar (i.e $v$). Porém para que qualquer $w_i$ seja o fecho de um ciclo e não seja necessário a adição de mais um vértice ele precisa ser $v$ e portanto $\exists P[u,v]$ \qed

## 1.4

## 1.5

Tal regra é o mesmo que afirmar que, dado qualquer grafo $G$, existem 2 vértices $u,v$ tal que $d(u)=d(v)$
Observe que a regra é válida quando $k=2$.

```{.dot scale="0.3" caption="possíveis vizinhanças com 2 vértices"}
graph g {
  rankdir=LR
  subgraph h{
    a[label="a"]
    b[label="b"]
  }
  subgraph j{
    c[label="a"]
    d[label="b"]
    c -- d
  }
  {rank=same a; c}
  {rank=same b; d}  
}
```

Suponha que a regra seja valida para algum $k>2$, mostraremos que também é valida para $k+1$.

Queremos adicionar o $k+1$-ésimo vértice ($v$) ao grafo $G_k$, se o vértice é isolado a propriedade se mantém, o mesmo acontece quando o vértice é universal. Para que a regra falhe é necessário que exista um número $j$ de vizinhos de $v$ em $G_k$ tal que a regra não seja válida, porém $0 < j < k$ onde a propriedade é sempre válida, então não existe tal configuração e a regra se aplica a $k+1$. \qed


## 2.3

Queremos mostrar : $G$ é floresta  $\iff |E(G)| = |V(G)| - \omega(G)$.


Seja $G$ uma floresta formada por $\omega(G)$ árvores, toda árvore $a_i$ tem $n_i$ vértices e consequentemente $n_i - 1$ arestas. Sendo assim se somarmos todas as árvores temos $\sum\limits_{i=1}^{\omega(G)}|E(a_i)|= \sum\limits_{i=1}^{\omega(G)}(|V(a_i)| - 1)$ que implica em:
$$|E(G)|= |V(G)| - \omega(G)$$.

A contra partida se mostra semelhante devido ao Teorema 2.3. Observe que a regra é válida para $\omega(G)=1$.

Suponha que valha para algum $k > 1$, mostraremos que vale então para $k+1$.

$\sum\limits_{i=1}^{k+1}|E(a_i)|= \sum\limits_{i=1}^{k+1}(|V(a_i)| - 1)$

$\sum\limits_{i=1}^{k}|E(a_i)| + |E(a_{k+1})|= \sum\limits_{i=1}^{k}(|V(a_i)| - 1) + |V(a_{k+1})| -1$

$|E(a_{k+1})| = |V(a_{k+1})| - 1$

e portanto $a_{k+1}$ é arvore. \qed
