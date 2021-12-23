### Git
- 분산 버전 관리 시스템(VCS)로, 프로젝트 파일의 변경 사항을 추적하는 시스템이다.

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

### Git reset, revert
- Reset
  - 특정시점으로 되돌린다.
- Revert
  - 특정 commit만 되돌린다.