> 데이터베이스 속성

- infomation_schema 	: 메타데이터 제공, 데이터베이스 정보제공(테이블, 열, 인덱스 등)
- Perfomance_schema 	: 시스템 성능 관련정보 제공(쿼리성능, 서버리소스 사용현황, 대기중인 이벤트 등)
- mysql         			: 인증정보(사용자정보, 권한정보 등)
- sys 			          : infomation_schema와Perfomance_schema의 분석을 돕기 위해 만들어진 DB

- 한글 글자당 3byte사용

> MySQL 실행 및 종료

cmd에서 mysql -u root -p 입력.
-u : 유저
root : 유저명
-p : 패스워드로 인증

종료는 exit;


> 데이터베이스 선택

use 데이터베이스명
``` mysql
use test2db;
```


> 테이블 속성 조회

desc 테이블명;
``` mysql
desc tbl_product;
```

> 테이블 내용 조회

select * from 데이터베이스명.테이블명;
``` mysql
select * from test2db.tbl_user;
```


> 테이블 생성

create table 데이터베이스명.테이블명(
컬럼명 자료형 제약조건 프라이머리키(선택사항),
컬럼명 자료형 제약조건);

```  mysql
create table test2db.tbl_product(
prod_id int primary key,
prod_name varchar(100) not null,
prod_category varchar(10) null,
prod_details varchar(1024) null,
reg_date datetime not null,
prod_price int not null);
```


> 테이블 수정

column 추가 : alter table 테이블명 add column 컬럼명 자료형 제약조건 after 이전컬럼;
column 수정 : 		       change column 기존컬럼명 변경컬럼명 변경자료형 제약조건;
column 삭제 : 		       drop column 컬럼명;

``` mysql
alter table tbl_product add column amount int not null after prod_price;
alter table tbl_product change column prod_price proc_price varchar(100) null;
alter table tbl_product drop column prod_details;
```

> 값넣기

insert into 테이블명(컬럼명1, 컬럼명2, 컬럼명3, 컬럼명4) values(값1, 값2, 값3, 값4);
문자열은 따옴표 안에 작성한다.

```mysql
insert into tbl_user(user_id, user_name, user_age, user_gender) values('aaa', '홍길동', 11, 'M');
```

> 값수정

``` mysql
update test2db.tbl_user set user_name='김범수', user_gender='W' where user_id='bbb';
```

>행 삭제

``` mysql
delete from test2db.tbl_user where(user_id='bbb');
```
