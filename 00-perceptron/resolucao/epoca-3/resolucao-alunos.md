# Treinamento do Perceptron - Época 3

Nesta terceira época, partimos dos pesos consolidados ao final da Época 2. O processo segue a mesma lógica: testar cada aluno, verificar o erro e ajustar os pesos para "girar" a reta de separação no gráfico.

**Configuração Inicial:**
* **Pesos Iniciais:** $w_0 = 0, w_1 = 0.2, w_2 = 0.12$
* **Taxa de Aprendizagem ($\eta$):** 0.2

---

### Aluno A (Entrada: 1, 0.2, 0.3 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (0 \cdot 1) + (0.2 \cdot 0.2) + (0.12 \cdot 0.3) = 0 + 0.04 + 0.036 = 0.076$
2. **Previsão ($\hat{y}$):**
   Como $0.076 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 0 - 1 = -1$ (Erro encontrado, precisamos atualizar).
4. **Atualização:**
   * $w_0^N = 0 + 0.2(-1)(1) = -0.2$
   * $w_1^N = 0.2 + 0.2(-1)(0.2) = 0.16$
   * $w_2^N = 0.12 + 0.2(-1)(0.3) = 0.06$
   **Novos Pesos:** $(-0.2, 0.16, 0.06)$

---

### Aluno B (Entrada: 1, 0.4, 0.6 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.16 \cdot 0.4) + (0.06 \cdot 0.6) = -0.2 + 0.064 + 0.036 = -0.1$
2. **Previsão ($\hat{y}$):**
   Como $-0.1 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 0 - 0 = 0$ (Acerto! Mantemos os pesos).

---

### Aluno C (Entrada: 1, 0.7, 0.6 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.16 \cdot 0.7) + (0.06 \cdot 0.6) = -0.2 + 0.112 + 0.036 = -0.052$
2. **Previsão ($\hat{y}$):**
   Como $-0.052 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 1 - 0 = 1$ (Erro encontrado, novo ajuste necessário).
4. **Atualização:**
   * $w_0^N = -0.2 + 0.2(1)(1) = 0$
   * $w_1^N = 0.16 + 0.2(1)(0.7) = 0.3$
   * $w_2^N = 0.06 + 0.2(1)(0.6) = 0.18$
   **Novos Pesos:** $(0, 0.3, 0.18)$

---

### Aluno D (Entrada: 1, 0.9, 0.8 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (0 \cdot 1) + (0.3 \cdot 0.9) + (0.18 \cdot 0.8) = 0 + 0.27 + 0.144 = 0.414$
2. **Previsão ($\hat{y}$):**
   Como $0.414 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 1 - 1 = 0$ (Acerto!).

**Resultado Final da Época 3:** Pesos $(0, 0.3, 0.18)$.
