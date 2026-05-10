# Treinamento do Perceptron - Época 5 (Convergência)

Esta é a época final. Como os pesos foram ajustados no início da Época 4 (Aluno A), precisamos rodar uma época inteira sem fazer alterações para garantir que esses pesos agora funcionam para **todos** os casos sem exceção.

**Configuração Inicial:**
* **Pesos Iniciais:** $w_0 = -0.2, w_1 = 0.26, w_2 = 0.12$
* **Taxa de Aprendizagem ($\eta$):** 0.2

---

### Aluno A (Entrada: 1, 0.2, 0.3 | Alvo: 0)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.26 \cdot 0.2) + (0.12 \cdot 0.3) = -0.2 + 0.052 + 0.036 = -0.112$
2. **Previsão ($\hat{y}$):**
   Como $-0.112 < 0$, a rede prevê $\hat{y} = 0$.
3. **Erro ($e$):**
   $e = 0 - 0 = 0$ (Acerto!).

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
   $e = 1 - 1 = 0$ (Acerto!).

---

### Aluno D (Entrada: 1, 0.9, 0.8 | Alvo: 1)
1. **Ativação ($\mu$):**
   $\mu = (-0.2 \cdot 1) + (0.26 \cdot 0.9) + (0.12 \cdot 0.8) = -0.2 + 0.234 + 0.096 = 0.13$
2. **Previsão ($\hat{y}$):**
   Como $0.13 \ge 0$, a rede prevê $\hat{y} = 1$.
3. **Erro ($e$):**
   $e = 1 - 1 = 0$ (Acerto!).

---

## Conclusão do Treinamento

O algoritmo convergiu! Como a Época 5 foi concluída com **Erro Total = 0**, os pesos encontrados são capazes de separar perfeitamente os alunos recomendados dos não recomendados nesta base de dados.

**Pesos Finais do Modelo:**
* $w_0$ (Viés) = -0.2
* $w_1$ (Peso da Nota) = 0.26
* $w_2$ (Peso da Frequência) = 0.12
