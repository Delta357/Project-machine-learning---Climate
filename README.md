# Inteligência artificial no combate ao efeito estufa

[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)
[![author](https://img.shields.io/badge/author-RafaelGallo-red.svg)](https://github.com/RafaelGallo?tab=repositories) 
[![](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/release/python-374/) 
[![](https://img.shields.io/badge/R-3.6.0-red.svg)](https://www.r-project.org/)
[![](https://img.shields.io/badge/ggplot2-white.svg)](https://ggplot2.tidyverse.org/)
[![](https://img.shields.io/badge/dplyr-blue.svg)](https://dplyr.tidyverse.org/)
[![](https://img.shields.io/badge/readr-green.svg)](https://readr.tidyverse.org/)
[![](https://img.shields.io/badge/ggvis-black.svg)](https://ggvis.tidyverse.org/)
[![](https://img.shields.io/badge/Shiny-red.svg)](https://shiny.tidyverse.org/)
[![](https://img.shields.io/badge/plotly-green.svg)](https://plotly.com/)
[![](https://img.shields.io/badge/XGBoost-red.svg)](https://xgboost.readthedocs.io/en/stable/#)
[![](https://img.shields.io/badge/Caret-orange.svg)](https://caret.tidyverse.org/)
[![](https://img.shields.io/badge/Pandas-blue.svg)](https://pandas.pydata.org/) 
[![](https://img.shields.io/badge/Matplotlib-blue.svg)](https://matplotlib.org/)
[![](https://img.shields.io/badge/Seaborn-green.svg)](https://seaborn.pydata.org/)
[![](https://img.shields.io/badge/Matplotlib-orange.svg)](https://scikit-learn.org/stable/) 
[![](https://img.shields.io/badge/Scikit_Learn-green.svg)](https://scikit-learn.org/stable/)
[![](https://img.shields.io/badge/Numpy-white.svg)](https://numpy.org/)
[![](https://img.shields.io/badge/PowerBI-red.svg)](https://powerbi.microsoft.com/pt-br/)

Projetos de machine learning aplicado temperatura clima e modelos machine learning, series temporais.
Nesse projeto modelo preve a temperatura como previsão do clima. Os dados foi coletadas de estações metrológicas salvado em csv.
Os modelos vai ser utilizado modelo de classificação, modelos estatisticos como series temporais em Python, R.
Criação de dashboards visualização das temperaturas e o clima.
Esse projeto pode ajudar a criar soluções para o clima do nosso planeta combate o efeito estufa.


![Logo](https://image.freepik.com/vetores-gratis/vetor-de-plano-de-fundo-de-mudanca-climatica-com-borda-de-nuvens-de-chuva_53876-112078.jpg)


## Autores

- [@RafaelGallo](https://github.com/RafaelGallo)


## Instalação 

Instalação das bibliotecas para esse projeto no python.

```bash
  conda install pandas 
  conda install scikitlearn
  conda install numpy
  conda install scipy
  conda install matplotlib

  python==3.6.4
  numpy==1.13.3
  scipy==1.0.0
  matplotlib==2.1.2
```
Instalação do Python É altamente recomendável usar o anaconda para instalar o python. Clique aqui para ir para a página de download do Anaconda https://www.anaconda.com/download. Certifique-se de baixar a versão Python 3.6. Se você estiver em uma máquina Windows: Abra o executável após a conclusão do download e siga as instruções. 

Assim que a instalação for concluída, abra o prompt do Anaconda no menu iniciar. Isso abrirá um terminal com o python ativado. Se você estiver em uma máquina Linux: Abra um terminal e navegue até o diretório onde o Anaconda foi baixado. 
Altere a permissão para o arquivo baixado para que ele possa ser executado. Portanto, se o nome do arquivo baixado for Anaconda3-5.1.0-Linux-x86_64.sh, use o seguinte comando: chmod a x Anaconda3-5.1.0-Linux-x86_64.sh.

Agora execute o script de instalação usando.


Depois de instalar o python, crie um novo ambiente python com todos os requisitos usando o seguinte comando

```bash
conda env create -f environment.yml
```
Após a configuração do novo ambiente, ative-o usando (windows)
```bash
activate "Nome do projeto"
```
ou se você estiver em uma máquina Linux
```bash
source "Nome do projeto" 
```
Agora que temos nosso ambiente Python todo configurado, podemos começar a trabalhar nas atribuições. Para fazer isso, navegue até o diretório onde as atribuições foram instaladas e inicie o notebook jupyter a partir do terminal usando o comando
```bash
jupyter notebook
```

# Ferramentas vai ser utilizado nesse projeto.
 
- Python
- R
- Análise de dados
- Machine learning
- Dashboard
- Series temporais

## Demo modelo Série temporal R

```bash
 # Série temporal Co2

# Carregando a bibliotecas
library(quantmod)
library(xts)
library(moments)
library(readxl) 
library(foreign)
library(dynlm) 
library(car) 
library(lmtest) 
library(sandwich)
library(fpp2) 
library(tseries) 
library(zoo)
library(xts)
library(forecast) 
library(ggplot2)

# Base de dados online
data <- read.csv("data.csv")
str(data)

# Dataset
data <-data <- apply.yearly(data, mean)
data

# Temperatura Global puxando dados de 1800 até 2021
temp <- data["1800/2017", 'Monthly.Anomaly.data']
temp

# Temperatura global puxando dados de 2001 até 2021
temp_test <- data["2001/2016", 'Monthly.Anomaly.data']
temp_test

#### Série temporal - modelo

library(tseries)

# Stationarity
data <- kpss.test(temp.data)
train_temp <- temp.data.diff1 <- diff(temp.data)
train_temp

# Stationarity - test
data_test <- kpss.test(temp.data.diff1)
data_test

# Transformando em séries temporal
lab_data <- BoxCox.lambda(temp.data)
temp_train <- BoxCox(temp.data,lambda)
temp_train

# Gráfico dos anos
library(dygraphs)

dygraph(temp.data, main = " Co2") %>%
  dyAxis("x", drawGrid = TRUE) %>% dyEvent("2000-1-01", "2022", labelLoc = "bottom") %>% 
  dyEvent("2000-1-01", "1800", labelLoc = "bottom") %>% 
  dyEvent("2000-5-01", "2000", labelLoc = "bottom") %>% 
  dyEvent("2017-12-11","2017", labelLoc = "bottom") %>%
  dyOptions(drawPoints = TRUE, pointSize = 2)


## PACF
p2 <- autoplot(Acf(temp.data.diff1, 
                   plot = F, 
                   lag.max = 15, 
                   type = 'partial')) + ggtitle('PACF')
p2


######### Modelo ARIMA ######### 

# Modelo ARIMA 1
model_arima_fit_1 <-Arima(temp.data, order = c(3, 1, 0))
model_arima_fit_1
summary(model_arima_fit_1)

checkresiduals(model_arima_fit_1)

# Modelo ARIMA 2
model_arima_fit_2 <- Arima(temp.data, order = c(3,1,1))
model_arima_fit_2      
summary(model_arima_fit_2)      

checkresiduals(model_arima_fit_2)

# Modelo ARIMA 3
model_arima_fit_3 <- Arima(temp.data, order = c(3,1,2))
model_arima_fit_3      
summary(model_arima_fit_3)         

checkresiduals(model_arima_fit_3)

# Modelo ARIMA 4
model_arima_fit_4 <- Arima(temp.data, order = c(2,1,2))
model_arima_fit_4      
summary(model_arima_fit_4)

checkresiduals(model_arima_fit_4)

# Modelo auto arima
model_arima_fit <- auto.arima(temp.data, seasonal = F)
model_arima_fit
summary(model_arima_fit)

checkresiduals(model_arima_fit)

# Residuos
g1 <- Acf(residuals(model_arima_fit))
g1

g1_test <- Box.test(residuals(model_arima_fit),
                    lag = 10,
                    fitdf = 6,
                    type = "L")
g1_test

# Previsão temperatura
model_predict <- predict(arima(temp.data, order = c(4,4,5)), n.ahead = 50)
model_predict

# Gráfico 1 - Previsão Co2
autoplot(forecast(model_arima_fit, h=50, title = "Revisão Co2",
                  xlab = "Total",
                  ylab = "Co2"))

# Gráfico 2 - Previsão Co2
plot(forecast(Arima(y = temp.data, order = c(1, 1, 2))))
plot(forecast(Arima(y = temp.data, order = c(3, 3, 4))))


# Gráfico 3 - Previsão das têmperaturas
pred.forecast <- forecast(model_arima_fit, h = 10)
plot(pred.forecast)
lines(ts(coredata(temp.global.test),
         start = start(temp.forecast$mean)[1],
         frequency = 1), col = 'magenta', main = "Co2")
```
## Projeto ML Climate 

| Nome             | Projeto                                                          |
| ----------------- | ------------------------------------------------------------------ |
| Data Analytics - Co2|[CO2 Emission](https://github.com/RafaelGallo/Project-machine-learning---Climate/blob/main/Notebook/CO2%20Emissions/Data%20Analytics%20-%20Co2.ipynb) |
| Série Temporal R - Effect Greenhouse|[Effect Greenhouse](https://github.com/RafaelGallo/Project-machine-learning---Climate/blob/main/R/S%C3%A9rie%20temporal%20Co2.r)|
| Série Temporal Python auto arima - Climate| [Climate](https://github.com/RafaelGallo/Project-machine-learning---Climate/blob/main/Notebook/Daily%20Climate/Climate%20-%20time%20series.ipynb)|
| Modelo regressão linear - NOAA Climate | [NOAA Climate](https://github.com/RafaelGallo/Project-machine-learning---Climate/blob/main/Notebook/NOOA/NOAA%20Climate.ipynb)|
| Série Temporal Python auto arima - Temperature change | [Temperature - model](https://github.com/RafaelGallo/Project-machine-learning---Climate/blob/main/Notebook/Temperature%20change/Models/Model%20-%20Temperature%20change.ipynb)|
| Carbon Emissions| https://www.kaggle.com/txtrouble/carbon-emissions |
| NOAA Global Historical Climatology Network | https://www.kaggle.com/noaa/global-historical-climatology-network|
| NOAA Severe Weather Data Inventory | https://www.kaggle.com/noaa/severe-weather-data-inventory|



## Screenshots

![App Screenshot](https://image.freepik.com/vetores-gratis/pessoas-com-conceito-de-sustentabilidade-ambiental_53876-66157.jpg)


## Documentation

[Documentation](https://linktodocumentation)


## 🚀 Sobre mim

Cientista de dados


## License

[MIT](https://choosealicense.com/licenses/mit/)


## Roadmap

- Additional browser support

- Add more integrations


## Contributing

Contributions are always welcome!

See `contributing.md` for ways to get started.

Please adhere to this project's  `code of conduct`.

