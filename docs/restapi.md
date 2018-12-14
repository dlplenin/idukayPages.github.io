[Regresar al menú principal](index.md){: .btn}
# Overview

Integrate our API to exchange data from our schools network.

# Getting Started
1. You must send Idukay (pablo.pazmino@idukay.com) the following information:
* 1. National identification number or passport number (RUC/cédula/passport/DNI)
* 2. Full names
* 3. Phone number
* 4. Email address

2. You will receive an email where you can set a password to activate your account. (This value must be included into the headers of each request afterwards)

3. When your account is activated you will receive your token, WorkingSchool, WorkingYear, WorkingProfile and ClientVersion. These values must be included into the headers of each request.

Example:

`REQUEST HEADERS:`

|      Key      |       Example value      |              Description              |
|---------------|--------------------------|---------------------------------------|
| Authorization | xyz                      | A tokey key provided by Idukay        |
| Password      | 123456                   | Your password                         |
| WorkingSchool | 53a0be2c1a9d5fb532000064 | School ID that you request to work in |
| WorkingYear   | 53a0a8665dc899392c00004b | Year ID that you request to work in   |
| WorkingProfile| 5beb1a44df5211cf15ad3ab4 | Profile ID assigned by Idukay         |
| ClientVersion | 0.0.0                    | API version                           |


# API Method list
**SANDBOX URI: `http://dev.idukay.net/`**

|          Resource                                   | Method |         Endpoint         |  
|-----------------------------------------------------|--------|--------------------------|
| [Students](#Students)                               | GET    | /students                |
| [Parents](#Parents)                                 | GET    | /parents                 |
| [Year](#Year)                                       | GET    | /years?_id={WorkingYear} |
| [Payment notification](#Payment_notification)       | POST   | /notifications_payments  |
| [Pending Payments](#Pending_Payments)           | PUT    | /students                |

## _Structure of the response_
```javascript
{
    "response": {},
    "errors": [] //"errors": ["invalid_year"]
}
```
An object will be returned with two keys (response, errors), one of them will have data depending on whether the request was processed correctly or not.

## Students
Students list filtered by school and year.

### HTTP request

`GET /students`

### Definitions

| Item            | Description                          | Example                  |
|-----------------|--------------------------------------|--------------------------|
| _id             | Student ID in Idukay                 | 53a1e89c51cfd2ec2700010e |
| addresses       | Addresses list                       |                          |
| citizenship     | Country ISO code                     | EC                       |
| emergency       | Emergency contacts                   |                          |
| medical_history | Medical history                      |                          |
| period_conduct  | Conduct score                        |                          |
| relatives       | Student's relatives list             |                          |
| school          | School ID in Idukay                  | 53a0a8665dc899392c00004b |
| user            | Student's user information           |                          |
| years           | Years history                        |                          |

### Example

<details>
  <summary>JSON response</summary>
  
```javascript
{
    "response": [
        {
            "_id": "53a1e89c51cfd2ec2700010e",
            "addresses": [
                {
                    "_id": "53a1e89c51cfd2ec27000110",
                    "bus_routes": [],
                    "main": true,
                    "main_street": "",
                    "name": "Domicilio",
                    "number": "",
                    "parish": "",
                    "secondary_street": "",
                    "trips": [
                        {
                            "_id": "53a1e89c51cfd2ec27000117",
                            "from": true,
                            "to": true,
                            "week_day": 0
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000116",
                            "from": true,
                            "to": true,
                            "week_day": 1
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000115",
                            "from": true,
                            "to": true,
                            "week_day": 2
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000114",
                            "from": true,
                            "to": true,
                            "week_day": 3
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000113",
                            "from": true,
                            "to": true,
                            "week_day": 4
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000112",
                            "from": false,
                            "to": false,
                            "week_day": 5
                        },
                        {
                            "_id": "53a1e89c51cfd2ec27000111",
                            "from": false,
                            "to": false,
                            "week_day": 6
                        }
                    ],
                    "zip_code": ""
                }
            ],
            "citizenship": "EC",
            "emergency": {
                "contacts": [
                    {
                        "phones": {
                            "mobile": null
                        }
                    }
                ]
            },
            "medical_history": {
                "allergies": [],
                "illnesses": [],
                "vaccines": []
            },
            "period_conduct": [
                {
                    "_id": "53a31de73cee9ed30b0002a8",
                    "period": "53a0be2c1a9d5fb532000059",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a7",
                    "period": "53a0be2c1a9d5fb532000058",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a6",
                    "period": "53a0be2c1a9d5fb532000057",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a5",
                    "period": "53a0be2c1a9d5fb532000056",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a4",
                    "period": "53a0be2c1a9d5fb532000055",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a3",
                    "period": "53a0be2c1a9d5fb532000054",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a2",
                    "period": "53a0be2c1a9d5fb532000053",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a1",
                    "period": "53a0be2c1a9d5fb532000052",
                    "score": null
                },
                {
                    "_id": "53a31de73cee9ed30b0002a0",
                    "period": "53a0be2c1a9d5fb532000051",
                    "score": null
                }
            ],
            "permissions": [
                "53a0a866fc09c1392c4a020f"
            ],
            "relatives": [],
            "school": "53a0a8665dc899392c00004b",
            "user": {
                "_id": "53d27b4a2c6c197fa0000041",
                "address": null,
                "birthday": 960940800,
                "email": "colosus@xmen.com",
                "fix_email_index_check": "",
                "gender": "M",
                "id_card": "1310292618",
                "is_passport": null,
                "name": "Piotr",
                "photo": null,
                "place_of_birth": "",
                "preferences": {
                    "receive_mail_on_notification": true
                },
                "profiles": [
                    {
                        "_id": "53a1e89c51cfd2ec2700010e",
                        "collection_name": "students"
                    }
                ],
                "school": "53a0a8665dc899392c00004b",
                "second_surname": "Colosus",
                "surname": "Rasputin",
                "system_access": false
            },
            "years": [
                {
                    "_id": "53a1e89c51cfd2ec2700010f",
                    "enrolled": true,
                    "grade": "53a0a8695dc899392c000061",
                    "registered": false,
                    "registered_date": 0,
                    "year": "53a0a8695dc899392c00004f",
                    "registration_type": "5671d70310bc97627548393b"
                },
                {
                    "_id": "53a1fd0751cfd2ec27000192",
                    "enrolled": true,
                    "grade": "53a0be2c1a9d5fb532000066",
                    "group": "53a1f82951cfd2ec2700017f",
                    "registered": false,
                    "registered_date": 0,
                    "year": "53a0be2c1a9d5fb532000051",
                    "registration_type": "5671d70310bc976275483941"
                }
            ],
            "relational_data": {
                "gender": "M",
                "name": {
                    "show": "Rasputin Colosus, Piotr",
                    "order": "rasputin colosus, piotr"
                },
                "id_card": {
                    "show": "1310292618",
                    "order": "1310292618"
                },
                "email": "colosus@xmen.com",
                "years": {
                    "53a0a8695dc899392c00004f": {
                        "grade": {
                            "show": "Primero de Básica, 2012-2013, Básica",
                            "order": "primero de basica, 2012-2013, basica"
                        },
                        "group": {
                            "show": "",
                            "order": ""
                        },
                        "all_data": "1310292618 rasputin colosus, piotr colosus@xmen.com primero de basica, 2012-2013, basica "
                    },
                    "53a0be2c1a9d5fb532000051": {
                        "all_data": "1310292618 rasputin colosus, piotr colosus@xmen.com segundo de basica, basica elemental 2b-b",
                        "group": {
                            "order": "2b-b",
                            "show": "2B-B"
                        },
                        "grade": {
                            "order": "segundo de basica, basica elemental",
                            "show": "Segundo de Básica, Básica Elemental"
                        }
                    }
                },
                "all_data": "1310292618 rasputin colosus, piotr colosus@xmen.com"
            }
        },
        {
            "_id": "53a1e3bd51cfd2ec270000ba",
            "addresses": [
                {
                    "zip_code": "",
                    "secondary_street": "10 de Agosto",
                    "parish": "Iñaquito",
                    "number": "E478-251",
                    "name": "Casa del Padre",
                    "main_street": "Mañosca",
                    "main": true,
                    "city_zone": "53a1e6b451cfd2ec270000d9",
                    "_id": "53a1e3bd51cfd2ec270000bd",
                    "trips": [
                        {
                            "week_day": 0,
                            "to": true,
                            "from": true,
                            "_id": "53a1e3bd51cfd2ec270000c4"
                        },
                        {
                            "week_day": 1,
                            "to": true,
                            "from": true,
                            "_id": "53a1e3bd51cfd2ec270000c3"
                        },
                        {
                            "week_day": 2,
                            "to": true,
                            "from": true,
                            "_id": "53a1e3bd51cfd2ec270000c2"
                        },
                        {
                            "week_day": 3,
                            "to": true,
                            "from": true,
                            "_id": "53a1e3bd51cfd2ec270000c1"
                        },
                        {
                            "week_day": 4,
                            "to": true,
                            "from": true,
                            "_id": "53a1e3bd51cfd2ec270000c0"
                        },
                        {
                            "week_day": 5,
                            "to": false,
                            "from": false,
                            "_id": "53a1e3bd51cfd2ec270000bf"
                        },
                        {
                            "week_day": 6,
                            "to": false,
                            "from": false,
                            "_id": "53a1e3bd51cfd2ec270000be"
                        }
                    ],
                    "bus_routes": []
                },
                {
                    "zip_code": "",
                    "secondary_street": "Severino Iturralde",
                    "parish": "Vicentina",
                    "number": "E632-457",
                    "name": "Casa de la Madre",
                    "main_street": "Luis Carvajal",
                    "main": false,
                    "city_zone": "53a99a79774b6ad71d000047",
                    "_id": "53a99a53774b6ad71d00003f",
                    "trips": [
                        {
                            "week_day": 0,
                            "to": true,
                            "from": true,
                            "_id": "53a99a53774b6ad71d000046"
                        },
                        {
                            "week_day": 1,
                            "to": true,
                            "from": true,
                            "_id": "53a99a53774b6ad71d000045"
                        },
                        {
                            "week_day": 2,
                            "to": true,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000044"
                        },
                        {
                            "week_day": 3,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000043"
                        },
                        {
                            "week_day": 4,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000042"
                        },
                        {
                            "week_day": 5,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000041"
                        },
                        {
                            "week_day": 6,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000040"
                        }
                    ],
                    "bus_routes": []
                },
                {
                    "zip_code": "",
                    "secondary_street": "Amazonas Esquina",
                    "parish": "La Mariscal",
                    "number": "E123-578",
                    "name": "Casa de la Abuela",
                    "main_street": "Luis Cordero",
                    "main": false,
                    "city_zone": "53a1e6c651cfd2ec270000da",
                    "_id": "53a99a53774b6ad71d000037",
                    "trips": [
                        {
                            "week_day": 0,
                            "to": true,
                            "from": false,
                            "_id": "53a99a53774b6ad71d00003e"
                        },
                        {
                            "week_day": 1,
                            "to": true,
                            "from": true,
                            "_id": "53a99a53774b6ad71d00003d"
                        },
                        {
                            "week_day": 2,
                            "to": true,
                            "from": false,
                            "_id": "53a99a53774b6ad71d00003c"
                        },
                        {
                            "week_day": 3,
                            "to": true,
                            "from": true,
                            "_id": "53a99a53774b6ad71d00003b"
                        },
                        {
                            "week_day": 4,
                            "to": true,
                            "from": true,
                            "_id": "53a99a53774b6ad71d00003a"
                        },
                        {
                            "week_day": 5,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000039"
                        },
                        {
                            "week_day": 6,
                            "to": false,
                            "from": false,
                            "_id": "53a99a53774b6ad71d000038"
                        }
                    ],
                    "bus_routes": []
                }
            ],
            "citizenship": "EC",
            "emergency": {
                "contacts": [
                    {
                        "_id": "561d1e5b209abd291100003b",
                        "phones": {
                            "mobile": null
                        }
                    }
                ]
            },
            "medical_history": {
                "vaccines": [],
                "illnesses": [],
                "allergies": []
            },
            "period_conduct": [
                {
                    "score": 7,
                    "period": "53a0be2c1a9d5fb532000059",
                    "_id": "53a31de73cee9ed30b00027b"
                },
                {
                    "score": 9.9,
                    "period": "53a0be2c1a9d5fb532000058",
                    "_id": "53a31de73cee9ed30b00027a"
                },
                {
                    "score": 8,
                    "period": "53a0be2c1a9d5fb532000057",
                    "_id": "53a31de73cee9ed30b000279"
                },
                {
                    "score": 8,
                    "period": "53a0be2c1a9d5fb532000056",
                    "_id": "53a31de73cee9ed30b000278"
                },
                {
                    "score": 9.8,
                    "period": "53a0be2c1a9d5fb532000055",
                    "_id": "53a31de73cee9ed30b000277"
                },
                {
                    "score": 8.67,
                    "period": "53a0be2c1a9d5fb532000054",
                    "_id": "53a31de73cee9ed30b000276"
                },
                {
                    "score": 9,
                    "period": "53a0be2c1a9d5fb532000053",
                    "_id": "53a31de73cee9ed30b000275"
                },
                {
                    "score": 9.5,
                    "period": "53a0be2c1a9d5fb532000052",
                    "_id": "53a31de73cee9ed30b000274"
                },
                {
                    "score": 9,
                    "period": "53a0be2c1a9d5fb532000051",
                    "_id": "53a31de73cee9ed30b000273"
                }
            ],
            "permissions": [
                "53a0a866fc09c1392c4a020f"
            ],
            "relatives": [
                {
                    "official_legal_guardian": true,
                    "relationship": "Padre",
                    "parent": "53a1df6351cfd2ec2700004f",
                    "is_legal_guardian": true,
                    "_id": "53a1e3bd51cfd2ec270000bc"
                }
            ],
            "school": "53a0a8665dc899392c00004b",
            "user": {
                "_id": "53d27b4a2c6c197fa0000037",
                "address": null,
                "birthday": 960940800,
                "email": "gambit@xmen.com",
                "fix_email_index_check": "",
                "gender": "F",
                "id_card": "0500972062",
                "is_passport": null,
                "name": "Remy",
                "photo": "6516.3b61d41b.baa6-de32.f3af-4fb5-ab90.e021-0531.045788df.1203ddbb.b9c8.jpg",
                "place_of_birth": "",
                "preferences": {
                    "receive_mail_on_notification": true
                },
                "profiles": [
                    {
                        "collection_name": "students",
                        "_id": "53a1e3bd51cfd2ec270000ba"
                    }
                ],
                "school": "53a0a8665dc899392c00004b",
                "second_surname": "Gambit",
                "surname": "LeBeau",
                "system_access": false
            },
            "years": [
                {
                    "registration_type": "5671d70310bc97627548393b",
                    "year": "53a0a8695dc899392c00004f",
                    "registered_date": 0,
                    "registered": false,
                    "grade": "53a0a8695dc899392c000061",
                    "enrolled": true,
                    "_id": "53a1e3bd51cfd2ec270000bb"
                },
                {
                    "paid": true,
                    "registration_type": "5671d70310bc976275483941",
                    "year": "53a0be2c1a9d5fb532000051",
                    "registered_date": 1444748891,
                    "registered": true,
                    "group": "53a1f7d451cfd2ec2700017e",
                    "grade": "53a0be2c1a9d5fb532000066",
                    "enrolled": true,
                    "_id": "53a1fc5151cfd2ec2700018b"
                }
            ],
            "relational_data": {
                "gender": "F",
                "name": {
                    "order": "lebeau gambit, remy",
                    "show": "LeBeau Gambit, Remy"
                },
                "id_card": {
                    "order": "0500972062",
                    "show": "0500972062"
                },
                "email": "gambit@xmen.com",
                "years": {
                    "53a0a8695dc899392c00004f": {
                        "all_data": "0500972062 lebeau gambit, remy gambit@xmen.com primero de basica, 2012-2013, basica",
                        "group": {
                            "order": "",
                            "show": ""
                        },
                        "grade": {
                            "order": "primero de basica, 2012-2013, basica",
                            "show": "Primero de Básica, 2012-2013, Básica"
                        }
                    },
                    "53a0be2c1a9d5fb532000051": {
                        "all_data": "0500972062 lebeau gambit, remy gambit@xmen.com segundo de basica, basica elemental 2b-a",
                        "group": {
                            "order": "2b-a",
                            "show": "2B-A"
                        },
                        "grade": {
                            "order": "segundo de basica, basica elemental",
                            "show": "Segundo de Básica, Básica Elemental"
                        }
                    }
                },
                "all_data": "0500972062 lebeau gambit, remy gambit@xmen.com"
            },
            "code": "x5"
        }
    ],
    "errors": []
}
```
</details>
<br>
<a href="#top">Back to top</a>

## Parents
Parents list filtered by school and year.

### HTTP request

`GET /parents`

### Definitions

| Item            | Description                           | Example                  |
|-----------------|---------------------------------------|--------------------------|
| _id             | Parent ID in Idukay                   | 53a1da6f51cfd2ec27000047 |
| citizenship     | Country ISO code                      | AF                       |
| lock            |                                       |                          |
| education_level | Education level                       |                          |
| occupation      | Ocuppation                            | Waitress                 |
| profession      | Profession                            | Dancer                   |
| system_access   | Point out if parent has system access |                          |
| home_address    | Home address                          | Civil war                |
| work_address    | Work address                          |                          |
| work_name       | Where parent works                    |                          |
| phones          | List of phone numbers                 |                          |
| school          | School ID in Idukay                   | 53a0a8665dc899392c00004b |
| user            | Parent's user information             |                          |

### Example

<details>
  <summary>JSON response</summary>
  
```javascript
{
    "response": [
        {
            "lock": false,
            "_id": "53a1da6f51cfd2ec27000047",
            "citizenship": "AF",
            "education_level": "Cuarto Nivel (Cursado)",
            "home_address": "La Guerra Civil",
            "occupation": "Dueña de comedor",
            "profession": "Bailarina",
            "school": "53a0a8665dc899392c00004b",
            "system_access": true,
            "user": {
                "_id": "53a1da6f51cfd2ec27000048",
                "__v": 0,
                "activated": true,
                "address": null,
                "birthday": null,
                "email": "old_silkspectre@watchmen.com",
                "fix_email_index_check": "",
                "gender": "F",
                "id_card": "85263655556",
                "is_passport": true,
                "name": "Sally",
                "photo": null,
                "school": "53a0a8665dc899392c00004b",
                "second_surname": "Silk Spectre",
                "surname": "Juspeczyk",
                "system_access": true,
                "preferences": {
                    "working_school": "53a0a8665dc899392c00004b",
                    "working_year": "53a0bfee1a9d5fb5320000bf",
                    "receive_mail_on_notification": true
                },
                "schools_registered": [],
                "profiles": [
                    {
                        "_id": "53a1da6f51cfd2ec27000047",
                        "collection_name": "parents"
                    }
                ]
            },
            "work_address": "Puyo",
            "work_name": "Petroecuador",
            "phones": {
                "work": "123456798",
                "mobile": {
                    "number": "5622512355",
                    "provider": "Claro"
                }
            }
        },
        {
            "lock": false,
            "_id": "53a1df6351cfd2ec2700004f",
            "citizenship": "EC",
            "education_level": "Bachiller",
            "home_address": "Quito",
            "occupation": "Reportero encubierto",
            "profession": "Mecánico",
            "school": "53a0a8665dc899392c00004b",
            "system_access": true,
            "user": {
                "_id": "53a1df6351cfd2ec27000050",
                "__v": 0,
                "activated": true,
                "address": null,
                "birthday": null,
                "email": "old_niteowl@watchmen.com",
                "fix_email_index_check": "",
                "gender": "M",
                "id_card": "123456789",
                "is_passport": true,
                "name": "Hollis",
                "photo": null,
                "school": "53a0a8665dc899392c00004b",
                "second_surname": "Nite Owl",
                "surname": "Mason",
                "system_access": true,
                "preferences": {
                    "selected_student": "53a1ea5251cfd2ec2700012c",
                    "working_profile": "53a1df6351cfd2ec2700004f",
                    "working_school": "53a0a8665dc899392c00004b",
                    "working_year": "53a0be2c1a9d5fb532000051",
                    "receive_mail_on_notification": true
                },
                "schools_registered": [],
                "profiles": [
                    {
                        "_id": "53a1df6351cfd2ec2700004f",
                        "collection_name": "parents"
                    }
                ]
            },
            "work_address": "Parque de la Carolina S/N",
            "work_name": "Megadatos",
            "phones": {
                "work": "123456798",
                "mobile": {
                    "number": "5623012355",
                    "provider": "Claro"
                }
            }
        }
    ],
    "errors": []
}
```
</details>
<br>
<a href="#top">Back to top</a>

## Year
Detail of school year.

### HTTP request

`GET /years?_id={WorkingYear}`

### Definitions

| Item           | Description                             | Example                  |
|----------------|-----------------------------------------|--------------------------|
| _id            | Yar ID in Idukay                        | 53a0be2c1a9d5fb532000051 |
| base_score     | Top score defined by the school         | 10                       |
| name           | Year name                               | 2013-2014                |
| passing_score  | Minimum score to be reached by students | 7                        |
| score_decimals | Decimal places of scores                | 2                        |
| school         | School ID in Idukay                     | 53a0a8665dc899392c00004b |

### Example

<details>
  <summary>JSON response</summary>
  
```javascript
{
    "response": [
        {
            "_id": "53a0be2c1a9d5fb532000051",
            "__v": 0,
            "base_score": 10,
            "master_year": "53a0be2c1a9d5fb53200002b",
            "name": "2013-2014",
            "passing_score": 7,
            "school": "53a0a8665dc899392c00004b",
            "score_decimals": 2,
            "dates": {
                "creation": 1403043372
            },
            "conduct_categories": [],
            "registration_types": [
                {
                    "_id": "5671d70310bc976275483941",
                    "name": "Matrícula ordinaria"
                },
                {
                    "_id": "5671d70310bc976275483942",
                    "name": "Matrícula extraordinaria"
                },
                {
                    "_id": "5671d70310bc976275483943",
                    "name": "Matrícula con pase de colegio"
                }
            ],
            "period_comments_titles": [
                {
                    "_id": "56b36fa80a2b9725667697a4"
                },
                {
                    "_id": "56b36fa80a2b9725667697a5"
                }
            ],
            "text_equivalences": {
                "conduct_letter": [
                    {
                        "_id": "53a0be2c1a9d5fb532000076",
                        "score": "E",
                        "text": "Insatisfactorio"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb532000075",
                        "score": "D",
                        "text": "Mejorable"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb532000074",
                        "score": "C",
                        "text": "Poco Satisfactorio"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb532000073",
                        "score": "B",
                        "text": "Satisfactorio"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb532000072",
                        "score": "A",
                        "text": "Muy Satisfactorio"
                    }
                ],
                "conduct_score": [
                    {
                        "_id": "53a0be2c1a9d5fb532000071",
                        "score": 0,
                        "text": "E"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb532000070",
                        "score": 3,
                        "text": "D"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb53200006f",
                        "score": 5,
                        "text": "C"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb53200006e",
                        "score": 7,
                        "text": "B"
                    },
                    {
                        "_id": "53a0be2c1a9d5fb53200006d",
                        "score": 9,
                        "text": "A"
                    }
                ],
                "qualitative_scores": [
                    {
                        "_id": "543d76e99f31341e35000045",
                        "description": "Insatisfactorio",
                        "letter": "E",
                        "score": 0,
                        "name": "E"
                    },
                    {
                        "_id": "543d76e99f31341e35000044",
                        "description": "Mejorable",
                        "letter": "D",
                        "score": 4,
                        "name": "D"
                    },
                    {
                        "_id": "543d76e99f31341e35000043",
                        "description": "Poco satisfactorio",
                        "letter": "C",
                        "score": 6,
                        "name": "C"
                    },
                    {
                        "_id": "543d76e99f31341e35000042",
                        "description": "Satisfactorio",
                        "letter": "B",
                        "score": 8,
                        "name": "B"
                    },
                    {
                        "_id": "543d76e99f31341e35000041",
                        "description": "Muy satisfactorio",
                        "letter": "A",
                        "score": 10,
                        "name": "A"
                    }
                ],
                "scores": [
                    {
                        "_id": "543d76e99f31341e35000040",
                        "score": 0,
                        "text": "No alcanza los aprendizajes requeridos"
                    },
                    {
                        "_id": "543d76e99f31341e3500003f",
                        "score": 4.01,
                        "text": "Está próximo a alcanzar los aprendizajes requeridos"
                    },
                    {
                        "_id": "543d76e99f31341e3500003e",
                        "score": 7,
                        "text": "Alcanza los aprendizajes requeridos"
                    },
                    {
                        "_id": "543d76e99f31341e3500003d",
                        "score": 9,
                        "text": "Domina los aprendizajes requeridos"
                    }
                ]
            },
            "graduation_category_types": [
                {
                    "_id": "5759eef7c26b2548328a0b79",
                    "name": "Promedio de 1ro a 5to",
                    "weight": 50
                },
                {
                    "_id": "5759eef7c26b2548328a0b78",
                    "name": "Promedio de 6to",
                    "weight": 30
                },
                {
                    "_id": "5759eef7c26b2548328a0b77",
                    "name": "Monografia",
                    "weight": 20
                }
            ],
            "show_for_grades": [],
            "sections": [
                {
                    "_id": "53a0be2c1a9d5fb532000064",
                    "abbreviation": "BA",
                    "name": "Básica Elemental",
                    "subjects_order": [],
                    "skill_scores": [
                        {
                            "_id": "543d76e99f31341e35000036",
                            "score": "SR",
                            "text": "Supera resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000035",
                            "score": "DR",
                            "text": "Domina resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000034",
                            "score": "AR",
                            "text": "Alcanza resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000033",
                            "score": "PR",
                            "text": "Está próximo a alcanzar resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000032",
                            "score": "NR",
                            "text": "No alcanza resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000031",
                            "score": "NA",
                            "text": "No aplica"
                        }
                    ],
                    "grades": [
                        {
                            "_id": "53a0be2c1a9d5fb532000067",
                            "abbreviation": "01",
                            "name": "Primero de Básica",
                            "master_grade": "53a0be2c1a9d5fb532000033",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        },
                        {
                            "graduate_students": true,
                            "_id": "53a0be2c1a9d5fb532000066",
                            "abbreviation": "02",
                            "name": "Segundo de Básica",
                            "master_grade": "53a0be2c1a9d5fb532000032",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        },
                        {
                            "_id": "53a0be2c1a9d5fb532000065",
                            "abbreviation": "03",
                            "name": "Tercero de Básica",
                            "master_grade": "53a0be2c1a9d5fb532000031",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        }
                    ]
                },
                {
                    "_id": "53a0be2c1a9d5fb532000060",
                    "abbreviation": "BU",
                    "name": "Bachillerato Unificado",
                    "subjects_order": [],
                    "skill_scores": [
                        {
                            "_id": "543d76e99f31341e3500003c",
                            "score": "SR",
                            "text": "Supera resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e3500003b",
                            "score": "DR",
                            "text": "Domina resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e3500003a",
                            "score": "AR",
                            "text": "Alcanza resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000039",
                            "score": "PR",
                            "text": "Está próximo a alcanzar resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000038",
                            "score": "NR",
                            "text": "No alcanza resultados esperados"
                        },
                        {
                            "_id": "543d76e99f31341e35000037",
                            "score": "NA",
                            "text": "No aplica"
                        }
                    ],
                    "grades": [
                        {
                            "_id": "53a0be2c1a9d5fb532000063",
                            "abbreviation": "01",
                            "name": "Primero",
                            "master_grade": "53a0be2c1a9d5fb53200002f",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        },
                        {
                            "_id": "53a0be2c1a9d5fb532000062",
                            "abbreviation": "02",
                            "name": "Segundo",
                            "master_grade": "53a0be2c1a9d5fb53200002e",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        },
                        {
                            "_id": "53a0be2c1a9d5fb532000061",
                            "abbreviation": "03",
                            "name": "Tercero",
                            "master_grade": "53a0be2c1a9d5fb53200002d",
                            "hour_schedules": [
                                {
                                    "day": 0,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 1,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 2,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 3,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 4,
                                    "schedules": [
                                        {
                                            "start": "07:00",
                                            "end": "07:45"
                                        },
                                        {
                                            "start": "07:45",
                                            "end": "08:30"
                                        },
                                        {
                                            "start": "08:30",
                                            "end": "09:15"
                                        },
                                        {
                                            "start": "09:15",
                                            "end": "10:00"
                                        },
                                        {
                                            "start": "10:45",
                                            "end": "11:30"
                                        },
                                        {
                                            "start": "11:30",
                                            "end": "12:15"
                                        },
                                        {
                                            "start": "12:15",
                                            "end": "13:00"
                                        }
                                    ]
                                },
                                {
                                    "day": 5,
                                    "schedules": []
                                },
                                {
                                    "day": 6,
                                    "schedules": []
                                }
                            ],
                            "subjects_order": []
                        }
                    ]
                }
            ],
            "categories": [
                {
                    "_id": "53a0be2c1a9d5fb53200005f",
                    "name": "Grupal",
                    "weight": 25
                },
                {
                    "_id": "53a0be2c1a9d5fb53200005e",
                    "name": "Individual",
                    "weight": 25
                },
                {
                    "_id": "53a0be2c1a9d5fb53200005d",
                    "name": "Examen",
                    "weight": 25
                },
                {
                    "_id": "53a0be2c1a9d5fb53200005c",
                    "name": "Diaria",
                    "weight": 25
                }
            ],
            "additional_exams": [
                {
                    "_id": "53a0be2c1a9d5fb53200005b",
                    "abbreviation": "Sup.",
                    "name": "Supletorio",
                    "closed_for_grades": []
                },
                {
                    "_id": "53a0be2c1a9d5fb53200010b",
                    "abbreviation": "Rem.",
                    "name": "Remedial",
                    "closed_for_grades": []
                },
                {
                    "_id": "53a0be2c1a9d5fb53200005a",
                    "abbreviation": "Gra.",
                    "name": "Gracia",
                    "closed_for_grades": []
                }
            ],
            "terms": [
                {
                    "_id": "53a0be2c1a9d5fb532000056",
                    "abbreviation": "Periodo 1",
                    "end_date": 1410393600,
                    "name": "Primer periodo",
                    "start_date": 1405641600,
                    "closed_for_grades": [],
                    "makeup_exam": {
                        "closed_for_grades": []
                    },
                    "exam": {
                        "weight": 20,
                        "name": "Examen Final Periodo",
                        "abbreviation": "Ex Final 1",
                        "closed_for_grades": []
                    },
                    "parts": {
                        "weight": 80,
                        "records": [
                            {
                                "_id": "53a0be2c1a9d5fb532000059",
                                "abbreviation": "Parcial 1",
                                "end_date": 1406764800,
                                "name": "Primer parcial",
                                "start_date": 1405728000,
                                "closed_for_grades": [
                                    "53a0be2c1a9d5fb532000067"
                                ]
                            },
                            {
                                "_id": "53a0be2c1a9d5fb532000058",
                                "abbreviation": "Parcial 2",
                                "end_date": 1409270400,
                                "name": "Segundo Parcial",
                                "start_date": 1407542400,
                                "closed_for_grades": []
                            },
                            {
                                "_id": "53a0be2c1a9d5fb532000057",
                                "abbreviation": "Parcial 3",
                                "end_date": 1409270400,
                                "name": "Tercer Parcial",
                                "start_date": 1407542400,
                                "closed_for_grades": []
                            }
                        ]
                    }
                },
                {
                    "_id": "53a0be2c1a9d5fb532000052",
                    "abbreviation": "Periodo 2",
                    "end_date": 1417651200,
                    "name": "Segundo Periodo",
                    "start_date": 1410480000,
                    "closed_for_grades": [],
                    "makeup_exam": {
                        "closed_for_grades": []
                    },
                    "exam": {
                        "weight": 20,
                        "name": "Examen Final Periodo",
                        "abbreviation": "Ex Final 2",
                        "closed_for_grades": []
                    },
                    "parts": {
                        "weight": 80,
                        "records": [
                            {
                                "_id": "53a0be2c1a9d5fb532000055",
                                "abbreviation": "Parcial 1",
                                "end_date": 1412294400,
                                "name": "Primer parcial",
                                "start_date": 1410566400,
                                "closed_for_grades": []
                            },
                            {
                                "_id": "53a0be2c1a9d5fb532000054",
                                "abbreviation": "Parcial 2",
                                "end_date": 1414108800,
                                "name": "Segundo Parcial",
                                "start_date": 1412380800,
                                "closed_for_grades": []
                            },
                            {
                                "_id": "53a0be2c1a9d5fb532000053",
                                "abbreviation": "Parcial 3",
                                "end_date": 1415923200,
                                "name": "Tercer Parcial",
                                "start_date": 1414195200,
                                "closed_for_grades": []
                            }
                        ]
                    }
                }
            ]
        }
    ],
    "errors": []
}
```
</details>
<br>
<a href="#top">Back to top</a>

## Payment notification <a name="Payment_notification"></a>
Generate a payment notification to a given list of users (_id).

### HTTP request

`POST /notifications_payments`

### Request body 
Must provide a list of recipients (user IDs).

**Example JSON (application/json):**

```javascript
{
 "recipients": ["53a1da6f51cfd2ec27000048", "53a1df6351cfd2ec27000050"]  
}
```

### Definitions - response

| Item       | Description                                     | Example                  |
|------------|-------------------------------------------------|--------------------------|
| _id        | Notification ID in Idukay                       | 5beb410d55489c7144ffd103 |
| sent       | Point out if the notification is already sended | true                     |
| subject    | Subject message                                 |                          |
| content    | Content message                                 |                          |
| sender     | Your ID in Idukay                               | 5beb1a44df5211cf15ad3ab4 |
| date       | Generation date as Bigint type                  | 1542144269               |
| recipients | A list of recipients                            |                          |
| school     | School ID in Idukay                             | 53a0a8665dc899392c00004b |

### Example

<details>
  <summary>JSON response</summary>
  
```javascript
{
    "response": {
        "__v": 0,
        "sent": true,
        "subject": "Aviso de Cobro",
        "content": "Usted tiene registrada cartera en mora",
        "sender": "5beb1a44df5211cf15ad3ab4",
        "date": 1542144269,
        "school": "53a0a8665dc899392c00004b",
        "_id": "5beb410d55489c7144ffd103",
        "attachments": [],
        "recipients": [
            {
                "user": "53a1da6f51cfd2ec27000048",
                "_id": "5beb410d55489c7144ffd105"
            },
            {
                "user": "53a1df6351cfd2ec27000050",
                "_id": "5beb410d55489c7144ffd104"
            }
        ]
    },
    "errors": []
}
```
</details>
<br>
<a href="#top">Back to top</a>

## Pending Payments <a name="Pending_Payments"></a>
Update the state of pending payments per user.

### HTTP request

`PUT /students`

### Request body 
Must provide the student's ID and a boolean (late_payment) with a WorkingYear into year object.

**Example JSON (application/json):**

```javascript
 {
   "_id": "53a1e04e51cfd2ec27000055",
   "years":[
    {
      "year": "53a0be2c1a9d5fb532000051", //WorkingYear
      "late_payment": true
    }
   ]
 }
```

### Definitions - response

| Item       | Description                                     | Example                  |
|------------|-------------------------------------------------|--------------------------|
| _id        | Student ID in Idukay                            | 53a1e04e51cfd2ec27000055 |
| user       | Student's user information	               |                          |
| years      | Afected year                                    |                          |

### Example

<details>
  <summary>JSON response</summary>
  
```javascript
{
    "response": {
        "_id": "53a1e04e51cfd2ec27000055",
        "__v": 0,
        "citizenship": "EC",
        "school": "53a0a8665dc899392c00004b",
        "user": {
            "_id": "53d27b4a2c6c197fa0000040",
            "address": null,
            "birthday": 960940800,
            "email": "",
            "fix_email_index_check": "5bec3b53b9e7d0aa59fe06be",
            "gender": "M",
            "id_card": "0301738852",
            "is_passport": null,
            "name": "John",
            "photo": null,
            "place_of_birth": "",
            "school": "53a0a8665dc899392c00004b",
            "second_surname": "Pyro",
            "surname": "Allerdyce",
            "system_access": false,
            "activated": true,
            "preferences": {
                "working_profile": "53a1e04e51cfd2ec27000055",
                "working_year": "53a0bfee1a9d5fb5320000bf",
                "alerts": null,
                "receive_mail_on_notification": true
            },
            "schools_registered": [],
            "profiles": [
                {
                    "collection_name": "students",
                    "_id": "53a1e04e51cfd2ec27000055"
                }
            ]
        },
        "years": [
            {
                "late_payment": true,
                "registration_type": "5671d70310bc976275483941",
                "year": "53a0be2c1a9d5fb532000051",
                "registered_date": 0,
                "registered": false,
                "group": "53a1f82951cfd2ec2700017f",
                "grade": "53a0be2c1a9d5fb532000066",
                "enrolled": true,
                "_id": "53a1fb4051cfd2ec27000180"
            }
        ]
    },
    "errors": []
}
```
</details>
<br>
<a href="#top">Back to top</a>
