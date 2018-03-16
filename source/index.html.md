---
title: Ajandam API Dökümantasyonu

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - java

toc_footers:
  - <p>Geliştiriciler</p>
  - <a href='https://github.com/umutsoysl'>Umut Soysal</a>
  - <a href='https://github.com/resobyte'>İsmail Reşat Akcan </a>
  - <a href='https://github.com/ramazan'>Ramazan Demir</a>

includes:
  - errors

search: true
---

# Giriş

Merhaba,

Ajandam projesi için API dökümantasyon sayfasına hoş geldiniz!

# Dersler

## Tüm Dersleri Getir

```shell
curl "https://spring-kou-service.herokuapp.com/api/lessons"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/lessons"
```

> Yukarıdaki gibi istek yapıldıgında şu şekilde bir JSON dönecektir :

```json
{
    "lessons": [
        {
            "id": 1,
            "name": "Java Programlama",
            "academician": {
                "id": 2,
                "name": "Yrd.Doç.Dr.Burak",
                "surname": "Inner",
                "username": "binner",
                "department": "Makine_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "clock": "10:30",
            "day": "Salı",
            "location": "305"
        },
        {
            "id": 2,
            "name": "Dağıtık Sistemler",
            "academician": {
                "id": 2,
                "name": "Yrd.Doç.Dr.Burak",
                "surname": "Inner",
                "username": "binner",
                "department": "Makine_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "clock": "19:45",
            "day": "Cuma",
            "location": "303"
        },
  ]
} 
```

Bu endpoint veritabanındaki tüm dersleri getirir .

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/lessons`

<aside class="success">
Hatırlatma — Dönen JSON Veritabanındaki tüm dersleri içerir! herhangi bir filtreleme içermez!
</aside>


## Akademisyenin Tüm Derslerin Getir

```shell
curl "https://spring-kou-service.herokuapp.com/api/lessons/{username}/academicianUsername"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/lessons/{username}/academicianUsername"
```


> Yukarıdaki gibi istek yapıldıgında şu şekilde bir JSON dönecektir :

```json
[
    {
        "id": 1,
        "name": "Java Programlama",
        "academician": {
            "id": 3,
            "name": "Doç.Dr.Ahmet",
            "surname": "Sayar",
            "username": "asayar",
            "department": "Bilgisiyar_Mühendisliği",
            "faculty": "Mühendislik"
        },
        "clock": "10:30",
        "day": "Salı",
        "location": "303"
    }
]
```

Bu endpoint veritabanındaki istenen akademisyenin tüm derslerini getirir .

### HTTP Request

`GET ttps://spring-kou-service.herokuapp.com/api/lessons/{username}/academicianUsername`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
username | false | Akademisyenin kullanıcı adı



## Akademisyenin Id'si ile Derslerini Getir

```shell
curl "https://spring-kou-service.herokuapp.com/api/lessons/{id}/academicianId"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/lessons/{id}/academicianId"
```


> Yukarıdaki gibi istek yapıldıgında şu şekilde bir JSON dönecektir :

```json
[
    {
        "id": 1,
        "name": "Java Programlama",
        "academician": {
            "id": 3,
            "name": "Doç.Dr.Ahmet",
            "surname": "Sayar",
            "username": "asayar",
            "department": "Bilgisiyar_Mühendisliği",
            "faculty": "Mühendislik"
        },
        "clock": "10:30",
        "day": "Salı",
        "location": "303"
    }
]
```

Bu endpoint veritabanındaki istenen akademisyenin tüm derslerini getirir .

### HTTP Request

`GET ttps://spring-kou-service.herokuapp.com/api/lessons/{id}/academicianId`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
id | false | Akademisyenin idsi



# Login (Kullanıcı Girişi)

## Öğrenci Kullanıcı girişi

```shell
curl "https://spring-kou-service.herokuapp.com/api/login?username=140202042&password=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/login"
```

> Yukarıdaki gibi istek yapıldıgında eğer kullanıcı bilgileri dogru ise şu şekilde bir JSON dönecektir :

```json
{
    "data": [
        {
            "id": 1,
            "name": "Umut",
            "number": 140202042,
            "surname": "Soysal",
            "macId": "RZ5G54K6GX4SYNF2C"
        }
    ],
    "lessons": [
        {
            "id": 1,
            "name": "Java Programlama",
            "academician": {
                "id": 2,
                "name": "Yrd.Doç.Dr.Burak",
                "surname": "Inner",
                "username": "binner",
                "department": "Makine_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "clock": "10:30",
            "day": "Salı",
            "location": "305"
        },
        {
            "id": 6,
            "name": "Programlama I",
            "academician": {
                "id": 1,
                "name": "Yrd.Doç.Dr.Pınar",
                "surname": "Onay Durdu",
                "username": "ponaydurdu",
                "department": "Endüstri_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "clock": "10:30",
            "day": "Salı",
            "location": "301"
        }
    ]
}
```

Bu endpoint öğrenci bilgileri doğru ise öğrencinin dersleriyle birlikte bilgilerini getirir.

### HTTP Request

`POST https://spring-kou-service.herokuapp.com/api/login?username=140202042&password=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
username | false | Akademisyenin kullanıcı adı  yada öğrencinin numarası
password | false | Akademisyenin yada öğrencinin şifresi



<aside class="success">
Hatırlatma — Dönen JSON akamdesiyen ve öğrenciye göre farklılık gösterir.
</aside>
