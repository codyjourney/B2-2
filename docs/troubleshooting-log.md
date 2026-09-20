# Git 트러블슈팅 실습 기록

## 1. git commit --amend
- 시나리오 실습 및 문서 작성
- **문제 상황:** 오타가 포함된 커밋 메시지로 로컬 커밋 생성
- **해결 과정:** `git commit --amend`를 사용하여 메시지 수정
- **검증 결과:** `git log -1`로 메시지 변경 확인 완료

## 2. git reset --soft HEAD~1
- 시나리오 실습
- **문제 상황:** 불필요한 파일이 포함된 커밋을 로컬에 생성함
- **해결 과정:** `git reset --soft HEAD~1`로 커밋 취소 후 변경 사항 유지
- **검증 결과:** `git status`로 스테이징 상태 유지 확인 완료

## 3. git revert
- 원격 푸시 후 복구 담당
- **문제 상황:** 원격에 이미 푸시된 잘못된 코드를 안전하게 되돌려야 함
- **해결 과정:** `git revert <hash>` 명령어로 취소 커밋 생성 후 푸시
- **검증 결과:** `git log`를 통해 revert 커밋 반영 확인

## 4. git stash / git stash pop
- 브랜치 전환 시뮬레이션
- **문제 상황:** 작업 도중 긴급 버그 수정을 위해 다른 브랜치로 이동해야 함
- **해결 과정:** `git stash`로 임시 저장 후 브랜치 이동 및 작업 후 `git stash pop`
- **검증 결과:** `git status`로 작업 내용 완벽 복원 확인



## Log
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Se
    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

    FEAT:Modify Function1

commit 4bc7ec25132d0ae7fa12f50f1af30613bb168e55
Author: name <name@example.com>
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

    FEAT:Modify Function1

commit 4bc7ec25132d0ae7fa12f50f1af30613bb168e55
Author: name <name@example.com>
Date:   Sun Sep 20 13:26:00 2026 +0900
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

    FEAT:Modify Function1

commit 4bc7ec25132d0ae7fa12f50f1af30613bb168e55
Author: name <name@example.com>
Date:   Sun Sep 20 13:26:00 2026 +0900

:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

    FEAT:Modify Function1

commit 4bc7ec25132d0ae7fa12f50f1af30613bb168e55
Author: name <name@example.com>
Date:   Sun Sep 20 13:26:00 2026 +0900

    DOCS:README
:...skipping...
commit 7bb7d8e3fe950ff4dca54a22da623c248276b395 (HEAD -> main, origin/main)
Author: name <name@example.com>
Date:   Sun Sep 20 13:55:00 2026 +0900

    DOCS: Add troubleshooting-log.md

commit e95ec70d0932788c2fb389afc408ce43d91d3736
Author: name <name@example.com>
Date:   Sun Sep 20 13:53:30 2026 +0900

    FEAT: Stash Test

commit 5d5fbad184a67c02233ab9ac9856621c57004b9a
Author: name <name@example.com>
Date:   Sun Sep 20 13:51:31 2026 +0900

    FEAT: Add Function 4

commit 6251abe3bd6aeb1b844b9b31a44829213df7904e
Author: name <name@example.com>
Date:   Sun Sep 20 13:49:20 2026 +0900

    Revert "FEAT: Add Function 3"
    
    This reverts commit 12c37fc9d8d982729f1e90d8156ff450bad7725b.

commit 12c37fc9d8d982729f1e90d8156ff450bad7725b
Author: name <name@example.com>
Date:   Sun Sep 20 13:47:56 2026 +0900

    FEAT: Add Function 3

commit f654959276e42210b194572f6be6a63273dca37a
Author: name <name@example.com>
Date:   Sun Sep 20 13:45:43 2026 +0900

    FEAT: ADD Retry

commit 726de12b8927e316a55e199c19c602f29aeb4a10
Author: name <name@example.com>
Date:   Sun Sep 20 13:35:02 2026 +0900

    FEAT:Modify Function1

commit 4bc7ec25132d0ae7fa12f50f1af30613bb168e55
Author: name <name@example.com>
Date:   Sun Sep 20 13:26:00 2026 +0900

    DOCS:README