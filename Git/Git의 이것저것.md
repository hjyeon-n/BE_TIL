# Git의 이것저것

Git은 알면 알수록 어렵다... 😂 모르는 용어나 프로세스가 이해가 안 될 때마다 여기다 정리해야지 👊

<br>

### remote 저장소

리모트 저장소는 인터넷이나 네트워크 어딘가에 있는 저장소를 말한다. 다른 사람들과 함께 일한다는 것은 리모트 저장소를 관리하면서 데이터를 거기에 Push 하고 Pull 하는 것이다. 리모트 저장소를 관리한다는 것은 저장소를 추가, 삭제하는 것뿐만 아니라 브랜치를 관리하고 추적할지 말지 등을 관리하는 것을 말한다. 원격 저장소라 하더라도 로컬 시스템에 위치할 수도 있다는 점을 유념하자. '리모트 저장소'라고 이름이 붙어있어도 이 원격 저장소가 사실 같은 로컬 시스템에 존재할 수도 있다.

[참고](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C)

<br>

### Git 명령어

**git push**

: local repository의 파일들을 remote repository로 올리는 명령어

```
git push [원격 저장소명] [원격 브랜치명]

ex) git push origin master
```

<br>

**git clone**

: 원격 저장소의 소스파일을 가지고 오는 명령어

```
git clone [원격 저장소 url]
```

<br>

**git fetch**

: local repository에서 remote repository의 내용들을 업데이트. local에 연결된 remote repository의 브랜치 목록과 그 파일 내용을 최신으로 업데이트 하는 명령어

<br>

**git pull**

: git fetch + git merge

<br>

**git stash**

: 워킹 디렉토리에서 수정한 파일들만 저장

→ **git stash pop**으로 꺼낼 수 있음! 

<br>

**git merge**

[참고](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EC%99%80-Merge-%EC%9D%98-%EA%B8%B0%EC%B4%88)

[출처](https://victorydntmd.tistory.com/74)

<br>

### Git 기본용어

**스테이징(Staging)**

: 확정할 변경 사항을 준비시키는 것.

**인덱스(Index)**: 

: 확정할 준비가 된 변경 사항들이 모인 영역.

<br>

[깃 기초는 여기서 재밌게 배울 수 있다!](https://evan-moon.github.io/2019/07/25/git-tutorial/)

[Git 버전 관리](https://evan-moon.github.io/2019/07/28/git-tutorial-advanced/)
