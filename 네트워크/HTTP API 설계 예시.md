### HTTP API 설계 예시

- HTTP API - 컬렉션
- HTTP API - 스토어
- HTTP FORM


#### 회원 관리 시스템

##### API 설계 - POST 기반 등록

-회원목록 /members -> GET
-회원등록 /members -> POST
-회원조회 /members/{id} -> GET
-회원수정 /members/{id} -> PATCH(부분 수정), PUT(전체 리소스를 수정, 게시판의 게시글 수정), POST(애매)
-회원삭제 /members/{id} -> DELETE

##### POST - 신규 자원 등록 특징

 - 클라이언트는 등록될 리소스의 URI는 모름
 - 서버가 새로 등록될 리소스 URI 를 생성
 - 컬렉션(Collection)  : 서버가 관리하는 리소스 디렉토리 / 서버가 리소스의 URI를 생성 관리 

#### 파일 관리 시스템 PUT 기반 등록

- 파일 목록 -> GET
- 파일 조회 -> GET
- 파일 등록 -> PUT
- 파일 삭제 -> DELETE
- 파일 대량 등록 -> POST

##### PUT - 신규 자원 등록 특징

 - 클라이언트가 리소스 URL를 알고 있어야 함.
 - 클라이언트가 직접 리소스의 URI를 지정함.
 - 스토어(Store) : 클라이언트가 관리하는 리소스 저장소 / 클라이언트 리소스의 URI를 알고 관리

* 대부분 실무에선 POST 기반의 컬렉션을 사용하고 있음.

##### HTML FROM

 - HTML FORM(순수한) ****GET,POST 만 지원
 - AJAX 같은 기술을 사용해서 해결 가능함.
 
 - 회원목록 /members-> GET
 - 회원 등록 폼 /members/new-> GET
 - 회원등록 /members/new(등록과 폼을 URL 경로를 맞추는 게 Validation Check에 용이하나 개인 개발자의 스타일), /members -> POST
 - 회원조회 /members/{id}-> GET
 - 회원수정 폼 /members/{id}/edit -> GET
 - 회원수정 /members/{id}/edit, /membeers/{id}-> POSt 
 - 회원 삭제 /members/{id}/delete -> POST
 
  - 컨트롤 URI
    - GET , POST 만 지원하므로 제약이 존재
    - 이런 제약을 해결하기 위해 ****동사 URL 경로 사용(삭제 수정 등)
    - HTTP 메서드로 해결하기 애매한 경우 사용(HTTP API 포함)
  
  * 주의할 점 : 너무 남발하는 건 좋지 못함, 최대한 가능한 한 쓰고 안될 때 사용
 
 ##### 문서, 컬렉션, 스토어, 컨트롤러(컨트롤 URI)
 
 참고 사이트 : http://restfulapi.net/resource-naming
 
