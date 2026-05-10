# 🧠 Estudos de Inteligência Artificial

Repositório de estudos e exercícios práticos sobre fundamentos de Inteligência Artificial e Machine Learning, desenvolvidos durante a graduação.

Cada módulo contém o **enunciado** do problema, uma **explicação detalhada** dos conceitos envolvidos e a **resolução passo a passo**.

---

## 📂 Estrutura do Repositório

```
estudos-ia/
├── 00-perceptron/          # Perceptron simples para classificação binária
├── 01-regressao-linear/    # Regressão Linear com gradiente descendente
├── 02-matriz-confusao/     # Métricas de avaliação e Matriz de Confusão
└── 03-redes-neurais/       # MLP com Backpropagation (resolução da Época 1)
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

### [03 — Redes Neurais (MLP + Backpropagation)](./03-redes-neurais/)

> Treinamento passo a passo de uma rede MLP com Retropropagação do Erro.

O módulo cobre o treinamento de uma rede *Multilayer Perceptron* com **1 neurônio oculto (sigmoide)** e **1 neurônio de saída (linear)**, resolvendo a **Época 1** completa ponto a ponto. Os tópicos incluem:

- **Forward Pass:** $Z_h \to h = \sigma(Z_h) \to \hat{y} = b_o + \mu \cdot h$
- **Cálculo do erro:** $E = y - \hat{y}$
- **Backpropagation da camada de saída:** atualização de $\mu$ e $b_o$
- **Backpropagation da camada oculta:** cálculo do delta $\delta_h = E \cdot \mu \cdot h(1-h)$ e atualização de $V_1$, $V_2$, $b_h$
- Evolução dos pesos ao longo dos 3 pontos da Época 1

**Taxa de aprendizagem:** $\eta = 0.1$ | **Topologia:** 2 entradas → 1 oculto → 1 saída

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
- [x] Compreender a arquitetura MLP e a diferença entre modelos lineares e não-lineares
- [x] Executar o algoritmo Backpropagation manualmente (Forward Pass + atualização de pesos em duas camadas)

---

*Repositório em desenvolvimento contínuo conforme o andamento das aulas.*
