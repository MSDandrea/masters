---
title: Complexidade Parametrizada
author: Matheus Souza D'Andrea Alves
date: 2018.2
---
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
