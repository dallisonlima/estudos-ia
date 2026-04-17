## Resolução Passo a Passo: Treinamento - Época 1

O algoritmo do Perceptron aprende ajustando os pesos toda vez que comete um erro. Vamos acompanhar esse processo começando pelo primeiro aluno da nossa base de dados.

### Aluno A

#### 1. Dados de Entrada e Pesos Iniciais
Para começar, pegamos os dados do Aluno A, a saída que esperamos (se ele é recomendado ou não) e os pesos iniciais da rede neural.

* **Entradas do Aluno A ($X_A$)**: $(1, 0.2, 0.3)$
  * $x_0 = 1$ (Viés / Bias)
  * $x_1 = 0.2$ (Nota normalizada)
  * $x_2 = 0.3$ (Frequência normalizada)
* **Saída Desejada ($d$)**: $0$ (Não recomendado)
* **Pesos Iniciais**: $w_0 = 0$, $w_1 = 0$, $w_2 = 0$
* **Taxa de Aprendizagem ($\eta$)**: $0.2$

---

#### 2. Cálculo da Ativação ($\mu$)
O primeiro passo do Perceptron é multiplicar cada entrada pelo seu respectivo peso e somar tudo. Isso nos dá o valor de ativação ($\mu$).

$$\mu = (w_0 \cdot x_0) + (w_1 \cdot x_1) + (w_2 \cdot x_2)$$
$$\mu = (0 \cdot 1) + (0 \cdot 0.2) + (0 \cdot 0.3)$$
$$\mu = 0 + 0 + 0$$
$$\mu = 0$$

---

#### 3. Previsão da Rede ($\hat{y}$)
Agora, passamos o valor de $\mu$ pela **Função de Ativação** para ver qual é a previsão da nossa rede. A regra definida no problema é:
* Se $\mu \ge 0$, prevê $1$
* Se $\mu < 0$, prevê $0$

Como nosso $\mu$ é exatamente $0$:
$$\hat{y} = 1$$
*(A rede previu erroneamente que o aluno deveria ser recomendado)*

---

#### 4. Cálculo do Erro ($e$)
O erro é a diferença entre o que nós queríamos ($d$) e o que a rede previu ($\hat{y}$).

$$e = d - \hat{y}$$
$$e = 0 - 1 = -1$$

Como o erro foi diferente de zero, **precisamos atualizar os pesos** para que a rede aprenda e não cometa o mesmo erro na próxima vez.

---

#### 5. Atualização dos Pesos
A fórmula para atualizar cada peso é: $w_i^N = w_i^{ANT} + \eta \cdot e \cdot x_i$. 
Vamos aplicar isso para os três pesos:

* **Atualizando o peso do Viés ($w_0$)**:
  $$w_0^N = 0 + 0.2 \cdot (-1) \cdot (1)$$
  $$w_0^N = 0 - 0.2 = -0.2$$

* **Atualizando o peso da Nota ($w_1$)**:
  $$w_1^N = 0 + 0.2 \cdot (-1) \cdot (0.2)$$
  $$w_1^N = 0 - 0.04 = -0.04$$

* **Atualizando o peso da Frequência ($w_2$)**:
  $$w_2^N = 0 + 0.2 \cdot (-1) \cdot (0.3)$$
  $$w_2^N = 0 - 0.06 = -0.06$$

---

#### 6. Resultado da Iteração
Após processar o Aluno A, a rede neural aprendeu com seu erro e atualizou seus "conhecimentos". Os novos pesos que serão passados para o teste do **Aluno B** são:

$$(w_0, w_1, w_2) = (-0.2, -0.04, -0.06)$$
