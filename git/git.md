### 1. 원격으로 커밋 밀어올리기(push)

Leopards의 members에 Evie 추가

커밋 메시지: Add Evie to Leopards

아래 명령어로 push

->git push


이미 git push -u origin main으로 대상 원격 브랜치가 지정되었기 때문에 가능

### 2.원격의 커밋 당겨오기(pull)

GitHub에서 Leopards의 members에 Dongho 추가

커밋 메시지: Add Dongho to Leopards

아래 명령어로 pull

->git pull

### 3. pull 할 것이 있을 때 push를 하면?

원격에 먼저 적용된 새 버전이 있으므로 적용 불가
pull 해서 원격의 버전을 받아온 다음 push 가능

### 4. 1. 브랜치 생성 / 이동 / 삭제하기
add-coach란 이름의 브랜치 생성

->git branch add-coach

브랜치 목록 확인

->git branch

add-coach 브랜치로 이동

->git switch add-coach

checkout 명령어가 Git 2.23 버전부터 switch, restore로 분리

💡 브랜치 생성과 동시에 이동하기

->git switch add-coach

기존의 git checkout -b (새 브랜치명)

🗑 브랜치 삭제하기

->git branch -d (삭제할 브랜치명)

to-delete란 브랜치 만들고 삭제해보기

지워질 브랜치에만 있는 내용의 커밋이 있을 경우
즉 다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지울 때는
-d 대신 -D(대문자)로 강제 삭제해야 합니다.

->git branch -D (강제삭제할 브랜치명)

✏️ 브랜치 이름 바꾸기

->git branch -m (기존 브랜치명) (새 브랜치명)

### 5. 서로 다른 브랜치를 합치는 두 방식
merge : 두 브랜치를 한 커밋에 이어붙입니다.

브랜치 사용내역을 남길 필요가 있을 때 적합한 방식입니다.
다른 형태의 merge에 대해서도 이후 다루게 될 것입니다.
rebase : 브랜치를 다른 브랜치에 이어붙입니다.

한 줄로 깔끔히 정리된 내역을 유지하기 원할 때 적합합니다.
이미 팀원과 공유된 커밋들에 대해서는 사용하지 않는 것이 좋습니다.

### 6. merge로 합치기
add-coach 브랜치를 main 브랜치로 merge

main 브랜치로 이동
아래의 명령어로 병합

->git merge add-coach

:wq로 자동입력된 커밋 메시지 저장하여 마무리
소스트리에서 확인

💡 merge는 reset으로 되돌리기 가능
merge도 하나의 커밋
merge하기 전 해당 브랜치의 마지막 시점으로

병합된 브랜치는 삭제
삭제 전 소스트리에서 add-coach 위치 확인

->git branch -d add-coach


### 7. rebase로 합치기
new-teams 브랜치를 main 브랜치로 rebase

new-teams 브랜치로 이동

🛑 merge때와는 반대!
아래의 명령어로 병합

->git rebase main

소스트리에서 상태 확인

main 브랜치는 뒤쳐져 있는 상황

main 브랜치로 이동 후 아래 명령어로 new-teams의 시점으로 fast-forward

->git merge new-teams

new-teams 브랜치 삭제

### 8.Git에서 과거로 돌아가는 두 방식
reset : 원하는 시점으로 돌아간 뒤 이후 내역들을 지웁니다.
revert : 되돌리기 원하는 시점의 커밋을 거꾸로 실행합니다.

### 9. reset 사용해서 과거로 돌아가기
아래 명령어로 커밋 내역 확인

->git log

되돌아갈 시점: Add team Cheetas의 커밋 해시 복사
:q로 빠져나가기

->git reset --hard (돌아갈 커밋 해시)

### 10.reset 하기 전 시점으로 복원해보기

->git reset --hard
 뒤에 커밋 해시가 없으면 마지막 커밋을 가리킴
 
 ### 11. revert 로 과거의 커밋 되돌리기
 
 ->git revert (되돌릴 커밋 해시)
 :wq로 커밋 메시지 저장
