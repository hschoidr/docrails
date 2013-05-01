ROR Lab.에서는 공식 레일스가이드의 `edge` 버전(http://edgeguides.rubyonrails.org) 을 한글화하는 프로젝트를 진행하고 있습니다. 
이전까지는 개인적으로(rorlab@gmail.com) 한글화 작업(레일스가이드의 MVC 부분과 asset pipeline)을 해 왔으나 혼자서 docrails의 edge버전을 업데이트해서 한글화하기에는 역부족임을 느끼게 되어, 뜻을 같이하는 분들도 참여할 수 있는 기회를 드리기 위해 공동으로 한글번역 작업을 진행하기로 했습니다.  

그래서 2013년 4월 30일, github.com의 기존 계정(rorlab)을 이용하여 `RORLabGuides`라는 그룹계정(github.com에서는 `Organization`이라고 말함)을 만든 후, 공식 docrails 저장소(lifo/docrails)를 fork하였습니다. 따라서 한글번역 작업의 소스를 관리할 저장소의 URL은 https://github.com/RORLabGuides/docrails 가 되겠습니다.

한글번역 작업을 하기 위해서는 자신의 로컬머신에 최소한 ruby와 git 이 설치되어 있어야 합니다. 
그리고 http://github.com에 로그인한 후(계정이 없는 분은 회원가입 후 로그인, 무료), 페이지 상단에 있는 검색란에 `RORLabGuides/docrails`라고 입력하고 엔터키를 칩니다. 또는 웹브라우저에서 `https://github.com/RORLabGuides/docrails` 주소로 직접 이동하셔도 됩니다.

저장소 Fork 하기
----

이 페이지의 상단에 있는 `Fork` 버튼을 클릭하여 소스를 본인의 계정으로 복사(`fork`에 대한 적당한 한글번역이 없군요^^) 합니다. 
이제 `github.com`에 본인 계정으로 로그인하면 본인의 `repositories`에 방금전에 `fork`한 `docrails 저장소`가 존재하게 됩니다. 

본인의 저장소 clone하기
----

실제로 한글 번역 작업을 하기 위해서 우선 본인의 로컬머신에 `ruby`와 `git` 가 설치되어 있는지 확인하고, 아래와 같이 터미널 쉘에서 소스를 `git clone` 합니다. 

```
$ git clone git@github.com:<user_git_accout>/docrails.git
```

여기서 주의할 것은 `<user_git_account>` 에는 본인의 git 계정명을 입력해야 합니다. 
clone후 docrails 디렉토리로 이동하고 아래와 같이 remote origin 브랜치의 주소를 https 프로토콜 주소로 변경해 줍니다. 

```
$ cd docrails
$ git remote show origin
* remote origin
  Fetch URL: git@github.com:<user_git_account>/docrails.git
  Push  URL: git@github.com:<user_git_account>/docrails.git
  HEAD branch: master
  Remote branches:
    gh-pages tracked
    master   tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
$ git remote rm origin
$ git remote add origin https://github.com/<user_git_account>/docrails.git
$ git remote show origin
* remote origin
  Fetch URL: https://github.com/<user_git_account>/docrails.git
  Push  URL: https://github.com/<user_git_account>/docrails.git
  HEAD branch: master
  Remote branches:
    gh-pages new (next fetch will store in remotes/origin)
    master   new (next fetch will store in remotes/origin)
  Local ref configured for 'git push':
    master pushes to master (up to date)
$ git push
Everything up-to-date
```

참고로 remote origin 브랜치의 주소를 https:// 프로토콜로 변경하는 이유는 본인의 github.com 계정정보에서 별도의 SSH Keys 등록 과정이 필요없기 때문입니다. 한편 이렇게 변경작업을 하지 않고 사용할 경우에는 본인의 ssh 공개키(~/.ssh/id_rsa)를 SSH Keys로 등록해 주어야 합니다. 

작업소스파일의 위치
----

이제, 아래의 디렉토리로 이동합니다. 

```
$ cd docrails/guides/source/ko
```

바로 여기에 있는 파일들이 번역을 할 소스입니다. 본인에게 할당된 파일을 에디터로 열고 한글로 번역을 하면 됩니다. 

한글 번역시 주의사항
---

`ko` 폴더에는 확장자가 `.md`, `.erb`, `.yaml`인 파일들이 존재하게 됩니다. 바로 이 폴더의 있는 파일들 중에 어떤 것을 작업할 것인지를 관리자와 상의해서 결정하게 되며, 다른 분들이 작업하는 파일과의 commit 충돌을 피하기 위해서, 다른 파일들에 대해서는 번역작업을 해서는 안됩니다. 즉, 한글번역 작업 파일로 할당받은 것에 대해서만 작업을 해야함을 잊어서는 안됩니다.

번역한 파일 커밋하기
---

번역을 완료하면 아래와 같이 `docrails/` 디렉토리로 이동합니다. 

```
$ cd docrails
```

그리고 아래와 같이 commit 작업을 합니다. 

```
$ git add .
$ git commit -m "translated <file_name>"
$ git push (origin master)
```

`<file_name>`에는 번역작업한 파일명을 입력하면 됩니다.
이후에 github.com 사이트의 본인의 docrails 페이지로 이동하여 해당파일이 변경되었는지를 확인하면 제대로 작업이 된 것입니다. 

pull-request하기
----

이제 본인의 docrails 페이지 상단에 있는 `Pull Request` 버튼을 클릭하면 잠시 후에 번역작업한 내용이 RORLabGuides/docrails 로 merge 요청이 완료됩니다. 

그러면 RORLabGuides/docrails 관리자(rorlab@gmail.com)가 요청된 내용을 검토하고 이상없으면 `merge` 작업을 하게 됩니다. 이 때 본인에게 확인메일이 발송됩니다. 

언제 `pull request` 내용이 `merge` 될 지는 순전히 관리자 마음에 달려 있죠^^. 확인메일을 확인한 후, RORLabGuides/docrails 페이지로 이동하여 최종결과를 확인하면 모든 절차가 일단락되는 것입니다. 

수고하셨습니다. 

관리자(rorlab@gmail.com)
