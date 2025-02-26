html : 
```
<script src="lib/CryptoJS v3.1.2/rollups/aes.js"></script>
```


js :
```
// secret key 생성
const secretKey = generateSecretKey();
const encryptedEmail = CryptoJS.AES.encrypt(userEmail, secretKey).toString();


// 복호화 코드
const bytes = CryptoJS.AES.decrypt(encryptedEmail, secretKey);
const decryptedEmail = bytes.toString(CryptoJS.enc.Utf8);
```




