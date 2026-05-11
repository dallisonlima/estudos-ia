# Resolução: Época 1 - Ponto 1

Neste documento, vamos detalhar o processamento do primeiro ponto da nossa base de dados. Aqui aplicamos tanto a fase de "Ida" (Forward Pass) quanto a fase de "Volta" (Backpropagation).

## Passo 0: Estado Inicial
Antes de começar, listamos os dados do aluno e os pesos da rede no momento "zero".

* **Dados do Aluno (Ponto 1):**
    * Entradas: $X_1 = 0,\ X_2 = 0$
    * Nota real esperada: $y = 0.2$
* **Pesos Iniciais:**
    * Camada Oculta: $V_1 = 0.2,\ V_2 = -0.1,\ b_h = 0$
    * Camada de Saída: $\mu = 0.3,\ b_o = 0.1$
* **Taxa de Aprendizado:** $\eta = 0.1$

---

## Passo 1: A "Ida" (Previsão / Forward Pass)

**1. Calculando a entrada do neurônio oculto ($Z_h$):**

$$Z_h = b_h + V_1 X_1 + V_2 X_2$$

$$Z_h = 0 + (0.2 \cdot 0) + (-0.1 \cdot 0)$$

$$Z_h = 0$$

**2. Aplicando a Função de Ativação Sigmoide ($h$):**

$$h = \frac{1}{1 + e^{-Z_h}}$$

$$h = \frac{1}{1 + e^0}$$

$$h = \frac{1}{1 + 1} = 0.5$$

**3. Calculando a Previsão Final ($\hat{y}$):**

$$\hat{y} = b_o + \mu \cdot h$$

$$\hat{y} = 0.1 + (0.3 \cdot 0.5)$$

$$\hat{y} = 0.1 + 0.15 = 0.25$$

---

## Passo 2: O Erro ($E$)
A rede previu $0.25$, mas a resposta certa era $0.2$.

$$E = y - \hat{y}$$

$$E = 0.2 - 0.25$$

$$E = -0.05$$

*(Até aqui, é exatamente o que estava escrito na lousa do Ponto 1. Daqui em diante, é a matemática oculta do Backpropagation!)*

---

## Passo 3: A "Volta" na Camada de Saída
Vamos ajustar os pesos que estão mais próximos do erro.

**1. Atualizando o Viés de Saída ($b_o$):**

$$b_{o,Novo} = b_o + \eta \cdot E$$

$$b_{o,Novo} = 0.1 + (0.1 \cdot -0.05)$$

$$b_{o,Novo} = 0.1 - 0.005$$

$$b_{o,Novo} = 0.095$$

**2. Atualizando o Peso da Saída ($\mu$):**

$$\mu_{Novo} = \mu + \eta \cdot E \cdot h$$

$$\mu_{Novo} = 0.3 + (0.1 \cdot -0.05 \cdot 0.5)$$

$$\mu_{Novo} = 0.3 - 0.0025$$

$$\mu_{Novo} = 0.2975$$

---

## Passo 4: A "Volta" na Camada Oculta
Agora, precisamos calcular a "parcela de culpa" do neurônio oculto para ajustar os pesos iniciais.

**1. Calculando a Culpa ($\delta_h$):**

$$\delta_h = E \cdot \mu \cdot h(1 - h)$$

$$\delta_h = -0.05 \cdot 0.3 \cdot 0.5(1 - 0.5)$$

$$\delta_h = -0.015 \cdot 0.25$$

$$\delta_h = -0.00375$$

**2. Atualizando o Viés Oculto ($b_h$):**

$$b_{h,Novo} = b_h + \eta \cdot \delta_h$$

$$b_{h,Novo} = 0 + (0.1 \cdot -0.00375)$$

$$b_{h,Novo} = -0.000375$$

*(Nota: O professor arredondou este valor para -0.00037 na lousa do Ponto 2).*

**3. Atualizando o Peso $V_1$:**

$$V_{1,Novo} = V_1 + \eta \cdot \delta_h \cdot X_1$$

$$V_{1,Novo} = 0.2 + (0.1 \cdot -0.00375 \cdot 0)$$

$$V_{1,Novo} = 0.2$$

*(Como $X_1$ era zero, a conexão não estava ativa, então o peso não muda).*

**4. Atualizando o Peso $V_2$:**

$$V_{2,Novo} = V_2 + \eta \cdot \delta_h \cdot X_2$$

$$V_{2,Novo} = -0.1 + (0.1 \cdot -0.00375 \cdot 0)$$

$$V_{2,Novo} = -0.1$$

---

## Passo 5: Estado Final (Prontos para o Ponto 2)
Após a primeira iteração de Backpropagation, nossos parâmetros deixam de ser os iniciais e passam a ser:

* $V_1 = 0.2$
* $V_2 = -0.1$
* $b_h = -0.00037$ (arredondado)
* $\mu = 0.2975$
* $b_o = 0.095$
