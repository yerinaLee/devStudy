### MariaDB 10.2.x에서 JSON 처리 방법

1. **`JSON` 타입**: MariaDB 10.2 버전부터는 `JSON` 데이터 타입을 지원하지만, 이 버전에서는 `JSON` 타입을 직접적으로 사용할 수 없고, **`TEXT`** 또는 **`LONGTEXT`** 타입으로 JSON 데이터를 저장합니다.
    
2. **JSON 관련 함수**: MariaDB 10.2.x 버전에서는 JSON 데이터를 처리하는 기본적인 함수들을 사용할 수 있습니다. 다만, 10.3 이상에서 제공되는 기능에 비해 제한적입니다.
    

### 1. **JSON 데이터 저장**

MariaDB 10.2에서 `JSON` 데이터를 `TEXT`나 `LONGTEXT` 데이터 타입으로 저장합니다.

```
CREATE TABLE my_table (
    id INT PRIMARY KEY,
    data TEXT
);

INSERT INTO my_table (id, data)
VALUES (1, '{"name": "John", "age": 30}');
```

### 2. **JSON 데이터 조회**

MariaDB 10.2 버전에서는 `JSON_EXTRACT()`와 같은 함수로 JSON 데이터에서 값을 추출할 수 있습니다. 단, MariaDB 10.3 이상에서는 `JSON` 타입을 공식적으로 지원하기 때문에 더 많은 기능이 추가됩니다.

```
SELECT JSON_EXTRACT(data, '$.name') AS name FROM my_table;
```

이 쿼리는 `data` 컬럼에서 JSON 객체의 `name` 필드를 추출합니다.

### 3. **JSON 데이터 수정**

MariaDB 10.2 버전에서는 JSON 데이터를 수정하는 데 `JSON_SET()`과 같은 함수를 사용할 수 없습니다. 대신 `TEXT` 컬럼을 직접 업데이트하거나 JSON 데이터를 문자열로 처리할 수 있습니다.

```
UPDATE my_table
SET data = '{"name": "John", "age": 31}'
WHERE id = 1;
```
### 4. **JSON 데이터 포함 여부 확인**

`JSON_CONTAINS()`와 같은 함수를 사용하여 특정 데이터가 JSON 객체 내에 포함되어 있는지 확인할 수 있습니다.

```
SELECT * FROM my_table
WHERE JSON_CONTAINS(data, '{"age": 30}');
```



