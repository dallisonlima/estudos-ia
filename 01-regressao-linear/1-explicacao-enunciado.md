# Fundamentos Teóricos: Regressão Linear Múltipla

Este documento detalha os conceitos teóricos de Machine Learning aplicados ao problema de previsão de notas de alunos. Ao contrário do **Perceptron**, que tem como objetivo classificar dados em categorias (ex: aprovado/reprovado), a **Regressão Linear** busca prever um valor numérico contínuo (ex: a nota exata).

## 1. O Problema e a Natureza dos Dados

Na aprendizagem supervisionada, fornecemos ao algoritmo exemplos históricos contendo as perguntas e as respostas corretas.

* **Features / Atributos ($X$):** São as variáveis independentes, as características que usamos para fazer a previsão. Neste problema, temos três dimensões ($X_1, X_2, X_3$). Como temos mais de uma feature, o problema é classificado como **Regressão Linear Múltipla**.
* **Target / Rótulo ($y$):** É a variável dependente, o alvo numérico contínuo que queremos que o modelo aprenda a prever (a nota final).
* **Vetor de Entrada:** O aluno é representado matematicamente como um vetor no espaço tridimensional: $x = (X_1, X_2, X_3)$.

## 2. O Modelo Matemático (O Hiperplano)

O modelo de regressão assume que existe uma relação linear entre as features de entrada e o rótulo de saída. A equação da previsão é:

$$\hat{y} = b + W_1X_1 + W_2X_2 + W_3X_3$$

* **$\hat{y}$ (y-chapéu):** Representa a previsão feita pelo modelo, para diferenciá-la do $y$ real.
* **Pesos Sinápticos / Weights ($W$):** Representam a "importância" de cada feature. Se o número de listas resolvidas ($X_2$) impactar mais a nota do que as horas de estudo ($X_1$), durante o treinamento o modelo atribuirá um valor maior para $W_2$ do que para $W_1$. Inicializamos com zero por convenção.
* **Viés / Bias ($b$):** É o ponto de interceptação. Ele representa o valor base da previsão quando todas as entradas ($X$) são zero. Sem o viés, o modelo seria forçado a sempre prever $0$ para um aluno com zero estudo, listas e participação, o que limitaria a flexibilidade da reta de se ajustar aos dados reais.

## 3. Função de Custo e Erro

Para que o modelo "aprenda", ele precisa saber o quão longe suas previsões estão da realidade.

$$E = y - \hat{y}$$

O erro ($E$) é simplesmente o resíduo: a diferença entre a nota real ($y$) e a nota prevista ($\hat{y}$). Se o erro for positivo, o modelo previu para baixo. Se for negativo, o modelo previu para cima. O objetivo do treinamento é minimizar esse erro ao longo do tempo.

## 4. Otimização: Gradiente Descendente Estocástico (SGD)

As fórmulas de atualização dos parâmetros representam o algoritmo de otimização buscando o menor erro possível.

$$W_{i,n} = W_{i,a} + \eta \cdot E \cdot X_i$$

* **Estocástico (Ponto a Ponto):** Note que atualizamos os pesos imediatamente após calcular o erro de um *único* aluno (ponto). Isso é a característica do SGD (Stochastic Gradient Descent). Se calculássemos o erro de todos os 5 alunos primeiro para só depois atualizar os pesos, estaríamos usando o *Batch Gradient Descent*.
* **A Correção:** A atualização é proporcional à entrada $X_i$. Se a entrada $X_1$ era grande e o modelo errou, o peso $W_1$ sofrerá um ajuste maior, pois aquela entrada teve grande responsabilidade na previsão incorreta.

## 5. Taxa de Aprendizado (Learning Rate - $\eta$)

A constante $\eta = 0.01$ (Eta) é o hiperparâmetro mais importante do algoritmo. Ela define o tamanho do "passo" que o modelo dá na direção do ajuste correto a cada iteração.

* **Se $\eta$ for muito alto:** O modelo pode dar passos largos demais, ultrapassar o ponto de ajuste ideal e não convergir (ficar oscilando ou divergir para o infinito).
* **Se $\eta$ for muito baixo:** O modelo dá passos minúsculos, tornando o treinamento extremamente lento e custoso computacionalmente.
* O valor de $0.01$ é uma escolha clássica e conservadora para garantir que a correção dos pesos (como $W_{1,n} = 0.09$) seja suave e progressiva.