# Resolução Detalhada: Época 1 - Ponto 4

Chegamos ao penúltimo aluno da nossa primeira época! O nosso modelo já está começando a ganhar forma e os pesos já não estão tão próximos de zero. Vamos usar o conhecimento herdado do Ponto 3.

---

## Passo 0: O que temos em mãos? (Estado Inicial)
* **Dados do Aluno (Ponto 4):**
    * Horas de estudo ($X_1$): $1$
    * Listas resolvidas ($X_2$): $2$
    * Participação ($X_3$): $1$
    * Nota real esperada ($y$): $11$
* **Pesos Atuais (Herdados do Ponto 3):**
    * Viés ($b$): $0.2434$
    * Pesos ($W_1, W_2, W_3$): $0.2823,\ 0.1534,\ 0.2373$
* **Taxa de Aprendizado ($\eta$):** $0.01$

---

## Passo 1: A Previsão ($\hat{y}$)
**O que estamos fazendo:** Calculando o palpite do modelo para este quarto aluno.

**Fórmula:**
$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Cálculo:**

$$\hat{y} = 0.2434 + (0.2823 \cdot 1) + (0.1534 \cdot 2) + (0.2373 \cdot 1)$$

$$\hat{y} = 0.2434 + 0.2823 + 0.3068 + 0.2373$$

$$\hat{y} = 1.0698$$

> **💡 O que aprendemos:** O modelo previu uma nota de $1.0698$. Pela primeira vez nossa previsão rompeu a barreira de 1 ponto! Isso mostra que o modelo está, aos poucos, subindo a reta para se aproximar das notas altas reais da tabela.

---

## Passo 2: O Cálculo do Erro ($E$)
**O que estamos fazendo:** Medindo o tamanho do nosso erro.

**Fórmula:**
$$E = y - \hat{y}$$

**Cálculo:**

$$E = 11 - 1.0698$$

$$E = 9.9302$$

> **💡 O que aprendemos:** Continuamos com um erro alto positivo ($9.9302$), o que significa que o modelo ainda precisa empurrar todos os pesos para cima para compensar essa previsão subestimada.

---

## Passo 3: A Atualização dos Pesos (O Aprendizado)
**O que estamos fazendo:** Ajustando as "crenças" do modelo. Para facilitar a leitura, o cálculo de $\eta \cdot E$ é $(0.01 \cdot 9.9302) = 0.0993$. 

**1. Atualizando o Viés ($b$):**

$$b_{novo} = b_{atual} + \eta \cdot E$$

$$b_{novo} = 0.2434 + 0.0993$$

$$b_{novo} = 0.3427$$

**2. Atualizando o Peso 1 ($W_1$ - Horas de estudo):**

$$W_{1,novo} = W_{1,atual} + \eta \cdot E \cdot X_1$$

$$W_{1,novo} = 0.2823 + (0.0993 \cdot 1)$$

$$W_{1,novo} = 0.2823 + 0.0993$$

$$W_{1,novo} = 0.3816$$

**3. Atualizando o Peso 2 ($W_2$ - Listas resolvidas):**

$$W_{2,novo} = W_{2,atual} + \eta \cdot E \cdot X_2$$

$$W_{2,novo} = 0.1534 + (0.0993 \cdot 2)$$

$$W_{2,novo} = 0.1534 + 0.1986$$

$$W_{2,novo} = 0.3520$$

> **💡 Dica de Fixação:** Atenção ao $W_2$! Como este aluno foi o que mais resolveu listas ($X_2 = 2$), essa variável sofreu a maior correção de todas nesta rodada ($0.1986$). O modelo diz: "se ele fez bastante lista e a nota foi alta, listas são importantes, vou aumentar esse peso mais rápido".

**4. Atualizando o Peso 3 ($W_3$ - Participação):**

$$W_{3,novo} = W_{3,atual} + \eta \cdot E \cdot X_3$$

$$W_{3,novo} = 0.2373 + (0.0993 \cdot 1)$$

$$W_{3,novo} = 0.2373 + 0.0993$$

$$W_{3,novo} = 0.3366$$

---

## Passo 4: Estado Final (Prontos para o Ponto 5)
O modelo terminou de processar o quarto aluno. Os pesos que levaremos para o **Ponto 5** (o último da primeira época) agora são:

* $b = 0.3427$
* $W_1 = 0.3816$
* $W_2 = 0.3520$
* $W_3 = 0.3366$
