### Aluno C

#### 1. Dados de Entrada e Pesos Herdados
Agora vamos testar o terceiro aluno. Continuamos utilizando os pesos que sobraram do passo anterior (que neste caso, permaneceram os mesmos do Aluno A, já que o Aluno B não gerou erro).

* **Entradas do Aluno C ($X_C$)**: $(1, 0.7, 0.6)$
  * $x_0 = 1$ (Viés / Bias)
  * $x_1 = 0.7$ (Nota normalizada)
  * $x_2 = 0.6$ (Frequência normalizada)
* **Saída Desejada ($d$)**: $1$ (Recomendado)
* **Pesos Atuais (herdados do Aluno B)**: $w_0 = -0.2$, $w_1 = -0.04$, $w_2 = -0.06$
* **Taxa de Aprendizagem ($\eta$)**: $0.2$

---

#### 2. Cálculo da Ativação ($\mu$)
Multiplicamos as entradas do Aluno C pelos pesos atuais:

$$\mu = (w_0 \cdot x_0) + (w_1 \cdot x_1) + (w_2 \cdot x_2)$$
$$\mu = (-0.2 \cdot 1) + (-0.04 \cdot 0.7) + (-0.06 \cdot 0.6)$$
$$\mu = -0.2 - 0.028 - 0.036$$
$$\mu = -0.264$$

---

#### 3. Previsão da Rede ($\hat{y}$)
Passamos o valor de $\mu$ pela Função de Ativação:
* Se $\mu \ge 0$, prevê $1$
* Se $\mu < 0$, prevê $0$

Como nosso $\mu$ deu um número negativo ($-0.264$):
$$\hat{y} = 0$$
*(A rede previu que o aluno não deveria ser recomendado)*

---

#### 4. Cálculo do Erro ($e$)
Calculamos a diferença entre o que queríamos (Aluno C deveria ser recomendado, $d=1$) e o que a rede previu ($\hat{y}=0$).

$$e = d - \hat{y}$$
$$e = 1 - 0 = 1$$

O erro foi **1**. Como houve erro na previsão, a rede precisa reajustar seus pesos.

---

#### 5. Atualização dos Pesos
Aplicamos a fórmula de aprendizado ($w_i^N = w_i^{ANT} + \eta \cdot e \cdot x_i$) para cada um dos três pesos:

* **Atualizando o peso do Viés ($w_0$)**:
  
  $$w_0^N = -0.2 + 0.2 \cdot (1) \cdot (1)$$
  
  $$w_0^N = -0.2 + 0.2 = 0$$

* **Atualizando o peso da Nota ($w_1$)**:
  
  $$w_1^N = -0.04 + 0.2 \cdot (1) \cdot (0.7)$$
  
  $$w_1^N = -0.04 + 0.14 = 0.1$$

* **Atualizando o peso da Frequência ($w_2$)**:
  
  $$w_2^N = -0.06 + 0.2 \cdot (1) \cdot (0.6)$$
  
  $$w_2^N = -0.06 + 0.12 = 0.06$$

---

#### 6. Resultado da Iteração
Após processar o Aluno C, a rede neural aprendeu com o erro e ajustou novamente seus pesos. Os novos pesos que serão passados para o teste do último aluno, o **Aluno D**, são:

$$(w_0, w_1, w_2) = (0, 0.1, 0.06)$$
