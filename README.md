# Tabla de contenido

<!--toc:start-->
- [Tabla de contenido](#tabla-de-contenido)
- [Hydro-proyect](#hydro-proyect)
- [Endpoints](#endpoints)
  - [Enpoints para consuta de datos por segundo](#enpoints-para-consuta-de-datos-por-segundo)
    - [[GET] Obtener historico de un dia en segundos](#get-obtener-historico-de-un-dia-en-segundos)
    - [[GET] Obtener historicos entre dos fechas en segundos](#get-obtener-historicos-entre-dos-fechas-en-segundos)
  - [Enpoint de consulta de datos promedio por minuto](#enpoint-de-consulta-de-datos-promedio-por-minuto)
    - [[GET] Obtener historicos de un dia en minutos](#get-obtener-historicos-de-un-dia-en-minutos)
    - [[GET] Obtener historico entre dos fechas en minutos](#get-obtener-historico-entre-dos-fechas-en-minutos)
  - [Enpoints de consultade datos promedio por hora](#enpoints-de-consultade-datos-promedio-por-hora)
    - [[GET] Obtener historico de un dia en horas](#get-obtener-historico-de-un-dia-en-horas)
    - [[GET] Obtener historico entre dos fechas](#get-obtener-historico-entre-dos-fechas)
    - [[POST] Actualizar los parametros limites de los sensores](#post-actualizar-los-parametros-limites-de-los-sensores)
      - [Body ejemplo](#body-ejemplo)
- [WebSockets](#websockets)
  - [Los nombre de los sensores para los endpoints son](#los-nombre-de-los-sensores-para-los-endpoints-son)
  - [Las rutas de los nodos mqtt son](#las-rutas-de-los-nodos-mqtt-son)
- [Pruebas con datos aleatorios](#pruebas-con-datos-aleatorios)
  - [Paso 1 (En la pagina de "Flujo completo")](#paso-1-en-la-pagina-de-flujo-completo)
  - [Paso 2](#paso-2)
  - [Paso 3 (En la pagina de Guadar promedios)](#paso-3-en-la-pagina-de-guadar-promedios)
<!--toc:end-->

# Hydro-proyect

Aplicacion para granja IoT

# Endpoints 

## Enpoints para consuta de datos por segundo

### [GET] Obtener historico de un dia en segundos

- Devuelve los datos entre la fecha date y 24 horas despues de la fecha especificada (Datos recolectados por segundo)

```
/data/historico/:sensor/date/:date
```

### [GET] Obtener historicos entre dos fechas en segundos

- Devuelve los datos por segundo entre las dos fechas.

```
/data/historico/:sensor/mindate/:min_date/maxdate/:max_date
```
## Enpoint de consulta de datos promedio por minuto

### [GET] Obtener historicos de un dia en minutos

- Devuelve los datos entre la fecha date y 24 horas despues a partir de fecha(los datos mostrados son el promedio de cada minuto) 
```
/data/historico/minutos/:sensor/date/:date
```

### [GET] Obtener historico entre dos fechas en minutos

- Devuelve los datos promedio de minutos entre dos fechas
```
/data/historico/minutos/:sensor/mindate/:min_date/maxdate/:max_date
```

## Enpoints de consultade datos promedio por hora

### [GET] Obtener historico de un dia en horas

- Devuelve los datos entre la fecha date y 24 horas despues a partir de fecha(los datos mostrados son el promedio de cada hora) 
```
/data/historico/horas/:sensor/date/:date
```

### [GET] Obtener historico entre dos fechas

- Devuelve los datos promedio de las horas en un rango de fechas
```
/data/historico/horas/:sensor/mindate/:min_date/maxdate/:max_date
```

### [POST] Actualizar los parametros limites de los sensores

Actualiza los parametros de estado optimo para los sensores

```
/params
```

#### Body ejemplo

```json
{
	"sensor": "humedad",
	"min_value": 20,
	"max_value": 60
}
```
# WebSockets

```
/ws/data/humedad
/ws/data/ph
/ws/data/temperatura/agua
/ws/data/temperatura/aire

```


## Los nombre de los sensores para los endpoints son

- humedad
- ph
- temp_aire
- temp_agua

## Las rutas de los nodos mqtt son 

- sensor/humedad
- sensor/ph
- sensor/temperatura/aire
- sensor/temperatura/agua

# Pruebas con datos aleatorios

Para hacer prueba generando datos aleatorios se debe hacer lo siguiente.

## Paso 1 (En la pagina de "Flujo completo")
Conectar los inputs, humedad, pH, temperatura del aire y temperatura del agua a su respectivo set global.
Hacer deploy y luego ejecutar cada input para un primer envío de datos.

## Paso 2
Desconectar los inputs de los sets global y configurar los inputs en un intervalo de 1 segundo y hacer el deploy

## Paso 3 (En la pagina de Guadar promedios)
Habilitar el flujo "Guardar promedios" para poblar las tablas de horas y minutos cuando sé del tiempo
