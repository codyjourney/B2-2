# Git 협업 미션

## 1. 미션 소개

Git은 단순한 버전 관리 도구가 아니라 팀 협업의 핵심 인프라입니다.

이번 미션에서는 3~5인 팀으로 실제 협업 상황을 시뮬레이션합니다. 같은 파일을 동시에 수정하여 충돌을 경험하고, Pull Request(PR)를 통해 코드 리뷰를 주고받으며, GitHub Flow 기반의 브랜치 전략을 적용합니다.

단순히 Git 명령어를 외우는 것이 아니라 다음 과정을 직접 경험하는 것을 목표로 합니다.

```text
Issue
  ↓
Feature Branch
  ↓
Commit
  ↓
Pull Request
  ↓
Code Review
  ↓
Review 반영
  ↓
Approve
  ↓
Merge
```

또한 실제 협업에서 발생할 수 있는 충돌과 Git 실수 상황을 의도적으로 재현하고 해결합니다.

> **핵심 목표:** 복잡한 프로그램을 만드는 것이 아니라, 팀원들이 Git을 이용하여 안전하고 재현 가능한 방식으로 협업하는 과정을 경험하고 증빙하는 것입니다.

---

# 2. 프로젝트 목표

이번 미션을 통해 다음 내용을 실제 협업 과정에서 이해하고 설명할 수 있도록 합니다.

* Git 브랜치가 커밋을 가리키는 포인터라는 것을 이해한다.
* 여러 사람이 동시에 작업하기 위해 브랜치를 분리하는 이유를 이해한다.
* GitHub Flow가 무엇인지 이해하고 실제 프로젝트에 적용한다.
* Pull Request의 목적과 코드 리뷰의 가치를 이해한다.
* Git 충돌이 발생하는 이유를 이해한다.
* `<<<<<<<`, `=======`, `>>>>>>>` 충돌 마커의 의미를 이해한다.
* `reset`, `revert`, `stash`의 차이를 이해한다.
* Git 협업 중 발생한 문제를 재현하고 해결 과정을 문서화한다.
* Issue → Branch → Commit → PR → Review → Merge의 협업 흐름을 경험한다.

---

# 3. 기술 환경

* Python 3.10+
* Git
* GitHub
* GitHub Flow
* GitHub Pull Request
* GitHub Issues

---

# 4. 프로젝트 구조

```text
repository/
│
├── README.md
├── SUBMISSION.md
│
├── src/
│   ├── math_utils.py
│   ├── string_utils.py
│   └── list_utils.py
│
├── docs/
│   ├── CONTRIBUTING.md
│   ├── conflict-resolution.md
│   └── troubleshooting-log.md
│
└── team/
    ├── member-a.md
    ├── member-b.md
    └── member-c.md
```

## 주요 문서

| 파일                            | 설명               |
| ----------------------------- | ---------------- |
| `README.md`                   | 프로젝트 및 협업 과정 설명  |
| `SUBMISSION.md`               | 평가용 제출물 및 증빙 인덱스 |
| `docs/CONTRIBUTING.md`        | 팀 협업 규칙          |
| `docs/conflict-resolution.md` | Git 충돌 해결 기록     |
| `docs/troubleshooting-log.md` | Git 트러블슈팅 기록     |
| `src/`                        | 간단한 결과물          |
| `team/`                       | 팀원별 소개 또는 학습 자료  |

---

# 5. GitHub Flow

이번 프로젝트에서는 GitHub Flow를 적용합니다.

```text
main
  │
  ├── feature/member-topic
  │       │
  │       ├── Commit
  │       └── Commit
  │
  ↓
Pull Request
  ↓
Code Review
  ↓
Review 반영
  ↓
Approve
  ↓
main Merge
```

## GitHub Flow를 선택한 이유

우리 팀은 작업 단위를 Feature Branch로 분리하여 `main`의 안정성을 유지하기 위해 GitHub Flow를 사용합니다.

모든 변경 사항을 Pull Request로 검토하여 코드 리뷰 과정을 보장합니다.

작은 팀에서도 단순한 브랜치 구조로 일관된 협업 흐름을 유지할 수 있습니다.

---

# 6. 브랜치 전략

## `main`

* 팀 기준에서 항상 깨지지 않는 상태를 유지합니다.
* 직접 Push를 금지합니다.
* Pull Request를 통해서만 Merge합니다.
* 최소 1명의 Approve를 받은 후 Merge합니다.

## `feature/*`

모든 기능 및 문서 작업은 Feature Branch에서 진행합니다.

브랜치 이름은 다음 규칙을 사용합니다.

```text
feature/<name>-<topic>
```

예:

```text
feature/kim-math-utils
feature/lee-string-utils
feature/park-contributing
feature/choi-readme
```

---

# 7. Issue 기반 작업

모든 작업은 GitHub Issue로 생성합니다.

예:

```text
Issue #1
팀 협업 규칙 문서 작성

Issue #2
수학 유틸 함수 추가

Issue #3
문자열 유틸 함수 추가

Issue #4
충돌 해결 실습

Issue #5
Troubleshooting Log 작성
```

각 Issue는 Feature Branch 및 Pull Request와 연결합니다.

```text
Issue #2
   ↓
feature/kim-math-utils
   ↓
PR #7
   ↓
Closes #2
```

이를 통해 어떤 작업이 어떤 코드 변경으로 이어졌는지 추적할 수 있도록 합니다.

---

# 8. Commit Message Convention

커밋 메시지는 변경 내용을 명확하게 알 수 있도록 작성합니다.

기본 형식:

```text
type: subject
```

## 사용 가능한 Type

| Type       | 용도           |
| ---------- | ------------ |
| `feat`     | 새로운 기능       |
| `fix`      | 버그 수정        |
| `docs`     | 문서 수정        |
| `refactor` | 코드 구조 개선     |
| `test`     | 테스트 추가 또는 수정 |
| `chore`    | 기타 설정 및 작업   |

## 예시

```bash
git commit -m "feat: add string utility functions"
git commit -m "fix: handle empty string input"
git commit -m "docs: add contributing guide"
git commit -m "refactor: simplify list utility"
git commit -m "test: add string utility tests"
```

## 금지하는 커밋 메시지

다음과 같이 변경 대상을 파악할 수 없는 메시지는 사용하지 않습니다.

```text
update
fix
temp
wip
final
bug fix
edit file
```

커밋 메시지만 확인해도 **무엇을 변경했는지 추측할 수 있도록** 작성합니다.

---

# 9. Pull Request 규칙

모든 Feature Branch는 Pull Request를 통해 `main`에 Merge합니다.

PR 본문에는 최소한 다음 내용을 포함합니다.

```markdown
Closes #이슈번호

## What

- 무엇을 변경했는가?

## Why

- 왜 변경했는가?

## How

- 어떻게 테스트하고 검증했는가?
```

## PR 예시

```markdown
Closes #2

## What

- 문자열 길이를 계산하는 유틸 함수를 추가했습니다.
- 빈 문자열 처리 로직을 추가했습니다.

## Why

- 팀 유틸 함수 모음에 문자열 관련 기능을 추가하기 위해 작업했습니다.

## How

- Python 실행 확인
- 일반 문자열 테스트
- 빈 문자열 테스트
- 특수문자 테스트
```

---

# 10. Code Review 규칙

모든 팀원은 다른 팀원의 PR을 리뷰합니다.

단순히 다음과 같은 리뷰만 작성하지 않습니다.

```text
LGTM
좋아요
확인했습니다.
```

최소 1개 이상의 실질적인 리뷰 코멘트를 작성합니다.

## 실질적인 리뷰 예시

```text
b가 0인 경우 ZeroDivisionError가 발생할 수 있습니다.
이 상황을 호출자가 처리하도록 할지 함수 내부에서
검증할지 결정하면 좋겠습니다.
```

또는:

```text
현재 함수는 빈 문자열을 전달했을 때 예상 결과가
명확하지 않습니다. 빈 문자열을 허용할지 예외 처리할지
정하면 좋겠습니다.
```

또는:

```text
이 부분은 반복문 대신 Python의 내장 함수를 사용하면
코드가 조금 더 간결해질 것 같습니다.
```

## 리뷰 반영 흐름

```text
Reviewer
   ↓
리뷰 코멘트
   ↓
Author
   ↓
답변 / 코드 수정
   ↓
추가 Commit
   ↓
Reviewer 확인
   ↓
Approve
   ↓
Merge
```

리뷰어와 작성자의 상호작용이 GitHub에 기록으로 남도록 합니다.

---

# 11. 팀원별 최소 기여 기준

모든 팀원은 아래 조건을 충족해야 합니다.

| 항목                 | 최소 기준 |
| ------------------ | ----: |
| PR 생성 및 Merge      | 2개 이상 |
| 다른 팀원 PR 리뷰        | 2개 이상 |
| 본인 PR 리뷰 피드백 반영    | 1회 이상 |
| 결과물 기여 Commit      | 1개 이상 |
| Troubleshooting 참여 | 1개 이상 |

예시:

| 팀원 | PR Merge | 타인 PR 리뷰 | 리뷰 반영 | 결과물 Commit | Troubleshooting |
| -- | -------: | -------: | ----: | ---------: | --------------: |
| A  |       2+ |       2+ |    1+ |         1+ |              1+ |
| B  |       2+ |       2+ |    1+ |         1+ |              1+ |
| C  |       2+ |       2+ |    1+ |         1+ |              1+ |
| D  |       2+ |       2+ |    1+ |         1+ |              1+ |

---

# 12. 충돌 해결 실습

Git 협업에서는 여러 사람이 같은 파일의 같은 부분을 동시에 수정할 수 있습니다.

예를 들어 A와 B가 같은 코드를 서로 다르게 수정하면 Git이 어느 변경 사항을 선택해야 하는지 자동으로 결정하지 못할 수 있습니다.

이 경우 다음과 같은 충돌 마커가 나타납니다.

```text
<<<<<<< HEAD
print("Hello Team A")
=======
print("Hello Team B")
>>>>>>> feature/team-b
```

## 충돌 마커 의미

```text
<<<<<<< HEAD
현재 기준 브랜치의 변경 내용

=======
두 변경 내용의 구분선

>>>>>>> feature/team-b
병합하려는 브랜치의 변경 내용
```

충돌은 단순한 Git 오류가 아니라 **두 변경 사항을 자동으로 합칠 수 없기 때문에 사람이 최종 내용을 결정해야 하는 상황**입니다.

---

# 13. 충돌 실습 요구사항

팀 전체 기준으로 최소 2회 이상의 충돌 해결 기록을 남깁니다.

그중 최소 1회는 비자명 충돌이어야 합니다.

## 충돌 예시 1

같은 파일의 같은 hunk를 서로 다르게 수정합니다.

```text
Branch A
→ 같은 함수 수정

Branch B
→ 같은 함수의 같은 부분 수정
```

## 충돌 예시 2

파일 이동 또는 삭제와 내용 수정을 충돌시킵니다.

```text
Branch A
→ example.py를 utils.py로 이름 변경

Branch B
→ example.py 내용 수정
```

---

# 14. 충돌 해결 과정

충돌이 발생하면 다음 과정을 따릅니다.

```text
충돌 발생
   ↓
충돌 파일 확인
   ↓
충돌 마커 확인
   ↓
각 브랜치의 변경 내용 확인
   ↓
팀원 간 해결 방향 결정
   ↓
최종 코드 작성
   ↓
충돌 마커 제거
   ↓
테스트
   ↓
Commit
   ↓
Push
   ↓
PR 업데이트
```

충돌 해결 과정은 `docs/conflict-resolution.md`에 기록합니다.

---

# 15. Conflict Resolution Log

`docs/conflict-resolution.md`에는 다음 내용을 기록합니다.

````markdown
# Conflict Resolution Log

## 충돌 기록 #1

### 참여자

- 작성자: <name>
- 상대: <name>

### 상황

- 어떤 브랜치에서 충돌이 발생했는지
- 어떤 파일에서 충돌이 발생했는지

### 충돌 내용

```text
<<<<<<< HEAD
...
=======
...
>>>>>>> feature/...
````

### 해결 과정

1. 충돌 파일 확인
2. 충돌 마커 확인
3. 양쪽 변경 사항 비교
4. 최종 해결 방향 결정
5. 충돌 마커 제거
6. 테스트
7. Commit 및 Push

### 결과

* 최종 병합 결과
* 관련 PR
* 관련 Commit

### 배운 점

* 충돌이 발생한 원인
* 다음에 예방하기 위한 방법

````

---

# 16. Git Troubleshooting

팀 전체가 다음 4가지 시나리오를 직접 수행합니다.

1. `git commit --amend`
2. `git reset --soft HEAD~1`
3. `git revert`
4. `git stash` / `git stash pop`

모든 과정은 `docs/troubleshooting-log.md`에 기록합니다.

---

# 17. `git commit --amend`

최근 커밋의 메시지 또는 내용을 수정할 때 사용합니다.

예:

```bash
git commit -m "docs: add contributng guide"
````

오타가 있다면:

```bash
git commit --amend -m "docs: add contributing guide"
```

즉, 최근 커밋을 다시 수정하는 상황을 경험합니다.

> 주의: 이미 여러 팀원이 사용하는 공유 커밋의 히스토리를 임의로 변경하면 협업에 문제가 발생할 수 있습니다.

---

# 18. `git reset --soft HEAD~1`

최근 커밋을 취소하지만 변경 내용은 유지합니다.

```text
Commit
  ↓
git reset --soft HEAD~1
  ↓
커밋 취소
  ↓
변경 내용 유지
```

예:

```bash
git reset --soft HEAD~1
```

로컬에서 잘못 만든 최근 커밋을 다시 정리하고 싶을 때 사용할 수 있습니다.

> 공유 브랜치에서 팀 합의 없이 히스토리를 재작성하거나 강제 Push하는 용도로 사용하지 않습니다.

---

# 19. `git revert`

이미 원격에 Push된 커밋의 변경 사항을 되돌릴 때 사용합니다.

```bash
git revert <commit-hash>
```

`reset`과의 차이는 다음과 같습니다.

```text
reset
→ 기존 커밋을 되돌리고 히스토리를 재작성

revert
→ 기존 변경을 취소하는 새로운 커밋 생성
```

따라서 공유된 브랜치에서는 기존 히스토리를 유지하면서 특정 변경 사항을 취소할 수 있습니다.

---

# 20. `git stash` / `git stash pop`

아직 Commit하지 않은 작업을 잠시 보관하고 다른 작업으로 전환할 때 사용할 수 있습니다.

```text
작업 중
  ↓
git stash
  ↓
작업 내용 임시 보관
  ↓
다른 브랜치 작업
  ↓
git stash pop
  ↓
기존 작업 복구
```

예:

```bash
git stash
git switch feature/other-work

# 다른 작업

git switch feature/my-work
git stash pop
```

---

# 21. Troubleshooting Log

`docs/troubleshooting-log.md`에는 각 시나리오를 다음 형식으로 기록합니다.

````markdown
# Troubleshooting Log

## 시나리오: amend

### 참여자

- <name>

### 상황

- 최근 커밋 메시지에 오타가 있었다.

### 시도한 명령 / 절차

```bash
git commit --amend -m "docs: update contributing guide"
````

### 결과

* 최근 커밋 메시지를 수정했다.

### 왜 이 방법을 선택했는가?

* 아직 원격에 공유하지 않은 최근 커밋을 수정하는 상황이었기 때문이다.

### 주의할 점

* 공유된 커밋을 임의로 수정하면 다른 팀원의 작업과 충돌할 수 있다.

````

동일한 형식으로 `reset`, `revert`, `stash/pop` 기록을 추가합니다.

---

# 22. 간단한 결과물

복잡한 기능 구현은 필요하지 않습니다.

다음 중 하나를 선택합니다.

## A. 유틸 함수 모음

```text
src/
├── math_utils.py
├── string_utils.py
├── list_utils.py
└── date_utils.py
````

각 팀원은 최소 1개의 함수를 구현합니다.

예:

```python
def add(a, b):
    return a + b
```

README 또는 docstring에 간단한 사용 예시를 작성합니다.

---

## B. 팀 소개

```text
team/
├── member-a.md
├── member-b.md
├── member-c.md
└── member-d.md
```

README에서 팀원별 소개 문서를 링크합니다.

---

## C. 학습 정리 노트

```text
team/
├── git-basics.md
├── branch.md
├── pull-request.md
└── conflict.md
```

각 팀원이 최소 1개의 학습 노트를 작성합니다.

---

# 23. Git History 증빙

최종 결과물에는 Git 히스토리 증빙을 포함합니다.

다음 명령을 실행합니다.

```bash
git log --oneline --graph --all
```

예:

```text
*   Merge pull request #10
|\
| * feat: add list utilities
|/
*   Merge pull request #9
|\
| * docs: update troubleshooting log
|/
*   Merge pull request #8
|\
| * feat: add string utilities
|/
* Initial commit
```

결과는 텍스트 파일 또는 스크린샷 형태로 제출합니다.

---

# 24. SUBMISSION.md

`SUBMISSION.md`는 평가자가 전체 결과물을 빠르게 확인할 수 있도록 만드는 제출물 인덱스입니다.

예:

```markdown
# Submission Index

## Team

- 팀명: <team-name>
- Repository: <repository-url>

## Member PRs

### <member-name>

- Issue: <issue-url>
- PR: <pr-url>
- PR: <pr-url>
- Review: <review-url>
- Review: <review-url>

### <member-name>

- Issue: <issue-url>
- PR: <pr-url>
- PR: <pr-url>
- Review: <review-url>
- Review: <review-url>

## Key Documents

- [Contributing Guide](docs/CONTRIBUTING.md)
- [Conflict Resolution](docs/conflict-resolution.md)
- [Troubleshooting Log](docs/troubleshooting-log.md)

## Evidence

- Git History: <evidence-url>
- Conflict PR: <pr-url>
- Troubleshooting Records: <document-url>
```

---

# 25. 평가자에게 설명하는 프로젝트 전체 흐름

이번 프로젝트의 전체 협업 과정은 다음과 같습니다.

```text
Issue 생성
    ↓
Feature Branch 생성
    ↓
작업
    ↓
의미 있는 Commit
    ↓
Push
    ↓
Pull Request
    ↓
Code Review
    ↓
리뷰 피드백 반영
    ↓
Approve
    ↓
main Merge
```

그리고 별도로 실제 협업에서 발생할 수 있는 문제를 경험합니다.

```text
충돌 발생
    ↓
원인 분석
    ↓
충돌 해결
    ↓
테스트
    ↓
문서화
```

Git 트러블슈팅도 직접 수행합니다.

```text
amend
reset --soft
revert
stash / stash pop
    ↓
재현
    ↓
해결
    ↓
문서화
```

---

# 26. 평가자 발표용 설명

> 저희 팀은 이번 미션에서 단순히 Git 명령어를 사용하는 것이 아니라, 실제 팀 협업에서 사용하는 GitHub Flow를 경험하는 것을 목표로 했습니다.
>
> 먼저 GitHub 저장소의 `main` 브랜치를 보호하고, 모든 작업을 Feature Branch에서 진행하도록 했습니다. 각 작업은 Issue로 만들고, 작업이 끝나면 PR을 생성하여 다른 팀원의 리뷰를 받은 뒤 `main`에 Merge하는 방식으로 진행했습니다.
>
> PR에는 What, Why, How와 연결된 Issue 정보를 작성했고, 리뷰에서는 단순한 LGTM이 아니라 실제 코드에 대한 개선 의견을 남겼습니다. 또한 리뷰 의견을 실제 수정에 반영하여 리뷰어와 작성자 사이의 협업 과정도 기록으로 남겼습니다.
>
> Git 협업에서 발생할 수 있는 문제도 직접 경험했습니다. 같은 부분을 서로 다르게 수정하는 방식으로 의도적인 충돌을 만들고 해결했으며, 충돌의 원인과 해결 과정을 `conflict-resolution.md`에 기록했습니다.
>
> 또한 `amend`, `reset --soft`, `revert`, `stash/pop` 네 가지 Git 트러블슈팅 시나리오를 직접 수행하고 `troubleshooting-log.md`에 재현 과정과 해결 방법을 기록했습니다.
>
> 최종적으로 `SUBMISSION.md`에서 팀원별 Issue, PR, 리뷰 기록과 주요 문서 및 증빙 자료를 한 번에 확인할 수 있도록 구성했습니다.
>
> 따라서 이 프로젝트의 핵심 결과물은 복잡한 프로그램 자체가 아니라, 팀원들이 Issue부터 Branch, Commit, PR, Review, Merge, 충돌 해결까지 실제 협업 Git Workflow를 수행했다는 기록과 증빙입니다.

---

# 27. 최종 제출 체크리스트

## 저장소

* [ ] 3~5명 모두 실제 Git 작업에 참여했는가?
* [ ] GitHub 저장소가 생성되어 있는가?
* [ ] `main` 직접 Push가 막혀 있는가?
* [ ] PR을 통해서만 `main`에 Merge했는가?
* [ ] 최소 1명 Approve 규칙이 설정되어 있는가?

## 브랜치

* [ ] `main`을 기준으로 작업하는가?
* [ ] `feature/*` 브랜치를 사용하는가?
* [ ] 브랜치 네이밍 규칙이 `CONTRIBUTING.md`에 있는가?

## Issue / PR

* [ ] 각 작업이 Issue로 생성되었는가?
* [ ] PR에 `Closes #이슈번호` 또는 `Fixes #이슈번호`가 있는가?
* [ ] 모든 Feature Branch가 PR을 통해 Merge되었는가?
* [ ] PR에 What / Why / How가 포함되어 있는가?

## 팀원별 PR / 리뷰

* [ ] 모든 팀원이 PR Merge 2개 이상인가?
* [ ] 모든 팀원이 다른 사람 PR 리뷰 2개 이상인가?
* [ ] 모든 팀원이 자신의 PR에서 리뷰 피드백을 1회 이상 반영했는가?
* [ ] 각 PR에 실질적인 리뷰 코멘트가 있는가?
* [ ] 리뷰어와 작성자 간 상호작용이 기록되어 있는가?

## 충돌

* [ ] 충돌을 최소 2회 실제로 발생시켰는가?
* [ ] 최소 1회가 비자명 충돌인가?
* [ ] 충돌 해결 과정이 `conflict-resolution.md`에 기록되어 있는가?
* [ ] 충돌 원인 / 해결 과정 / 결과 / 배운 점이 기록되어 있는가?

## Git 트러블슈팅

* [ ] `git commit --amend`를 수행했는가?
* [ ] `git reset --soft HEAD~1`을 수행했는가?
* [ ] `git revert`를 수행했는가?
* [ ] `git stash` / `git stash pop`을 수행했는가?
* [ ] 모든 시나리오가 `troubleshooting-log.md`에 기록되어 있는가?
* [ ] 모든 팀원이 최소 1개 이상의 시나리오에 참여했는가?

## 결과물

* [ ] 선택한 결과물에 모든 팀원이 최소 1개 이상의 기여 Commit을 남겼는가?
* [ ] README에 결과물 사용 방법 또는 목차가 있는가?

## 증빙

* [ ] `git log --oneline --graph --all` 결과가 있는가?
* [ ] GitHub Issue 링크가 있는가?
* [ ] 팀원별 PR 링크가 있는가?
* [ ] 팀원별 리뷰 링크 또는 증빙이 있는가?
* [ ] 충돌 해결 PR 또는 Commit 링크가 있는가?
* [ ] `SUBMISSION.md`에서 모든 자료를 쉽게 찾을 수 있는가?

---

# 28. 핵심 정리

이 미션에서 가장 중요한 것은

> **"무엇을 만들었는가?"보다 "팀이 Git을 이용해 어떻게 함께 만들었는가?"**

입니다.

전체 과정을 한 문장으로 정리하면 다음과 같습니다.

```text
Issue
→ Feature Branch
→ Commit
→ Pull Request
→ Code Review
→ Review 반영
→ Approve
→ Merge
→ 충돌 / 트러블슈팅 경험
→ 문서화
→ Git History로 증빙
```

즉, 이 미션은 **Git 명령어 암기 과제가 아니라 실제 협업 상황에서 안전하게 변경 사항을 만들고, 검토하고, 충돌과 실수를 해결하는 과정을 경험하는 Git 협업 실습**입니다.
