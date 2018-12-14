# Contable

[Menú principal](index.md)

Los webhooks son una herramienta para enviar datos después de un evento determinado dentro de la plataforma **IDUKAY**:
* Creación/actualización de un [Estudiante](#estudiante)
* Creación/actualización de un [Padre](#padre)
* Creación/actualización de un [Grado](#grado)

Se registra por partner-evento una URL https:// donde los datos del evento se envían en formato _JSON_ en el _body_ de la petición.


***

## Estudiante

El objeto JSON que **Idukay** genera tiene los siguientes campos:

|      Campo     |                               Significado                               |          Ejemplo         |
|:--------------:|:-----------------------------------------------------------------------:|:------------------------:|
| _id            | Identificador en Idukay del estudiante                                  | 53a1ea5251cfd2ec2700012c |
| citizenship    | Código ISO del país                                                     | EC                       |
| relative       | Identificador en Idukay del padre (representante económico o principal) | 53a1df6351cfd2ec2700004f |
| school         | Identificador en Idukay de la escuela                                   | 53a0a8665dc899392c00004b |
| email          | Email del estudiante                                                    | Opcional                 |
| id_card        | Cédula o pasaporte                                                      | 0400606844               |
| is_passport    | Indica si es pasaporte                                                  | false                    |
| name           | Primer nombre                                                           | Kurt                     |
| second_name    | Segundo nombre                                                          | Opcional                 |
| surname        | Primer apellido                                                         | Wagner                   |
| second_surname | Segundo apellido                                                        | Nightcrawler             |
| id             | Identificador del estudiante en el sistema partner                      | 4pzb8yAoxSp4dEwN         |


**Ejemplo:**
```javascript
{
 "_id": "53a1e04e51cfd2ec27000055",
 "citizenship": "EC",
 "id_card": "0301738852",
 "is_passport": false,
 "name": "John",
 "second_name": "",
 "surname": "Allerdyce",
 "second_surname": "Pyro",
 "email": "",
 "school": "53a0a8665dc899392c00004b",
 "relative": "53a1df6351cfd2ec2700004f",
 "id": "4pzb8yAoxSp4dEwN"
}
```
<a href="#top">Ir al inicio</a>

## Padre

El objeto JSON que **Idukay** genera tiene los siguientes campos:

|      Campo     |              Significado                           |          Ejemplo         |
|:--------------:|:--------------------------------------------------:|:------------------------:|
| _id            | Identificador en Idukay del padre                  | 53a1da6f51cfd2ec27000047 |
| citizenship    | Código ISO del país                                | AF                       |
| home_address   | Dirección                                          | Quito NA                 |
| school         | Identificador en Idukay de la escuela              | 53a0a8665dc899392c00004b |
| email          | Email del padre                                    | Opcional                 |
| id_card        | Cédula o pasaporte                                 | 85263655556              |
| is_passport    | Indica si es pasaporte                             | true                     |
| name           | Primer nombre                                      | Sally                    |
| second_name    | Segundo nombre                                     | Opcional                 |
| surname        | Primer apellido                                    | Silk Spectre             |
| second_surname | Segundo apellido                                   | Juspeczyk                |
| id             | Identificador del padre en el sistema partner      | 4pzb8yAoxSp4dEwN         |

**Ejemplo:**
```javascript
{
 "_id": "53a1da6f51cfd2ec27000047",
 "home_address": "La Guerra Civil",
 "school": "53a0a8665dc899392c00004b",
 "id_card": "85263655556",
 "is_passport": true,
 "name": "Sally",
 "second_name": "na",
 "surname": "Juspeczyk",
 "second_surname": "Silk Spectre",
 "email": "old_silkspectre@watchmen.com",
 "id": "4pzb8yAoxSp4dEwN"
}
```
<a href="#top">Ir al inicio</a>

## Grado

El objeto JSON que **Idukay** genera tiene los siguientes campos:

|  Campo  |                        Significado                       |          Ejemplo         |
|:-------:|:--------------------------------------------------------:|:------------------------:|
| _id     | Identificador en Idukay del grado                        | 53a0be2c1a9d5fb532000067 |
| name    | Nombre del grado                                         | Primero de Básica        |
| section | Sección a la que pertenece el grado                      | 53a0be2c1a9d5fb532000064 |
| school  | Identificador en Idukay de la escuela                    | 53a0a8665dc899392c00004b |
| year    | Identificador del año al que pertenece el grado          | 53a0be2c1a9d5fb532000051 |
| id      | Identificador del grado en el sistema partner (producto) | RYjbq2ZyZfjwdLNg         |

**Ejemplo:**
```javascript
{
 "_id": "5bcf8b2cf0b0d70539d0ff46",
 "name": "Grado 2, sección 2",
 "section": "5bcf8b2cf0b0d70539d0ff44",
 "school": "53a0a8665dc899392c00004b",
 "year": "5bcf8b2cf0b0d70539d0ff3b",
 "id": "RYjbq2ZyZfjwdLNg"
}
```
<a href="#top">Ir al inicio</a>
