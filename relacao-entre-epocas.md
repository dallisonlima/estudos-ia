# A Relação entre Épocas no Treinamento do Perceptron

No aprendizado de máquina, entender como as épocas se conectam é fundamental para compreender como o modelo evolui de um estado inicial zerado até o reconhecimento completo de um padrão.

## 1. O que define uma Época?
Uma época é uma passagem completa por **todos** os dados do conjunto de treinamento. No nosso exemplo (Alunos A, B, C e D), uma época só termina após o processamento do Aluno D.

## 2. A Continuidade dos Pesos (A "Memória" da Rede)
A relação mais importante entre as épocas é que o Perceptron utiliza o estado final de uma época como o ponto de partida para a próxima. Não há um "reset".

* **Época 1:** Começa com pesos zerados ($w=0$).
* **Época 2:** Começa exatamente com os pesos que sobraram da atualização do Aluno C na Época 1.
* **Época 3 em diante:** Cada ciclo herda o "conhecimento" acumulado de todos os ajustes anteriores.



## 3. Exemplo Prático de Evolução (Pesos Finais)

Observe como os pesos se transformaram ao longo das épocas para conseguir separar os alunos recomendados dos não recomendados:

| Fase | Peso $w_0$ (Viés) | Peso $w_1$ (Nota) | Peso $w_2$ (Freq) | Resultado |
| :--- | :---: | :---: | :---: | :--- |
| **Início Época 1** | 0 | 0 | 0 | Estado inicial. |
| **Final Época 1** | 0 | 0.1 | 0.06 | Primeiro aprendizado. |
| **Final Época 2** | 0 | 0.2 | 0.12 | Refinamento. |
| **Final Época 3** | 0 | 0.3 | 0.18 | Ajuste fino. |
| **Final Época 4** | -0.2 | 0.26 | 0.12 | **Convergência encontrada.** |

## 4. Por que precisamos de várias épocas?
Raramente a rede aprende tudo na primeira passagem. As múltiplas épocas servem para:

1.  **Refinar a Fronteira de Decisão:** Cada erro em um aluno específico "empurra" a reta de separação para uma posição melhor no gráfico.
2.  **Consolidar o Acerto Global:** O objetivo não é acertar apenas o Aluno A ou o Aluno C isoladamente, mas encontrar pesos que funcionem para **todos os quatro simultaneamente**.
3.  **Superar Conflitos:** Muitas vezes, ajustar o peso para acertar o Aluno C pode fazer a rede errar o Aluno A novamente. As épocas continuam até que todos os conflitos matemáticos sejam resolvidos.

## 5. O Ponto de Convergência
O treinamento encerra quando a interferência entre as épocas acaba. Quando uma época inteira roda e os pesos iniciais são iguais aos pesos finais (Erro = 0 para todos), o modelo **convergiu**. No nosso caso, isso foi garantido na **Época 5**, validando os pesos da Época 4.
