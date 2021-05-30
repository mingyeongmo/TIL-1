# GitHub란 

<img width = "300" src = "https://media.vlpt.us/images/sv002/post/045b6118-4d28-4a34-8269-e672a6168d8a/image.png">


<br>
<br>


### Git 이란
> Git은 소스코드를 효율적으로 관리하기 위해 사용하는 버전 관리 시스템이다. (VCS: Version Control System)

### Git을 사용하는 이유
> 개발자들이 협업하거나 파일들을 유지/ 보수 할때, 특히 코드를 수저앴지만 수정하기 전으로 되돌려야 할때 등등..
버전별 소스코드를 저장 및 관리가 가능한 GIT이 필요하다.

### Git의 여러가지 명령어

**git명령어 모음**
```
git 혼자 할 때


git init - creative git repository

git config --global user.name "own name" - input name
git config --globla user.email "own email" - input email
= 한번만 입력해도 됨 (이름이랑 이메일)

git config user.name - show name
git config user.email - show email

git status - 변경, 삭제, 추가된 파일 보기

git add -A - add all

git commit -m "name" - git commit and set name

git log - git history

git reset 일련번호 앞 6자리 --hard - 전 시점으로 돌아감(전 시점 후 다음 시점들은 지워짐

git revert 6자리 
:wq - 그 시점 것으로 새로 저장함

git brech 이름 - creat new brech

git checkout 이름 - 이름 brech로 넘어감

git marge brech이름 - brech병합

git rebase brech이름 - berch 재배치

git branch -D branch이름 - branch 삭제



github 협업

git push origin master - 깃허브로 보냄

git fetch - 깃허브의 최근 내역을 불러옴

git status - 깃허브와 뭐가 다른 지 알려줌

git pull origin master - 깃허브에서 다운

git checkout -b 브랜치명 - 브랜치를 만들고 그 브랜치로 넘어감

git branch -a - 깃허브에 연결된 모든 브랜치를 봄

git checkout -b 브랜치1 저장소/브랜치2 - 브랜치1을 만들고 브랜치 1에 저장소/브랜치2의 내용을 불러온 후 브랜치 1로 넘어감

git push -d 저장소 브랜치명 - 원격의 저장소를 지움
```

### GitHub란? 
github는 local에서 관리한 소스코드를 업로드하고 공유할 수 있는 **remote repository**(원격 저장소)이다.

내 **local repository**(개인 저장공간)에서 git을 통해 자료를 다른 사람과 공유하거나 백업 해놓을 수 있다.

또한 내가 작업한 것을 올리는 것 뿐만 아니라 다른 사람이 github에 올린 자료를 가져올 수 있다.


