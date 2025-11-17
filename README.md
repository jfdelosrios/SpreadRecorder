# Spread Recorder Expert Advisor

## Descripción

Un Expert Advisor para MetaTrader 5 que registra automáticamente el spread del par de divisas en un archivo CSV. Útil para análisis histórico de spreads y evaluación de condiciones de mercado.

## Características

- ✅ Monitoreo en tiempo real del spread
- ✅ Registro automático en archivo CSV
- ✅ Timestamp de cada registro
- ✅ Gestión segura de archivos
- ✅ Manejo de errores y validación

## Funcionamiento

### Inicialización (OnInit)
- Inicializa la clase `CSymbolInfo` para el par de divisas actual
- Crea un archivo CSV con el nombre: `spread_[NombreDelPar].csv`
- Escribe los encabezados: "Time" y "Spread"

### Durante la operación (OnTick)
- Cada tick registra:
  - **Hora**: Timestamp actual en formato fecha y hora
  - **Spread**: Valor actual del spread del instrumento

### Cierre (OnDeinit)
- Cierra el archivo CSV correctamente cuando se detiene el EA

## Archivos generados

Los archivos CSV se crean en la carpeta común del terminal de MetaTrader 5:
```
spread_EURUSD.csv
spread_GBPUSD.csv
spread_[NombreDelPar].csv
...
```

## Formato del archivo CSV

```
Time;Spread
2025-11-16 14:30:45;2
2025-11-16 14:30:46;2
2025-11-16 14:30:47;3
```

## Requisitos

- MetaTrader 5
- Compilador MQL5
- Acceso a escritura en la carpeta del terminal

## Uso

1. Compilar el archivo `SpreadRecorder.mq5`
2. Arrastrar el EA a un gráfico del par de divisas deseado
3. El EA comenzará a registrar datos automáticamente
4. Los datos se guardarán en el archivo CSV correspondiente

## Autor

**Jorge Fernando De Los Ríos**
- Email: jfdelosrios@hotmail.com
- Copyright 2020

## Notas

- El archivo CSV es útil para:
  - Análisis histórico de spreads
  - Evaluación de calidad de ejecución
  - Estudios de condiciones de mercado
  - Auditoría de operaciones
  
- Los datos se van acumulando en el archivo mientras el EA está activo
- Si detiene el EA, puede reiniciarlo sin perder datos anteriores (se añaden nuevos registros)
