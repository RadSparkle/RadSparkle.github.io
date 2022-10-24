---
layout: default
title: study
nav_order: 3
has_children: true
premalink: /docs/study
---


--공부목록
웹소켓
페이징
/api/v1/home/myfeed/latest 공부
lvdisplay
df -h
lsblk
curl
builder
jar war 개념적 차이점, 배포할시 셋팅 차이점


- 파티션 용량 변경방법
lsblk
df -h
blkid
ext4 파일시스템일 경우 resize2fs 명령어를 사용

xfs파일시스템일 경우 xfs_growfs 명령어를 사용
xfs_growfs -d /home


- MySQL의 경우 디폴트로 에러 로그는 /var/log 디렉토리 밑에 mysqld.log 파일에 기록된다.


<span style="color:green"> CentOS > secret option required for sessions </span>
======================================================================

yarn build:prod를 하여서 빌드후 재기동하니깐 정상작동함

<span style="color:green"> SSL 인증서 갱신하는법 </span>
======================================================================

인증서 갱신 테스트
sudo certbot renew --dry-run
인증서 갱신
 sudo certbot renew

------------------------------------------------------
2022-10-17 TIL

Mybatis에서 쓰는 if문은 쿼리를 조건으로 받아들일수있지않고
파라미터를 조건으로 받아들일수있다. 이 점 유의하자

MySQL에서 COUNT와 LIMIT는 한 쿼리절에서 동시에 사용할수없는것같다.

그래서 
```
SELECT COUNT(*) FROM (SELECT id FROM id_table WHERE age=20 LIMIT 5) a ;
```
이런식으로 사용해야된다

ELK 즉 엘라스틱 서치는 사용자가 정해놓은 INDEX파일에 데이터를 저장해놓고 꺼내오는 방식이다

API에서 API를 호출하는방법도 배웠다