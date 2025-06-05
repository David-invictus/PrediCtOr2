# PrediCtOr2
_Repositório do artigo sobre o PrediCtOr2_

Nesta seção, estão descritas as _Equações_, os _Algoritmos_ e _Gráficos_ do estudo.

A cima, encontram-se _Tabelamentos_ em formato _.csv_ com as predições produzidas para o estudo.

## Regressão Linear
Para se trabalhar com os dados no caso linear pelo MMQ, aplicou-se a _Equação 1_ depois de descobriu-se $a$ e $b$.

$y = ax+b$ (Equação 1)

No qual, $y$ é a variável dependente (valor observado), $x$ é a variável independente (valor de entrada), $a$ é a interceptação da linha de regressão e $b$ é a inclinação da linha de regressão.

Para estimar os coeficientes $a$ e $b$, usou-se as fórmulas derivadas do MMQ:

$a = \cfrac{n . (\sum x_i . y_i) - \sum x_i . \sum y_i}{
				n . \sum x^2_i - (\sum x_i)^2}$ (Equação 2)

$b = \cfrac{\sum x_i . (\sum x_i . y_i) - \sum y_i . \sum x^2_i}{
				(\sum x_i)^2 - n . \sum x^2_i}$ (Equação 3)

## Função Logarítmica
A equação para a transformação logarítmica é:

$y' = \log(y)$ (Equação 4)

No qual, $y'$ é o valor transformado da variável $y$.
A função logarítmica é frequentemente usada quando a variável dependente apresenta uma relação logarítmica com a variável independente. Assim, a equação para a função logarítmica é:

$y = a .\ln(x) + b$ (Equação 5)

No qual, $y$ é a variável dependente, $x$ é a variável independente, $a$ é o intercepto, $b$ é a inclinação, e $\log(x)$ representa o logaritmo natural de $x$.

## Função Exponencial
A função exponencial é utilizada quando a variável dependente mostra uma relação exponencial com a variável independente. A equação para a função exponencial é:

$y = b . \exp^{a . x}$ (Equação 6)

No qual, $y$ é a variável dependente, $x$ é a variável independente, $b$ é o intercepto, $a$ é a inclinação, e $\exp(x)$ representa a função exponencial de $x$.

Para estimar os coeficientes $a$ e $b$ na função exponencial, utilizamos os seguintes dados linearizados:

$\ln(y) = ax + \ln(b)$ (Equação 7)

## PrediCtOr2
A teoria de ML prevê o modelo básico de Regressão Linear _(_$wx+b$_, que retorna a Função_ $g(x) = ax+b$_)_. É sob essa base que o modelo _PrediCtOr2_ foi implementado.

Para isso, foram implementados 4 algorítimos sendo:

_Algoritmo 1_ que define um modelo de regressão linear com base no _Função 01_.

O _Algoritmo 2_ é a função de perda da Diferença de variância média ou Erro Quadrático Médio _(Mean Square Error – MSE)_, expressa:

$MSE = \cfrac{1}
        {n} .
        \sum^n_{i=1} . (y_i - \hat{y}_i)^2$ (Equação 8)

No qual, $y_i$ são os valores reais, $\hat{y}_i$ são os valores previstos, e $n$ é o número de observações. O MSE penaliza fortemente grandes erros, uma vez que os erros são elevados ao quadrado. Isso pode ser útil quando grandes desvios são indesejáveis.

O _Algoritmo 3_  é uma função de otimização com base no método de Gradiente descendente. No contexto de aprendizado de máquina, essa função geralmente é a função de custo ou perda, que mede a diferença entre os valores previstos pelo modelo e os valores reais observados [Bishop e Nasrabadi, 2006].

Por fim, _Algoritmo 4_ é uma função de iteração que retorna $a$ e $b$, após receber em cada iteração o _Algoritmo 3_, com base no número de épocas estipuladas.
Após esses preparativos, se inicializa os parâmetros a e b usando as _Equações 9 e 10_.

$a = \cfrac{y_i - \hat{y}} {x_i - \hat{x}}$ (Equação 9)

$b = \cfrac{(\hat{y} . x_i) - (y_i . \hat{x})} {x_i - \hat{x}}$ (Equação 10)

No qual, $y_i$ são os valores da Média mês (índices mensais de $CO_2$), $\hat{y}$ é o valor observado da Média mês, $xi$ são os valores dos Dados decimais (referência numérica para mês/ano da coleta), $\hat{y}$ é o valor observado dos Dados decimais. Em seguida, define-se o valor de $Lr$ (_Learning rate_). Com isso, pode-se iniciar as iterações de $a$ e $b$, que recebem o _Algoritmo 4_. Define-se a variável $prediction$ (predição) que utiliza o _Algoritmo 1_, a variável local $loss$ (perda) que recebe o _Algoritmo 2_. Rescreve-se os parâmetros $a$ e $b$, bem como a variável $loss$; e, finalmente, exibe-se os resultados ($x$, $y$ e $prediction$).

## O Coeficiente de Determinação $R^2$
De forma a mensurar, se os modelos aplicados estão aceitáveis ou não, precisa-se de uma ferramenta que dê tal segurança, é nesse contexto que entra o coeficiente de determinação, ou seja, ele vai mensurar a qualidade do ajuste.

[Almeida, 2019] e [Montgomery e Runger, 2010] informam que o coeficiente de determinação ($R^2$) é uma medida estatística que indica a proporção da variância na variável dependente que é explicada pela(s) variável(eis) independente(s) em um modelo de regressão linear. A equação para $R^2$ é:

O $R^2$ é usado para avaliar a qualidade do ajuste de um modelo e varia de 0 a 1, com valores mais altos indicando melhor ajuste.

$R^2 = \cfrac{SQreq}
            {SQtotal}$ (Equação 11)

No qual:

$SQreq = \sum[G(x_i) - \bar{y}]^2$ (Equação 12)

$SQtotal = \sum(y_i - \bar{y})^2$ (Equação 13)

$\bar{y} = \cfrac{1} {n} . \sum y$ (Equação 14)

Com isso, $(0<= R^2 <= 1)$, no qual $G(x_i)$ é o valor estimado no ponto (observado), $y_i$ é o valor tabelado, $\bar{y}$ é a média dos valores observados, e $n$ é o tamanho da amostra. Segundo [Montgomery e Runger, 2010] um valor de $R^2$ próximo de 1 indica que o modelo explica uma grande proporção da variância na variável dependente e, portanto, é considerado um bom ajuste. Por outro lado, um valor de $R^2$ próximo de 0 indica que o modelo não explica muita variância na variável dependente, sendo considerado um ajuste ruim.

## Raiz do Erro Quadrático Médio (_Root Mean Squared Error - RMSE_)

Além do $R^2$, optou-se por outra forma confiável de aferição de modelos preditivos para mensurar a qualidade dos modelos empregados no, o RMSE. Este, é a uma das métricas mais amplamente usadas para aferição de acurácia de modelos preditivos de ML. Tal métrica parte da premissa simples, fazer a média dos erros (no qual subtrai-se o valor real de $y$ do valor predito de $y$) elevado ao quadrado, e por fim, tira-se a raiz da soma.

Pode-se melhor entender tal métrica ao expressá-la (_Equação 15_):

$RMSE = \sqrt{ \cfrac{1}
        {n} .
        \sum^n_{i=1} . (y_i - \hat{y}_i)^2}$ (Equação 15)

Segundo [Kumar et al., 2020] “Enquanto a (_Mean Squared Error - MSE_) trabalha sobre viés e variância para previsões, o (_Root Mean Square Error - RMSE_) traz a unidade de volta à unidade original ao tomar a raiz quadrada do MSE. O RMSE é utilizado para medir a análise da discrepância entre os valores reais e estimados.”

Essa medida também tende a superestimar erros grandes, ao elevar os desvios ao quadrado para impedir que os desvios positivos e negativos se cancelem, o que pode ajudar a eliminar os métodos com esses erros.
Nessa métrica, quanto menor for seu resultado, melhor a qualidade do modelo.

## Gráficos
Gráfico de disperção do SKLearn - Todos os casos
![SBPO 2025 {Artigo  - Gráfico de dispersão (SKLearn)](https://github.com/user-attachments/assets/cfd685cb-bbf9-4542-a8d6-ff83e2d01215)

Gráfico de disperção do MMQ - Todos os casos
![SBPO 2025 {Artigo  - Gráfico de dispersão (MMQ)](https://github.com/user-attachments/assets/d9dc0d21-ee9c-4649-a0b6-9eb6bd810fb4)

Gráfico de disperção do PrediCtO2 - Todos os casos
![SBPO 2025 {Artigo  - Gráfico de dispersão (PrediCtOr2)](https://github.com/user-attachments/assets/4b018656-10d6-45ea-a5d2-32b755c633bc)

Gráfico de disperção do PrediCtO2 - Todos os casos [Recorte de 2024]
![SBPO 2025 {Artigo  - Gráfico de dispersão (PrediCtOr2) - Recorte 2024](https://github.com/user-attachments/assets/5e62c881-e141-429a-96d0-758c3c7ca1ce)
