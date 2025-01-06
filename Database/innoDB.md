mysql은 주로 `MyISAM`, `InnoDB` 두가지 스토리지 엔진중 하나를 사용한다.

MySQL 5.5 버젼 이후에는 InnoDB를 기본 스토리지 엔진으로 사용된다

#### 1) MyISAM
- MyISAM은 Table과 Index를 각각 다른 파일로 관리
- Read Only기능이 많은 서비스일 수록 MyISAM엔진이 효율적

#### 2) InnoDB
- 트랜잭션 처리가 필요하고 대용량의 데이터를 다루기 위해서는 InnoDB가 효율적
- InnoDB는 `Tablespace` 개념을 사용한다.
- innodb_system 이라는 테이블스페이스로 기본적으로 구성된다.
- mysql 설치시 디폴트로 ibdata 파일이 있음
- 환경변수 : innodb_data_file_path, innodb_data_home_dir