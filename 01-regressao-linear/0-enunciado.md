# Regressão Linear

Queremos construir um modelo de Machine Learning para prever uma nota final $y$ de um aluno a partir de 3 características:

* $X_1$ = Horas de estudo
* $X_2$ = Número de listas de exercícios resolvidas
* $X_3$ = Participação em aula

O aluno é representado por um vetor $(X_1, X_2, X_3)$. O objetivo é construir um modelo que irá estimar o rótulo numérico $y$.

## 1) Dados

| Ponto | $X_1$ | $X_2$ | $X_3$ | $y$ |
| --- | --- | --- | --- | --- |
| 1 | 1 | 0 | 2 | 9 |
| 2 | 0 | 1 | 1 | 6 |
| 3 | 2 | 1 | 0 | 10 |
| 4 | 1 | 2 | 1 | 11 |
| 5 | 2 | 0 | 1 | 12 |

## 2) Modelo de Regressão

$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

## 3) Valores Iniciais

* $b = 0$
* $W_1 = 0$
* $W_2 = 0$
* $W_3 = 0$

**Taxa de aprendizado:** $\eta = 0.01$

## 4) Fórmulas

**Previsão:**


$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Erro:**


$$E = y - \hat{y}$$

**Atualização dos Parâmetros** *(onde $n$ = novo e $a$ = atual)*:


$$b_n = b_a + \eta \cdot E$$

$$W_{1,n} = W_{1,a} + \eta \cdot E \cdot X_1$$

$$W_{2,n} = W_{2,a} + \eta \cdot E \cdot X_2$$

$$W_{3,n} = W_{3,a} + \eta \cdot E \cdot X_3$$

*(Neste caso temos 5 pontos para a atualização)*