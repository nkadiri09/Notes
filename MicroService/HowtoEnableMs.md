## How to Enable MicroServices in Spring Boot aapplication.

Link: https://spring.io/blog/2015/07/14/microservices-with-spring

### Microservices allow large systems to be built up from a number of collaborating components. It does at the process level what Spring has always done at the component level: loosely coupled processes instead of loosely coupled components.

For example imagine an online shop with separate microservices for user-accounts, product-catalog order-processing and shopping carts:

Service Registration
When you have multiple processes working together they need to find each other. If you have ever used Java’s RMI mechanism you may recall that it relied on a central registry so that RMI processes could find each other. Microservices has the same requirement.

The developers at Netflix had this problem when building their systems and created a registration server called Eureka (“I have found it” in Greek). Fortunately for us, they made their discovery server open-source and Spring has incorporated into Spring Cloud, making it even easier to run up a Eureka server. Here is the complete discovery-server application:

		@SpringBootApplication
		@EnableEurekaServer
		public class ServiceRegistrationServer {

		  public static void main(String[] args) {
			// Tell Boot to look for registration-server.yml
			System.setProperty("spring.config.name", "registration-server");
			SpringApplication.run(ServiceRegistrationServer.class, args);
		  }
		}
		
Spring Cloud is built on Spring Boot and utilizes parent and starter POMs. The important parts of the POM are:

			<parent>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-starter-parent</artifactId>
				<version>_Brixton_.RELEASE</version>  <!-- Name of release train -->
			</parent>
			<dependencies>
				<dependency>
					<!-- Setup Spring Boot -->
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-starter</artifactId>
				</dependency>

				<dependency>
					<!-- Setup Spring MVC & REST, use Embedded Tomcat -->
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-starter-web</artifactId>
				</dependency>

				<dependency>
					<!-- Spring Cloud starter -->
					<groupId>org.springframework.cloud</groupId>
					<artifactId>spring-cloud-starter</artifactId>
				</dependency>

				<dependency>
					<!-- Eureka for service registration -->
					<groupId>org.springframework.cloud</groupId>
					<artifactId>spring-cloud-starter-eureka-server</artifactId>
				</dependency>
			</dependencies>
			
#### By default Spring Boot applications look for an application.properties or application.yml file for configuration. By setting the spring.config.name property we can tell Spring Boot to look for a different file - useful if you have multiple Spring Boot applications in the same project - as I will do shortly.

