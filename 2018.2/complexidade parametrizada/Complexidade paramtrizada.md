---
title: Complexidade Parametrizada
author: Matheus Souza D'Andrea Alves
institute: UFF
date: 2018.2
header-includes: | # pacotes latex para uso no texto
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

# Introdução

## Complexidade clássica

Suponha um problema $\Pi$, se $\Pi$ possui um algoritmo que o resolve em tempo polinomial dizemos que $\Pi \in P$.

Se dado um certificado de resposta sim para $\Pi$ se posso validar tal resposta em tempo polinomial então $\Pi \in NP$.

Chamamos de $NP-Completo$ a classe de problemas $\Pi'$ no qual dado o problema $3-SAT$ $3S$ $3s \propto \Pi'$.

## Complexidade Parametrizada

### O que traz de diferente?

Une teoria e prática, não ignorando nuances práticas de um problema sabidamente NP-Completo, resolve problemas.
Difere de heurísticas e aproximações, pois não perde garantia de tempo ou otimalidade.

O objetivo é desenvolver um algoritmo $\mathcal{O}(f(k).n^{\mathcal{O}(1)})$. Se um problema $\Pi$ admite uma solução dessa forma, dizemos que $\Pi \in FPT$. Quando isso ocorre, afirmamos que existe um pré-processesamento capaz de reduzir a entrada obtendo uma instância menor, limitado por $k$, chamamos isso de kernelização; Uma solução para o kernel é uma solução para o problema.

Características
 - $FPT \subset XP$

# Técnicas de FPT

## Bound search Tree

## Kernelização

Dizemos que se um problema possui um kernel, então por definição o mesmo é FPT.

### Pré processamento

chamamos de pré processamento um conjunto de regras que aplicados a uma instancia do problema, pode ou não retirar composições da entrada de forma a podar a instãncia.

Suponha um problema $\Pi$, que tem entrada $I$ um parametro $k$ e uma questão $q$.

Uma kernelização é um algoritmo de pré processamento que recebe $I$ como entrada com o paramêtro $k$, e retorna uma instância do problema e um inteiro representatne do paramêtro.

$$f(k) \mapsto |I'|$$
$$g(k) \mapsto k' $$

### O quão bom pode ser?

Depende de como se planeja abordar o problema, suponha dois algoritmos de kernelização, $A$ e $B$; Se $A$ chega a um kernel de tamanho $\theta(k)$ em tempo $\theta(n^2)$, e $B$ chega a um tamanho $\theta(k^2)$ em tempo $\theta(n)$ na literatura, diríamos que $A$ é _melhor_ pois nos dá um kernel menor.

\teorema{Se $(\Pi, k) \in FPT$ então $(\Pi, k)$ admite um kernel.}{
  Como $(\Pi,k) \in FPT$ logo o mesmo pode ser resolvido por um algoritmo $A$ em tempo $f(k)n^c$ para $c$ constante.

  Considere portanto a seguinte kernelização.
  \begin{itemize}
  \item Execute os $n^{c+1}$ passos de $A$.  
  \item O problema foi resolvido?  
  \begin{itemize}  
    \item Sim:  
    \item Não: logo $f(k)n^c > n.c \implies f(k)>n$ logo a entrada já era um kernel.
  \end{itemize}
\end{itemize}
}
