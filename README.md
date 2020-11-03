# PREVISAO-DE-INADIMPLENCIA-DE-CARTAO-DE-CREDITO-UMA-COMPARAÇAO-DE-ACURACIA
O objetivo deste trabalho é comparar o desempenho da acurácia entre a Regressão logística e o algoritmo XGBoost por meio de matrizes de confusão, analisando a especificidade e sensibilidade quanto a previsão de inadimplência de clientes que utilizam cartão de crédito de um determinado banco não especificado. 
Disponível em: https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients



# pacote para leitura de dados em Excel
library(readxl)

# Transformando as va em numeros
default_of_credit_card_clients <- read_excel("seu repositorio com a base de dados", 
                                             col_types = c("numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric", "numeric", "numeric", 
                                                           "numeric"))

============

# NESTA ETAPA ACONTECERÁ AS TRANSFORMAÇÕES DAS VARIÁVEIS

# retirando a coluna dos dados sobre ID 
loan.new = default_of_credit_card_clients[,-1]

# linha sem valores
loan.new = as.data.frame(loan.new[-1,])

# Verificando se tem N/A
sapply(loan.new, function(x) sum(is.na(x)))

# Gender. Se 1 = homem, 2 = mulher. Transformando para mulheres
loan.new$X2 = ifelse(loan.new$X2 == 2,1,0)

# Education. Se 1 = pós-graduação, 2 = superior, 3 = ensino médio, 4 = outros. Analisando para superior
loan.new$X3 = ifelse(loan.new$X3 == 2,1,0)


# Marital status. Se 1 = casado, 2 = solteiro, 3 = outros. Analisando para solteiro
loan.new$X4 = ifelse(loan.new$X4 == 2,1,0)

# X5 idade. Não precisa de alteração

# X6 - X11
São históricos de pagamentos de Abril até Setembro.Os valores são referente a quando foi pago a divida e o tempo,em meses, de atraso dela, mas não afirmaque são as dívidas com cc, são apenas contas em atraso: histórico de "bom pagador". Se -1 =pagamento adiantado, se 0 >, pagamento atrasado. A variável não sofrerá alteração.


# X12-X17
Estatus da quantidade de contas. Não sofrerá alteração

# X18-X23 
Valor do pagamento anterior (dólar NT). X18 = valor pago em setembro de 2005; X19 = valor pago em agosto de 2005; . . .; X23 = valor pago em abril de 2005. Não sofrerá alteração




# Dividindo a base em teste e treino
idx = sample(dim(loan.new)[1] , 0.75*dim(loan.new)[1] , replace = F)
trainset = loan.new[idx , ]
testset = loan.new[-idx , ]

