# Resolução Detalhada: Época 1 - Ponto 2

Continuando nossa Época 1, agora vamos processar o segundo aluno da nossa base de dados. Preste muita atenção no **Passo 0**, pois é aqui que a "passagem de bastão" do Gradiente Descendente Estocástico (SGD) acontece.

---

## Passo 0: O que temos em mãos? (Estado Inicial)
Agora, nossos pesos **não são mais zeros**. Nós vamos usar os pesos exatos que foram calculados no final do Ponto 1.

* **Dados do Aluno (Ponto 2):**
    * Horas de estudo ($X_1$): $0$
    * Listas resolvidas ($X_2$): $1$
    * Participação ($X_3$): $1$
    * Nota real esperada ($y$): $6$
* **Pesos Atuais (Herdados do Ponto 1):**
    * Viés ($b$): $0.09$
    * Pesos ($W_1, W_2, W_3$): $0.09,\ 0,\ 0.18$
* **Taxa de Aprendizado ($\eta$):** $0.01$

---

## Passo 1: A Previsão ($\hat{y}$)
**O que estamos fazendo:** Vamos ver qual nota o modelo prevê para este novo aluno, usando o pouco que ele já aprendeu.

**Fórmula:**
$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Cálculo:**

$$\hat{y} = 0.09 + (0.09 \cdot 0) + (0 \cdot 1) + (0.18 \cdot 1)$$

$$\hat{y} = 0.09 + 0 + 0 + 0.18$$

$$\hat{y} = 0.27$$

> **💡 O que aprendemos:** O modelo previu que este aluno tiraria $0.27$. Ainda está muito longe da nota real ($6$), mas repare que já não é mais o palpite cego de "zero" que tivemos no primeiro aluno. O modelo já começou a associar que a participação ($X_3$) gera pontos na nota.

---

## Passo 2: O Cálculo do Erro ($E$)
**O que estamos fazendo:** Comparando a previsão com a realidade.

**Fórmula:**
$$E = y - \hat{y}$$

**Cálculo:**

$$E = 6 - 0.27$$

$$E = 5.73$$

> **💡 O que aprendemos:** O erro foi de $5.73$. Ainda é um erro positivo (previu para baixo), então os pesos ainda precisam subir, mas note que o erro foi menor do que o do Ponto 1 (onde erramos por 9 pontos).

---

## Passo 3: A Atualização dos Pesos (O Aprendizado)
**O que estamos fazendo:** Corrigindo os pesos novamente, usando o novo erro ($5.73$).

**1. Atualizando o Viés ($b$):**

$$b_{novo} = b_{atual} + \eta \cdot E$$

$$b_{novo} = 0.09 + 0.01 \cdot 5.73$$

$$b_{novo} = 0.09 + 0.0573$$

$$b_{novo} = 0.1473$$

**2. Atualizando o Peso 1 ($W_1$ - Horas de estudo):**

$$W_{1,novo} = W_{1,atual} + \eta \cdot E \cdot X_1$$

$$W_{1,novo} = 0.09 + 0.01 \cdot 5.73 \cdot 0$$

$$W_{1,novo} = 0.09$$

> **💡 Dica de Fixação:** O Peso 1 não mudou. Por quê? Porque este aluno estudou zero horas ($X_1 = 0$). Se a falta de estudo não contribuiu para o erro positivo que tivemos, o modelo não mexe nesse peso agora.

**3. Atualizando o Peso 2 ($W_2$ - Listas resolvidas):**

$$W_{2,novo} = W_{2,atual} + \eta \cdot E \cdot X_2$$

$$W_{2,novo} = 0 + 0.01 \cdot 5.73 \cdot 1$$

$$W_{2,novo} = 0.0573$$

> **💡 Dica de Fixação:** Finalmente o Peso 2 saiu do zero! Como este aluno resolveu listas ($X_2 = 1$), o modelo percebeu que precisa começar a dar valor para essa característica.

**4. Atualizando o Peso 3 ($W_3$ - Participação):**

$$W_{3,novo} = W_{3,atual} + \eta \cdot E \cdot X_3$$

$$W_{3,novo} = 0.18 + 0.01 \cdot 5.73 \cdot 1$$

$$W_{3,novo} = 0.18 + 0.0573$$

$$W_{3,novo} = 0.2373$$

---

## Passo 4: Estado Final (Prontos para o Ponto 3)
O modelo terminou de processar o segundo aluno e ficou um pouco mais inteligente. Os pesos que levaremos para o **Ponto 3** agora são:

* $b = 0.1473$
* $W_1 = 0.09$
* $W_2 = 0.0573$
* $W_3 = 0.2373$
