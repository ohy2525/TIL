@Configuration 
- 설정을 구성한다.

@Bean 
- 스프링 컨테이너에 스프링 빈으로 등록한다.

@Component 
- Bean을 따로 등록하지 않아도 사용할 수 있다.
- 빈 등록을 빈 클래스 자체에 할 수 있음.

@ComponentScan
- @Component, @Service, @Repository, @Controller 어노테이션이 부탁된 클래스들을 자동으로 스캔하여 Bean으로 등록해주는 역할


@Service
- 서비스 레이어, 내부에서 자바 로직을 처리함

@Repository
- 퍼시스턴스 레이어, DB나 파일같은 외부 I/O 작업을 처리함

@Controller
- 프레젠테이션 레이어, 웹 요청과 응답을 처리함

@Autowired

@RequiredArgsConstructor

@Qualifier

@Primary

@PostConstruct

@PreDestroy

@Scope

@Lookup

@Servlet

@WebServlet

@Override