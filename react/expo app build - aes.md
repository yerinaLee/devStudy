```
npx eas-cli login
```

-> expo 로그인


```
npx eas-cli build
```

이렇게 하면 .aab 로 구글 플레이스토어 배포용 파일 나옴. APK로 재빌드 하려면 app/eas.json 파일에 아래 코드 입력후

```
    "preview": {
      "distribution": "internal",
      "android": {
        "buildType": "apk"
      }
    },
```

재빌드
```powershell
npx eas-cli build -p android --profile preview
```



첫빌드는 15~20분 사이로 오래걸림