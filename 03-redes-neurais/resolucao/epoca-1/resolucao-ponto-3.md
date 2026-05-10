# Resolução: Época 1 - Ponto 3

Chegamos ao terceiro e último aluno do nosso conjunto de dados. Ao finalizar este ponto, teremos concluído a **Época 1** do treinamento da nossa Rede Neural.

## Passo 0: Estado Inicial
Vamos herdar exatamente os pesos que saíram do cálculo do Ponto 2.

* **Dados do Aluno (Ponto 3):**
    * Entradas: $X_1 = 1,\ X_2 = 0$
    * Nota real esperada: $y = 0.6$
* **Pesos Atuais (Herdados do Ponto 2):**
    * Camada Oculta: $V_1 = 0.2,\ V_2 = -0.0988,\ b_h = 0.0008$
    * Camada de Saída: $\mu = 0.3053,\ b_o = 0.1114$
* **Taxa de Aprendizado:** $\eta = 0.1$

---

## Passo 1: A "Ida" (Previsão / Forward Pass)

**1. Calculando a entrada do neurônio oculto ($Z_h$):**
$$Z_h = b_h + V_1 X_1 + V_2 X_2$$
$$Z_h = 0.0008 + (0.2 \cdot 1) + (-0.0988 \cdot 0)$$
$$Z_h = 0.0008 + 0.2 + 0$$
$$Z_h = 0.2008$$

**2. Aplicando a Função de Ativação Sigmoide ($h$):**
$$h = \frac{1}{1 + e^{-Z_h}}$$
$$h = \frac{1}{1 + e^{-0.2008}}$$
$$h = \frac{1}{1 + 0.8180}$$
$$h = \frac{1}{1.8180} = 0.5500$$

**3. Calculando a Previsão Final ($\hat{y}$):**
$$\hat{y} = b_o + \mu \cdot h$$
$$\hat{y} = 0.1114 + (0.3053 \cdot 0.5500)$$
$$\hat{y} = 0.1114 + 0.1679$$
$$\hat{y} = 0.2793$$

---

## Passo 2: O Erro ($E$)
Vamos comparar a previsão com a nota real ($0.6$).
$$E = y - \hat{y}$$
$$E = 0.6 - 0.2793$$
$$E = 0.3207$$

> **💡 O que aprendemos:** Tivemos um erro positivo considerável. A rede previu $\approx 0.28$, mas o valor real era $0.6$. Como $X_1$ estava ativo ($1$), o algoritmo vai focar em aumentar os pesos ligados a essa entrada.

---

## Passo 3: A "Volta" na Camada de Saída (Backpropagation)

**1. Atualizando o Viés de Saída ($b_o$):**
$$b_{o,Novo} = b_o + \eta \cdot E$$
$$b_{o,Novo} = 0.1114 + (0.1 \cdot 0.3207)$$
$$b_{o,Novo} = 0.1114 + 0.0321$$
$$b_{o,Novo} = 0.1435$$

**2. Atualizando o Peso da Saída ($\mu$):**
$$\mu_{Novo} = \mu + \eta \cdot E \cdot h$$
$$\mu_{Novo} = 0.3053 + (0.1 \cdot 0.3207 \cdot 0.5500)$$
$$\mu_{Novo} = 0.3053 + 0.0176$$
$$\mu_{Novo} = 0.3229$$

---

## Passo 4: A "Volta" na Camada Oculta

**1. Calculando a Culpa ($\delta_h$):**
*(Nota: Utilizamos o $\mu$ antigo ($0.3053$) para calcular a parcela do erro).*
$$\delta_h = E \cdot \mu \cdot h(1 - h)$$
$$\delta_h = (0.3207) \cdot (0.3053) \cdot (0.5500) \cdot (1 - 0.5500)$$
$$\delta_h = 0.0979 \cdot 0.5500 \cdot 0.4500$$
$$\delta_h = 0.0979 \cdot 0.2475$$
$$\delta_h = 0.0242$$

**2. Atualizando o Viés Oculto ($b_h$):**
$$b_{h,Novo} = b_h + \eta \cdot \delta_h$$
$$b_{h,Novo} = 0.0008 + (0.1 \cdot 0.0242)$$
$$b_{h,Novo} = 0.0008 + 0.0024$$
$$b_{h,Novo} = 0.0032$$

**3. Atualizando o Peso $V_1$:**
$$V_{1,Novo} = V_1 + \eta \cdot \delta_h \cdot X_1$$
$$V_{1,Novo} = 0.2 + (0.1 \cdot 0.0242 \cdot 1)$$
$$V_{1,Novo} = 0.2 + 0.0024$$
$$V_{1,Novo} = 0.2024$$
> **💡 Dica de Fixação:** Como esperado, o peso $V_1$ subiu, já que a característica $X_1$ estava presente neste aluno e a rede havia previsto um valor muito abaixo do esperado.

**4. Atualizando o Peso $V_2$:**
$$V_{2,Novo} = V_2 + \eta \cdot \delta_h \cdot X_2$$
$$V_{2,Novo} = -0.0988 + (0.1 \cdot 0.0242 \cdot 0)$$
$$V_{2,Novo} = -0.0988$$
> **💡 Dica de Fixação:** Característica ausente ($X_2 = 0$), peso intocado!

---

## Passo 5: FIM DA ÉPOCA 1
Passamos por todos os 3 pontos do nosso conjunto de dados! Nossa rede completou a sua **Primeira Época** de aprendizado. 

Olha o quanto ela mudou desde a inicialização cega:
* **Início da Época:** $V_1 = 0.2$, $V_2 = -0.1$, $b_h = 0$, $\mu = 0.3$, $b_o = 0.1$
* **Fim da Época 1:** $V_1 = 0.2024$, $V_2 = -0.0988$, $b_h = 0.0032$, $\mu = 0.3229$, $b_o = 0.1435$

A rede aprendeu a ajustar seus pesos ligeiramente para cima, porque, de forma geral, suas previsões estavam sendo menores que os valores reais. Na **Época 2**, iniciaríamos novamente pelo Ponto 1, mas substituindo os pesos zeros por este novo conjunto, obtendo um erro menor e ajustando o modelo cada vez mais!