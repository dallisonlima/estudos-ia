# Treinamento do Perceptron - Época 4

Iniciamos a quarta época. Repare que a rede está começando a chegar perto dos valores ideais, mas o Aluno A ainda causa instabilidade.

**Configuração Inicial:**
* **Pesos Iniciais:** $w_0 = 0, w_1 = 0.3, w_2 = 0.18$
* **Taxa de Aprendizagem ($\eta$):** 0.2

---

### Aluno A (Entrada: 1, 0.2, 0.3 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (0 \cdot 1) + (0.3 \cdot 0.2) + (0.18 \cdot 0.3) = 0 + 0.06 + 0.054 = 0.114$
2. **Previsão ($\hat{y}$):**
   Como $0.114 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 0 - 1 = -1$ (Ajuste necessário).
4. **Atualização:**
   * $w_0^N = 0 + 0.2(-1)(1) = -0.2$
   * $w_1^N = 0.3 + 0.2(-1)(0.2) = 0.26$
   * $w_2^N = 0.18 + 0.2(-1)(0.3) = 0.12$
   **Novos Pesos:** $(-0.2, 0.26, 0.12)$

---

### Aluno B (Entrada: 1, 0.4, 0.6 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.26 \cdot 0.4) + (0.12 \cdot 0.6) = -0.2 + 0.104 + 0.072 = -0.024$
2. **Previsão ($\hat{y}$):**
   Como $-0.024 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 0 - 0 = 0$ (Acerto!).

---

### Aluno C (Entrada: 1, 0.7, 0.6 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.26 \cdot 0.7) + (0.12 \cdot 0.6) = -0.2 + 0.182 + 0.072 = 0.054$
2. **Previsão ($\hat{y}$):**
   Como $0.054 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 1 - 1 = 0$ (Acerto! Pela primeira vez a rede acertou o Aluno C nesta configuração).

---

### Aluno D (Entrada: 1, 0.9, 0.8 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.26 \cdot 0.9) + (0.12 \cdot 0.8) = -0.2 + 0.234 + 0.096 = 0.13$
2. **Previsão ($\hat{y}$):**
   Como $0.13 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 1 - 1 = 0$ (Acerto!).

**Resultado Final da Época 4:** Pesos $(-0.2, 0.26, 0.12)$.
