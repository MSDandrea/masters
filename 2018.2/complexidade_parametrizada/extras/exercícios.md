---
title: Exercícios de Parametrizada
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

# _Bounded search tree_


## Cluster editing

Observe as seguintes definições:

\definicao{Grafo Cluster}{Um grafo $G$ onde toda componente conexa $\delta_i$(G) é uma clique.}

\definicao{Grafo livre de $P_3$}{
  Um grafo $G$ é chamado de livre de $P_3$ se e somente se não possuir um grafo caminho com 3 vértices.
}

Dessa forma demonstraremos o seguinte teorema.

\teorema{Um grafo $G$ é cluster se e somente se é livre de $P_3$.}{
  Suponha por absurdo que $G$ não é livre de $P_3$ isso implica em que exista um subgrafo induzido $G'$ onde existem dois vértices não vizinhos na mesma componente, isso implica que alguma componente de $G$ não é uma clique o que é absurdo.\\

  Suponha agora que um grafo $H$ qualquer não possua $P_3$ isso implica em que dado quaisquer pares de vértices $u,v \in V(G)$ ou $ \exists (u,v) \in E(G)$, ou os vértices estão em componentes distintas de $H$, e portanto $H$ é um cluster.
}

Abordaremos o problema de cluster editing para esse exercício conforme descrito abaixo.

\problema{Cluster editing}{Um grafo $G$}{Qual é o menor número de arestas que podem ser removidas ou inseridas em $G$ que causam o grafo resultante ser um cluster.}

Como vimos acima, um grafo cluster é livre de $P_3$ e portanto podemos abordar o problema de cluster editing como o problema de eliminação de $P_3$ em um grafo $G$.  Para eliminar um p3 existem 3 possibilidades:

```{.dot scale="0.4" caption="Um P3"}
graph G {
  nodesep=2
  rankdir=LR
  node[shape=circle]
  A -- B[label=1]
  B -- C[label=2]
}
```

- Remover aresta 1
- Remover aresta 2
- Adicionar aresta entre A e C

Sabemos que é possível encontrar $P_3$ em tempo $\mathcal{O}(n+m)$ portanto usando o número de movimentos restantes como paramêtro segue o algoritmo.

```{.lang .numberLines }
Function ClusterEditable(Graph g, int remainingMovements): bool{
  if g.hasP3()  {
    if remainingMovements = 0 {
      return false
    } else {
      p3 = g.getP3()
      g1 = g.removeEdge(p3.edges[0])
      g2 = g.removeEdge(p3.edges[1])
      g3 = g.addEdge(p3.vertices[0],p3.vertices[2])
      remainingMovements--
      return ClusterEditable(g1,remainingMovements)
            or ClusterEditable(g2,remainingMovements)
            or ClusterEditable(g3,remainingMovements)
    }     
  } else
      return true
}
```

Tal algoritmo é resolvível em tempo $\mathcal{O}(k^3 (n+m))$

## Distância entre Strings
