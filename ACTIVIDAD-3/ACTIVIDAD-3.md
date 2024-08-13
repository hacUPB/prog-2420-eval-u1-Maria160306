# ACTIVIDAD-3
## 1. Problema 3: Simular el crecimiento de una población de bacterias en un cultivo en base a una tasa de crecimiento diaria.
### Análisis del problema:
1. Obtener número inicial de bacterias y la tasa de crecimiento diaria.
2. Determinar el número de bacterias al final de cada día, durante un período específico.
3. Calcular la población final después de un determinado número de días.
#### Variables:
- tasa_crecimiento: Tasa de crecimiento diaria (porcentaje).
- número_días:Número de días que durará el experimento.
- bacterias_iniciales: Número inicial de bacterias.
- bacterias_totales: Numero total de bacterias al final del experimento.
#### Pasos a seguir:
1. Asignar bacterias_iniciales a bacterias_totales para comenzar el cálculo.
2. Iterar desde el día 1 hasta número_días.
3. En cada iteración, calcular el crecimiento de las bacterias usando: incremento = bacterias_totales * tasa_crecimiento / 100.
4. Sumar el incremento a bacteria_totales.
5. Imprimir el resultado.
#### Pseudocódigo:
/// Inicio
    // Definir e inicializar variables
    Leer bacterias_iniciales
    Leer tasa_crecimiento
    Leer numero_dias
    bacterias_totales = bacterias_iniciales

    // Simulación del crecimiento diario
    Para dia = 1 hasta numero_dias Hacer
        incremento = bacterias_totales * tasa_crecimiento / 100
        bacterias_totales = bacterias_totales + incremento
    FinPara

    // Imprimir el resultado
    Imprimir "Número total de bacterias después de", numero_dias, "días: ", bacterias_totales
Fin ///
## 2. Problema 5: Calcular el total de puntos obtenidos en un juego de bolos basado en las puntuaciones de cada tiro.
### Análisis del problema:
1. Obtener una lista de las puntuaciones de cada tiro.
2. Sumar los puntos obtenidos en cada tiro, considerando las reglas especiales de los bolos:
- Strike: Cuando todos los pinos son derribados con el primer tiro, se suman los puntos de los siguientes dos tiros.
- Spare: Cuando todos los pinos son derribados en dos tiros dentro de un cuadro, se suman los puntos del siguiente tiro.
- Normal: Se suman los puntos de los tiros realizados.
#### Variables: 
- puntuaciones: Lista con las puntuaciones de cada tiro.
- total_puntos: total de puntos obtenidos.
- cuadro_actual: Número de cuadro actual.
- tiro: Representa el tiro actual dentro de la lista de puntuaciones.
#### Constantes: 
- máximo_cuadros: 10 cuadros en un juego.
#### Pasos a seguir:
1. Asignar total_puntos a 0 para comenzar a acumular el puntaje.
2. Inicializar cuadro_actual a 1 y tiro a 0 para comenzar el cálculo desde el primer cuadro y primer tiro. 
3. Hacer una iteración desde el cuadro_actual = 1 hasta cuadro_actual = 10.
4. Verificar si es un strike.
5. Verificar si es un spare.
6. Calcular puntuación normal.
7. Imprimir resultado.
#### Pseudocódigo:
/// Inicio
    // Definir e inicializar variables
    Leer puntuaciones
    total_puntos = 0
    cuadro_actual = 1
    tiro = 0

    // Iterar sobre los cuadros
    Mientras cuadro_actual <= 10 Hacer
        Si puntuaciones[tiro] == 10 Entonces // Strike
            total_puntos = total_puntos + 10 + puntuaciones[tiro + 1] + puntuaciones[tiro + 2]
            tiro = tiro + 1
            cuadro_actual = cuadro_actual + 1
        Sino Si puntuaciones[tiro] + puntuaciones[tiro + 1] == 10 Entonces // Spare
            total_puntos = total_puntos + 10 + puntuaciones[tiro + 2]
            tiro = tiro + 2
            cuadro_actual = cuadro_actual + 1
        Sino // Puntuación normal
            total_puntos = total_puntos + puntuaciones[tiro] + puntuaciones[tiro + 1]
            tiro = tiro + 2
            cuadro_actual = cuadro_actual + 1
        FinSi
    FinMientras

    // Imprimir el resultado
    Imprimir "Total de puntos: ", total_puntos
Fin ///
## 3. Problema 6: Calcular la edad de una persona a partir de su fecha de nacimiento y la fecha actual.
### Análisis del problema:
1. Obtener fecha de nacimiento (Día, mes y año).
2. Obtener fecha actual (Día, es y año).
3. Calcular los años, meses y días transcurridos desde la fecha de nacimiento hasta la fecha actual.
4. Determinar si la persona ya ha cumplido años este año.
5. Determinar si hoy es su cumpleaños.
#### Variables: 
- dia_nacimiento, mes_nacimiento, año_nacimiento.
- dia_actual, mes_actual, año_actual.
- edad_años.
- edad_meses: Meses transcurridos desde el último cumpleaños.
- edad_dias: Días transcurridos desde el último mes cumplido.
- ha_cumplido_este_año.
- es_cumpleaños_hoy.
#### Pasos a seguir:
1. Asignar edad_años, edad_meses y edad_dias a 0-
2. Inicializar ha_cumplido_este_año y es_cumpleaños_hoy como falso.
3. Calcular la edad en años.
4. Calcular los meses.
5. Calcular los días. 
6. Verificar si hoy es su cumpleaños.
7. Imprimir resultados.
#### Pseudocódigo:
/// Inicio
    // Entrada de datos
    Leer dia_nacimiento, mes_nacimiento, año_nacimiento
    Leer dia_actual, mes_actual, año_actual

    // Inicialización
    edad_años = 0
    edad_meses = 0
    edad_días = 0
    ha_cumplido_este_año = Falso
    es_cumpleaños_hoy = Falso

    // Calcular edad en años
    Si (mes_actual > mes_nacimiento) O (mes_actual = mes_nacimiento Y dia_actual >= dia_nacimiento) Entonces
        edad_años = año_actual - año_nacimiento
        ha_cumplido_este_año = Verdadero
    Sino
        edad_años = año_actual - año_nacimiento - 1
        ha_cumplido_este_año = Falso
    FinSi

    // Calcular los meses
    Si (mes_actual >= mes_nacimiento) Entonces
        edad_meses = mes_actual - mes_nacimiento
    Sino
        edad_meses = 12 - (mes_nacimiento - mes_actual)
    FinSi

    // Calcular los días
    Si (dia_actual >= dia_nacimiento) Entonces
        edad_días = dia_actual - dia_nacimiento
    Sino
        días_del_mes_anterior = CalcularDiasMesAnterior(mes_actual, año_actual)
        edad_días = (días_del_mes_anterior - dia_nacimiento) + dia_actual
    FinSi

    // Verificar si hoy es el cumpleaños
    Si (dia_actual = dia_nacimiento) Y (mes_actual = mes_nacimiento) Entonces
        es_cumpleaños_hoy = Verdadero
    FinSi

    // Imprimir los resultados
    Imprimir "Edad: ", edad_años, " años, ", edad_meses, " meses, ", edad_días, " días"
    Imprimir "Ha cumplido años este año: ", ha_cumplido_este_año
    Imprimir "Hoy es su cumpleaños: ", es_cumpleaños_hoy
Fin ///
