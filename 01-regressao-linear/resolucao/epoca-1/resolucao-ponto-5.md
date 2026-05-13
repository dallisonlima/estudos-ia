# Resolução Detalhada: Época 1 - Ponto 5

Chegamos ao último ponto da nossa primeira iteração (Época 1) por todo o conjunto de dados. Vamos herdar os pesos calculados no final do Ponto 4.

---

## Passo 0: O que temos em mãos? (Estado Inicial)
* **Dados do Aluno (Ponto 5):**
    * Horas de estudo ($X_1$): $2$
    * Listas resolvidas ($X_2$): $0$
    * Participação ($X_3$): $1$
    * Nota real esperada ($y$): $12$
* **Pesos Atuais (Herdados do Ponto 4):**
    * Viés ($b$): $0.3427$
    * Pesos ($W_1, W_2, W_3$): $0.3816,\ 0.3520,\ 0.3366$
* **Taxa de Aprendizado ($\eta$):** $0.01$

---

## Passo 1: A Previsão ($\hat{y}$)
**O que estamos fazendo:** Calculando a previsão final desta época.

**Fórmula:**
$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

**Cálculo:**

$$\hat{y} = 0.3427 + (0.3816 \cdot 2) + (0.3520 \cdot 0) + (0.3366 \cdot 1)$$

$$\hat{y} = 0.3427 + 0.7632 + 0 + 0.3366$$

$$\hat{y} = 1.4425$$

> **💡 O que aprendemos:** A previsão foi $1.4425$. Nossa reta começou prevendo $0$ no primeiro aluno e agora já consegue prever quase $1.5$. O modelo está, passo a passo, "escalando" em direção às notas reais que variam entre 6 e 12.

---

## Passo 2: O Cálculo do Erro ($E$)
**O que estamos fazendo:** Medindo o nosso último erro da Época 1.

**Fórmula:**
$$E = y - \hat{y}$$

**Cálculo:**

$$E = 12 - 1.4425$$

$$E = 10.5575$$

> **💡 O que aprendemos:** Este aluno tem a maior nota da turma ($12$). Como nossa reta ainda está "baixa", o erro foi o maior até agora ($10.5575$). Isso resultará em uma correção bem forte nos pesos.

---

## Passo 3: A Atualização dos Pesos (O Aprendizado)
**O que estamos fazendo:** Fazendo o último ajuste da época. Para as contas, usaremos $\eta \cdot E = (0.01 \cdot 10.5575) = 0.1056$ (arredondado para 4 casas para facilitar).

**1. Atualizando o Viés ($b$):**

$$b_{novo} = b_{atual} + \eta \cdot E$$

$$b_{novo} = 0.3427 + 0.1056$$

$$b_{novo} = 0.4483$$

**2. Atualizando o Peso 1 ($W_1$ - Horas de estudo):**

$$W_{1,novo} = W_{1,atual} + \eta \cdot E \cdot X_1$$

$$W_{1,novo} = 0.3816 + (0.1056 \cdot 2)$$

$$W_{1,novo} = 0.3816 + 0.2112$$

$$W_{1,novo} = 0.5928$$

> **💡 Dica de Fixação:** Mais uma vez, como o aluno estudou 2 horas ($X_1 = 2$), essa variável recebeu uma carga dupla de ajuste. O $W_1$ está se tornando o peso mais forte do modelo, indicando que as horas de estudo são cruciais para a nota.

**3. Atualizando o Peso 2 ($W_2$ - Listas resolvidas):**

$$W_{2,novo} = W_{2,atual} + \eta \cdot E \cdot X_2$$

$$W_{2,novo} = 0.3520 + (0.1056 \cdot 0)$$

$$W_{2,novo} = 0.3520$$

> **💡 Dica de Fixação:** Como o aluno não resolveu listas ($X_2 = 0$), o modelo ignora essa variável na hora de culpar alguém pelo erro. O peso permanece intacto.

**4. Atualizando o Peso 3 ($W_3$ - Participação):**

$$W_{3,novo} = W_{3,atual} + \eta \cdot E \cdot X_3$$

$$W_{3,novo} = 0.3366 + (0.1056 \cdot 1)$$

$$W_{3,novo} = 0.3366 + 0.1056$$

$$W_{3,novo} = 0.4422$$

---

## Passo 4: FIM DA ÉPOCA 1 (Prontos para a Época 2)
Nós passamos por todos os 5 alunos da nossa base de dados. Isso significa que **a Época 1 foi concluída**. 

Veja a diferença: nós começamos a época com o modelo zerado ($b=0, W_1=0, W_2=0, W_3=0$). Agora, após apenas 5 passos de treinamento, os parâmetros do nosso modelo são:

* $b = 0.4483$
* $W_1 = 0.5928$
* $W_2 = 0.3520$
* $W_3 = 0.4422$

### E agora?
Se fôssemos continuar o treinamento manualmente, iniciaríamos a **Época 2**. 
Voltaríamos para o **Ponto 1** (Aluno que tirou nota 9), **mas não usaríamos mais zeros**. Faríamos a primeira previsão da Época 2 usando estes novos pesos ($b=0.4483...$). 

Com esses pesos maiores, a previsão $\hat{y}$ será bem maior que $0$, o erro será menor que $9$, e as correções serão cada vez menores, até que os pesos estabilizem (covirjam) nas épocas futuras.
