
`@Modifying`
- JPA에게 이 쿼리가 select가 아닌 INSERT or UPDATE or DELETE 문이라는거 알림

`@Transactional`
- 메서드를 트랜잭션으로 묶음, @Modifying은 무조건 transactional 위에서 작동  

`@Query("update User u set u.tokkenkey = :tokken where u.id = :id")`
- 테이블 명 x 엔티티 클래스명 oint updateTokkenKey(@Param("id") Long id, @Param("tokken") String tokken); // @Param("\[쿼리 내 변수명]") \[변수값]


