# DB Index란 무엇인가?

### Index의 의미

RDBMS에서 속도를 높이기 위해서 사용하는 한가지 기술이다.
Index는 영어를 직역하면 색인 이라는 뜻을 가지고있다.
Table의 컬럼을 색인화해서 검색하면 해당 테이블의 Record를 처음부터 끝까지 스캔하는게 아니라, 색인 되어있는 Index파일을 검색해서 속도를 빠르게한다.

Index는 Tree구조로 색인화를 진행한다. RDBMS에서 사용하는 Index는 Balance Search Tree를 사용하고있고
실제로는 B+Tree를 사용한다고 한다.

### Index의 원리
Index를 해당 컬럼에 주게 되면 초기 테이블 생성시 만들어진 MYD, MYI, FRM 3개의 파일 중에 MYI에 해당 컬럼을 색인화 하여 저장한다.
물론 Index를 사용하지 않을 시에는 비어있게된다.
그래서 Index를 해당 컬럼에 만들게 되면 컬럼을 따로 인덱싱하여 MYI파일에 입력하게 된다.
그렇기 때문에 Select쿼리로 Index가 사용하는 쿼리를 사용시 해당 TABLE을 검색하는게 아니라
Tree로 정리해둔 MYI파일의 내용을 검색하게 된다.
만약 Index를 사용하지 않은 Select 쿼리라면, TABLE을 전부다 스캔해서 검색한 결과를 보여준다.

### Index의 장점
- 키 값을 기초로해서 테이블에서 검색과 정렬 속도를 향상시킨다.
- 질의나 보고서에서 그룹화 작업 속도를 향상시킨다
- 인덱스를 사용하면 테이블 행의 고유성 강화
- 테이블의 기본 키는 자동으로 인덱스 된다.
- 필드 중에는 데이터 형식 때문에 인덱스 될 수 없는 필드도 존재한다.
- 여러 필드로 이루어진 인덱스를 사용하면, 첫 필드 값이 같은 레코드도 구분이 가능하다.

### Index의 단점
- 인덱스를 만들면 .mdb 파일의 크기가 증가한다.
- 여러 사용자 응용 프로그램에서 여러 사용자가 한 페이지를 동시에 수정할수 있는 병행성이 줄어든다.
- 인덱스 된 필드에서 데이터를 업데이트 하거나, 레코드를 추가, 또는 삭제할 때 성능이 떨어진다.
- 인덱스가 데이터 베이스 공간을 차지해서 추가적인 공간이 필요해진다.
- 인덱스를 생성할 때 시간이 많이 소모될수 있다.
- 데이터 변경 작업이 자주 일어날 경우, 인덱스를 재 작성 해야해서 성능에 문제가 생긴다.
따라서 어느 필드를 인덱스 해야하는지 미리 설계하고 결정하는것이 좋다.
인덱스를 추가하면 쿼리가 1초정도 빨라지지만, 데이터 행을 추가하는 속도는 2초정도 느려지게 되어
여러 사용자가 사용하는 경우, 레코드 잠금 문제가 발생할수 있다.

또 다른 필드에 대해 인덱스를 만들게 되면 성능이 별로 향상되지 않을수 있다.



### 결론
- 사용하면 좋은 경우
    - Where 절에서 자주 사용되는 Column
    - 외래키가 사용되는 Column
    - Join 에 자주 사용되는 Column
- Index 사용을 피해야 하는 경우
    - Data중복도가 높은 Column
    - DML이 자주 일어나는 경우
