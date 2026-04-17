# Treinamento do Perceptron - Época 2

Nesta segunda época, começamos com os pesos que foram aprendidos e consolidados no final da Época 1. O objetivo é continuar testando os alunos e ajustando a reta de separação sempre que a rede cometer um erro.

**Configuração Inicial:**
* **Pesos Iniciais (vindos da Época 1):** $w_0 = 0$, $w_1 = 0.1$, $w_2 = 0.06$
* **Taxa de Aprendizagem ($\eta$):** $0.2$

---

### Aluno A (Entrada: 1, 0.2, 0.3 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (0 \cdot 1) + (0.1 \cdot 0.2) + (0.06 \cdot 0.3) = 0 + 0.02 + 0.018 = 0.038$
2. **Previsão ($\hat{y}$):**
   Como $0.038 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 0 - 1 = -1$ (Erro encontrado, precisamos atualizar).
4. **Atualização:**
   * $w_0^N = 0 + 0.2 \cdot (-1) \cdot (1) = -0.2$
   * $w_1^N = 0.1 + 0.2 \cdot (-1) \cdot (0.2) = 0.1 - 0.04 = 0.06$
   * $w_2^N = 0.06 + 0.2 \cdot (-1) \cdot (0.3) = 0.06 - 0.06 = 0$
   
   **Novos Pesos:** $(-0.2, 0.06, 0)$

---

### Aluno B (Entrada: 1, 0.4, 0.6 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.06 \cdot 0.4) + (0 \cdot 0.6) = -0.2 + 0.024 + 0 = -0.176$
2. **Previsão ($\hat{y}$):**
   Como $-0.176 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 0 - 0 = 0$ (Acerto! Mantemos os pesos).

---

### Aluno C (Entrada: 1, 0.7, 0.6 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.06 \cdot 0.7) + (0 \cdot 0.6) = -0.2 + 0.042 + 0 = -0.158$
2. **Previsão ($\hat{y}$):**
   Como $-0.158 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 1 - 0 = 1$ (Erro encontrado, novo ajuste necessário).
4. **Atualização:**
   * $w_0^N = -0.2 + 0.2 \cdot (1) \cdot (1) = -0.2 + 0.2 = 0$
   * $w_1^N = 0.06 + 0.2 \cdot (1) \cdot (0.7) = 0.06 + 0.14 = 0.2$
   * $w_2^N = 0 + 0.2 \cdot (1) \cdot (0.6) = 0 + 0.12 = 0.12$
   
   **Novos Pesos:** $(0, 0.2, 0.12)$

---

### Aluno D (Entrada: 1, 0.9, 0.8 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (0 \cdot 1) + (0.2 \cdot 0.9) + (0.12 \cdot 0.8) = 0 + 0.18 + 0.096 = 0.276$
2. **Previsão ($\hat{y}$):**
   Como $0.276 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 1 - 1 = 0$ (Acerto!).

**Resultado Final da Época 2:** Pesos $(0, 0.2, 0.12)$. Como houve erros nos alunos A e C, precisamos seguir para a Época 3.
