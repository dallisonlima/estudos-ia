# Teoria: Redes Neurais (MLP) e Backpropagation

Até agora, lidamos com modelos "planos" (como o Perceptron simples e a Regressão Linear), onde as entradas ($X$) se conectavam diretamente à saída ($\hat{y}$). Esses modelos são ótimos, mas têm um limite matemático: só conseguem resolver problemas lineares (separar coisas com uma reta reta).

Para resolver problemas complexos do mundo real, adicionamos **Camadas Ocultas** no meio da rede. É aqui que nasce o **Deep Learning**. 

Entender essa arquitetura se divide em duas grandes fases: a "Ida" (Forward Pass) e a "Volta" (Backpropagation). 

## 1. O Dicionário de Variáveis (Topologia da Rede)

Neste exercício específico, nosso professor montou uma rede pequena, mas poderosa:
* **Entradas ($X_1, X_2$):** Os dados do aluno/problema.
* **$V_1, V_2$:** Os **Pesos da 1ª Camada**. Eles controlam a força da conexão entre as Entradas e o Neurônio Oculto.
* **$b_h$ (Bias Hidden):** O **Viés da Camada Oculta**. Permite que o neurônio oculto ajuste seu limiar de ativação.
* **$h$ (Hidden):** O **Neurônio Oculto**. Ele recebe as informações mastigadas, aplica uma função matemática e gera um sinal intermediário.
* **$\mu$ (Mi):** O **Peso da 2ª Camada**. Controla a força da conexão entre o Neurônio Oculto e a Saída final.
* **$b_o$ (Bias Output):** O **Viés da Camada de Saída**.

---

## 2. Fase 1: A Ida (Forward Pass)

Na "Ida", o sinal elétrico (os dados) viaja da esquerda para a direita, atravessando a rede até gerar uma previsão.

### A. O que acontece no Neurônio Oculto?
Primeiro, ele soma tudo o que chega nele (igualzinho fazíamos no Perceptron). Chamamos esse "bolo" de energia de $Z_h$:
$$Z_h = b_h + V_1 X_1 + V_2 X_2$$

Mas o neurônio oculto não repassa esse valor cru. Ele passa o $Z_h$ por um "filtro" chamado **Função de Ativação Sigmoide**. A função sigmoide esmaga qualquer número para que ele fique entre $0$ e $1$. Isso introduz a "não-linearidade" que deixa a rede inteligente. O resultado desse filtro é o nosso valor $h$:
$$h = \frac{1}{1 + e^{-Z_h}}$$

### B. O que acontece na Saída?
Agora, o neurônio de saída pega o sinal do neurônio oculto ($h$), multiplica pelo peso final ($\mu$) e soma seu próprio viés ($b_o$) para gerar a previsão final ($\hat{y}$):
$$\hat{y} = b_o + \mu \cdot h$$

---

## 3. O Erro
A rede deu seu palpite ($\hat{y}$). Agora nós a confrontamos com a realidade ($y$) para ver o tamanho do estrago:
$$E = y - \hat{y}$$

---

## 4. Fase 2: A Volta (Backpropagation)

Se a rede errou, ela precisa aprender. Mas como atualizar os pesos $V_1$ e $V_2$ que estão lá no começo da rede, escondidos, se o erro só foi descoberto no final? 

É aí que entra a **Retropropagação do Erro (Backpropagation)**. O erro viaja da direita para a esquerda, de trás para frente.

### A. Atualizando a Camada de Saída (É a mais fácil)
Como a camada de saída é a culpada direta pelo erro, atualizamos seus parâmetros usando a mesma lógica que já conhecemos da Regressão Linear. Onde a taxa de aprendizado é $\eta$:
$$b_{o,Novo} = b_{o,Atual} + \eta \cdot E$$
$$\mu_{Novo} = \mu_{Atual} + \eta \cdot E \cdot h$$
*(Note que usamos o $h$ em vez de $X$, porque a entrada do neurônio de saída foi o sinal $h$ enviado pelo neurônio oculto).*

### B. Atualizando a Camada Oculta (A grande sacada)
Nós não podemos usar o Erro Final ($E$) direto para atualizar o peso $V_1$. Precisamos calcular **a parcela de culpa** que o neurônio oculto teve nesse erro.

Chamamos essa "parcela de culpa" de Delta ($\delta_h$). A fórmula do Delta do neurônio oculto multiplica o erro ($E$), o peso da conexão ($\mu$) e a derivada da função sigmoide $h(1-h)$, que basicamente mede o quão sensível o neurônio estava naquele momento:
$$\delta_h = E \cdot \mu \cdot h(1 - h)$$

Com a "culpa" ($\delta_h$) em mãos, agora sim podemos atualizar os parâmetros iniciais, exatamente como fazíamos antes, mas substituindo o $E$ pelo $\delta_h$:
$$b_{h,Novo} = b_{h,Atual} + \eta \cdot \delta_h$$
$$V_{1,Novo} = V_{1,Atual} + \eta \cdot \delta_h \cdot X_1$$
$$V_{2,Novo} = V_{2,Atual} + \eta \cdot \delta_h \cdot X_2$$

> **💡 Resumo Mental:** > 1. Dados entram.
> 2. Rede calcula pra frente e prevê.
> 3. Medimos o erro.
> 4. Ajustamos a saída.
> 5. Calculamos a culpa do neurônio oculto ($\delta_h$).
> 6. Ajustamos a entrada.
> 7. Próximo ponto!