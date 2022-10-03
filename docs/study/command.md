---
layout: post
title:  "Command"
date:   2022-07-20 14:29:06 +0900
categories: study
---
<span style="color:green">리눅스 명령어</span>
==============================================

<span style="color:red"> CentOS</span>
--------------------------------------
<br>

파일 복사
```
cp file file2     

옵션
-a  복사가되면서 파일의 속성까지 복사
-p  원본 파일의 소유자,그룹,권한 등의 정보까지 복사
-i  덮어쓰기할지 묻는다.
-r  하위 디렉토리 및 파일까지 모두 복사
-v  현재 보사 진행 작업을 표시
-u  최신 파일이면 복사
-b  이미 존재하는 파일이면 백업파일 생성
```

특정 단어 검색
```
ps -ef | grep 찾을단어


ps(Process Status)
-e 모든 프로세스 출력
-f 풀 포맷으로 보여줌(UID,PID 등)

grep의 옵션
-i  대소문자 구분하지않고 검색
-n 줄 번호를 함께 출력
-x 패턴과 단어 전체가 일치하는 라인 출력
```

해당 포트를사용하는 프로세스  검색
```
netstat -nap | grep 포트번호   
```

해당 PID 종료
```
kill -9 PID 
```

복사,붙여넣기
```
 YY 1줄복사 , P 붙여넣기
```

삭제
```
rm file.txt

만약의 사태를 대비해서
rm 보다는 밑의 방법을 사용하자.

find . -name '*.jar'   해당 디렉토리의 .jar파일 모두 검색
find . -name 'test.jar' -delete  해당 디렉토리의 test.jar파일을 삭제
```

파일이름변경 or 디렉터리 이동
```
mv 기존파일명 변경파일명
```

방화벽 확인
```
dnf install firewalld 
```

허용할 80포트를 등록
```
firewall-cmd —zone=public —add-port=80/tcp —permanent
```

방화벽 새로고침
```
firewall-cmd —reload
```

아파치 설치
```
dnf install httpd
```

아파치 실행
```
systemctl start httpd
```

아파치 상태 확인
```
systemctl status httpd
```

에러로그 확인
```
vi /var/log/httpd/error_log 
```

파일의 마지막행 기준 10줄 출력
```
tail [옵션] [파일명]
```

파일 변경내용 모니터링
```
tail -f [파일명]

tail 명령을 중단하려면 Ctrl+C
```

현재 디렉터리의 전체 경로
```
pwd
```

파일생성(파일이 이미 존재하면 최종수정시간 변경)
```
touch [파일명]
```

권한 변경
```
chmod
```

파일 및 디렉토르 검색
```
find [경로] -name [파일명]

```




<br>

<span style="color:red"> MySQL </span>
--------------------------------------
<br>

MySQL 패키지 삭제
```
dnf `remove -y mysql-community-*` 
```

MySQL 설치
```
dnf install mysql-server
```

활성화, 실행, 상태확인
```
systemctl enable mysqld

systemctl start mysqld

systemctl status mysqld
```

임시 비밀번호 확인


```
grep ‘temporary password’ /var/log/myqld.log
```

*mysql -u root -p // 로그인*

root 비밀번호 변경
```
ALTER USER 'root'@'localhost' IDENTIFIED BY '변경할비밀번호'; 
```

DB생성
```
CREATE DATABASE {DB명} default CHARACTER SET UTF8;
```

user 생성
```
create user '{testName}'@'%' identified by '{rozeuS1000!}';
```

user 생성2
```
CREATE USER testUser@localhost identified by 'password'; 
```

현재 존재하는 DB 보기
```
SHOW DATABASES;
```

테이블 사용
```
use 테이블명; 
```

테이블 생성
```
CREATE TABLE 테이블명(id INT, name VARCHAR(20), email VARCHAR(20)); 
```

디렉토리 확인
```
show variables like 'datadir';
```

에러 로그 경로
```
vi /var/log/mysqld.log
```

권한 확인
```
ls-al //권한보기
```

slow query log 설정 상태 확인
```
show variables like ‘slow_query_%’;
```

MySQL 재가동
```
service mysqld restart
```

<span style="color:green">터미널 명령어</span>
==============================================
프로젝트 clean, build
```
./gradlew clean build
```

젠킨스파일 유효성 검사
```
curl --user rozadmin:rozeuS1000! -X POST -F "jenkinsfile=<Jenkinsfile" http://192.168.0.213:7000/pipeline-model-converter/validate
```

<span style="color:green">인텔리제이 단축키</span>
=================================================

getter, setter 생성 
```
alt+insert
```

대소문자 변환
```
ctrl+shift+x
```
RUN
```
ctrl+shift+F10
```

STOP
```
ctrl+F2
```




