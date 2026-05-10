# Teoria: Matriz de Confusão e Métricas de Classificação

Para avaliar um modelo de classificação, não basta saber a porcentagem geral de acertos. Precisamos entender *como* ele erra. Para isso, extraímos 4 variáveis fundamentais comparando a previsão do modelo com a realidade, e a partir delas, calculamos as métricas de performance.

## 1. As 4 Variáveis Base (A Matriz)

Imagine uma tabela 2x2. Cada e-mail testado vai cair em um destes 4 baldes:

* **VP (Verdadeiro Positivo):** O modelo previu Positivo (SPAM) e a realidade era Positivo (SPAM). **(Acerto)**
* **VN (Verdadeiro Negativo):** O modelo previu Negativo (NÃO SPAM) e a realidade era Negativo (NÃO SPAM). **(Acerto)**
* **FP (Falso Positivo):** O modelo previu Positivo (SPAM), mas a realidade era Negativo (NÃO SPAM). **(Erro - Alarme Falso)**
* **FN (Falso Negativo):** O modelo previu Negativo (NÃO SPAM), mas a realidade era Positivo (SPAM). **(Erro - Passou Despercebido)**

*Valores extraídos do nosso conjunto de teste (20 e-mails):*
`VP = 6` | `VN = 10` | `FP = 2` | `FN = 2`

---

## 2. As Fórmulas (Métricas de Avaliação)

Com as 4 variáveis em mãos, aplicamos as seguintes fórmulas matemáticas para obter indicadores de qualidade do modelo, que variam de 0 a 1 (ou 0% a 100%).

### Acurácia (Accuracy)
É a métrica mais intuitiva. Responde à pergunta: **"De todos os e-mails, qual a porcentagem total de acertos do modelo?"**

$$\text{Acurácia} = \frac{VP + VN}{VP + VN + FP + FN}$$

* **Cálculo no nosso exemplo:** $(6 + 10) / 20 = 16 / 20 = 0.80$ (ou 80%)
* **O problema da Acurácia:** Ela pode ser enganosa se a base de dados for desbalanceada (ex: se tivermos 99 e-mails normais e 1 spam).

### Precisão (Precision)
Foca na qualidade das previsões positivas. Responde à pergunta: **"De todos os e-mails que o modelo DISSE que era Spam, quantos REALMENTE eram?"**

$$\text{Precisão} = \frac{VP}{VP + FP}$$

* **Cálculo no nosso exemplo:** $6 / (6 + 2) = 6 / 8 = 0.75$ (ou 75%)
* **Quando é importante:** Quando o Falso Positivo custa muito caro. No nosso caso, queremos alta precisão para evitar que e-mails importantes de trabalho (Não Spam) sejam jogados na lixeira (Spam).

### Sensibilidade ou Recall (True Positive Rate)
Foca em não deixar o alvo escapar. Responde à pergunta: **"De todos os Spams que REALMENTE existem na base, quantos o modelo conseguiu ENCONTRAR?"**

$$\text{Recall} = \frac{VP}{VP + FN}$$

* **Cálculo no nosso exemplo:** $6 / (6 + 2) = 6 / 8 = 0.75$ (ou 75%)
* **Quando é importante:** Quando o Falso Negativo custa caro. Por exemplo, em um modelo que detecta câncer. É melhor dar um alarme falso (FP) do que deixar um paciente doente passar batido (FN).

### F1-Score
É a média harmônica entre a Precisão e o Recall. 

$$F1 = 2 \cdot \frac{\text{Precisão} \cdot \text{Recall}}{\text{Precisão} + \text{Recall}}$$

* **Quando usar:** Geralmente, quando você tenta aumentar a Precisão, o Recall cai (e vice-versa). O F1-Score é a métrica ideal quando você precisa encontrar um ponto de equilíbrio entre os dois ou quando sua base de dados é muito desbalanceada.