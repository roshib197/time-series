# Cargar los datos de la serie de tiempo
datos_serie_tiempo <- read.csv("datos_serie_tiempo.csv")

# Convertir los datos de la serie de tiempo en un objeto de serie de tiempo
serie_tiempo <- ts(datos_serie_tiempo$valor, start = c(2020, 1), frequency = 12)

# Visualizar la serie de tiempo
plot(serie_tiempo)

# Implementar el modelo ARIMA
library(forecast)

modelo_arima <- auto.arima(serie_tiempo)

# Realizar pronósticos utilizando el modelo ARIMA
pronosticos_arima <- forecast(modelo_arima, h = 12)

# Visualizar los pronósticos
plot(pronosticos_arima)

# Evaluar la precisión del modelo utilizando el error cuadrático medio (RMSE)
rmse_arima <- sqrt(mean((pronosticos_arima$mean - serie_tiempo)^2))
