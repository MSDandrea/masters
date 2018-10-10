---
bibliography: bibliografia.bib
---

\title{\sc UNIVERSIDADE FEDERAL FLUMINENSE \\ Instituto de Computação \\ Programa de Pós-Graduação em Computação \\ \vspace{1cm}
       PROPOSTA DE ESTUDO ORIENTADO \\ \vspace{1cm}
       Coloração de Grafos$(r,\ell)$}

\author{Aluno: Matheus S. D'Andrea Alves \\ \underline{Orientador}: Uéverton dos Santos Souza}
\vspace{1cm}
\date{26 de setembro de 2018}

\maketitle


\maketitle
\thispagestyle{empty}

\vspace{1cm}
\begin{center}

\underline{\hspace{10cm}}\\
 Matheus Souza D'Andrea Alves \vspace{.5cm}
\vspace{2cm}
\underline{\hspace{10cm}}\\
Uéverton dos Santos Souza (D.Sc., UFF)
\end{center}

\newpage
\newpage


#  \sc Descrição do tema

A proposta do trabalho é a de pesquisar e desenvolver algoritmos parametrizados para o problema de Coloração própria quando aplicados a Grafos$(r,\ell)$.

#  \sc Introdução

Uma das principais motivações do estudo de classes de grafos é o fato de que diversos problemas, que são difíceis para grafos em geral, tornam-se tratáveis quando restritos a classes especiais de grafos. Assim, busca-se delimitar a partir de que ponto um determinado problema pode ser resolvido de forma eficiente.
Particularmente, o problema de particionamento em grafos tem despertado muito interesse devido às pesquisas de grafos perfeito e também pela procura de algoritmos eficientes para o reconhecimento de determinadas classes de grafos.
O problema de partição de grafos pode ser descrito como tendo por objetivo particionar o conjunto dos vértices de um grafo em subconjuntos $V_1,V_2,
\ldots, V_k$ onde $V_1 \cup V_2 \cup \ldots \cup V_k = V$ e $V_i \cap V_j = \emptyset$, $i \neq j$, $1 \leq i \leq k$ e $1 \leq j \leq k$, exigindo-se, porém, algumas propriedades sobre estes subconjuntos de vértices. Estas propriedades podem ser \textit{internas}, como por exemplo exigir que os vértices de cada subconjunto $V_i$ sejam dois-a-dois adjacentes (isto é, $V_i$ seja uma clique) ou dois-a-dois não-adjacentes (isto é, $V_i$ seja um conjunto independente), ou \textit{externas}, onde as exigências são feitas sobre os pares de $V_i\times V_j$, podem ser adjacentes ou não-adjacentes entre si.

Um problema bem conhecido é o de verificar se um dado grafo $G$ é split, isto é, verificar se os vértices de $G$ podem ser particionados em dois subconjuntos, dos quais um é independente e o outro uma clique. Brandstädt foi o responsável por generalizar a definição de split no que chamamos aqui de Grafos$(r,\ell)$, um grafo que pode ser particionado em $r$ conjuntos independentes e $\ell$ cliques.

Em outra perspectiva o problema de coloração de vértices de um grafo também é de grande interesse, tendo suas aplicações em diversas áreas; \emph{Pattern matching}, escalonamento em esportes e no trânsito, e resolução de problemas de \emph{Sudoku} são alguns exemplos de problemas onde a coloração de grafos pode ser empregada. O problema de coloração mínima dos vértices de um grafo chamado também de coloração própria de um grafo é descrito como a atribuição de cores em um grafo $G$ de forma que seja possível atribuir a cada um dos vértices de $G$ uma entre $k$ cores de forma que, dado quaisquer dois vértices vizinhos em $G$ eles não compartilhem uma mesma cor e $k$ seja o menor número onde tal restrição é atingida.

Ainda são poucas as pesquisas realizadas quanto a coloração em Grafos$(r,\ell)$. Pretendemos com o trabalho a desenvolver explorar esse nicho sob perspectivas de complexidade computacional e parametrizada.

# \sc Objetivos e Resultados Esperados

Desejamos para expandir o estado atual do conhecimento de coloração em Grafos$(r,\ell)$ obter principalmente três resultados.

- Uma dicotomia $\mathcal{P}/\mathcal{NP}$ para o problema.
- Uma análise sob a perspectiva parametrizada do problema.
- Algoritmos parametrizados que o solucionem ou provas de impossibilidade de parametrização.

Após a pesquisa obter tais resultados pretendemos o estruturar para submetê-lo à publicação e apresentação em congresso.

# \sc Critérios de Avaliação

Durante o estudo orientado serão realizadas apresentações semanais do desenvolvimento da pesquisa, e desenvolvido um artigo
técnico com os resultados obtidos.
O aluno será avaliada de acordo com seu desempenho nas apresentações semanais e pela qualidade do artigo final obtido.
Os critérios utilizados para avaliação serão: Qualidade das apresentações semanais; avanço semanal da pesquisa; qualidade dos resultados obtidos.

# \sc Cronograma das Atividades

| Data           | Produto desenvolvido |
| :------------- | :------------------- |
| Setembro       | Revisão da Literatura|
| Outubro        | Estruturação e pesquisa|
| Novembro       | Submissão dos achados ao \sc LAGOS 2019|

\printbibliography
