1. 도커 컨테이너 이름 확인
`docker ps`
-- 여기서 name 컬럼값 확인


2. SQL파일 실행(SQL문이 있는 로컬 폴더 CMD)
```powershell
docker exec -i <컨테이너이름> psql -U fridge -d fridge < sql/schema.sql
```


예를 들어 컨테이너 이름이 `postgres`면:

```powershell
docker exec -i postgres psql -U fridge -d fridge < sql/schema.sql
docker exec -i postgres psql -U fridge -d fridge < sql/data.sql
```



