# Problema: Perceptron para Seleção de Candidatos

Considere um modelo de Perceptron simples para classificar se um aluno deve ser recomendado ou não, com base em sua nota e frequência.

## 1. Variáveis
* **$X_1$**: Nota normalizada do aluno
* **$X_2$**: Frequência normalizada do aluno
* **Vetor de entrada ($X$)**: $X = (x_0, x_1, x_2) = (1, x_1, x_2)$
  *(Onde $x_0 = 1$ representa o viés/bias)*

## 2. Saída Desejada ($d$)
* **$d = 1$**: Aluno recomendado
* **$d = 0$**: Aluno não recomendado

## 3. Fórmulas do Modelo
* **Cálculo da Ativação ($\mu$)**: 
  $$\mu = w_0x_0 + w_1x_1 + w_2x_2$$

* **Função de Ativação ($\hat{y}$)**:
  $$\hat{y} = \begin{cases} 1, & \text{se } \mu \ge 0 \\ 0, & \text{se } \mu < 0 \end{cases}$$

* **Cálculo do Erro ($e$)**: 
  $$e = d - \hat{y}$$

* **Regra de Atualização dos Pesos**: 
  $$w_i^N = w_i^{ANT} + \eta \cdot e \cdot x_i$$

## 4. Parâmetros Iniciais
* **Pesos Iniciais**: $w_0 = 0$, $w_1 = 0$, $w_2 = 0$
* **Taxa de Aprendizagem ($\eta$)**: $0.2$

## 5. Base de Dados (Treinamento)

| Aluno | $x_0$ (Viés) | $x_1$ (Nota) | $x_2$ (Freq) | Saída Desejada ($d$) |
| :---: | :---: | :---: | :---: | :---: |
| **A** | 1 | 0.2 | 0.3 | 0 |
| **B** | 1 | 0.4 | 0.6 | 0 |
| **C** | 1 | 0.7 | 0.6 | 1 |
| **D** | 1 | 0.9 | 0.8 | 1 |
