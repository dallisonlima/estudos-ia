# Avaliação de Modelos: Métricas de Classificação

Este repositório contém o estudo sobre como avaliar a performance de um modelo de Machine Learning após o seu treinamento, utilizando a Matriz de Confusão.

## O Problema

Vamos analisar um classificador treinado para identificar se um e-mail é **SPAM** ou **NÃO SPAM**. 

Para isso, definimos as nossas classes:
* **Classe Positiva:** SPAM (SP)
* **Classe Negativa:** NÃO SPAM (NSP)

Temos um conjunto de testes com 20 e-mails onde já sabemos a resposta verdadeira (Classe Real) e passamos esses dados pelo nosso modelo para ver o que ele adivinhou (Classe Predita).

## Dados de Teste

| E-mail | Classe Real | Classe Predita |
| :---: | :---: | :---: |
| 1 | SP | SP |
| 2 | SP | SP |
| 3 | SP | SP |
| 4 | SP | NSP |
| 5 | SP | SP |
| 6 | SP | NSP |
| 7 | SP | SP |
| 8 | SP | SP |
| 9 | NSP | NSP |
| 10 | NSP | NSP |
| 11 | NSP | SP |
| 12 | NSP | NSP |
| 13 | NSP | NSP |
| 14 | NSP | NSP |
| 15 | NSP | SP |
| 16 | NSP | NSP |
| 17 | NSP | NSP |
| 18 | NSP | NSP |
| 19 | NSP | NSP |
| 20 | NSP | NSP |