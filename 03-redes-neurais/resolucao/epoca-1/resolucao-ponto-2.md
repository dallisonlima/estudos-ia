# Resolução: Época 1 - Ponto 2

Avançando no treinamento da nossa Rede Neural, agora vamos processar o segundo aluno. Preste atenção no **Passo 0**: a rede não está mais "zerada". Nós herdamos o aprendizado (os pesos ajustados) do Ponto 1.

## Passo 0: Estado Inicial
* **Dados do Aluno (Ponto 2):**
    * Entradas: $X_1 = 0,\ X_2 = 1$
    * Nota real esperada: $y = 0.4$
* **Pesos Atuais (Herdados do Ponto 1):**
    * Camada Oculta: $V_1 = 0.2,\ V_2 = -0.1,\ b_h = -0.00037$
    * Camada de Saída: $\mu = 0.2975,\ b_o = 0.095$
* **Taxa de Aprendizado:** $\eta = 0.1$

---

## Passo 1: A "Ida" (Previsão / Forward Pass)

**1. Calculando a entrada do neurônio oculto ($Z_h$):**
$$Z_h = b_h + V_1 X_1 + V_2 X_2$$
$$Z_h = -0.00037 + (0.2 \cdot 0) + (-0.1 \cdot 1)$$
$$Z_h = -0.00037 + 0 - 0.1$$
$$Z_h = -0.10037$$

**2. Aplicando a Função de Ativação Sigmoide ($h$):**
$$h = \frac{1}{1 + e^{-Z_h}}$$
$$h = \frac{1}{1 + e^{-(-0.10037)}}$$
$$h = \frac{1}{1 + e^{0.10037}}$$
$$h = 0.4749$$

**3. Calculando a Previsão Final ($\hat{y}$):**
$$\hat{y} = b_o + \mu \cdot h$$
$$\hat{y} = 0.095 + (0.2975 \cdot 0.4749)$$
$$\hat{y} = 0.095 + 0.1413$$
$$\hat{y} = 0.2363$$

---

## Passo 2: O Erro ($E$)
Vamos comparar a previsão da rede com a nota real deste aluno.
$$E = y - \hat{y}$$
$$E = 0.4 - 0.2363$$
$$E = 0.1637$$

> **💡 O que aprendemos:** A rede previu $0.2363$, mas a nota era $0.4$. Tivemos um erro positivo, o que significa que a rede precisa aumentar seus pesos para tentar chegar mais perto do $0.4$ na próxima vez.

---

## Passo 3: A "Volta" na Camada de Saída (Backpropagation)
Atualizando os parâmetros do final da rede em direção ao começo.

**1. Atualizando o Viés de Saída ($b_o$):**
$$b_{o,Novo} = b_o + \eta \cdot E$$
$$b_{o,Novo} = 0.095 + (0.1 \cdot 0.1637)$$
$$b_{o,Novo} = 0.095 + 0.01637$$
$$b_{o,Novo} = 0.1114$$

**2. Atualizando o Peso da Saída ($\mu$):**
$$\mu_{Novo} = \mu + \eta \cdot E \cdot h$$
$$\mu_{Novo} = 0.2975 + (0.1 \cdot 0.1637 \cdot 0.4749)$$
$$\mu_{Novo} = 0.2975 + 0.0078$$
$$\mu_{Novo} = 0.3053$$

---

## Passo 4: A "Volta" na Camada Oculta
Calculando a culpa do neurônio oculto para ajustar os pesos iniciais.

**1. Calculando a Culpa ($\delta_h$):**
$$\delta_h = E \cdot \mu \cdot h(1 - h)$$
$$\delta_h = (0.1637) \cdot (0.2975) \cdot (0.4749) \cdot (1 - 0.4749)$$
$$\delta_h = 0.0487 \cdot 0.4749 \cdot 0.5251$$
$$\delta_h = 0.0121$$

**2. Atualizando o Viés Oculto ($b_h$):**
$$b_{h,Novo} = b_h + \eta \cdot \delta_h$$
$$b_{h,Novo} = -0.00037 + (0.1 \cdot 0.0121)$$
$$b_{h,Novo} = -0.00037 + 0.00121$$
$$b_{h,Novo} = 0.0008$$

**3. Atualizando o Peso $V_1$:**
$$V_{1,Novo} = V_1 + \eta \cdot \delta_h \cdot X_1$$
$$V_{1,Novo} = 0.2 + (0.1 \cdot 0.0121 \cdot 0)$$
$$V_{1,Novo} = 0.2$$
> **💡 Dica de Fixação:** Mais uma vez, como este aluno tem a entrada $X_1 = 0$, a conexão de $V_1$ ficou inativa para ele. O peso não se altera.

**4. Atualizando o Peso $V_2$:**
$$V_{2,Novo} = V_2 + \eta \cdot \delta_h \cdot X_2$$
$$V_{2,Novo} = -0.1 + (0.1 \cdot 0.0121 \cdot 1)$$
$$V_{2,Novo} = -0.1 + 0.00121$$
$$V_{2,Novo} = -0.0988$$
> **💡 Dica de Fixação:** Como a entrada $X_2$ estava ativa ($1$), o peso $V_2$ sofreu alteração, subindo levemente de $-0.1$ para $-0.0988$.

---

## Passo 5: Estado Final (Prontos para o Ponto 3)
A rede processou o segundo aluno. Os parâmetros atualizados que levaremos para o **Ponto 3** agora são:

* $V_1 = 0.2$
* $V_2 = -0.0988$
* $b_h = 0.0008$
* $\mu = 0.3053$
* $b_o = 0.1114$