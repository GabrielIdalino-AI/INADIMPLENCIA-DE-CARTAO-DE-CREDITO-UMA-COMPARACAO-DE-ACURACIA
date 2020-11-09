# PREVISÃO DE INADINPLÊNCIA: UMA COMPARAÇÃO ENTRE REGRESSÃO LOGÍSTICA E O ALGORITMO XGBOOST
O objetivo deste trabalho é comparar o desempenho da acurácia entre a Regressão logística e o algoritmo XGBoost por meio de métricas de validação para modelos de classificação aplicados a previsão de inadimplência. Como os dados têm origem de uma pesquisa científica previamente realizada, não houve a necessidade de uma maior manipulação, pois não há presença significativa de outliers, e nenhum missing value em qualquer uma das variáveis. As informações são de clientes que utilizam cartão de crédito de um determinado banco não especificado.
O dicionário e a base de dados estão disponíveis em: https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients


## Descrição das Variáveis
- X1: Valor do crédito concedido (dólar NT): inclui tanto o crédito ao consumidor pessoa física quanto o crédito familiar (suplementar).
- X2: Gênero (1 = masculino; 2 = feminino).
- X3: Educação (1 = pós-graduação; 2 = universidade; 3 = ensino médio; 4 = outros).
- X4: Estado civil (1 = casado; 2 = solteiro; 3 = outros).
- X5: Idade (ano).
- X6 - X11: Histórico de pagamentos anteriores. Rastreamos os registros de pagamentos mensais anteriores (de abril a setembro de 2005) da seguinte maneira: X6 = o status de reembolso em setembro de 2005; X7 = situação de amortização em agosto de 2005; . . .; X11 = estado de reembolso em abril de 2005. A escala de medição para o estado de reembolso é: -1 = pagamento em dia; 1 = atraso no pagamento por um mês; 2 = atraso no pagamento por dois meses; . . .; 8 = atraso no pagamento por oito meses; 9 = atraso no pagamento de nove meses ou mais.
- X12-X17: Valor da fatura (dólar NT). X12 = valor da fatura em setembro de 2005; X13 = valor da fatura em agosto de 2005; . . .; X17 = valor da fatura em abril de 2005.
- X18-X23: Valor do pagamento anterior (dólar NT). X18 = valor pago em setembro de 2005; X19 = valor pago em agosto de 2005; . . .; X23 = valor pago em abril de 2005.
- Y: inadimplência como variável de resposta 1 = inadimplente 0 = adimplente 




## Quais métricas serão analisadas?
- Acurácia
- Valor preditivo negativo (VPN) 
- Valor preditivo positivo (VPP)
- Sensibilidade
- Especificidade
- Curva ROC e área (AUC)

### Etapas do processo
1. Transformação das variáveis
2. Dividir em dados de treino e teste
3. Aplicação dos modelos 
4. Matriz de Confusão
5. Curva ROC

#### Transformação das variáveis
As características dos individuos escolhidos para esta análise foram selecionadas por ocuparem em maiores proporções relativamente a quantidade total na base de dados, contudo, caso haja interesse, as propriedades podem ser alteradas. A análise correspondente aos resultados aqui compartilhados se resumem a individuos com determinados aspectos:

- Gênero: Feminino
- Escolaridade: superior
- Estado civil: solteiro(a)

#### Divisão, dados de treino e teste
Os dados foram divididos nas seguintes proporções:
- Dados de Treino: 75%
- Dados de Teste: 25%

#### Aplicação dos modelos
Os modelos tiveram como resultados das probabilidades as seguintes distribuições
> Regressão logistica

| Dados Teste | Dados Treino |
| ------------ | ------------- |
| <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/Distribui%C3%A7%C3%A3o.RLG.teste.png" width="250"> | <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/Distribui%C3%A7%C3%A3o.RLG.treino.png" width="250">|

> XGBoost

| Dados Teste | Dados Treino |
| ------------ | ------------- |
| <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/Distribui%C3%A7%C3%A3o.P.XGB.teste.png" width="250"> | <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/Distribui%C3%A7%C3%A3o.P.XGB.treino.png" width="250">|


 #### Análise da matriz de confusão
- Regressão logística
> O ponto de corte que retornou o maior valor da acurácia se encontra em 0.4

| Métricas  |      Dados Treino      |  Dados Teste |
|----------|:-------------:|------:|
| Acurácia|  0.8174 | 0.8159 |
| VPN |    0.6463   |   0.6472 |
| VPP | 0.8428 |    0.8417 |
| Especificidade | 0.3739 |    0.3847 |
| Sensibilidade | 0.9412 |    0.9398 |



- XGBoost
> O ponto de corte que retornou o maior valor da acurácia se encontra em 0.5

| Métricas  |      Dados Treino      |  Dados Teste |
|----------|:-------------:|------:|
| Acurácia|  0.8033 | 0.8128 |
| VPN |    0.7036   |   0.7239 |
| VPP | 0.8098 |    0.8198 |
| Especificidade | 0.1947 |    0.2401 |
| Sensibilidade | 0.9766 |    0.9742 |




#### Curva ROC
Analisando o desempenho dos modelos para a área abaixo da curva (AUC):
> Regressão logística


| AUC  |      Dados Treino      |  Dados Teste |
|----------|:-------------:|------:|
| Área |  0.7279 | 0.7214 |


| Dados treino | Dados Teste |
| ------------ | ------------- |
| <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/GLM.%20ROC%20Curve.%20trainset.png" width="250"> | <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/GLM%20ROC%20Curve.%20Testset.png" width="250">|


> XGBoost

| AUC  |      Dados Treino      |  Dados Teste |
|----------|:-------------:|------:|
| Área |  0.7732 | 0.7823 |


| Dados treino | Dados Teste |
| ------------ | ------------- |
| <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/XGBoost%20ROC%20Curve.%20trainset.png" width="250"> | <img src="https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/XGBoost%20ROC%20Curve.%20Testset.png" width="250">|

# Conclusão
Como o objetivo é analisar os individuos inadimplentes, as métricas de validação relevantes dizem aqueles voltados para a validação dos valores classificados como positivo que realmente são positivos, tais métricas são: VPP , Sensibilidade, e a área abaixo da curva ROC (AUC). Portanto, dentre os três critérios avaliados, o algoritmo XGBoost apresentou melhor performance em dois: AUC e Sensibilidade. Em contrapartida, a Regressão logística teve melhores resultados em apenas um: VPP. Esses métodos são importantes na escolha do modelo pois a acurácia, por mais que apresente valores mais altos para uma das ferramentas, não é a melhor forma de dizer que um modelo esta classificando corretamente suas previsões, assim as métricas de validação auxiliam na escolha do modelo.

## Os códgios das etapas estão presentes aqui:
1. Pacotes necessários: https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/1%20-%20Pacotes%20necess%C3%A1rios
2. Preparação dos dados: https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/2%20-%20Transformando%20os%20dados
3. Aplicando a Regressão Logística:https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/3%20-%20Aplicando%20a%20Regress%C3%A3o%20log%C3%ADstica
4. Aplicando o XGBoost: https://github.com/GabrielIdalino-AI/INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARACAO-DE-ACURACIA/blob/main/4%20-%20Aplicando%20o%20XGBoost



