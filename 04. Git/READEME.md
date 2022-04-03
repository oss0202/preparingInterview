## Git
분산 버전 관리 시스템(VCS)로, 프로젝트 파일의 변경 사항을 추적하는 시스템이다.
![git_staging_repository](../img/git_staging_repository.png)
- Staging Area(index)
  - git이 파일에서 발생하는 변경 사항을 추적하고 저장하기 시작할 때 입니다.
  - Staging Area에 파일 추가방법
    - ``` git add #filename#``` : 파일단위 추가
    - ``` git add . ``` : 모든 파일을 의미하는 와일드 카드


### Git의 장점
- **분산적인 개발** 
  - 깃(Git)을 사용하는 전체 개발 내역을 각 개발자의 로컬 컴퓨터로 복사할 수 있다.
  - 나중에 서로 수정된 내역을 합치기(Merge)할 수도 있으며, 이 때 Git의 고유한 프로토콜을 이용하게 된다.

- **효율적인 개발** 
  - 깃(Git)은 일반적인 다른 버전 관리 시스템보다 성능이 뛰어나며, 변경 이력이 많더라도 변경된 내용만 처리한다는 점에서
  메모리적인 효율성이 뛰어나다.

- **비선형적인 개발** 
  - 깃(Git)은 브랜치(Branch)라는 개념이 사용된다. 다시 말해서 프로젝트의 가지치기가 가능하다는 뜻이다.
  이는 트리 구조, 다시 말해서 비선형적인 구조라고 볼 수 있다.

- **변경 이력 보장** 
  - 작업된 모든 내역(Commit 내역)들은 모두 별도의 영역에서 관리되어 안전하게 프로젝트를 운영할 수 있다.

### Repository
- Git으로 관리하는 프로젝트 저장소

### Commit
- 프로젝트의 현재상태를 나나태는 스냅샷

### Branch
- 독립적으로 어떤 작업을 진행하기 위한 개념
- 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행 할 수 있다.

### GitHub
- Git repository를 위한 호스팅 플랫홈이다.

### Pull Request(PR)
- 자신이 작업한 브랜치 작업 내용을 master 브랜치에 반영해달라는 요청

### Conflicts
- 어떤 파일의 변경 사항이 기준이 되는 master 브랜치의 팡리과 겹쳐, Git에서 어떤 버전의 코드를 선택해야 할지 모를 때 발생

### Merge와 Rebase
- Merge
  - commit 묶음 
    - 이력이 보존된다.
  - merge 커밋을 리셋하면 관련 커밋이 모두 리셋된다.
  - branch를 통합
- Rebase
  - branch의 base를 옮김
  - 커밋트리를 깔끔하게 정리해서 보기가 좋다.

## 자주사용하는 명령어
- ```git init``` : 새 git 저장소 생성
- ```git add .``` : staging area에 모든파일 추가
- ```git commit -m "커밋 메세지"``` : local repository에 변경 사항 추가
- ```git push ``` : local repository에 변경 사항을 remote repository에 푸시
- ```git pull ``` : remote repository에 local repository로 코드 가져오기
- ```git brach ``` : 현재 branch 확인
- ```git brach -r ``` : remote branch 확인
- ```git checkout -b 브랜치명 ``` : branch 생성 후 해당 branch로 전환
- ```git log ``` : 최근 커밋 내역 표시
- ```git log -p ``` : 최근 커밋 내역 자세히 표시
- ```git status ``` : 추적 죽인 파일과 추적되지 않은 파일 표시
- ```git stash ``` : 현재 작업중인 내역(add or commit) 임시 보관하기

### Git reset, revert
- Reset
  - 특정시점으로 되돌린다.
- Revert
  - 특정 commit만 되돌린다.

## Git reset
### add 취소하기
- Staging Area(git add 명령 후의 상태)에 넣은 파일을 빼고 싶을 때가 있다.
```shell

```


