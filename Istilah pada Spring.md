## Daftar Istilah Pada Spring

Istilah | Deskripsi
------------ | -------------
@Autowired | Anotasi yang digunakan untuk melakukan inject instance dari suatu bean ke objek yang memiliki dependency
@Configuration | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas dan menunjukkan bahwa suatu kelas mendeklarasikan satu atau lebih method @bean (kelas konfigurasi).  (Best practice) Kelas yang mendefinisikan method main dapat menjadi kelas @Configuration utama. Tidak semua konfigurasi harus diletakkan dalam 1 kelas, anotasi @Import dapat digunakan untuk mengimport kelas @Configuration tambahan. Cara lain dapat menggunakan @ComponentScan untuk mencari secara otomatis kelas @Configuration.
@Component | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas
@ComponentScan | Anotasi yang digunakan untuk melakukan scan @Component, @Service, @Controller, @RestController, @Repository pada saat aplikasi mulai dijalankan, ketika @Component, @Service, @Controller, @RestController, @Repository ditemukan disinilah proses pembentukan bean terjadi yang nantinya akan digunakan untuk proses dependency injection
@Controller | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas dan menunjukkan kelas tersebut adalah kelas controller
@Repository | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas dan menunjukkan kelas tersebut adalah kelas repository
@RestController | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas dan menunjukkan kelas tersebut adalah kelas rest controller
@RequestMapping | Anotasi yang digunakan untuk melakukan mapping url dengan method
@Service | Anotasi yang digunakan agar Spring container dapat membuat definisi bean dari suatu kelas dan menunjukkan kelas tersebut adalah kelas service
@SpringBootApplication | Anotasi yang digunakan untuk menggantikan deklarasi @Configuration, @EnableAutoConfiguration dan @ComponentScan secara bersamaan dengan menggunakan atribut default dari masing-masing anotasi yang digantikan tadi. Untuk @ComponentScan atribut default untuk package yang discan adalah package yang ada pada kelas yang memiliki anotasi ini
@EnableAutoConfiguration | Anotasi yang digunakan agar Spring dapat melakukan konfigurasi secara otomatis berdasarkan dependency jar yang ditambahkan. (Best practice) Dalam satu projek Spring, anotasi @EnableAutoConfiguration hanya boleh digunakan satu kali dan biasanya ditambahkan hanya di kelas @Configuration utama.
Bean | Objek yang dibuat dan diatur oleh Spring IoC Container
Dispatcher Servlet atau Front Controller | Program yang digunakan untuk mengatur alur kerja pemrosesan request web pada Spring
IoC (Inverse of Control) atau Dependency Injection | Spring akan mengatur dependency suatu objek dengan membuat suatu instance atas dependency objek tersebut
Runtime | Waktu pada saat program mulai dijalankan pada komputer (tahap compile)
Servlet | Program kecil pada web server Java yang akan berjalan secara otomatis sebagai bentuk respon dari inputan user
