## Pengenalan REST
REST (Representational State Transfer) dikenalkan dan didefinisikan pada tahun 2000 oleh Roy Fielding pada saat disertasi doktoralnya. REST merupakan suatu gaya arsitektur untuk mendesain sistem terdistribusi.

## Prinsip REST
- __Resources__, mengekspos struktur direktori URI yang mudah dipahami
  - Suatu resource mempunyai URI (Uniform Resource Identifier)
  - Suatu resrouce dapat memiliki representasi yang berbeda: XML, HTML atau JSON. Umumnya JSON digunakan untuk REST.
- __Representations__, mengirimkan JSON atau XML untuk merepresentasikan objek data dan atribut
- __Messages__, menggunakan method HTTP (HyperText Transfer Protocol) seperti GET, POST, PUT dan DELETE
- __Stateless__, tidak ada session yang disimpan di server, session disimpan oleh client.

## HTTP methods
Menggunakan method HTTP untuk memapingkan operasi CRUD(Create, Retrieve, Update, Delete) ke request HTTP

Method | Deskripsi | URI
------------ | ------------- | -------------
GET | Digunakan untuk mendapatkan suatu informasi | GET /addresses/1
POST | Digunakan untuk membuat resource baru | POST /addresses
PUT | Digunakan untuk mengupdate resource yang sudah ada. Pada saat proses update, jika hanya beberapa elemen data yang tersedia maka sisa elemen data yang tidak ada akan diupdate null | PUT /addresses/1
PATCH | Digunakan untuk mengupdate spesifik elemen data pada suatu resource | PATCH /addresses/1
DELETE | Digunakan untuk menghapus resource | DELETE /addresses/1

## Status Kode HTTP
Status kode HTTP menunjukkan hasil atau respon dari suatu request HTTP.

Kode | Deskripsi
------------ | -------------
1XX | Informasi
2XX | Sukses
3XX | Redirection
4XX | Error pada klien
5XX | Error pada server

## Media Type
__Accept__ dan __Content-Type__ pada HTTP header digunakan untuk menggambarkan konten yang sedang dikirimkan atau direquest didalam  HTTP request. Klien harus mengatur Accept menjadi "application/json", jika klien merequest respon dalam bentuk JSON. sebaliknya, ketika mengirimkan data pada saat melakukan request, klien harus mengatur Content-Type menjadi "application/xml" jika klien mengirimkan data dalam bentuk XML.

## Dokumentasi Service Definition
Tools yang digunakan untuk dokumentasi service definition adalah
- WADL (Web Application Definition Language)
- Swagger
