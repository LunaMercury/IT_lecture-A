## 워크벤치 사용

> 유저 생성

![[Pasted image 20250106142409.png]]
%는 모두, 나머지는 설정할 수 있다.

> 권한 부여

![[Pasted image 20250106142607.png]]
![[Pasted image 20250106142721.png]]
권한을 줄 데이터베이스를 선택
 ![[Pasted image 20250106142841.png]]
권한 목록 선택


## cmd 사용

> 사용자 조회

```mysql
select host,user from user;
```
host 뒤에 점이 아니라 쉼표다.


> 사용자 생성

``` mysql
create user user3@'%' identified by '1234';
```


> 권한부여

grant 허용명령어 on 데이터베이스.테이블 to 계정;
``` mysql
grant select,insert,update on *.* to user3;
```
`*` 은 모두라는 뜻이다. 즉 모든 데이터베이스의 모든 테이블에 select,insert,update 권한을 user3에게 준다는 뜻이다.


> 권한 조회
``` mysql
show grants for user3@'%';
```

