# PrediCtOr2
_Repositório do artigo sobre o PrediCtOr2_

Nesta seção, estão descritas a _Motivação_, as _Equações_, os _Algoritmos_ e _Gráficos_ do estudo.

A cima, encontram-se _Tabelamentos_ em formato _.csv_ com as predições produzidas para o estudo.

## Motivação
O oxigênio é um dos bens mais preciosos para os seres vivos. Do primeiro respirar até o último, toda uma existência se firma. No entanto, nosso ar e atmosfera não são compostos unicamente por oxigênio respirável (O2). Diversos outros elementos os compõem, alguns destes atuam como uma barreira protetora para os seres vivos. Uma destas barreiras é a Camada de Ozônio (composta de ozônio, O3), localizada entre 25 a 30 km acima da superfície terrestre, na estratosfera. Essa camada nos protege dos raios solares, como um filtro para os raios ultravioletas (raios UV). Um dos fatores que contribuem para o enfraquecimento da Camada de Ozônio é a presença excessiva de gases danosos, os chamados Gases do Efeito Estufa (GEE), como Óxido Nítrico (NO), Óxido Nitroso (N2O), Metano (CH4) e o Dióxido de Carbono (CO2).

O CO2 é uma estrutura química formafa pela ligação de um átomo de Carbono com dois de Oxigênio forma [Souza, 2023]. Foi descoberto pelo escocês Joseph Black em 1975 [Souza, 2023]. É possível observá-lo na atmosfera sendo gerado naturalmente ou por intervenção do homem. Na natureza, esse gás é importante, dentre outras funções, para plantas e oceanos.

Segundo [Rasera, 2005], “os processo envolvidos na retirada de CO2 da atmosfera são fotossíntese e a dissolução de CO2 nos oceanos, e os principais processos envolvidos no retorno do CO2 para atmosfera são a oxidação da matéria orgânica pela respiração ou queima e a liberação de CO2 dos oceanos, nas áreas onde a concentração deste gás é superior em relação à atmosfera.”

Em contrapartida, como explicado por [Rasera, 2005], esses gases são gerados pela decomposição de matéria orgânica, nas erupções vulcânicas [NASA, 2022] e pela liberação das plantas e oceanos. Vale ressaltar, que tal processo é natural, e serve para equilibrar a vida na terra, gerando, assim, o efeito estufa abaixo da Camada de Ozônio.

Diametralmente oposto ao propósito natural da liberação desse gás, a ação antrópica tem sua parcela de contribuição.
Ao observar os dados [NOOA, 2022], vê-se que a cada ano aumenta-se a quantidade de CO2 emitida na atmosfera.

O gráfico adiante mostra os níveis de CO2 durante os três últimos ciclos glaciais da Terra, que foram obtidos por meio da captura por bolhas de ar presas em camadas de gelo e geleiras.
![CO2 - Níveis histórico da elevação (Nasa)](https://github.com/user-attachments/assets/aa432373-b071-4413-9597-615cf0437596)

O segundo gráfico mostra os níveis atmosféricos de CO2 nos últimos anos, com as mudanças naturais e sazonais removidas (NASA, 2022).
<img width="629" height="300" alt="CO2 - 2005-Present (Nasa)" src="https://github.com/user-attachments/assets/d46da7bc-4d05-43ad-94f7-2073a4edc4ab" />

Os gráficos apresentados revelam, visualmente, a evolução da concentração de CO2 na atmosfera.

Sendo assim, o objetivo deste trabalho é elaborar e treinar um modelo de ML (PrediCtOr2), utilizando como entrada dados compilados pela agência norte-americana NASA (National Aeronautics and Space Administration - "Administração Nacional da Aeronáutica e Espaço, em tradução direta") e monitorados pela NOAA (National Oceanic and Atmospheric Administration - "Administração Nacional Oceânica e Atmosférica", em tradução direta), referente ao período de 1958 até maio de 2024 [NOAA, 2022]. Utilizando o método de classificação por Regressão, foram considerados tanto o ajuste linear quanto os modelos não lineares logarítmico e exponencial, com intuito de predizer os próximos índices de emissão de CO2 na atmosfera terrestre, assumindo a manutenção da tendência de comportamento observadas nas séries temporais.

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

## Referências

Almeida, C. G. d. (2019). Cálculo Numérico. UFU. URL https://repositorio.ufu.br/bitstream/123456789/25218/1/Calculo%20Numerico.pdf.

Amarpuri, L., Yadav, N., Kumar, G., e Agrawal, S. (2019). Prediction of co2 emissions using deep learning hybrid approach: A case study in indian context. In 2019 Twelfth International Conference on Contemporary Computing (IC3), p. 1–6.

Bishop, C. M. e Nasrabadi, N. M. (2006). Pattern recognition and machine learning, volume 4. Springer, 1 edition.

Box, G. E., Jenkins, G. M., Reinsel, G. C., e Ljung, G. M. (2015). Time series analysis: forecasting and control. John Wiley & Sons, 5 edition. ISBN 978-1-118-67502-1.

Ferreira, D. F. P. (2025). Predictor2. GitHub repository. URL https://github.com/David-invictus/PrediCtOr2.git. Repositório de software no GitHub.

Houghton, R. A. e Woodwell, G. M. (1989). Global climatic change. Scientific American, 260(4):36–47. ISSN 00368733, 19467087. URL http://www.jstor.org/stable/24987210.

Kumar, R., Kumar, P., e Kumar, Y. (2020). Time series data prediction using iot and machine learning technique. Procedia Computer Science, 167:373–381. ISSN 1877-0509. URL https://www.sciencedirect.com/science/article/pii/S1877050920307067. International Conference on Computational Intelligence and Data Science.

Kumari, S. e Singh, S. K. (2023). Machine learning-based time series models for effective co2 emission prediction in india. Environmental Science and Pollution Research, 30(55):116601–
116616. URL https://doi.org/10.1007/s11356-022-21723-8.

Li, L., Lei, Y., He, C., Wu, S., e Chen, J. (2017). Prediction on the peak of the c [o. sub. 2] emissions in china using the stirpat model. Advances in Meteorology, 2017. URL https:
//doi.org/10.1155/2016/5213623.

Masson-Delmotte, V., Zhai, P., Pörtner, H.-O., Roberts, D., Skea, J., Shukla, P. R., Pirani, A., Moufouma-Okia, W., Péan, C., Pidcock, R., Connors, S., Matthews, J. B. R., Chen, Y., Zhou,
X., Gomis, M. I., Lonnoy, E., Maycock, T., Tignor, M., e Waterfield, T. (2019). Aquecimento global de 1,5°c: Sumário para formuladores de políticas. Relatório Especial do IPCC sobre o
Aquecimento Global de 1,5°C, Versão em Português. URL https://www.ipcc.ch/site/assets/uploads/2019/07/SPM-Portuguese-version.pdf. Tradução não oficial para o português. Relatório original publicado em 2018.

Montgomery, D. C. e Runger, G. C. (2010). Applied statistics and probability for engineers. John wiley & sons, 5 edition. ISBN 13: 978-0-470-05304-1.

Nações Unidas (2022). O que são as mudanças climáticas? URL https://brasil.un.org/pt-br/175180-o-que-sao-mudancas-climaticas.

NOAA (2022). Co2 measurements. Noaa.gov. URL https://gml.noaa.gov/webdata/ccgg/trends/co2/co2_mm_mlo.txt.

Pinto, E. d. P. P., Moutinho, P., Stella, O., Castro, I., Mazer, S., Rettmann, R., e Moreira, P. F. (2010). Perguntas e respostas sobre aquecimento global. Technical report, Instituto de Pesquisa Ambiental da Amazônia, Belém/PA. URL https://cmsdespoluir.cnt.org.br/Documents/PDFs/Perguntas%20e%20respostas%20sobre%20AQUECIMENTO%20GLOBAL.pdf.

Silva, H. A. P. D. (2022). Simulação da elevação do nível médio do mar utilizando métodos numéricos e ferramentas de geoprocessamento: estudo de caso. Master’s thesis, Universidade Federal Rural do Semi-Árido (UFERSA), Mossoró/RN. URL https://repositorio.ufersa. edu.br/handle/prefix/9072.

Taheri, S. e Razban, A. (2021). Learning-based co2 concentration prediction: Application to indoor air quality control using demand-controlled ventilation. Building and Environment, 205:108164. ISSN 0360-1323. URL https://www.sciencedirect.com/science/article/pii/S0360132321005655.

Souza, Líria Alves de (2023). Dióxido de Carbono; Brasil Escola. Disponível em: https://brasilescola.uol.com.br/quimica/dioxido-de-carbono.htm. Acesso em 18 fev. 2023.

Rasera, Maria de Fátima Fernades Lamy (2005). O papel das emissões de CO2 para a atmosfera, em rios da bacia do Ji- Paraná (RO), no ciclo regional do carbono. Orientador: Prof. Dr. Alex Vladimir Krusche. 69 p. Dissertação (Mestra) - Centro de Energia Nuclear na Agricultura, Universidade de São Paulo, Piracicaba-SP, Brasil, 2005. Disponível em: https://www.teses.usp.br/teses/disponiveis/64/64135/tde-31072006-083532/publico/Rasera_MFFL.pdf. Acesso em: 15 out. 2022.

NASA (2022). HOLLY SHAFTEL. (ed.). Vital Signs: carbon dioxide. Carbon Dioxide. Editora de Ciências: Susan Callery. Disponível em: https://climate.nasa.gov/vital-signs/carbon-dioxide/. Acesso em: 21 set. 2022.
