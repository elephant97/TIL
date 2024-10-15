# 소셜 로그인 기능 (Oauth)

### [kakao login](https://github.com/subwate/subwate-back/pull/6)
> 기능: 사용자는 kakao 계정으로 로그인 및 회원가입을 할 수 있다.
* [x] 카카오 콜백 함수로 return 받도록 컨트롤러 생성
* [x] 카카오 API 응답에 따른 처리 ( 네트워크 오류 및 인증 실패)
* [x] 올바른 응답 반환 시 user table에 정보 존재여부 확인하여 회원가입 필요한 유저인지 확인
* [x] request mapping 통일화
* [x] user 정보 존재 확인 시 login 처리 (jwt토큰 생성하여 반환) 
* [x] secret 값들 keys.properties로 분리
* [x] 테스트 시 h2 database 사용하도록 application.yaml 테스트 용으로 분리
* [x] ci/cd 시 keys.properties secret으로 불러와서 작성되도록 수정

### Google Login 
