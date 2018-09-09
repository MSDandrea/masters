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
Function ClusterEdit(Graph g, int remainingMovements): Graph{
  if g.hasP3()  {
    if remainingMovements = 0 {
      return null
    } else {
      var p3 = g.getP3()
      var g1 = g.removeEdge(p3.edges[0])
      var g2 = g.removeEdge(p3.edges[1])
      var g3 = g.addEdge(p3.vertices[0],p3.vertices[2])
      remainingMovements--
      return ClusterEditable(g1,remainingMovements)
            or ClusterEditable(g2,remainingMovements)
            or ClusterEditable(g3,remainingMovements)
    }     
  } else
      return g
}
```

Tal algoritmo é resolvível em tempo $\mathcal{O}(k^3 (n+m))$

## Cadeia mais próxima

Observe as seguintes definições

\definicao{Distancia entre strings}{Um inteiro que representa quantos caracteres são diferentes entre uma string $s$ e uma string $s'$}

\problema{Cadeia mais próxima}{Um conjunto de strings $S$ um inteiro $d$.}{Existe uma string $s$ tal que $distance(s,s_i) \leq d; \quad \forall s_i \in S$}


Um parâmetro intuitivo para o problema é a distância.

Usando esse parâmetro podemos formular o seguinte algoritmo, suponha o seguinte conjunto $S$ de strings:

----- -----
  ADB AAB
  BDB ABD
  JBD QAB
----- -----

Escolha uma string $s \in S$. Observe que para cada string em $S$ temos uma distânca a atual string.

Suponha $s = ADB$ e $d=2$, nossas distâncias são:

----- -----
    0 1
    2 2
    3 2
----- -----

Escolha agora um $s' \in S$ qualquer tal que $distance(s,s') > d$. Portanto seja $s' =  JBD$, escolhemos as $d+1$ posições onde $s$ difere de $s'$

| `0 1 2`
| `A D B`
| `J B D`  $\implies \{0,1,2\}$
| \color{red} `J B D` \color{black}

Para cada posição diferente realize a troca do caracter na string atual, logo:

| JDB:
|    ----- -----
|        1 2
|        1 3
|        2 2
|    ----- -----
|
|
| ABB:
|    ----- -----
|        1 1
|        1 1
|        2 2
|    ----- -----
|
|
| ADD:
|    ----- -----
|        1 2
|        1 1
|        2 3
|    ----- -----

Cada instância gerada deve estar a uma distância $d'=d-1$ para a próxima iteração. Observe que, se $distance(s,s_i) > d + d'$ esta instância é inviável, pois seria impossível reduzir a distânca para o esperado com os movimentos possíveis.

Observe que em nosso exemplo já encontramos $ABB$ que é uma solução possível, pois $\forall s \in S \; distance(s,ABB) \leq 2$.

O algoritmo é sintetizado a seguir.

```{.lang .numberLines}
Function ClosestString(Set<string> set,int maxDistance,
                       string current, int remainingDistance): string {
    if remainingDistance < 0 {
      return null
    }
    if set.Any(str -> {distance(current,str) > maxDistance + remainingDistance}){
      return null
    }
    if set.All(str -> {distance(current,str) <= maxDistance }){
      return current
    }
    var distant = set.First(str -> {distance(str,current) > maxDistance})
    var differentLettersPositions = distant.PositionOf(pos -> {
      distant[pos] != current[pos]
    })
    var range = differentLettersPositions[0...maxDistance]
    for position in range do {
      var newCurrent = current
      newCurrent[position] = distant[position]
      var result = ClosestString(set,maxDistance,newCurrent,remainingDistance-1)
      if result not null {
        return result
      }  
    }
    return null
}
```
