gitignore(application.properties와 gradle-wrapper.jar)
==

application.properties
--
gitignore.io를 사용해서 만들 경우 손쉽게 git에 올리지 않을 파일들을 쭉 만들어준다.

그러나 이렇게 만들 경우 포함되지 않는 파일이 있는데 바로 application.properties가 있다.

이 파일은 단순한 정보들이 있을 경우 상관없지만 db 비밀번호, api키 등의 정보들이 포함될 수 있다!

따라서 application.properties 파일을 추가해주거나

환경 변수를 활용하여 spring.datasource.password=${DB_PASSWORD} 이런 식으로 중요 정보를 포함하지 않도록 해야한다!

gradle-wrapper.jar
--
또 혹시나 처음 파일들 중 올리면 안되는 파일이 있을까 하여 gpt에게 물어봤다.

gradle-wrapper.jar는 올리지 않아도 gradle-wrapper.properties에 지정된 버전을 기준으로 자동 다운로드 된다므로 올리는게 선택사항이라고 답했다!

그러나 생성된 gitignore파일을 보면

> "# Avoid ignoring Gradle wrapper jar file (.jar files are usually ignored)
!gradle-wrapper.jar"

이렇게 작성되어있는 것을 볼 수 있음!

그래서 gradle-wrapper를 gitignore에 포함하고 하지 않는 경우를 따져보면
- 포함 X
    - Gradle이 없는 환경에서도 빌드 가능 - 프로젝트를 클론한 사람이 Gradle을 설치하지 않아도 바로 ./gradlew build로 빌드할 수 있다.
    - 빌드 환경 표준화 - 
   CI/CD 환경에서 Gradle을 따로 설치할 필요 없이, 저장소의 gradle-wrapper.jar를 실행하면 됨.
- 포함 O
    - 파일 크기가 쌓일 가능성 - 크기가 크진 않지만, 여러 버전이 Git 히스토리에 남으면 쌓일 수 있다.
    - gradle 설치 환경에서는 gradle-wrapper.properties에 지정된 버전을 기준으로 자동 다운로드

정리
--
application.properties는 처음부터 gitignore 또는 환경 변수 등의 상황에 맞게

gradle-wrapper는 개인 플젝의 경우 포함하여도 상관없고, 
팀 프로젝트의 경우 포함하지 않는 것이 좋아보인다.

팀에서 합의한 방향으로 두 파일을 관리하자!