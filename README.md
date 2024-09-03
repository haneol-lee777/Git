# Git
Overview of git branch, gitlab, version control

## Git Branch

### Git 기초

- `git init`
- `git add`
- `git commit`
- `git log`

### Git 원격저장소 (remote)

- `git remote add [저장소이름] [저장소주소]`
- `git remote` : 원걱저장소의 리스트(이름)
- `git remote -v` : 원격저장소의 리스트(이름, 주소)

### Git 브랜치(branch)

- `git branch` : Branch 리스트 출력
- `git branch [브랜치이름]` : 새로운 Branch 생성
- `git checkout [브랜치이름]` & `git switch [브랜치이름]` : Branch 이동
- `git branch -d [브랜치이름]` : Branch 삭제
- `git branch -b [브랜치이름]` & `git switch -c [브랜치이름]` : Branch 생성 & 이동
- `git merge [브랜치이름]` : 현재 Branch에서 특정 Branch를 병합

### Git Merge 시나리오

1. fast-forward merge
2. auto merge (without conflict)
3. merge with conflict

### Conflict 해결방법

#### conflict 발생조건

- 동일 파일 그리고 동일 라인의 내용이 충돌될 때

### Git Merge & Pull Request 단계별 프로세스:

1. **dev 브랜치에서 새로운 커밋을 추가:**
   - 개발 작업을 `dev` 브랜치에서 계속 진행합니다. 새로운 기능을 추가하거나 버그 수정을 완료합니다.

2. **main 브랜치로 전환 후 업데이트:**
   - 작업이 완료된 후 `main` 브랜치로 전환합니다:
     ```bash
     git checkout main
     ```
   - 그 다음, `main` 브랜치를 최신 상태로 업데이트합니다. 여기서 `git pull` 또는 `git fetch`를 사용할 수 있습니다:
     - `git pull`: 리모트 저장소의 최신 커밋을 가져오고, 현재 로컬 브랜치에 병합합니다.
     - `git fetch`: 리모트 저장소의 최신 커밋을 가져오지만, 로컬 브랜치에는 병합하지 않습니다.
     - 이후 `git merge origin/main`을 사용해 병합할 수 있습니다.

3. **dev 브랜치로 돌아가 main 브랜치 병합:**
   - `main` 브랜치가 최신 상태로 업데이트된 것을 확인한 후, 다시 `dev` 브랜치로 돌아갑니다:
     ```bash
     git checkout dev
     ```
   - `main` 브랜치의 변경 사항을 `dev` 브랜치에 병합합니다:
     ```bash
     git merge main
     ```
   - 이 과정에서 충돌이 발생할 수 있으며, 필요한 경우 충돌을 해결한 후 병합을 완료합니다.

4. **PR(Pull Request) 생성하여 main 브랜치에 병합:**
   - `dev` 브랜치에서 작업이 모두 완료되고 `main` 브랜치와의 병합이 완료되면, `dev` 브랜치에서 `main`으로 PR을 생성합니다. 이 PR을 통해 `dev`에서 작업한 내용이 `main` 브랜치에 반영됩니다.
   - 코드 리뷰 및 테스트를 거쳐, 최종적으로 PR을 승인하고 `main` 브랜치에 병합합니다.

### 장점:
- **안정성 확보**: `main` 브랜치를 항상 최신 상태로 유지하면서, `dev` 브랜치의 작업을 반영하기 때문에 안정성을 확보할 수 있습니다.
- **충돌 방지**: `dev` 브랜치에서 `main` 브랜치와의 충돌을 미리 해결할 수 있어, PR 과정에서 발생할 수 있는 충돌을 최소화할 수 있습니다.
- **협업 효율성 증가**: PR을 통한 코드 리뷰와 피드백 과정을 통해 코드 품질을 유지하고, 팀 내 협업을 강화할 수 있습니다.

### 결론:
이 프로세스는 `dev`와 `main` 브랜치 간의 지속적인 동기화를 통해 충돌을 최소화하고, 코드 품질을 유지하는 데 효과적인 방법입니다. `dev` 브랜치에서의 작업이 `main` 브랜치에 반영되기 전에 충분한 검토와 테스트를 거치는 구조를 유지함으로써, 프로젝트의 안정성과 협업 효율성을 높일 수 있습니다.


### Git 실습
echo "# Git" >> README.md

내용 작성 후:

git init
git add README.md
git commit -m "Add overview of Git branch management and version control basics"
git branch -M main
git remote add origin https://github.com/haneol-lee777/Git.git
git push -u origin main

-----

git checkout -b dev
git push -u origin dev

git checkout -b feature/dif
수정 후:

git add .
git commit -m "Amend dev branch"
