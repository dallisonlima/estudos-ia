# Resolução: Calculando as Métricas do Modelo

Neste documento, vamos resolver o problema extraindo a Matriz de Confusão do nosso conjunto de 20 e-mails e, em seguida, calculando as métricas de performance do nosso filtro de Spam.

A resolução de problemas de avaliação sempre segue dois passos:
1. Contar os quadrantes da Matriz de Confusão.
2. Aplicar as fórmulas das métricas.

---

## Passo 1: Extraindo a Matriz de Confusão
Vamos olhar nossa tabela de dados e classificar cada um dos 20 e-mails nos 4 quadrantes possíveis. 

Lembrando nossa regra de negócio:
* **Classe Positiva (SPAM):** SP
* **Classe Negativa (NÃO SPAM):** NSP

**1. Verdadeiros Positivos (VP):** Era SPAM e o modelo bloqueou como SPAM.
* E-mails: 1, 2, 3, 5, 7 e 8.
* **Total VP = 6**

**2. Verdadeiros Negativos (VN):** Era normal (NSP) e o modelo deixou passar (NSP).
* E-mails: 9, 10, 12, 13, 14, 16, 17, 18, 19 e 20.
* **Total VN = 10**

**3. Falsos Positivos (FP):** Era normal (NSP), mas o modelo deu alarme falso e bloqueou (SP).
* E-mails: 11 e 15.
* **Total FP = 2**

**4. Falsos Negativos (FN):** Era SPAM, mas o modelo não viu e deixou passar (NSP).
* E-mails: 4 e 6.
* **Total FN = 2**

> **💡 Verificação:** A soma dos 4 quadrantes ($6 + 10 + 2 + 2$) é exatamente igual a 20, o total de e-mails testados. Não deixamos nenhum de fora!

---

## Passo 2: Calculando as Métricas

Com os valores da Matriz em mãos (`VP=6`, `VN=10`, `FP=2`, `FN=2`), vamos calcular o quão bom é esse modelo.

### 1. Acurácia
Mede a taxa de acerto geral (em tudo).
$$\text{Acurácia} = \frac{VP + VN}{VP + VN + FP + FN}$$
$$\text{Acurácia} = \frac{6 + 10}{6 + 10 + 2 + 2}$$
$$\text{Acurácia} = \frac{16}{20} = 0.80$$
> **Resultado:** O modelo acertou **80%** de todas as previsões.

### 2. Precisão
Mede a qualidade dos bloqueios. De tudo que ele jogou na lixeira, quanto era lixo mesmo?
$$\text{Precisão} = \frac{VP}{VP + FP}$$
$$\text{Precisão} = \frac{6}{6 + 2}$$
$$\text{Precisão} = \frac{6}{8} = 0.75$$
> **Resultado:** A precisão é de **75%**. Isso significa que a cada 4 e-mails que o modelo joga na lixeira, 1 é um e-mail de trabalho importante (Falso Positivo). 

### 3. Recall (Sensibilidade)
Mede a capacidade de encontrar o alvo. De todos os Spams que existiam, quantos ele pegou?
$$\text{Recall} = \frac{VP}{VP + FN}$$
$$\text{Recall} = \frac{6}{6 + 2}$$
$$\text{Recall} = \frac{6}{8} = 0.75$$
> **Resultado:** O recall é de **75%**. Isso significa que de todos os Spams que chegam, o modelo deixa passar 25% deles para a caixa de entrada (Falso Negativo).

### 4. F1-Score
Média harmônica entre Precisão e Recall.
$$F1 = 2 \cdot \frac{\text{Precisão} \cdot \text{Recall}}{\text{Precisão} + \text{Recall}}$$
$$F1 = 2 \cdot \frac{0.75 \cdot 0.75}{0.75 + 0.75}$$
$$F1 = 2 \cdot \frac{0.5625}{1.50}$$
$$F1 = 0.75$$
> **Resultado:** O F1-Score do modelo é **75%**.

---

## Conclusão do Teste
O modelo tem uma acurácia geral boa (80%), mas em um cenário de negócios, a Precisão de 75% pode ser problemática. Bloquear 1 e-mail legítimo a cada 4 bloqueios (Falsos Positivos) causaria muita dor de cabeça para os usuários. Este modelo precisaria de ajustes (talvez um novo treinamento com mais dados ou alterar o limiar de decisão) antes de ir para produção.