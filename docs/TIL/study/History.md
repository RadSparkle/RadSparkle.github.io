---
layout: post
title:  "History"
date:   2022-07-20 14:29:06 +0900
categories: 
---

<span style="color:green">tomcat profile 설정</span>
===================================================

인텔리제이에서 application.yml 의 profile은 설정하고 셋팅까지 완료한 후 centOS에 배포하였다.

하지만 local에서 셋팅한 profile로 정상 작동하던게 centOS에서는 작동하지않았다.

profile을 셋팅했다고 생각한건 인텔리제이에서의 tomcat profile설정이였고 centOS에서는 변수를 추가해서 profile을 설정해줘야된다...

톰캣폴더/bin/sentenv.sh를 만들고

```
export JAVA_OPTS="$JAVA_OPTS -Dspring.profiles.active=프로파일 이름"
```

위와같이 입력하고 저장한다. 

미리 셋팅한 profile에 해당하는 설정이 실행될것이다.

<span style="color:green">jenkins deploy > Neither the JAVA_HOME nor the JRE_HOME environment variable is defined 오류 </span>
====================================================
자바 환경변수가 잡혀있지않아서 발생하는 오류이다.

catalina.sh 파일안에 자바 환경변수가 제대로 작성되어있는지 확인한다.

필자는 자바를 재설치하였고 환경변수를 다시 세팅해주니깐 해결되었다.


<span style="color:green">centos 쉘파일 실행시 /root: Is a directory</span>
==========================================================================
쉘 스크립트 마지막줄에 공백이 있으면 지우자.








