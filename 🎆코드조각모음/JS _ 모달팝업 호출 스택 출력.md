```
$('#pup1').on('show.bs.modal', function (e) {  
    console.log("pup1 모달 열림!");  
    console.log("relatedTarget:", e.relatedTarget);  // 버튼이나 트리거 element    console.trace(); // 호출 스택 출력  
});
```


출력결과(콘솔) :
![[Pasted image 20250822132501.png]]