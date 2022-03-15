## 왜 Get 메소드를 사용해야하는 가에 대한 의문
-  Get을 사용하면 주소창에 쿼리 스트링이 그대로 보여지기 때문에 보안이 취약하다고 알고 있음.
-  ex) 실제 운영중인 레거시 시스템에서 파일 팝업시 do?FILE_ID=action.FILE&ACTION_ID=&ATTACH_DOC_NAME=IP_BL&ATTACH_DOC_ID=**49630** ID가 노출되고 있었음.
-  Post로 다 보내면 되는거 아닌가 하는 단순한 생각에 해당 HTTP 메소드에 대한 개념을 정리.

### 멱등성, Idempotent 

[HTTP멱등성정의](https://datatracker.ietf.org/doc/html/rfc7231#section-4.2.2)

동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 결과, 서버의 상태도 동일하게 남을 때, 
HTTP 메서드가 멱등성을 가졌다고 말합니다 (메서드 :  PUT, DELETE, TRACE 및 GET, HEAD, OPTIONS )


### GET 

GET 메소드는 주로 Read(읽기), 검색(Retrieve) 시 사용되는 메소드 - HTTP 명세 의하면 GET 은 데이터 읽을 때만 사용, 수정할 때는 사용 X
GET Idempotent 하게 설계(따라서, 동일한 요청을 여러 번 하더라도 동일한 결과,응답)되어 조회,읽기 등을 할 때에 사용한다.
데이터를 변경하는 등의 안전하지 않은 연산에 사용하면 안된다

URL 끝에 파라미터로 포함, 파라미터가 여러 개이면 &로 연결하며 이 부분을 쿼리스트링이라 함(이 쿼리스트링을 통해 데이터를 전달함)
