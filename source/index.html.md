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


# Yoklama

## Yoklama kaydet (Ben burdayım) (Öğrenci)

```shell
curl "https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1&beaconId=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1&beaconId=1"
```

> Yukarıdaki gibi istek yapıldıgında eğer yoklama bilgisi başarıyla kaydedilirse aşagıdaki gibi cevap dönülür :

```text
true
```

Bu endpoint öğrencinin aldıgı derse katıldıgı bilgisini servera gönderir.

### HTTP Request

`POST https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1&beaconId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
studentId | false | Öğrencinin id'si
lessonId | false | Dersin id'si
beaconId | false | Beacon'ın id'si


## Devam bilgilerini göster (Öğrenci)

```shell
curl " https://spring-kou-service.herokuapp.com/api/rollcall/RollCallInfo?studentId=1"
```

```java
curl " https://spring-kou-service.herokuapp.com/api/rollcall/RollCallInfo?studentId=1"
```

> Yukarıdaki gibi istek yapıldıgında öğrencinin hangi derste ne kadar devam bilgisi oldugu döner.

```json

{
    "devam_bilgileri": [
        {
            "dersAdi": "Linux Ağ Yönetimi",
            "devamBilgisi": 0,
            "devamsizlikBilgisi": 17
        },
        {
            "dersAdi": "Dağıtık Sistemler",
            "devamBilgisi": 1,
            "devamsizlikBilgisi": 16
        },
        {
            "dersAdi": "Java Programlama",
            "devamBilgisi": 3,
            "devamsizlikBilgisi": 14
        },
        {
            "dersAdi": "Kontrol Sistemleri",
            "devamBilgisi": 0,
            "devamsizlikBilgisi": 17
        }
    ]
}

```

Bu endpoint öğrencinin aldıgı derslere katılım bilgisini gösterir

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/rollcall/RollCallInfo?studentId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
studentId | false | Öğrencinin id'si
lessonId | false | Dersin id'si

## Ders özelinde Devam Bilgisi göster (Öğrenci)

```shell
curl " https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1"
```

```java
curl " https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1"
```

> Yukarıdaki gibi istek yapıldıgında öğrencinin ilgili dersin idsi ile devam bilgisi döner

```json

{
    "devamlilik_sayisi": [
        3
    ],
    "yoklama": [
        {
            "id": 2,
            "beaconId": "AZ1231CVDFG",
            "student": {
                "id": 1,
                "name": "Umut",
                "number": 140202042,
                "surname": "Soysal",
                "macId": "RZ5G54K6GX4SYNF2C"
            },
            "lesson": {
                "id": 1,
                "name": "Java Programlama",
                "clock": "13:30",
                "day": "Çarşamba",
                "location": "Amfi-B"
            }
        },
        {
            "id": 8,
            "beaconId": "AZ1231CVDFG",
            "student": {
                "id": 1,
                "name": "Umut",
                "number": 140202042,
                "surname": "Soysal",
                "macId": "RZ5G54K6GX4SYNF2C"
            },
            "lesson": {
                "id": 1,
                "name": "Java Programlama",
                "clock": "13:30",
                "day": "Çarşamba",
                "location": "Amfi-B"
            }
        },
        {
            "id": 10,
            "beaconId": "1",
            "student": {
                "id": 1,
                "name": "Umut",
                "number": 140202042,
                "surname": "Soysal",
                "macId": "RZ5G54K6GX4SYNF2C"
            },
            "lesson": {
                "id": 1,
                "name": "Java Programlama",
                "clock": "13:30",
                "day": "Çarşamba",
                "location": "Amfi-B"
            }
        }
    ]
}

```

Bu endpoint öğrencinin aldıgı ilgili derse katılım bilgisini gösterir

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/rollcall?studentId=1&lessonId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
studentId | false | Öğrencinin id'si
lessonId | false | Dersin id'si



## Dersi alan ögrencileri devam biligleri ile getirir

```shell
curl "https://spring-kou-service.herokuapp.com/api/lesson/rollcall?lessonId=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/lesson/rollcall?lessonId=1"
```

> Yukarıdaki gibi istek yapıldıgında öğrencinin ilgili dersin idsi ile devam bilgisi döner

```json
{
    "ogrenci_devam_bilgileri": [
        {
            "ogrenci": {
                "id": 3,
                "name": "İsmail",
                "number": 140202042,
                "surname": "Reşat",
                "macId": "5Y7VRV54MUFS9NHXQ"
            },
            "devamsizlik": {
                "dersAdi": "Java Programlama",
                "devamBilgisi": 2,
                "devamsizlikBilgisi": 12
            }
        },
        {
            "ogrenci": {
                "id": 2,
                "name": "Ramazan",
                "number": 140202092,
                "surname": "Demir",
                "macId": "HG95QJ2J862FJKVE5"
            },
            "devamsizlik": {
                "dersAdi": "Java Programlama",
                "devamBilgisi": 2,
                "devamsizlikBilgisi": 12
            }
        },
        {
            "ogrenci": {
                "id": 1,
                "name": "Umut",
                "number": 140202040,
                "surname": "Soysal",
                "macId": "RZ5G54K6GX4SYNF2C"
            },
            "devamsizlik": {
                "dersAdi": "Java Programlama",
                "devamBilgisi": 2,
                "devamsizlikBilgisi": 12
            }
        }
    ]
}

```

Bu endpoint hangi öğrencinin ne kadar  derse katılım bilgisini oldugunu gösterir

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/rollcall?lessonId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
lessonId | false | Dersin id'si

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

`GET https://spring-kou-service.herokuapp.com/api/lessons/{username}/academicianUsername`

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

`GET https://spring-kou-service.herokuapp.com/api/lessons/{id}/academicianId`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
id | false | Akademisyenin idsi



## Öğrenciyi Derse Kaydet 

```shell
curl "https://spring-kou-service.herokuapp.com/api/lesson/saveStudent?lessonId=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/lesson/saveStudent?lessonId=1"
```


> Yukarıdaki gibi istek yapıldıgında şu şekilde bir JSON dönecektir :

```text
true
```

Bu endpoint öğrenciyi derse kaydeder

### HTTP Request

`POST https://spring-kou-service.herokuapp.com/api/lesson/saveStudent?lessonId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
lessonId | false | Ders id

Post atarken json olarak öğrencinin bilgilerini post etme

{"number":"140202014","name":"Sevgi","surname":"Demir"}


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

# Duyuru

## Duyuru Gönder (Akademisyen)

```shell
curl -H "Content-Type: application/json" -X POST 
-d 
'{ 
"title": "Duyuru Başlığı 1 ",
"content": "Duyuru içeriği 1 2 3 ",
"academician" : {
		"id" : "2"
	},
	"lesson" : {
		"id" : "6"
	}
}
' "https://spring-kou-service.herokuapp.com/api/announcement"

```

```java
```

> Yukarıdaki gibi istek yapıldıgında verilen academisyenin verilen dersi için duyuru atılır.

```text
true
```

Bu endpoint akademisyenin istediği derse duyuru atmasını sağlar

### HTTP Request

`POST https://spring-kou-service.herokuapp.com/api/announcement`



<aside class="warning">
Hatırlatma — Duyuru bilgileri  yanda belirtilen json formatında request body'e eklenerek post edilmelidir!
</aside>


## Duyuru listele (Akademisyen)

```shell
curl "https://spring-kou-service.herokuapp.com/api/announcement/academician?academicianId=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/announcement/academician?academicianId=1"
```

> Yukarıdaki gibi istek yapıldıgında eğer kullanıcı bilgileri dogru ise şu şekilde bir JSON dönecektir :

```json
{
    "duyurular": [
        {
            "id": 14,
            "title": "Deneme hoca id 1 ",
            "content": "Deneme ders asdsadadaadssda 1 imiş var ben",
            "date": "2018-03-16",
            "academician": {
                "id": 2,
                "name": "Yrd.Doç.Dr.Burak",
                "surname": "Inner",
                "username": "binner",
                "department": "Makine_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "lesson": {
                "id": 6,
                "name": "Programlama I",
                "clock": "10:30",
                "day": "Salı",
                "location": "301"
            }
        },
        {
            "id": 7,
            "title": "Programlama I QH8dwtxRK65g",
            "content": "Programlama I Dersi için açıklama GejUTlbhA7xIytmROfxffvGClCvRxxHTRAxx8FkAuE",
            "date": "2018-03-16",
            "academician": {
                "id": 1,
                "name": "Yrd.Doç.Dr.Pınar",
                "surname": "Onay Durdu",
                "username": "ponaydurdu",
                "department": "Endüstri_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "lesson": {
                "id": 6,
                "name": "Programlama I",
                "clock": "10:30",
                "day": "Salı",
                "location": "301"
            }
        }
    ]
}
```

Bu endpoint akademisyenin attıgı duyuruları verir.

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/announcement/academician?academicianId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
academicianId | false | Akademisyenin id'si

## Duyuru listele (Öğrenci)

```shell
curl "https://spring-kou-service.herokuapp.com/api/announcement/student?studentId=1"
```

```java
curl "https://spring-kou-service.herokuapp.com/api/announcement/student?studentId=1"
```

> Yukarıdaki gibi istek yapıldıgında eğer kullanıcı bilgileri dogru ise şu şekilde bir JSON dönecektir :

```json
{
    "duyurular": [
        {
            "id": 14,
            "title": "Deneme hoca id 1 ",
            "content": "Deneme ders asdsadadaadssda 1 imiş var ben",
            "date": "2018-03-16",
            "academician": {
                "id": 2,
                "name": "Yrd.Doç.Dr.Burak",
                "surname": "Inner",
                "username": "binner",
                "department": "Makine_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "lesson": {
                "id": 6,
                "name": "Programlama I",
                "clock": "10:30",
                "day": "Salı",
                "location": "301"
            }
        },
        {
            "id": 7,
            "title": "Programlama I QH8dwtxRK65g",
            "content": "Programlama I Dersi için açıklama GejUTlbhA7xIytmROfxffvGClCvRxxHTRAxx8FkAuE",
            "date": "2018-03-16",
            "academician": {
                "id": 1,
                "name": "Yrd.Doç.Dr.Pınar",
                "surname": "Onay Durdu",
                "username": "ponaydurdu",
                "department": "Endüstri_Mühendisliği",
                "faculty": "Mühendislik"
            },
            "lesson": {
                "id": 6,
                "name": "Programlama I",
                "clock": "10:30",
                "day": "Salı",
                "location": "301"
            }
        }
    ]
}
```

Bu endpoint öğrencinin aldıgı derslere attılan duyuruları listeler.

### HTTP Request

`GET https://spring-kou-service.herokuapp.com/api/announcement/student?studentId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
studentId | false | Akademisyenin id'si

## Duyuru Sil (Akademisyen)

```text
true
```


Bu endpoint akademisyenin attıgı duyuruyu siler.

### HTTP Request

`POST https://spring-kou-service.herokuapp.com/api/announcement/delete?announcementId=1`

### Sorgu Parametreleri

Parametre | Default | Açıklama
--------- | ------- | -----------
announcementId | false | Akademisyenin attıgı duyrunun id'si
