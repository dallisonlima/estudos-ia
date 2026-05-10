### Aluno D

#### 1. Dados de Entrada e Pesos Herdados
Chegamos ao último aluno da nossa base de dados. Vamos utilizar os pesos recém-atualizados após o aprendizado com o Aluno C.

* **Entradas do Aluno D ($X_D$)**: $(1, 0.9, 0.8)$
  * $x_0 = 1$ (Viés / Bias)
  * $x_1 = 0.9$ (Nota normalizada)
  * $x_2 = 0.8$ (Frequência normalizada)
* **Saída Desejada ($d$)**: $1$ (Recomendado)
* **Pesos Atuais (herdados do Aluno C)**: $w_0 = 0$, $w_1 = 0.1$, $w_2 = 0.06$
* **Taxa de Aprendizagem ($\eta$)**: $0.2$

---

#### 2. Cálculo da Ativação ($\mu$)
Multiplicamos as entradas do Aluno D pelos pesos atuais:

$$\mu = (w_0 \cdot x_0) + (w_1 \cdot x_1) + (w_2 \cdot x_2)$$
$$\mu = (0 \cdot 1) + (0.1 \cdot 0.9) + (0.06 \cdot 0.8)$$
$$\mu = 0 + 0.09 + 0.048$$
$$\mu = 0.138$$

---

#### 3. Previsão da Rede ($\hat{y}$)
Passamos o valor de $\mu$ pela Função de Ativação:
* Se $\mu \ge 0$, prevê $1$
* Se $\mu < 0$, prevê $0$

Como nosso $\mu$ deu um número positivo ($0.138$):
$$\hat{y} = 1$$
*(A rede previu corretamente que o aluno deveria ser recomendado)*

---

#### 4. Cálculo do Erro ($e$)
Calculamos a diferença entre o que queríamos (Aluno D recomendado, $d=1$) e o que a rede previu ($\hat{y}=1$).

$$e = d - \hat{y}$$
$$e = 1 - 1 = 0$$

O erro foi **0**. A rede neural acertou a previsão para este aluno com os pesos atuais.

---

#### 5. Atualização dos Pesos
Como o erro foi $0$, a rede não precisa realizar nenhum ajuste. Multiplicar o erro por zero na fórmula ($w_i^N = w_i^{ANT} + \eta \cdot e \cdot x_i$) anula a atualização.

Portanto, **os pesos permanecem os mesmos**.

---

#### 6. Resultado da Iteração (Fim da 1ª Época)
Após processar o Aluno D, a rede neural finaliza a sua primeira passagem completa por todos os dados (o que chamamos de 1ª Época). Os pesos finais desta época são:

$$(w_0, w_1, w_2) = (0, 0.1, 0.06)$$

> **Nota:** Como houve erros durante esta época (nos Alunos A e C), o ideal em um treinamento real seria iniciar uma 2ª Época, testando novamente os Alunos A, B, C e D com esses pesos finais, repetindo o processo até que a rede não cometa mais nenhum erro (erro zero para todos os alunos).
