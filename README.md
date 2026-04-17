# 🧠 Treinamento de Perceptron Passo a Passo

Bem-vindo ao repositório de estudo do **Perceptron Simples**! 

Este projeto contém a resolução matemática, detalhada e iterativa do treinamento de uma rede neural de camada única (Perceptron). O objetivo do modelo treinado aqui é resolver um problema de classificação: decidir se um aluno deve ser **Recomendado ($d=1$)** ou **Não Recomendado ($d=0$)** com base em duas variáveis de entrada (Nota e Frequência).

---

## 📂 Estrutura do Repositório

O repositório está organizado de forma sequencial para facilitar o acompanhamento do fluxo de aprendizado do algoritmo.

```text
📦 perceptron-passo-a-passo
 ┣ 📜 enunciado.md              # O problema, as fórmulas e a base de dados inicial
 ┣ 📜 explicaco-enunciado.md      # Dicas importantes para não errar os cálculos
 ┣ 📜 relacao-entre-epocas.md         # Explicação teórica de como os pesos fluem entre as épocas
 ┣ 📜 conclusao-final.md         # Conclusao final do exercicio
 ┣ 📂 epoca1                    # Resolução do 1º ciclo de treinamento (Alunos A ao D)
 ┣ 📂 epoca2                    # Resolução do 2º ciclo de treinamento
 ┣ 📂 epoca3                    # Resolução do 3º ciclo de treinamento
 ┣ 📂 epoca4                    # Resolução do 4º ciclo de treinamento (Ajuste final)
 ┗ 📂 epoca5                    # 5º ciclo: Época sem erros (Convergência atingida)

```
## 🚀 Como utilizar este material de estudo
Para aproveitar ao máximo as resoluções, recomendo seguir esta ordem de leitura:
 1. **Entenda o problema:** Comece pelo arquivo enunciado.md na raiz do projeto. Familiarize-se com as entradas, saídas desejadas, a taxa de aprendizagem (\eta) e as fórmulas de ativação e atualização de pesos.
 2. **Entenda a teoria contínua:** Leia relacao_epocas.md para entender por que não zeramos os pesos ao final de cada rodada e como a rede constrói sua "memória".
 3. **Siga o cálculo passo a passo:** * Entre na pasta epoca1/ e acompanhe os cálculos do Aluno A até o D.
   * Note como os pesos de saída de um aluno se tornam os pesos de entrada do próximo.
   * Prossiga para as pastas epoca2/, epoca3/ e epoca4/, observando como o erro (e) força a atualização da fronteira de decisão.
 4. **Convergência:** Na pasta epoca5/, você verá que a rede consegue processar todos os alunos sem cometer nenhum erro (e=0), sinalizando que o treinamento foi finalizado com sucesso.
 5. **Revisão:** Finalize lendo dicas_e_conclusao.md para fixar os pontos de atenção (como regras de sinais e condições de parada do algoritmo).
## 🧮 Fórmulas Principais Utilizadas
 * **Cálculo da Ativação (\mu):**
   
 * **Função de Ativação (Regra de Decisão):**
   
 * **Regra de Aprendizado (Atualização de Pesos):**
   
   
   *(Só é calculada quando existe erro, ou seja, quando o erro e \neq 0)*
💡 **Nota:** Este material foi construído como guia prático para disciplinas de Inteligência Artificial e Aprendizado de Máquina, focando na execução matemática em papel/planilha para consolidação teórica antes de ir para o código.