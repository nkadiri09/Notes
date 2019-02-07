# SpringBoot-api

## Spring Boot does not compete with Spring or Spring MVC. It makes it easy to use them.

  SpringBoot provide the conviniance over the configuration, Generally spring framework is light weight,
  bit configuration wise it has very huge configuration.

  In springboot it provides the easy of configuration by creating our own project as a child project of the actual springboot
  application and we customize the application.

  Spring Boot aims to make it easy to create Spring-powered, production-grade applications and services with min knoledge. 
  It takes an opinionated view of the Spring platform so that new and existing users can quickly get to the bits they need. 
  You can use it to create stand-alone Java applications that can be started using‘java -jar’ or more traditional WAR 
  deployments. We also provide a command line tool that runs ‘spring scripts’.

  on top of it, Springboot also supports to integrate with the Spring Ecosystem that majorly includes Spring ORM, Spring JDBC,
  Spring Security, Spring Data and many other things

  It tests the web applications easily with the help of different Embedded HTTP servers that includes Tomcat, 
  Jetty and many others.

  It offers Command Line Interface (CLI) tool for developing and testing Spring Boot.
  It offers a number of plugins for developing and testing Spring Boot Applications easily using Maven/Gradle- the build         tools.

### Steps to create Springboot Application.

1. First, let’s use Spring Initializr to generate the base for our project.

          The generated project relies on the Boot parent:

          <parent>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-parent</artifactId>
              <version>2.0.1.RELEASE</version>
              <relativePath />
          </parent>
          
          <-------- Other Dependencies --------->
          
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-web</artifactId>
          </dependency>
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-data-jpa</artifactId> .  <--hibernet/JPA--->
          </dependency>
          <dependency>
              <groupId>com.h2database</groupId>                         <-- H2 Database like Oracle -->
              <artifactId>h2</artifactId>
          </dependency>

 2. Next, we’ll configure a simple main class for our application:
 
         @SpringBootApplication
        public class Application {
            public static void main(String[] args) {
                SpringApplication.run(Application.class, args);
            }
        }
     Notice how we’re using @SpringBootApplication as our primary application configuration class; behind the scenes, that’s        equivalent to @Configuration, @EnableAutoConfiguration, and @ComponentScan together
     
     Finally, we’ll define a simple application.properties file
     
     #### server.port=8081
     
     #### server.port changes the server port from the default 8080 to 8081; there are of course many more Spring Boot properties available.


3. Next, let’s have a look at a web tier – and we’ll start that by setting up a simple controller – the BookController.
We’ll implement basic CRUD operations exposing Book resources with some simple validation:

        @RestController
        @RequestMapping("/api/books")
        public class BookController {

            @Autowired
            private BookRepository bookRepository;

            @GetMapping
            public Iterable findAll() {
                return bookRepository.findAll();
            }

            @GetMapping("/{id}")
            public Book findOne(@PathVariable Long id) {
                return bookRepository.findById(id)
                  .orElseThrow(BookNotFoundException::new);
            }
        }
 
 
 
