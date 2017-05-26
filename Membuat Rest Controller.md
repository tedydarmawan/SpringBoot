## Membuat Rest Controller

@GetMapping
@PathVariable

@RequestParam

JSONView Chrome



#### WelcomeController.java
``` java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class WelcomeController {
	
	//Dependency Injection
	@Autowired
	private WelcomeService service;
	
	@RequestMapping("/welcome")
	public String welcome(){
		return service.retrieveWelcomeMessage();
	}
	
}

//Spring will manage this bean and create an instance of this bean
@Component
class WelcomeService{
	public String retrieveWelcomeMessage(){
		return "Selamat Datang lagi";
	}
}
```

## Konfigurasi Eksternal application.properties
Spring bisa menggunakan konfigurasi eksternal dengan menggunakan application.properties. Berikut ini contoh konfigurasi eksternal untuk mengaktifkan mode DEBUG di Spring.

#### /src/main/resources/application.properties
``` java
logging.level.org.springframework: DEBUG
```

## Spring Developer Tools
Pada saat proses pengembangan aplikasi, setiap kali ada perubahan kode maka aplikasi Spring Boot yang sedang berjalan harus dihentikan terlebih dahulu kemudian dijalankan kembali secara manual (restart manual). Dengan adanya Spring Developer Tools dapat membantu developer untuk mempersingkat proses restart manual tadi sehingga ketika ada perubahan kode aplikasi Spring Boot otomatis akan melakukan restart agar perubahan kode tersebut masuk ke dalam aplikasi yang sedang berjalan. Untuk itu maka diperlukan untuk menambahkan dependency Spring Developer Tools ke dalam projek Java.

``` xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-devtools</artifactId>
  <optional>true</optional>
</dependency>
```
