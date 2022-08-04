
## spring security란
+ 스플이 기반 애플리케이션의 보안(인증과 권한)을 담당하는 프레임워크
+ 세션과 쿠키 방식으로 인증을 진행

## spring security 처리과정
1. 사용자가 로그인 정보와 함께 인증 요청을 한다.(Http Request)
2.  AuthenticationFilter가 요청을 가로채고, 가로챈 정보를 통해 UsernamePasswordAuthenticationToken의 인증용 객체를 생성한다.

3.AuthenticationManager의 구현체인 ProviderManager에게 생성한 UsernamePasswordToken 객체를 전달한다. 
4. AuthenticationManager는 등록된 AuthenticationProvider(들)을 조회하여 인증을 요구한다. 
5.실제 DB에서 사용자 인증정보를 가져오는 UserDetailsService에 사용자 정보를 넘겨준다. 
6. 넘겨받은 사용자 정보를 통해 DB에서 찾은 사용자 정보인 UserDetails 객체를 만든다
7. AuthenticationProvider(들)은 UserDetails를 넘겨받고 사용자 정보를 비교한다. 
8. 인증이 완료되면 권한 등의 사용자 정보를 담은 Authentication 객체를 반환 
9. 다시 최초의 AuthenticationFilter에 Authentication 객체가 반환된다. 
10. Authenticaton 객체를 SecurityContext에 저장한다.


## 인증 구현을 위해 Spring Security를 사용한 이유
+ 공식문서에서 기본적인 인증과 권한 부여 기능을 제공하기 때문
+ Filter를 통해 인증을 구현하고 싶어 사용

## 인증을 위해 어떻게 Spring Security를 사용했는가
+ Firebase 인증 관련 모듈을 초기화 해주기 위한 FirebaseInitializer 클래스 생성
    + FirebaseApp을 초기화 하고 FirebaseAuth를 초기화 하도록 함
+ 토큰을 검증하는 FirebaseTokenFilter를 만들었다
1. Authorization Header에서 Token을 가져온다
2. FirebaseAuth를 사용하여 Token을 검증한다
3. UserDetailsService에서 사용자 정보를 가져와 SecurityContext에 추가해 준다
    + 사용자 정보를 가져오기 위해 firebase에서 제공하는 uid를 사용
    + userDetailsService.loadUserByUsername(uid)
4. 인증 실패시 HttpStatus 403과 json으로 상태코드를 응답한다
+ SecurityConfig에 FirebaseTokenFilter를 적용

## OAuth란
+ 타사의 사이트에 대한 접근 권한을 얻고 그 권한을 사용하여 개발할 수 있도록 도와주는 프레임워크

## OAuth 동작 방식
1. 사용자가 Client를 통해 Authorization Server에 인증을 하면 JWT형태의 인증 토큰을 받는다
    + JWT 토큰에는 인증한 사용자의 정보와 Authorization Server의 서명과 유효 시간이 적요한다
    + JWT 토큰은 인증 서비스 제공자의 서명이 포함된 일정시간 동안 유효한 인증 토큰이다
2. Client가 Resource Service에 인증토큰을 동봉해 요청한다
3. Resource Server는 Authorization Server를 통해 인증토큰의 유효성 검증을 진행한다
4. 유효하고 사용자의 권한이 적절하면 Client Resource를 전달한다
