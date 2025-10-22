Spring 공부 노트
=================

#1. 개념
-----

> 컨테이너(Container) : 객체(Bean)를 생성·관리·소멸시키는 주체로, 프로그램 실행 중 객체의 생명주기를 대신 관리하는 공간.

> IoC (Inversion of Control, 제어의 역전) : 객체의 생성과 의존성 관리의 제어권을 개발자가 아닌 스프링 컨테이너에게 위임하는 개념
- → 즉, 객체를 new로 직접 만들지 않고 스프링이 대신 생성하고 주입

> DI (Dependency Injection, 의존성 주입) : 객체 간의 의존 관계를 코드 내부에서 직접 연결하지 않고, 외부(컨테이너)가 주입해주는 방식
- → IoC를 구현하는 구체적인 방법이며, IoC의 하위 개념
  - ex) @Autowired

> Bean : 스프링 컨테이너에 의해 관리되는 객체(인스턴스)
- → @Component, @Service, @Repository, @Controller 등의 어노테이션이나 @Bean 메서드로 등록됨

> BeanFactory : 가장 기본적인 IoC 컨테이너로, Bean의 생성·조회·관리만 담당하는 단순한 객체 공장.

> Spring Container : Bean을 생성, 관리, 소멸시키는 역할을 하는 IoC 엔진
- → 대표 구현체는 BeanFactory 와 ApplicationContext

> ApplicationContext : BeanFactory의 확장판으로, Bean 관리 + 환경 설정, 메시지 처리, 이벤트 발행, AOP 지원 등을 함께 제공하는 스프링의 핵심 컨테이너

> AOP (Aspect Oriented Programming, 관점 지향 프로그래밍) : 핵심 로직(Core Concern) 과 공통 로직(Cross-cutting Concern) 을 분리하여, 공통 기능을 횡단 관심사(Aspect) 로 관리하는 방식
- → 예: 로깅, 트랜잭션, 보안 처리 등

> POJO (Plain Old Java Object) : 스프링이 관리하는 Bean의 기본 형태로, 특정 프레임워크에 종속되지 않은 순수 자바 객체
- → 스프링은 POJO에 IoC, DI, AOP를 적용해 유연한 구조를 제공함




#2. @Annotations
------------------

@ConfigurationProperties(prefix = "app")
- application.properties / application.yml 또는 환경 변수 등에서 특정 접두사(prefix)를 가진 설정 값을 자바 빈(POJO)에 바인딩(맵핑)해 주는 어노테이션

@ComponetScan(basePackages = {"com.example.service", "com.example.batch"})
- basePackages와 그 하위 패키지 전체를 스캔해서 "컴포넌트 후보"로 판단되는 클래스들은 전부 스프링 빈으로 등록 
