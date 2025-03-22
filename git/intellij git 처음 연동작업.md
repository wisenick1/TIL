아래처럼 github와 연결은 되어 있는 상황
![alt text](image/image.png)

로컬 Git Repository 생성
--
- VCS → Create Git Repository -> 해당 프로젝트 파일 선택

Intellij에서 GitHub Repository 등록
--
- Git → Manage Remotes

![alt text](image/image-1.png)

연결 하는 git repository의 주소 가져오기

![alt text](image/image-2.png)

연동 확인

gitignore 설정
--
- gitignore 설정 시 gitignore.io 페이지에서 간편하게 설정가능, 만들어서 gitignore에 복붙

- git pull 하기
- git commit 하고 push 하면 끝

- :punch: 그냥 application.properties 자체를 올리지 않고 싶었지만 로컬 Git Repository 생성할 때 commit 자체에 잡혀버려서 이건 어떻게 해야할지 정말 열심히 찾아보고 다해봤지만 모르겠다....
-> gitignore 작성 후 ctrl + s를 눌러서 저장해주면 자동으로 적용된다....

-> 만약 git에 올려버렸다면!
git rm -r --cached .
또는 git rm -r --cached [해당 파일]

git add .

git commit -m "fixed untracked files"

git push

gitignore를 적용하도록 이 과정들을 통해 추적하지 않도록 만들어주자!





