# 🧠 Estudos de Inteligência Artificial

Repositório de estudos e exercícios práticos sobre fundamentos de Inteligência Artificial e Machine Learning, desenvolvidos durante a graduação.

Cada módulo contém o **enunciado** do problema, uma **explicação detalhada** dos conceitos envolvidos e a **resolução passo a passo**.

---

## 📂 Estrutura do Repositório

```
estudos-ia/
├── 00-perceptron/          # Perceptron simples para classificação binária
├── 01-regressao-linear/    # Regressão Linear com gradiente descendente
└── 02-matriz-confusao/     # Métricas de avaliação e Matriz de Confusão
```

---

## 📚 Módulos

### [00 — Perceptron](./00-perceptron/)

> Classificação binária com o algoritmo Perceptron.

O problema consiste em treinar um Perceptron simples para **recomendar ou não um aluno**, com base em sua nota e frequência normalizadas. O exercício cobre:

- Cálculo da ativação: $\mu = w_0x_0 + w_1x_1 + w_2x_2$
- Função de ativação degrau (step function)
- Cálculo do erro: $e = d - \hat{y}$
- Regra de atualização de pesos: $w_i^{\text{novo}} = w_i^{\text{ant}} + \eta \cdot e \cdot x_i$

**Taxa de aprendizagem:** $\eta = 0.2$ | **Pesos iniciais:** $w_0 = w_1 = w_2 = 0$

---

### [01 — Regressão Linear](./01-regressao-linear/)

> Previsão de nota final com Regressão Linear multivariável.

O modelo estima a nota final $\hat{y}$ de um aluno a partir de três características: horas de estudo ($X_1$), listas resolvidas ($X_2$) e participação em aula ($X_3$).

$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

O exercício cobre:

- Definição do modelo linear multivariável
- Cálculo do erro: $E = y - \hat{y}$
- Atualização dos pesos via gradiente descendente

**Taxa de aprendizagem:** $\eta = 0.01$ | **5 pontos de treinamento**

---

### [02 — Matriz de Confusão](./02-matriz-confusao/)

> Avaliação de modelos de classificação com métricas de desempenho.

O estudo analisa um classificador de **spam/não-spam** em um conjunto de teste de 20 e-mails. Os tópicos abordados incluem:

- Construção da Matriz de Confusão (TP, FP, TN, FN)
- Cálculo de **Acurácia**, **Precisão**, **Recall** e **F1-Score**
- Interpretação das métricas e análise crítica do modelo

---

## 🛠️ Como usar este repositório

Os arquivos são escritos em **Markdown** com notação matemática LaTeX. Para melhor visualização, recomenda-se:

- **VS Code** com a extensão [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)
- **Obsidian** (suporte nativo a LaTeX com MathJax)
- Qualquer visualizador Markdown com suporte a MathJax/KaTeX

---

## 🎯 Objetivos de Aprendizagem

- [x] Entender o funcionamento do Perceptron e a regra de aprendizagem
- [x] Implementar Regressão Linear com atualização de pesos via gradiente
- [x] Construir e interpretar a Matriz de Confusão
- [x] Calcular e analisar métricas de avaliação de modelos (Acurácia, Precisão, Recall, F1)

---

*Repositório em desenvolvimento contínuo conforme o andamento das aulas.*
