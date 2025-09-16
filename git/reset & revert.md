
## reset 

브랜치를 **나만**!!!! 사용한다면 사용 OK
커밋 기록을 _삭제

```
git commit -m "1"
git commit -m "2"
git commit -m "3"

git reset [1번commit hash]
git push
```

### options
**--hard**
돌아간 커밋 이후의 변경 이력은 모두 삭제


**--mixed**
변경 이력은 모두 삭제, 변경 내용은 unstage에 남아있음
unStage 상태로 코드가 남아있기에 코드 반영하려면 add 후 commit


**--soft**
변경 이력은 모두 삭제, 변경 내용은 stage에 남아있음
`add`명령어 필요없이 바로 commit 진행




## revert

공유 브랜치인 경우 사용
커밋 기록을 _추가

reset과 동일한 결과를 가져오지만 이력은 `Revert "..."`라는 메세지가 추가됨

```
git commit -m "1번 커밋"
git commit -m "2번 커밋"
git commit -m "3번 커밋"

git revert [1번commit hash]
```

