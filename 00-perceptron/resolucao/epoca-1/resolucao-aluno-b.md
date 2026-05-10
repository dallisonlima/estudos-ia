### Aluno B

#### 1. Dados de Entrada e Pesos Herdados
Agora, testamos o segundo aluno da base de dados. O detalhe mais importante aqui é que **não usamos mais os pesos iniciais zerados**, mas sim os pesos que a rede acabou de aprender na etapa do Aluno A.

* **Entradas do Aluno B ($X_B$)**: $(1, 0.4, 0.6)$
  * $x_0 = 1$ (Viés / Bias)
  * $x_1 = 0.4$ (Nota normalizada)
  * $x_2 = 0.6$ (Frequência normalizada)
* **Saída Desejada ($d$)**: $0$ (Não recomendado)
* **Pesos Atuais (herdados do Aluno A)**: $w_0 = -0.2$, $w_1 = -0.04$, $w_2 = -0.06$
* **Taxa de Aprendizagem ($\eta$)**: $0.2$

---

#### 2. Cálculo da Ativação ($\mu$)
Multiplicamos as entradas do Aluno B pelos novos pesos:

$$\mu = (w_0 \cdot x_0) + (w_1 \cdot x_1) + (w_2 \cdot x_2)$$
$$\mu = (-0.2 \cdot 1) + (-0.04 \cdot 0.4) + (-0.06 \cdot 0.6)$$
$$\mu = -0.2 - 0.016 - 0.036$$
$$\mu = -0.252$$

---

#### 3. Previsão da Rede ($\hat{y}$)
Passamos o valor de $\mu$ pela Função de Ativação:
* Se $\mu \ge 0$, prevê $1$
* Se $\mu < 0$, prevê $0$

Como nosso $\mu$ deu um número negativo ($-0.252$):
$$\hat{y} = 0$$
*(A rede previu corretamente que o aluno não deve ser recomendado)*

---

#### 4. Cálculo do Erro ($e$)
Calculamos a diferença entre o que queríamos e o que a rede previu.

$$e = d - \hat{y}$$
$$e = 0 - 0 = 0$$

Como o erro foi **zero**, significa que a rede neural acertou a previsão para este aluno específico com os pesos atuais.

---

#### 5. Atualização dos Pesos
A regra de aprendizado diz que só ajustamos os pesos quando há erro. Como o erro foi $0$, a fórmula de atualização ($w_i^N = w_i^{ANT} + \eta \cdot e \cdot x_i$) resultaria em somar zero aos pesos atuais. 

Portanto, **não há atualização de pesos nesta etapa**. Os pesos permanecem intactos.

---

#### 6. Resultado da Iteração
Após processar o Aluno B, a rede neural manteve seus pesos, pois acertou a previsão. Os pesos que serão passados para o teste do **Aluno C** são:

$$(w_0, w_1, w_2) = (-0.2, -0.04, -0.06)$$
