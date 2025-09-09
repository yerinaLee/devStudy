```
sudo -l
```



권한 있을때 : 
```
Matching Defaults entries for happytuk on web-01:
...
User user may run the following commands on web-01:
    (ALL) ALL
```

- **`(ALL)`**: 어떤 사용자로도 실행할 수 있다는 의미입니다. 일반적으로는 `root` 권한을 말합니다.
- **`ALL`**: 모든 명령어를 실행할 수 있다는 뜻입니다.

즉, 해당 시스템에서 `root` 계정은 `sudo`를 사용해 어떤 명령어든 실행할 수 있으며, 어떤 사용자로도 실행할 수 있습니다.




권한 없을때 : 
```
Sorry, user user may not run sudo on web-01.
```



