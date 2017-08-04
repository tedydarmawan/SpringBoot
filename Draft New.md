# RESTful Web Services

## Social Media Application
User -> Post

- Memperoleh semua user - GET /users
- Membuat user - POST /users
- Memperoleh spesifik user - Get /users/{id} -> /users/1
- Hapus spesifik user - DELETE /users/{id} -> /users/1

- Memperoleh semua post dari spesifik user - GET users/{id}/posts
- Membuat post untuk spesifik user - POST /users/{id}/posts
- Memperoleh detail dari spesifik post dari spesifik user - GET /users/{id}/posts/{post_id}

## Membuat REST service serderhana dengan mengembalikan suatu String
Buat kelas HelloWorldController.java
``` java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {
	
    @GetMapping(path = "/hello-world")
    public String getHello(){
        return "Hello World";
    }
	
}
```

- @RestController digunakan untuk menandakan bahwa kelas tersebut adalah suatu controller rest.
- @GetMapping digunakan untuk memappingkan method dengan URI dengan menggunakan method HTTP GET sehingga pada saat user mengakses URI tersebut pada browser maka method yang diberikan anotasi @GetMapping tersebut akan dieksekusi.


## Membuat REST service sederhana dengan mengembalikan suatu Bean
Buatlah kelas HelloWorldBean.java
``` java
public class HelloWorldBean {

    private String message;
	
    public HelloWorldBean(String message) {
        this.message = message;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }

    @Override
    public String toString() {
        return "HelloWorldBean [message=" + message + "]";
    }

}
```

Pada kelas HelloWorldController.java, tambahkan method getHelloBean()

``` java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {
	
    @GetMapping(path = "/hello-world")
    public String getHello(){
        return "Hello World";
    }
	
    @GetMapping(path = "/hello-world-bean")
    public HelloWorldBean getHelloBean(){
        return new HelloWorldBean("Hello World");
    }
	
}
```

## Membuat REST service sederhana dengan menggunakan path variable
Pada kelas HelloWorldController.java, tambahkan method getHelloPathVariable()

``` java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloWorldController {
	
    @GetMapping(path = "/hello-world")
    public String getHello(){
        return "Hello World";
    }
	
    @GetMapping(path = "/hello-world-bean")
    public HelloWorldBean getHelloBean(){
        return new HelloWorldBean("Hello World");
    }
    
    @GetMapping(path = "/hello-world/{name}")
    public HelloWorldBean getHelloPathVariable(@PathVariable String name){
        return new HelloWorldBean(String.format("Hello World, %s", name));
    }
	
}
```

## Membuat User Bean dan User Service
Buat kelas User.java
``` java
import java.util.Date;

public class User {
    private Integer id;
    private String name;
    private Date birthDate;

    public User() {
		
    }
	
    public User(Integer id, String name, Date birthDate) {
        this.id = id;
        this.name = name;
        this.birthDate = birthDate;
    }

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public Date getBirthDate() {
        return birthDate;
    }

    public void setBirthDate(Date birthDate) {
        this.birthDate = birthDate;
    }

    @Override
    public String toString() {
        return "User [id=" + id + ", name=" + name + ", birthDate=" + birthDate + "]";
    }

}
```

Buat kelas UserDaoService.java
``` java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

import org.springframework.stereotype.Component;

@Component
public class UserDaoService {
    private static List<User> users = new ArrayList<>();
	
    private static int usersCount = 3;
	
    static{
        users.add(new User(1, "Tedy Darmawan", new Date()));
        users.add(new User(2, "Tri Apriyono", new Date()));
        users.add(new User(3, "Denny Krisbiantoro", new Date()));
    }
	
    public List<User> findAll(){
        return users;
    }
	
    public User save(User user){
        if(user.getId() == null){
            user.setId(++usersCount);
        }
        users.add(user);
        return user;
    }
	
    public User findOne(int id){
        for(User user: users){
            if(user.getId() == id){
                return user;
            }
        }
        return null;
    }
	
}
```
## Implementasi method GET untuk memperoleh data User
Buat kelas UserController.java
``` java
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserController {
	
	@Autowired
	private UserDaoService service;
	
	@GetMapping(path = "/users")
	public List<User> getAllUsers(){
		return service.findAll();
	}
	
	@GetMapping(path = "/users/{id}")
	public User getUser(@PathVariable int id){
		return service.findOne(id);
	}
	
}
```

Untuk mengubah output format tanggal JSON, pada application.properties tambahkan properti berikut ini:
``` properties
spring.jackson.serialization.write-dates-as-timestamps=false
```

//inspect Google Chrome untuk melihat Header dan Response

## Implementasi method POST untuk membuat data User
``` java
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class UserController {
	
	@Autowired
	private UserDaoService service;
	
	@GetMapping(path = "/users")
	public List<User> getAllUsers(){
		return service.findAll();
	}
	
	@GetMapping(path = "/users/{id}")
	public User getUser(@PathVariable int id){
		return service.findOne(id);
	}
	
	@PostMapping("/users")
	public void createUser(@RequestBody User user){
		User savedUser = service.save(user);
	}
	
}
```

Untuk menguji web service dengan method HTTP POST maka perlu menggunakan tools yakni Postman, yang dapat didownload dari http://www.getpostman.com. Postman merupakan rest client yang dapat digunakan untuk menguji aplikasi web service.

Pada Postman,
- Pilih Method HTTP POST
- Masukan URL http://localhost:8080/users
- Masukan Request Body, pada Tab Body, pilih raw dan JSON (application/json)
``` json
{
	"name": "New User",
	"birthDate": "2017-08-04T08:10:35.979+0000"
}
```
- Klik Send

## Implementasi method POST untuk membuat data User dan mengganti kode status HTTP
``` java
package com.mayora.boot;

import java.net.URI;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

@RestController
public class UserController {
	
	@Autowired
	private UserDaoService service;
	
	@GetMapping(path = "/users")
	public List<User> getAllUsers(){
		return service.findAll();
	}
	
	@GetMapping(path = "/users/{id}")
	public User getUser(@PathVariable int id){
		return service.findOne(id);
	}
	
	@PostMapping("/users")
	public ResponseEntity<Object> createUser(@RequestBody User user){
		User savedUser = service.save(user);
		
		URI location = ServletUriComponentsBuilder.fromCurrentRequest()
			.path("/{id}").buildAndExpand(savedUser.getId()).toUri();
		
		return ResponseEntity.created(location).build();
	}
	
}
```

## Implementasi Exception Handling jika resource tidak ditemukan
Buat kelas UserNotFoundException.java
``` java
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.ResponseStatus;

@ResponseStatus(HttpStatus.NOT_FOUND)
public class UserNotFoundException extends RuntimeException {

	public UserNotFoundException(String message) {
		super(message);
	}
	
}
```

Ubah method getUser
``` java
import java.net.URI;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.servlet.support.ServletUriComponentsBuilder;

@RestController
public class UserController {
	
	@Autowired
	private UserDaoService service;
	
	@GetMapping(path = "/users")
	public List<User> getAllUsers(){
		return service.findAll();
	}
	
	@GetMapping(path = "/users/{id}")
	public User getUser(@PathVariable int id){
		User user = service.findOne(id);
		
		if(user == null)
			throw new UserNotFoundException("id-" + id);
		
		return user;
	}
	
	@PostMapping("/users")
	public ResponseEntity<Object> createUser(@RequestBody User user){
		User savedUser = service.save(user);
		
		URI location = ServletUriComponentsBuilder.fromCurrentRequest()
			.path("/{id}").buildAndExpand(savedUser.getId()).toUri();
		
		return ResponseEntity.created(location).build();
	}
	
}

