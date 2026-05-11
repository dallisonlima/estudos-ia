# Resolução Detalhada: Época 1 - Ponto 1

Neste documento, vamos destrinchar o passo a passo da primeira iteração do nosso modelo de Regressão Linear. O objetivo aqui é entender a **ordem lógica** do algoritmo para que o fluxo de atualização (SGD) fique gravado na mente.

A ordem lógica de resolução de qualquer ponto sempre será:
1. Ver o que temos (Estado Inicial)
2. Tentar adivinhar a nota (Previsão)
3. Ver o quanto erramos (Erro)
4. Corrigir o modelo (Atualização)

---

## Passo 0: O que temos em mãos? (Estado Inicial)
Antes de fazer qualquer conta, precisamos separar os dados do aluno atual e o "conhecimento" atual do modelo.

* **Dados do Aluno (Ponto 1):**
    * Horas de estudo ($X_1$): $1$
    * Listas resolvidas ($X_2$): $0$
    * Participação ($X_3$): $2$
    * Nota real esperada ($y$): $9$
* **Pesos Atuais (O modelo "nasceu" agora, então não sabe de nada):**
    * Viés ($b$): $0$
    * Pesos ($W_1, W_2, W_3$): $0, 0, 0$
* **Taxa de Aprendizado ($\eta$):** $0.01$ (O tamanho do nosso passo de correção).

---

## Passo 1: A Previsão ($\hat{y}$)
**O que estamos fazendo:** O modelo vai tentar adivinhar a nota do aluno usando os pesos que ele tem no momento. Como tudo é zero, o resultado lógico também será zero.

**Fórmula:**
$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Cálculo:**

$$\hat{y} = 0 + (0 \cdot 1) + (0 \cdot 0) + (0 \cdot 2)$$

$$\hat{y} = 0$$

> **💡 O que aprendemos:** A previsão inicial de um modelo "zerado" é sempre zero. Ele previu que o aluno tiraria nota 0.

---

## Passo 2: O Cálculo do Erro ($E$)
**O que estamos fazendo:** Vamos comparar a nota que o modelo adivinhou ($0$) com a nota real que o aluno de fato tirou ($9$) para ver o tamanho da nossa falha.

**Fórmula:**
$$E = y - \hat{y}$$

**Cálculo:**

$$E = 9 - 0$$

$$E = 9$$

> **💡 O que aprendemos:** O modelo errou por 9 pontos. Como o erro é **positivo**, significa que ele previu para baixo (subestimou a nota). O algoritmo saberá que precisa empurrar os pesos para cima no próximo passo.

---

## Passo 3: A Atualização dos Pesos (O Aprendizado)
**O que estamos fazendo:** É aqui que o modelo realmente aprende. Vamos pegar o Erro ($9$) e usá-lo para alterar os pesos. Nós usamos a Taxa de Aprendizado ($\eta$) para o ajuste não ser brusco demais, e multiplicamos pela entrada ($X$) para dar mais "peso" à característica que estava mais presente no aluno.

**1. Atualizando o Viés ($b$):** O viés não multiplica por $X$.

$$b_{novo} = b_{atual} + \eta \cdot E$$

$$b_{novo} = 0 + 0.01 \cdot 9$$

$$b_{novo} = 0.09$$

**2. Atualizando o Peso 1 ($W_1$ - Horas de estudo):**

$$W_{1,novo} = W_{1,atual} + \eta \cdot E \cdot X_1$$

$$W_{1,novo} = 0 + 0.01 \cdot 9 \cdot 1$$

$$W_{1,novo} = 0.09$$

**3. Atualizando o Peso 2 ($W_2$ - Listas resolvidas):**

$$W_{2,novo} = W_{2,atual} + \eta \cdot E \cdot X_2$$

$$W_{2,novo} = 0 + 0.01 \cdot 9 \cdot 0$$

$$W_{2,novo} = 0$$

> **💡 Dica de Fixação:** O peso 2 continuou zero. Por quê? Porque esse aluno não fez listas ($X_2 = 0$). Se a característica não estava presente, ela não influenciou na previsão incorreta, logo, seu peso não muda neste momento.

**4. Atualizando o Peso 3 ($W_3$ - Participação):**

$$W_{3,novo} = W_{3,atual} + \eta \cdot E \cdot X_3$$

$$W_{3,novo} = 0 + 0.01 \cdot 9 \cdot 2$$

$$W_{3,novo} = 0.18$$

> **💡 Dica de Fixação:** Como a participação desse aluno era alta ($X_3 = 2$), essa característica recebeu o **dobro** de ajuste em relação ao tempo de estudo ($X_1 = 1$). A matemática pune/premia as variáveis proporcionalmente à presença delas.

---

## Passo 4: Estado Final (Prontos para o Ponto 2)
**O que estamos fazendo:** Fechando o pacote. O modelo processou o primeiro aluno e aprendeu um pouco. Agora, para calcular o **Ponto 2**, os pesos iniciais deixam de ser zeros e passam a ser:

* $b = 0.09$
* $W_1 = 0.09$
* $W_2 = 0$
* $W_3 = 0.18$
