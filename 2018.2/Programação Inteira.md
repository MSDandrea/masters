---
title: Programação Inteira
author: Matheus Souza D'Andrea Alves
date: 2018.2
lang: pt-br
header-includes: |
 \usepackage{mathtools}
 \usepackage{amsmath}
---

\tableofcontents
\pagebreak

# Introdução



## Infos gerais
[Site](www.ic.uff.br/~yuri/pi.html)

Salas:

- 2ª 306
- 4ª 202

Para a parte prática vamos implementar modelos e soluções usando o [CPlex]()
## Programação linear

É um problema de otimização onde tanto a função objetivo quanto as restriçĩes são lineares.

min/max c^tX

A_x <eq b
X >eq 0

Modelagem

 - Defina as variáveis do problema $\to$ como representar uma solução do problema
 - Definir as restrições do problema $\to$ limites que definem o conjunto de pontos viáveis.
 - A função objetivo $\to$ que vai ponderar cada solução

### Fluxo máximo
Existe um grafo direcionado $G=(V,E)$ com um e apenas um vértice fonte e sumidouro, $\forall (i,j) \in E(G)$ tem uma capacidade $C_{i,j}$. Queremos maximizar a quantidade de produto que passa de $F \to S$

**São minhas variáveis**: $X_{i,j} \to \forall(i,j) \in E(G)$. Representando a quantidade de produto que sai de $i$ e chega em $j$.

**São minhas restrições**: $X_{i,j} < C_{i,j}$;
<!-- $\forall i \in V \backslash {F,S} \sum\limits_{j \in N^{-}(i)} = \sum\limits_{i \in N^{+}(j)} $ -->

**É meu objetivo**: $max\{\sum\limits_{j \in N^{+}(S)} X_{j,s}\}$


### Para solução

Métodos:

- Simplex (exponencial, rápido)
- Ponto Interiores (polinomial, rápido)

# Modelagem

## Categorização em formulação matemática

As categorias quando modelamos problemas em matemática caem nas seguintes categorias.

- Linear ou não linear
- Convexo ou não-convexo
- Contínuo ou Discreto
- Estocástica ou Determinismo

Dentro dessa categorização a programação inteira busca resolver os problemas:

- Discretos
- Determinísticos
- Não convexos
- Lineares e não lineares

Isso faz com que seja possível resolver a maioria dos problemas combinatórios propostos em computação.

## Composição de um problema

Um problema de programação matemática é composto de :

- Variáveis de decisão
- Restrições
- Função objetivo
- Parametro de entrada

Um problema de programação inteira tem formato:
$$
\begin{cases}
 min/max\{f(x)\}\\
 g_i(x) \left.
 \begin{cases}
 \leq \\
 = \\
 \geq
 \end{cases}
 \right\} b_i \\
 x \in X | X \text{é discreto}
\end{cases}
$$

Definição:

**Solução viável**: valores atribuidos as variáveis que respeitam as Restrições.
**Solução ótima**: é uma solução viável que maximiza/minimiza a função objetivo.

Forma padrão:

$$
\begin{cases}
 max C^Tx\\
 A_x \leq b\\
 x \in Z_{+}^p * R_{+}^{n-p}
\end{cases}
$$

A melhor formulação possível, é uma formulação que defina a involtória convexa dos pontos inteiros, i.e. as o poliedro minimal que contém  toda solução inteira, se isso acontecer conseguimos resolver através de PL, e logo resolver de forma polinomial.

Porém, a involtória convexa não é conhecida, ou sua representação é exponencial.

## Modelando com variáveis inteiras.

### Impor que uma ação x só pode ser feira se outra ação y for realizada.   

 > $x,y \in [0,1] | y \leq x$

**Problema da Localização Facilitada:**

 - Conjunto de facilidades $J$
 - Conjunto de Clientes $I$

 Que facilidades precisam ser abertas para atender as demandas dos Clientes a um custo mínimo?

 Seja $C_{i,j}$ o custo da facilidade $j$ atender o cliente $i$. $f_j$ o custo da abertura de uma facilidade.

 **Variáveis**:

 $$
 X_{j,i} = \begin{cases} 1\text{, se $j$ atende $i$} \\ 0, \text{caso contrário.} \end{cases}
 $$

 $$
 Y_{j} = \begin{cases} 1\text{, se $j$ aberto} \\ 0, \text{caso contrário.} \end{cases}
 $$

**Restrições**:

$$X_{j,i} \in \{0,1\}, \forall j \in J, \forall i \in I$$

$$Y_j \in \{0,1\, \forall j \in J$$

$$\sum\limits_{j \in J}X_{j,i} , \forall i \in I$$

$$|I|Y_{j} \geq \sum\limits_{i \in I} X_{j,i}$$

### Impor que uma variável $X$ assumir apenas um dos valores de um conjunto finito $A={a_1,a_2,..,a_m}$

$$ Y_i = \begin{cases} 1, \text{se $X$ assume $a_i$ }. \\ 0, \text{caso contrário} \end{cases} $$

$$\sum\limits_{i=1}^{m} Y_i = 1 $$

$$X = \sum\limits_{i=1}^{m} Y_i a_i$$

# Otimização relaxamento limites

# _Branch and bound_

# Plano de corte

# _Branch and cut_

# Relaxação Lagrangiana

# Geração de colunas em PI

# _Branch and Price_

# Teoria Poliédrica

## Cortes

## Faces

## Facetas
