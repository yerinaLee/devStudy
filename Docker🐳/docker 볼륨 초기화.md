상황 : flyway로 DB 재설계 후 IDE에선 초기화. but docker에서도 초기화해줘야함

## 도커 볼륨까지 완전 초기화

`infra` 폴더에서:
docker compose down -v
docker volume ls`

그리고 다시:
docker compose up -d

> `down -v`가 핵심: **볼륨 삭제**(= DB 데이터/플라이웨이 기록까지 싹 삭제)



