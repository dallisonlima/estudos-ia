# Entendendo o Cenário: Avaliação do Modelo

Nos estudos anteriores (como Perceptron e Regressão Linear), o nosso foco era **treinar** o modelo. Nós passávamos os dados repetidas vezes para ajustar os pesos até que ele aprendesse a fazer previsões. 

Agora, o cenário é outro. O modelo **já está treinado**. O que nós temos em mãos é a fase de **Teste e Avaliação**. Precisamos descobrir se esse modelo é bom o suficiente para ser colocado em produção (uso real).

Para entender o enunciado e a tabela de dados, precisamos dominar três conceitos fundamentais:

## 1. Classe Positiva vs. Classe Negativa
Em problemas de classificação binária (onde a resposta é A ou B, Sim ou Não), nós sempre dividimos as respostas em "Positiva" e "Negativa". 

* **Atenção:** "Positivo" na inteligência artificial não significa "coisa boa". Significa **"aquilo que eu estou procurando"** ou **"o evento aconteceu"**.
* Como o nosso modelo é um filtro de Spam, o nosso alvo (o que queremos detectar e bloquear) é o Spam. 
* Portanto:
    * **Classe Positiva = SPAM (SP)**
    * **Classe Negativa = NÃO SPAM (NSP)** (O e-mail normal, legítimo).

## 2. Classe Real vs. Classe Predita
Se você olhar a tabela de dados, verá duas colunas muito importantes que contam a história do nosso teste:

* **Classe Real ($y_{true}$):** É a verdade absoluta. É o gabarito. Nós (humanos) olhamos esses 20 e-mails e rotulamos manualmente o que era Spam e o que não era.
* **Classe Predita ($y_{pred}$):** É o palpite da máquina. Nós pegamos o texto desses 20 e-mails, escondemos o gabarito, e pedimos para a IA classificar. 

Quando a *Classe Real* é igual à *Classe Predita*, o modelo **acertou**. Quando são diferentes, o modelo **errou** (como aconteceu no E-mail 4, que era SPAM, mas o modelo disse que era NSP).

## 3. Por que precisamos ir além do "Acertou ou Errou"?
Olhando a tabela, o modelo acertou 16 e-mails e errou 4. Isso dá uma precisão de $80\%$. Parece bom, certo? 

Porém, em Machine Learning, **nem todo erro tem o mesmo peso**. 
* **Erro Tipo A:** O modelo acha que uma propaganda de farmácia é um e-mail de trabalho e deixa cair na sua caixa de entrada. (Chato, mas você só perde 2 segundos apagando).
* **Erro Tipo B:** O modelo acha que o e-mail do seu chefe com um documento urgente é Spam e joga na lixeira oculta. (Grave, pode causar um grande prejuízo).

É exatamente por isso que não usamos apenas a porcentagem de acertos. Nós usamos a **Matriz de Confusão**  para separar esses erros e entender exatamente *onde* o modelo está se confundindo.