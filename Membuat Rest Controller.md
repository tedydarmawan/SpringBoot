## Membuat Rest Controller

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
