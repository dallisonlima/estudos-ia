# Resolução: Treinamento do Perceptron - Época 2

Nesta etapa, utilizamos os pesos finais obtidos na Época 1 como os pesos iniciais. O objetivo é continuar o ajuste da fronteira de decisão até que o erro seja zero para todos os exemplos.

**Parâmetros:**
* **Taxa de Aprendizagem ($\eta$):** 0.2
* **Pesos Iniciais (da Época 1):** $w_0 = 0$, $w_1 = 0.1$, $w_2 = 0.06$

---

### 1. Aluno A
* **Entrada:** $(1, 0.2, 0.3)$ | **Desejado ($d$):** 0
* **Ativação ($\mu$):** $(0 \cdot 1) + (0.1 \cdot 0.2) + (0.06 \cdot 0.3) = 0.038$
* **Previsão ($\hat{y}$):** $\mu \ge 0 \Rightarrow 1$
* **Erro ($e$):** $0 - 1 = -1$
* **Atualização de Pesos:**
  * $w_0 = 0 + 0.2 \cdot (-1) \cdot 1 = -0.2$
  * $w_1 = 0.1 + 0.2 \cdot (-1) \cdot 0.2 = 0.06$
  * $w_2 = 0.06 + 0.2 \cdot (-1) \cdot 0.3 = 0$
* **Novos Pesos:** $(-0.2, 0.06, 0)$

---

### 2. Aluno B
* **Entrada:** $(1, 0.4, 0.6)$ | **Desejado ($d$):** 0
* **Ativação ($\mu$):** $(-0.2 \cdot 1) + (0.06 \cdot 0.4) + (0 \cdot 0.6) = -0.176$
* **Previsão ($\hat{y}$):** $\mu < 0 \Rightarrow 0$
* **Erro ($e$):** $0 - 0 = 0$
* **Pesos:** Mantidos em $(-0.2, 0.06, 0)$

---

### 3. Aluno C
* **Entrada:** $(1, 0.7, 0.6)$ | **Desejado ($d$):** 1
* **Ativação ($\mu$):** $(-0.2 \cdot 1) + (0.06 \cdot 0.7) + (0 \cdot 0.6) = -0.158$
* **Previsão ($\hat{y}$):** $\mu < 0 \Rightarrow 0$
* **Erro ($e$):** $1 - 0 = 1$
* **Atualização de Pesos:**
  * $w_0 = -0.2 + 0.2 \cdot 1 \cdot 1 = 0$
  * $w_1 = 0.06 + 0.2 \cdot 1 \cdot 0.7 = 0.2$
  * $w_2 = 0 + 0.2 \cdot 1 \cdot 0.6 = 0.12$
* **Novos Pesos:** $(0, 0.2, 0.12)$

---

### 4. Aluno D
* **Entrada:** $(1, 0.9, 0.8)$ | **Desejado ($d$):** 1
* **Ativação ($\mu$):** $(0 \cdot 1) + (0.2 \cdot 0.9) + (0.12 \cdot 0.8) = 0.276$
* **Previsão ($\hat{y}$):** $\mu \ge 0 \Rightarrow 1$
* **Erro ($e$):** $1 - 1 = 0$
* **Pesos:** Mantidos em $(0, 0.2, 0.12)$

---

## Resumo da Época 2

Ao final da segunda época, a rede ainda apresentou erros nos alunos **A** e **C**. Portanto, o treinamento deve prosseguir para a Época 3.

| Aluno | $\mu$ | $\hat{y}$ | $d$ | Erro ($e$) | Novos Pesos $(w_0, w_1, w_2)$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **A** | 0.038 | 1 | 0 | -1 | (-0.2, 0.06, 0) |
| **B** | -0.176 | 0 | 0 | 0 | (-0.2, 0.06, 0) |
| **C** | -0.158 | 0 | 1 | 1 | (0, 0.2, 0.12) |
| **D** | 0.276 | 1 | 1 | 0 | (0, 0.2, 0.12) |

**Pesos finais para a Época 3:** $(0, 0.2, 0.12)$
