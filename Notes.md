# Learning notes while building the application

## Integration Test for User

- Controller test uses spring context. To achieve that we need  
`
@RunWith(SpringRunner.class)  
`


- For integration testing we need web application running
- `@SpringBootTest(webEnvironment = RANDOM_PORT)`
Will initializing application for test environment(Web server will be started)  
- By default, web server gets initialised on port 8080. Here we are initialising it on random port


- Spring gives us flexibility to run applications in different profiles. We can achieve configurable runtime behaviour through it.
To achieve it we use 
`@ActiveProfiles("test")`


- `@Data` annotation of Lombok creates getters, setters, equals ,and hashcode method for model

:bulb: ⌘ + F12 will open class outline

- We need a http client to post request to the backend. For that we need TestRestTemplate

- When we run spring-boot test, spring will create `application context`.  
- That context will contain an instance of `TestRestTemplate`.  
- We can `@Autowire` the `testRestTemplate` and use it.  
 

- To tell class to be responsible about http requests we need `@RestController`
Parsing and response generation