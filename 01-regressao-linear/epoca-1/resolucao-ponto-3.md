# Resolução Detalhada: Época 1 - Ponto 3

Avançando na Época 1, vamos processar o terceiro aluno. Novamente, herdamos os pesos exatos que acabaram de ser calculados no Ponto 2. Para manter a leitura fácil, vamos arredondar os cálculos para 4 casas decimais.

---

## Passo 0: O que temos em mãos? (Estado Inicial)
* **Dados do Aluno (Ponto 3):**
    * Horas de estudo ($X_1$): $2$
    * Listas resolvidas ($X_2$): $1$
    * Participação ($X_3$): $0$
    * Nota real esperada ($y$): $10$
* **Pesos Atuais (Herdados do Ponto 2):**
    * Viés ($b$): $0.1473$
    * Pesos ($W_1, W_2, W_3$): $0.09,\ 0.0573,\ 0.2373$
* **Taxa de Aprendizado ($\eta$):** $0.01$

---

## Passo 1: A Previsão ($\hat{y}$)
**O que estamos fazendo:** O modelo vai calcular a previsão de nota para este terceiro aluno usando os pesos atuais.

**Fórmula:**
$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Cálculo:**
$$\hat{y} = 0.1473 + (0.09 \cdot 2) + (0.0573 \cdot 1) + (0.2373 \cdot 0)$$
$$\hat{y} = 0.1473 + 0.18 + 0.0573 + 0$$
$$\hat{y} = 0.3846$$

> **💡 O que aprendemos:** A previsão foi $0.3846$. A reta do nosso modelo está subindo lentamente e fazendo previsões maiores, mas ainda está bem longe do objetivo (que é a nota 10). 

---

## Passo 2: O Cálculo do Erro ($E$)
**O que estamos fazendo:** Verificando a diferença entre a nota real e a previsão.

**Fórmula:**
$$E = y - \hat{y}$$

**Cálculo:**
$$E = 10 - 0.3846$$
$$E = 9.6154$$

> **💡 O que aprendemos:** Tivemos um erro grande de $9.6154$. Isso aconteceu porque as variáveis que este aluno tem forte presença (como as 2 horas de estudo) ainda estão com pesos muito baixos no modelo. O algoritmo usará esse erro para dar um belo "puxão" nesses pesos.

---

## Passo 3: A Atualização dos Pesos (O Aprendizado)
**O que estamos fazendo:** Aplicando o erro na fórmula de atualização para ajustar os parâmetros.

**1. Atualizando o Viés ($b$):**
$$b_{novo} = b_{atual} + \eta \cdot E$$
$$b_{novo} = 0.1473 + (0.01 \cdot 9.6154)$$
$$b_{novo} = 0.1473 + 0.0961$$
$$b_{novo} = 0.2434$$

**2. Atualizando o Peso 1 ($W_1$ - Horas de estudo):**
$$W_{1,novo} = W_{1,atual} + \eta \cdot E \cdot X_1$$
$$W_{1,novo} = 0.09 + (0.01 \cdot 9.6154 \cdot 2)$$
$$W_{1,novo} = 0.09 + 0.1923$$
$$W_{1,novo} = 0.2823$$
> **💡 Dica de Fixação:** Veja o salto que o $W_1$ deu! Como o aluno estudou 2 horas e a previsão errou feio, o modelo aumentou drasticamente a importância de estudar na composição da nota.

**3. Atualizando o Peso 2 ($W_2$ - Listas resolvidas):**
$$W_{2,novo} = W_{2,atual} + \eta \cdot E \cdot X_2$$
$$W_{2,novo} = 0.0573 + (0.01 \cdot 9.6154 \cdot 1)$$
$$W_{2,novo} = 0.0573 + 0.0961$$
$$W_{2,novo} = 0.1534$$

**4. Atualizando o Peso 3 ($W_3$ - Participação):**
$$W_{3,novo} = W_{3,atual} + \eta \cdot E \cdot X_3$$
$$W_{3,novo} = 0.2373 + (0.01 \cdot 9.6154 \cdot 0)$$
$$W_{3,novo} = 0.2373$$
> **💡 Dica de Fixação:** Lembra o que aconteceu no Ponto 1 e 2? Se a característica é zero ($X_3 = 0$), o peso dela não é ajustado. O modelo não culpa a "participação em aula" pelo erro na previsão, já que o aluno não participou.

---

## Passo 4: Estado Final (Prontos para o Ponto 4)
O modelo terminou de processar o terceiro aluno e reajustou suas crenças sobre o que importa para a nota. Os pesos que levaremos para o **Ponto 4** agora são:

* $b = 0.2434$
* $W_1 = 0.2823$
* $W_2 = 0.1534$
* $W_3 = 0.2373$