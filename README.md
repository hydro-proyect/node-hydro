hydro-proyect
=============

Aplicacion para granja IoT

## Endpoints 

### [GET]

- Devuelve los datos que tengas mayor a la fecha date (Datos recolectados por segundo)

```
/data/historico/:sensor/date/:date
```

### [GET]

- Devuelve los datos por segundo entre las dos fechas.

```
/data/historico/:sensor/mindate/:min_date/maxdate/:max_date
```

### [GET]

- Devuelve los datos promedio de horas del dia
- La variable date recibe la fecha con 00:00:00 horas en formato timestamp

```
/data/historico/:sensor/horas/date/:date
```

### [GET]

- Devuelve los datos promedio de minutos
```
/data/historico/minutos/:sensor/mindate/:min_date/maxdate/:max_date
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

## Los nombre de los sensores son

- humedad
- ph
- temp_aire
- temp_agua
