---
layout: post
title:  "History"
date:   2022-07-20 14:29:06 +0900
categories: study
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



<span style="color:green"> Gitea의 repo를 public에서 private로 전환시 Jenkins가 접근못하는 오류 </span>
===========================================================================

기존에는 Gitea에서 repository들을 private가아닌 public으로 사용하고있었다.

하지만 public으로 사용할 시 누구나 접근할수있기때문에 우리의 조직에속한 멤버들만 접근할수있도록 private로 바꾸었다.

하지만 repository를 private로 바꾸니 Jenkins에서 repository에 접근하지못하고 빌드의 check revision 파이프라인에서 

오류가 발생하였다.

처음에는 Jenkins와 Gitea가 설치되어있는 서버에서 ssh-keygen을 발급받은후 해당키를 Gitea의 배포키에 등록한후 Jenkins에서 키를 등록해줘된다고 생각해서 여러방향으로 시도해보았지만 결국 실패하였다.

또한, Jenkins에서 Credential을 발급받은후 해당 키를 Gitea에 등록하는 방법도 시도해보았지만 결국 실패하였다.

며칠동안 매달려본결과 해결방법은

각 repository에있는 프로젝트들의 Jenkinsfile안에 checkout revision 파이프라인의 

userRemoteConfigs: [[url: '{url}', credentialsId: '{credentialID}']]

이 부분이 원래는 url부분만 적혀있었다. 하지만 보이다싶이 credentialsId를 추가하여 Jenkins에 등록되어있는 Credential Id를 작성하였더니 정상적으로 Jenkins에서 Gitea의 private repository에 접근하여 빌드와 배포를 할수있게되었다.


<span style="color:green"> CentOS > No match for argument 에러 </span>
===========================================================================
```
sudo dnf install https://pkgs.dyn.su/el8/base/x86_64/raven-release-1.0-1.el8.noarch.rpm

sudo dnf --enablerepo=raven-extras install mod_evasive
```

<span style="color:green"> CentOS > RPM-GPG-KEY-CentOS-Official </span>
===========================================================================

centos.repo

RPM-GPG-KEY-CentOS-Official.
