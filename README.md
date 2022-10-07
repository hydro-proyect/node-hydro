hydro-proyect
=============

Aplicacion para granja IoT

# Endpoints 

## Enpoints para consuta de datos por segundo

### [GET]

- Devuelve los datos entre la fecha date y 24 horas despues de la fecha especificada (Datos recolectados por segundo)

```
/data/historico/:sensor/date/:date
```

### [GET]

- Devuelve los datos por segundo entre las dos fechas.

```
/data/historico/:sensor/mindate/:min_date/maxdate/:max_date
```
## Enpoint de consulta de datos promedio por minuto

### [GET]

- Devuelve los datos entre la fecha date y 24 horas despues a partir de fecha(los datos mostrados son el promedio de cada minuto) 
```
/data/historico/minutos/:sensor/date/:date
```


### [GET]

- Devuelve los datos promedio de minutos entre dos fechas
```
/data/historico/minutos/:sensor/mindate/:min_date/maxdate/:max_date
```

## Enpoints de consultade datos promedio por hora

### [GET]

- Devuelve los datos entre la fecha date y 24 horas despues a partir de fecha(los datos mostrados son el promedio de cada hora) 
```
/data/historico/horas/:sensor/date/:date
```

### [GET]

- Devuelve los datos promedio de las horas en un rango de fechas
```
/data/historico/horas/:sensor/mindate/:min_date/maxdate/:max_date
```

### [POST]

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


## Los nombre de los sensores son

- humedad
- ph
- temp_aire
- temp_agua
