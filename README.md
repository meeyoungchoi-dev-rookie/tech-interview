# tech-interview
면접때 받았던 기술관련 질문 정리
    

- dto 와 repository 차이
    dto는 계층간 데이터 교환을 위해 사용하는 객체
    
    클라이언트 요청에 포함된 데이터를 담아 서버에 전달하고 서버의 응답 데이터를 담아 클라이언트에 전달하기 위해 사용하는 객체
    
    
    repository는 
    
    데이터베이스에 CRUD 명령을 실행할 수 있게 만드는 인터페이스
    
    인터페이스를 사용하면 복잡한 절차없이 CRUD 명형을 데이터베이스에 전달하여 원하는 쿼리를 실행할 수 있다
    
    
    

- JPA와 mybatis 차이
    
    mybatis:  자바에서 SQL Mapper를 지원해주는 프레임워크
    
    SQL을 직접 작성하여 쿼리 수행 결과를 객체와 매핑해 준다
    
    JPA: 자바 ORM기술의 표준
    
    CRUD 메서드를 기본으로 제공해 준다
    
    쿼리를 만들지 않아도 되며 객체 중심으로 개발이 가능하다
    
    하지만 복잡한 쿼리는 해결이 어려운 단점이 있다
    
    

- JPA와 mybatis의 장단점
    
    JPA 장점
    
    - 기본적인 CRUD 메서드를 제공해주기 때문에 비즈니스 로직에 집중할 수 있다
    - 쿼리를 직접 작성할 필요없이 메서드 호출하여 사용할 수 있다
    
    JPA 단점
    
    - 단방향 , 양방향 , 임베디드 관계등 공부할 내용이 많다
    - 연관관계에 대한 이해 없이 코딩하게 되면 성능 문제를 일으킬 수 있다
    
    MyBatis 장점
    
    - SQL 쿼리를 그대로 사용하기 때문에 JOIN과 같이 복잡한 쿼리를 편하게 작성할 수 있다
    - SQL 쿼리의 세부 내용을 수월하게 변경할 수 있다
    - 동적 쿼리를 JPA 보다 간편하게 구현할 수 있다
    
    MyBatis 단점

    - 스키마 변경시 SQL 쿼리를 직접 수정해주어야 한다.
    
    - 반복된 쿼리가 발생하여 반복 작업이 있다.
    
    - 런타임시에 오류를 확인할 수 있다.
    
    - 쿼리를 직접 작성하기 때문에 데이터베이스에 종속된 쿼리문이 발생할 수 있다. 
    - 데이터베이스 변경시 로직도 함께 수정해주어야 한다.
    
    
     spring DI가 무엇인지
    
    - Dependency Injection
    
    - 의존관계 주입을 의미한다
    
    - spring을 사용하기 전에는 개발자가 직접 생성자 , 세터 등을 사용하여 필요한 객체를 주입해 줬다
    
    - spring을 사용하면 spring 컨테이너가 객체를 생성하여 타입에 맞는 객체를 자동으로 주입해준다