## Qual o objetivo dessa questão?

O objetivo de resolver esse problema é **treinar o Perceptron** para que ele "aprenda" um padrão e consiga separar os alunos em dois grupos: os recomendados ($d=1$) e os não recomendados ($d=0$), baseando-se em suas notas e frequências.

Matematicamente, o que você está fazendo a cada atualização de peso é girar e mover uma **reta de separação** (fronteira de decisão) em um gráfico. 

O objetivo final do exercício é encontrar um conjunto de pesos "perfeito" $(w_0, w_1, w_2)$ que consiga classificar corretamente **todos** os alunos da base de dados de treinamento. Uma vez que esses pesos são encontrados, o modelo está pronto e poderia ser usado na vida real para prever se um **novo** aluno (um Aluno E, por exemplo) deveria ser recomendado ou não, apenas passando a nota e a frequência dele pela fórmula final.

---

## O que fazer após fechar a Época 1?

A regra de ouro do Perceptron é: **o treinamento só acaba quando ocorre uma época inteira sem nenhum erro.**

Como houve erros durante a Época 1 (a rede errou a previsão no Aluno A e no Aluno C), isso significa que a reta de separação ainda não está no lugar certo. A rede **ainda não aprendeu totalmente**.

O que você deve fazer agora é iniciar a **Época 2**:

1. **Volte para o início da lista:** Você vai calcular novamente a ativação e o erro para o Aluno A, depois o B, o C e o D.
2. **Use os últimos pesos encontrados:** A grande diferença é que você **não** volta para aqueles pesos zerados do início do problema. O aprendizado é cumulativo. Você vai iniciar o teste do Aluno A na Época 2 usando os pesos exatos que sobraram no final da Época 1: 
   $$(w_0, w_1, w_2) = (0, 0.1, 0.06)$$
3. **Continue atualizando se errar:** Se a rede errar novamente, você atualiza os pesos com a mesma fórmula. Se acertar, mantém os pesos e vai para o próximo aluno.

### Quando o exercício acaba?
Você vai repetir esse ciclo, criando uma Época 3, Época 4, etc., até que você consiga passar pelos 4 alunos em uma mesma época e o erro ($e$) for igual a **zero para todos eles**. Quando isso acontecer, significa que o Perceptron convergiu, aprendeu o padrão, e o problema está finalizado!
