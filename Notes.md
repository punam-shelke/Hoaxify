# Learning notes while building the application

## Integration Test for User

- Controller test uses spring context. To achieve that we need  
`
@RunWith(SpringRunner.class)  
`


- For integration testing we need web application running.
  - `@SpringBootTest(webEnvironment = RANDOM_PORT)`
Will initializing application for test environment(Web server will be started)  
  - By default, web server gets initialised on port 8080. Here we are initialising it on random port


- Spring gives us flexibility to run applications in different profiles. We can achieve configurable runtime behaviour through it.
To achieve it we use 
`@ActiveProfiles("test")`


- `@Data` annotation of Lombok creates getters, setters, equals ,and hashcode method for model

- :bulb: ⌘ + F12 will open class outline

- We need a http client to post request to the backend. For that we need TestRestTemplate

- When we run spring-boot test, spring will create `application context`.  
  - That context will contain an instance of `TestRestTemplate`.  
  - We can `@Autowire` the `testRestTemplate` and use it.  
 

- To tell class to be responsible about http requests, we need `@RestController`

- Repository should be an interface for database access layer.
  - one repository will be responsible for handling one entity and respective table for that entity in a database.
  - we don't need to specify `@Repository` annotation for repositories.
  - spring will automatically search for interfaces extending JPARepository


- `@Entity` maps object to a database table
    - If a class is entity then we have to give it an id using `@Id`
    - to automate the generation of that id we use `@GeneratedValue`
  
### Responsibilities
- Controller
  - http request response generation
  - gathering data from incoming request and passing them to business logic and responding back accordingly.
  - Parsing and response generation


- Service
  - business logic


- Repository
  - data access layer operation


-`@Service` annotation is used in service classes.
  - with this annotation we are telling spring to initialise this class.
  - we should use A constructor injection which is easy to test


- :bulb: **constructor injection does not need `@Autowired` annotation**


- at controller level we can use field injection
  - `@RequestBody` tells that we want request body of incoming message and also we define what type of object we are waiting for.
  - Spring will take incoming json and convert into user object.
```
eg. @RequestBody User user
```
- for these conversions spring is using jackson library.

### TDD
- Generally tests run randomly. We can fix the order if we want with @FixedMethodOrder(MethodSorters.<way-of-sorting>)
```
eg. @FixedMethodOrder(MethodSorters.NAME_ASCENDING)
```
- In TDD each test must run in controlled environment **i.e.** it must start in a non state and return everything to original after test is completed.
so the next test will not be affected by the changed data.


- :bulb: `⌘ + ⇧ + V` gives option to paste from history

- to get the response from the endpoint we can use ``response.getbody()`` method.