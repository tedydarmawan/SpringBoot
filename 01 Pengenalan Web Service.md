# Outline
- Apa itu Web Service?
- Pertanyaan-Pertanyaan Penting Terkait Web Service
- Web Service - Key Terminology
- Pengenalan RESTful Web Service

# Apa itu Web Service?
> Software system designed to support interoperable machine-to-machine interaction over a network. - W3C (World Wide Web Consortium)

Berdasarkan pengertian dari W3C, web service adalah sistem perangkat lunak yang didesain untuk pertukaran dan pemanfaatan informasi dari interaksi mesin-ke-mesin melalui suatu jaringan.

3 Karakteristik dari Web Service:
- Didesain untuk interaksi mesin-ke-mesin (atau aplikasi-ke-aplikasi)
- Harus dapat bertukar dan memanfaatkan informasi, tidak bergantung pada suatu teknologi  
- Harus dapat berkomunikasi melalui jaringan

Contoh Web Service : SOAP dan RESTful

# Pertanyaan-Pertanyaan Penting Terkait Web Service
## Bagaimana pertukaran data diantara aplikasi berlangsung?
- Input ke web service disebut Request.
- Output dari web service disebut Response.

Jika suatu aplikasi membutuhkan suatu data dari web service maka aplikasi tersebut akan melakukan request ke web service kemudian web service akan memproses request tersebut dan memberikan output atau response berupa data yang dibutuhkan oleh aplikasi tersebut.

## Bagaimana membuat web service tidak bergantung pada teknologi tertentu (platform independent)?
Dengan menggunakan format pertukaran data baik pada Request ataupun Response.

Format data yang dapat digunakan untuk request dan response adalah
- XML (eXtensible Markup Language)
``` xml
<getDetailCustomer>
  <id>100001</id>
</getDetailCustomer>
```

- JSON (JavaScript Object Notation)
``` json
[
  {
    "id": 100001,
    "name": "Toko Mandiri"
  },
  {
    "id": 100002,
    "name": "Toko Jaya"
  }
]
```

## Bagaimana suatu aplikasi dapat mengetahui format request dan response suatu web service?
Dengan menyediakan service definition:
- Request/Response Format: XML atau JSON
- Struktur Request
- Struktur Response
- Endpoint: Bagaimana cara memanggil suatu service biasanya berupa URL

# Web Service - Key Terminology
- Request dan Response
  - Request adalah input ke web service
  - Response adalah output dari web service
- Format pertukaran data
  - XML dan JSON merupakan format yang digunakan oleh Request atau Response pada saat pertukaran data atau informasi.
- Service Provider atau Server
  Aplikasi yang menyediakan service yang akan digunakan oleh service consumer atau klien.
- Service Consumer atau Klien
  Aplikasi yang menggunakan service yang disediakan oleh service provider atau server.
- Service Definition
  - Format Request/Response
  - Struktur Request
  - Struktur Response
  - Endpoint, bagaimana cara memanggil suatu service biasanya berupa URL.
- Transport
  - HTTP
  Suatu protokol yang digunakan untuk berkomunikasi melalui internet

## Pengenalan RESTful Web Service
https://github.com/tedydarmawan/SpringBoot/blob/master/Pengenalan%20REST.md




