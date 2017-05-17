## Membuat Projek Maven

Langkah-langkah membuat projek maven di Eclipse atau Spring Tool Suite (STS):
1. Klik File > New > Maven Project
2. Centang "Create a simple project (skip archetype selection)"
3. Isi Group Id: "com.mayora.web"
4. Isi Artifact Id: "sample-project".
   
   Semua projek Maven memiliki Group Id dan Artifact Id.  Group Id + Artifact Id = Nama Projek.
5. Biarkan Version: "0.0.1-SNAPSHOT" dan packaging: "jar". 
   
   SNAPSHOT menunjukkan bahwa projek sedang dalam fase development.
6. Klik Finish

#### Struktur Projek
src/main/java = source code java

src/test/java = source code junit java

#### Dependency
Semua eksternal jar/library yang berhubungan dengan projek

#### Cara manual mengatur dependency
Download jar secara manual dan letakkan di dalam projek

#### Maven
Build tool yang dapat digunakan untuk mengatur dependency (dependency management) dengan cara mendownload jar yang berhubungan dengan projek secara otomatis.

pom.xml = Project Object Model, File konfigurasi untuk projek Maven, yang medefinisikan semua dependency (eksternal jar/library) yang terkait dengan projek.
``` java
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mayora.web</groupId>
  <artifactId>sample-project</artifactId>
  <version>0.0.1-SNAPSHOT</version>
</project>
```

## Menambahkan Dependency ke Maven
Cari dependency yang akan ditambahkan di Maven repository, misal spring-core:
``` java
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-core</artifactId>
    <version>4.3.8.RELEASE</version>
</dependency>
```

Tambahkan dependency tersebut ke dalam pom.xml
``` java
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mayora.web</groupId>
  <artifactId>sample-project</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  
  <dependencies>
    
    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-core</artifactId>
      <version>4.3.8.RELEASE</version>
    </dependency>
    
  </dependencies>
</project>
```
 Maven akan mendownload dan meletakkan spring-core di CLASSPATH sehingga dependency tersebut dapat digunakan didalam projek. Dapat dilihat pada "Maven Dependencies" di Project Explorer, semua file jar yang terdownload akan muncul disana.
 
 #### Transitive Dependency
 Dependency dari suatu dependency (Transitive dependency). Jika suatu dependency (A) bergantung pada dependency (B) lain maka dependency (B) akan terdownload juga secara otomatis.

 ## 5 Langkah Membuat Projek Spring Boot
 1. Tambahkan Spring Boot Starter Parent dependency
    Spring Boot Starter Parent akan mengurus versi dari semua dependency Spring.
    ``` xml
    <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>1.5.3.RELEASE</version>
    </parent>
    ```
    
 2. Tambahkan Spring Boot Starter Web dependency
    Spring Boot Starter Web akan mengurus semua dependency Spring untuk pengembangan aplikasi web.
    ``` xml
    <dependencies>
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-web</artifactId>
      </dependency>
    </dependencies>
    ```
    
 3. Override Java Version 8
    ``` xml
    <properties>
  	   <java.version>1.8</java.version>
    </properties>
    ```
    
 4. Tambahkan Spring Boot Maven Plugin
    Spring Boot Maven Plugin digunakan untuk membuat aplikasi jar/war dan menjalankan aplikasi Spring Boot.
    ``` xml
    <build>
      <plugins>
         <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
         </plugin>
      </plugins>
    </build>
    ```
    
 5. Buat Launcher untuk Spring Boot Application
    @SpringBootApplication sama dengan mendeklarasikan @Configuration, @EnableAutoConfiguration, @ComponentScan secara bersamaan dengan default atribut
 
    #### Application.java
    ``` java
    import org.springframework.boot.SpringApplication;
    import org.springframework.boot.autoconfigure.SpringBootApplication;
    import org.springframework.context.ApplicationContext;

    @SpringBootApplication
    public class Application {
      
      public static void main(String[] args){
		   ApplicationContext ctx = SpringApplication.run(Application.class, args);
	   }
      
    }
    ```

## pom.xml Lengkap
``` xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.project.web</groupId>
  <artifactId>sample-project</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  
  <properties>
  	<java.version>1.8</java.version>
  </properties> 
  
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.3.RELEASE</version>
  </parent>
  
  <dependencies>
    <dependency>
	  <groupId>org.springframework.boot</groupId>
	  <artifactId>spring-boot-starter-web</artifactId>
	</dependency>
  </dependencies>
  
  <build>
    <plugins>
      <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
      </plugin>
    </plugins>
  </build>
  
</project>
```
