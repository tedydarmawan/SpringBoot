## Membuat Rest Controller
Dependency Injection = Spring akan mengatur dependency suatu objek dengan membuat suatu instance dari dependency objek tersebut

Bean = Objek yang dibuat dan diatur oleh Spring IoC Container

@Component, @Service, @Repository = Anotasi ini digunakan agar Spring dapat membuat bean dari kelas yang memiliki anotasi ini

@Autowired = Digunakan untuk melakukan inject suatu bean pada objek yang memiliki dependency.

@RestController = Digunakan untuk membuat bean dari suatu kelas dan menandakan bahwa kelas tersebut adalah controller REST

@RequestMapping = Anotasi ini digunakan untuk melakukan mapping url dengan method


## WelcomeController.java
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
