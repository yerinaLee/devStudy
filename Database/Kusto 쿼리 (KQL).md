
Kusto 쿼리는 데이터를 처리하고 결과를 반환하기 위한 읽기 전용 요청입니다. 요청은 읽기, 작성 및 자동화하기 쉬운 데이터 흐름 모델을 사용하여 일반 텍스트로 명시됩니다. Kusto 쿼리는 하나 이상의 쿼리 문으로 이루어집니다.


특징
- 대소문자 구별

select 문
```
StormEvents
| where StartTime between (datetime(2007-11-01) .. datetime(2007-12-01))
| where State == "FLORIDA"
| count
```


create문
```
.create table Logs (Level:string, Text:string)
```



## KQL 연산자

**where**
- has

**extend** : 결과값에 열을 추가함
```
StormEvents
| project EndTime, StartTime
| extend Duration = EndTime - StartTime
```

| EndTime              | StartTime            | Duration |
| -------------------- | -------------------- | -------- |
| 2007-01-01T00:00:00Z | 2007-01-01T00:00:00Z | 00:00:00 |
| 2007-01-01T00:25:00Z | 2007-01-01T00:25:00Z | 00:00:00 |


**project** : 해당 데이터를 표기함

```
StormEvents
| project StartLocation = BeginLocation, TotalInjuries = InjuriesDirect + InjuriesIndirect
| where TotalInjuries > 5
```

| StartLocation | TotalInjuries |
| ------------- | ------------- |
| LYDIA         | 15            |
| ROYAL         | 15            |
| GOTHENBURG    | 9             |
| PLAINS        | 8             |
