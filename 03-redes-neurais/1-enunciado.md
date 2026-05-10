# Treinamento de Rede Neural (MLP) com Backpropagation

## O Problema
Considere uma Rede Neural Artificial do tipo *Multilayer Perceptron* (MLP) projetada para realizar uma tarefa de regressão/aproximação de função. 

A rede possui a seguinte topologia:
* **Camada de Entrada:** 2 características ($X_1, X_2$).
* **Camada Oculta:** 1 neurônio com função de ativação Sigmoide ($h$).
* **Camada de Saída:** 1 neurônio com função de ativação linear ($\hat{y}$).

O objetivo é realizar o treinamento passo a passo (ponto a ponto) da **Primeira Época** utilizando o algoritmo de Retropropagação do Erro (*Backpropagation*).

## 1) Conjunto de Dados

| Ponto | $X_1$ | $X_2$ | $y$ (Real) |
| :---: | :---: | :---: | :---: |
| 1 | 0 | 0 | 0.2 |
| 2 | 0 | 1 | 0.4 |
| 3 | 1 | 0 | 0.6 |

## 2) Valores Iniciais dos Parâmetros

Os pesos e vieses (bias) da rede foram inicializados com os seguintes valores:
* Pesos da Entrada para Oculta: $V_1 = 0.2$ | $V_2 = -0.1$
* Viés do Neurônio Oculto: $b_h = 0$
* Peso da Oculta para Saída: $\mu = 0.3$
* Viés do Neurônio de Saída: $b_o = 0.1$

**Taxa de Aprendizado:** $\eta = 0.1$

## 3) Fórmulas da Rede (Forward Pass)

**Cálculo do Neurônio Oculto:**
$$Z_h = b_h + V_1 X_1 + V_2 X_2$$
$$h = \frac{1}{1 + e^{-Z_h}} \quad \text{(Função Sigmoide)}$$

**Cálculo do Neurônio de Saída (Previsão):**
$$\hat{y} = b_o + \mu \cdot h$$

**Cálculo do Erro:**
$$E = y - \hat{y}$$

## 4) Fórmulas de Atualização (Backpropagation)

Onde a letra $N$ no subscrito indica o valor "Novo".

**Atualização da Camada de Saída:**
$$b_{o,N} = b_o + \eta \cdot E$$
$$\mu_N = \mu + \eta \cdot E \cdot h$$

**Atualização da Camada Oculta:**
Para atualizar a camada oculta, precisamos calcular o delta ($\delta_h$), que representa o quanto o neurônio oculto foi "culpado" pelo erro final. A fórmula já inclui a derivada da função sigmoide:
$$\delta_h = E \cdot \mu \cdot h(1 - h)$$

Com o delta calculado, atualizamos os pesos iniciais:
$$b_{h,N} = b_h + \eta \cdot \delta_h$$
$$V_{1,N} = V_1 + \eta \cdot \delta_h \cdot X_1$$
$$V_{2,N} = V_2 + \eta \cdot \delta_h \cdot X_2$$