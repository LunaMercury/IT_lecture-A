> 데이터베이스 속성

- infomation_schema : 메타데이터 제공, 데이터베이스 정보제공(테이블, 열, 인덱스 등)
- Perfomance_schema : 시스템 성능 관련정보 제공(쿼리성능, 서버리소스 사용현황, 대기중인 이벤트 등)
- mysql : 인증정보(사용자정보, 권한정보 등)
- sys : infomation_schema와Perfomance_schema의 분석을 돕기 위해 만들어진 DB

- 한글 글자당 3byte사용

### 실행 및 입력

> MySQL 실행 및 종료

cmd에서 mysql -u root -p 입력.  
-u : 유저  
root : 유저명  
-p : 패스워드로 인증  
-h : 호스트
```mysql
mysql -u user2 -p -h 192.168.16.25
#로컬호스트에 접속할 때는 -h와 ip가 필요없다.
```
-h 와 그 뒤의 ip는 로컬호스트가 아닌 다른 컴퓨터의 데이터베이스에 접근할 때 사용한다.

종료는 exit;


> 데이터베이스 조회

```mysql
show databases;
```
![[Pasted image 20250106153852.png]]
데이터베이스 뒤에 s 붙여야 한다

> 데이터베이스 선택

```mysql
use table1db;
```

> 테이블 조회

```mysql
show tables;
```
![[Pasted image 20250106154215.png]]

> 테이블 선택(내용 조회)

``` mysql
select * from test1db.tbl_user;
```
![[Pasted image 20250106154455.png]]

> 값 입력

insert into 테이블명(컬럼명1, 컬럼명2, 컬럼명3, 컬럼명4) values(값1, 값2, 값3, 값4);  
문자열은 따옴표 안에 작성한다.
``` mysql

insert into test1db.tbl_user(user_id, age, address, gen) values('홍길동', 30, '서울', '남')
```
![[Pasted image 20250106231732.png]]

> 값수정

update 데이터베이스명.테이블명 set 컬럼명='내용', 컬럼명='내용' where 컬럼명='내용';  
where 뒤의 컬럼명은 주로 primary key를 가진 속성을 참조한다.
``` mysql
update test1db.tbl_user set user_id='김범수', age=25 where user_id='홍길동';
```


### 생성

> 데이터베이스 생성

``` mysql
create schema test1db;
#schema 대신에 database 입력해도 된다.
```
![[Pasted image 20250106224437.png]]

> 테이블 생성

create table 데이터베이스명.테이블명(  
컬럼명 자료형 제약조건 프라이머리키(선택사항),  
컬럼명 자료형 제약조건);  

```  mysql
create table test1db.tbl_user(
user_id varchar(100) primary key,
age int not null,
address varchar(1024) null,
gen varchar(100)) not null;
```
![[Pasted image 20250106231427.png]]

> 테이블 속성 조회

desc 데이터베이스명.테이블명;
``` mysql
desc test1db.tbl_user;
```
![[Pasted image 20250106231504.png]]

> 테이블 속성 수정

column 추가 : alter table 테이블명 add column 컬럼명 자료형 제약조건 after 이전컬럼;  
column 수정 : alter table 테이블명 change column 기존컬럼명 변경컬럼명 변경자료형 제약조건;  
column 삭제 : alter table 테이블명 drop column 컬럼명;  

``` mysql
alter table tbl_product add column amount int not null after prod_price;
alter table tbl_product change column prod_price proc_price varchar(100) null;
alter table tbl_product drop column prod_details;
```

>행 삭제

delete from 데이터베이스명.테이블명 where(컬럼명='컬럼내용(주로 프라이머리키를 가진 컬럼)');
``` mysql
delete from test1db.tbl_user where(user_id='홍길동');
```