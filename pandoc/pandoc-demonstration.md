---
documentclass: article # tipo de publicação a padrão é article, pode ser [memoir,book,report ou qqr cls presente no diretório
title: Teoria dos Pombos # titulo do texto e do pdf
toc: true #adição ou não de sumário
numbersections: true
author:  # autores do texto
 - Pombo 1
 - Pombo 2
date: 2018.2 #data
lang: pt-br #linugagem utilizada no texto
keywords: [pombo, teoria computacional, física quântica]
abstract: |
  Aqui vai o seu resumo.

  Pode escrever usando \LaTeX  aqui também.
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
 \usepackage{animate}
 \tcbuselibrary{theorems}
 \newtcbtheorem{theorem}{Teorema}{colback=green!5,colframe=green!45!black,fonttitle=\bfseries}{th}
 \newtcbtheorem{coro}{Corolario}{colback=blue!5,colframe=blue!45!black,fonttitle=\bfseries}{cr}
 \newtcbtheorem{lemma}{Lema}{colback=orange!5,colframe=orange!35!black,fonttitle=\bfseries}{lm}
 \newtcbtheorem{define}{Definição}{colback=black!5,colframe=black,fonttitle=\bfseries}{lm}
 \newtcbtheorem{problem}{Problema}{colback=gray!5,colframe=gray!45!black,fonttitle=\bfseries}{lm}

# veja mais em https://pandoc.org/MANUAL.html#variables-for-latex
---

 <!-- pode-se usar comandos de latex normalmente -->
\newcommand{\teorema}[2]{\begin{theorem}{#1}{th} \textbf{Demonstração.}\\ #2 \qed \end{theorem}}
\newcommand{\corolario}[2]{\begin{coro}{#1}{cr} \textbf{Demonstração.}\\ #2 \qed \end{coro}}
\newcommand{\lema}[2]{\begin{lemma}{#1}{lm} \textbf{Demonstração.}\\ #2 \qed \end{lemma}}
\newcommand{\definicao}[2]{\begin{define}{#1}{lm}  #2 \end{define}}
\newcommand{\problema}[3]{\begin{problem}{#1}{lm} \textbf{Entrada:}  \textit{#2} \\ \textbf{Questão:} #3  \end{problem}}
\newpage

# Seção

Começa aqui então...

## Subseção

### Subsubseção

Essa é a maior profundidade para seções numeradas

## Subseção forçadamente não numerada{.unnumbered}

# Formatação

## Texto

Isso é _italico_, e isso **negrito**; Assim é it*áli*co no meio da palavra.
Assim é `monoespaçada`, e assim ~~riscado~~.

| Pode escrever assim,
|    para que mantenha a identação.
|    
|    Novas linhas
| e tal.

Usa-se o modelo do latex de $ para input matemático.  
$G(V_i, E_i) \mapsto H^{abc} \quad \forall i \in \overline{AB}$


Usa-se o dobro de $ para destaque

$$X_{j,t,i} = \begin{cases} 1, \text{se  $j$ é $t$, na máquina $i$}. \\ 0, \text{caso contrário} \end{cases}$$

Pode usar comandos próprios de \LaTeX

\newcommand{\tuple}[1]{\langle #1 \rangle}

$\tuple{a, b, c}$


Links podem ser feitos diretamente <https://google.com>, ou camuflados [assim](https://google.com)
Referência obscura.^[Nota de rodapé explicando referência obscura.] \newpage

## _Quoting_.
O Quote coloca uma frase em destaque a deslocando do texto.

> Aqui é uma quote

ela pode ter vários parágrafos

> Aqui uma quote de vários paragrafos
>
> taran!!!  

e pode ter outros textos em maior destaque

> Aqui uma quote
>
> > aqui uma quote aninhada
>
> volta.

## Code block

Aqui tem um code block; A linguagem a seguir está definida no arquivo lang.xml e é colorida a partir do arquivo def.theme

```{.pseudo .numberLines }
Function tree.Center(): Set<Vertex>
  var aux = self
  while aux.vertices.size >= 3 do
    variable leafs = aux.leafs
    aux = aux.induced(aux.vertices - leafs)
  return aux.vertices

```

E aqui `Function Sum(a,b) = a + b;`{.pseudo} um code _inline_.

# Estruturas

## Listas

### Lista simples

- A
- B
- C

### Lista com várias linhas

- Começo a falar aqui  
  termino em outra linha.
- B


### Listas com Listas

* fruits
  + apples
    - macintosh
    - red delicious
  + pears
  + peaches
* vegetables
  + broccoli
  + chard

### Lista numerada padrão

#. first
#. second
#. third

### lista numerada a partir de um nº

7. first
#. second
#. third

### Lista numerada diferente

i. first
#. second
#. third

<!--  -->

1) first
2) second
3) third

### Lista rastreavel.

(@) primeiro exemplo.
(@) segundo exemplo.

Explicações de exemplos

(@) terceiro exemplo.

### Lista referenciavel

(@st) Primeiro.
(@nd) Segundo.
(@banana) Terceiro.

Posso referenciar aqui os elementos (@st),(@nd),(@banana)

## Linhas

Utilizamos uma sequencia de  pelo menos 3 hífens ou asteriscos para definir uma linha.

-----------------------------------------------

***

## Tabelas

### Tabelas simples

As tabelas são alinhadas de acordo com a posição relativa entre o cabeçalho e a linha separadora.

se estiver _flushed_ para a direita (i.e. alinhado a última linha separadora ele alinhará o conteudo a direita). o mesmo se repete para esquerda e centro.

  Right     Left     Center     Default
-------     ------ ----------   -------
     12     12        12            12
    123     123       123          123
      1     1          1             1

Table:  Tabela simples.

### Tabelas sem cabeçalho.

Tabelas sem cabeçalho são alinhadas de acordo com a posição relativa do primeiro elemento.

-------     ------ ----------   -------
     12     12        12             12
    123     123       123           123
      1     1          1              1
-------     ------ ----------   -------

Table: Tabela sem cabeçalho.

### Tabela multi linha

-------------------------------------------------------------
 Centered   Default           Right Left
  Header    Aligned         Aligned Aligned
----------- ------- --------------- -------------------------
   First    row                12.0 Example of a row that
                                    spans multiple lines.

  Second    row                 5.0 Here's another one. Note
                                    the blank line between
                                    rows.
-------------------------------------------------------------

Table: Tabela
multi linha.

### Tabela com grid

: Tabela com grid.

+---------------+---------------+--------------------+
| Fruit         | Price         | Advantages         |
+===============+===============+====================+
| Bananas       | $1.34         | - built-in wrapper |
|               |               | - bright color     |
+---------------+---------------+--------------------+
| Oranges       | $2.10         | - cures scurvy     |
|               |               | - tasty            |
+---------------+---------------+--------------------+


\newpage
\problema{Ser Fruta.}{Uma parte $F$ de uma planta $P$}{$F$ é uma fruta de $P$?}
\definicao{Frutas}{
  Parte das plantas que
  $\mapsto$
  funcionam como proteção e suplemento às sementes.}
\teorema{Frutas são boas.}{São saborosas.}
\corolario{Banana é bom.}{Banana é uma fruta.}
\lema{Banana da terra é fruta.}{É uma banana.}

```{.dot scale="0.4" caption="Banana" label="my_lbl"}
digraph graphname{
  rankdir=BT;
  edge [style="-latex"  ];
  node [style=filled texmode="math" shape=circle fillcolor=darkolivegreen2];
  b[xlabel=tchu];
  a -> "\\Pi";
	b -- d;
}
```

\animategraphics[height=2.8in,autoplay,controls]{12}{./pandoc/imagepdf/animate_}{0}{57}

asdajksdkywiqtehfadvsdffdddd at \ref{my_lbl}

\begin{tikzpicture}
  \begin{scope}[opacity=0.7]
    \fill[red!30!white]   ( 90:1.2) circle (2);
    \fill[green!30!white] (210:1.2) circle (2);
    \fill[blue!30!white]  (330:1.2) circle (2);
  \end{scope}
  \node at ( 90:2)    {Typography};
  \node at (210:2)    {Design};
  \node at (330:2)    {Coding};
  \node [font=\Large] {\LaTeX};
\end{tikzpicture}

<!--
\begin{theorem}
blablbalba
bbalblabla
blablbalbaa
\end{theorem} -->
