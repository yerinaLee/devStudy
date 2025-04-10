
라테일 주소
https://la.happytuk.co.jp/la/index?MODE=LIVE&isMobile=false


라테일 : template12



gameMainAction

템플릿 101이면 
lostArkMainAction 여기로 넘어감

이 안에 jp로 분기처리?


cdn 복제 
-> 

/ht-platform-cdn/web_images/tw/template/ge

하위폴더 전체

/qa-platform-cdn/web_images/jp/template/closers 복제



mangot5 ->

happytuk

co.jp

src/com/jc/view/template-common12.xml


라테일 로그인 주소
https://la.happytuk.co.jp/web/login?gname=la

로그인
결제포인트?
회원가입
카테고리 목록 = menuList['NAV_BOX']
WebContent/WEB-INF/jsp/game/layout/template102/common/navbar.jsp

로그인하니까 template 7 , 99로 넘어가네..?


놉 로그인같은 공통페이지는 jsp/globalPortal 하위로 넘어감



공통헤더는 숨김처리만 ㄱㄱ~



<a class="dropdown-item" href="/game/ge/storey">遊戲背景</a> <!--STOREY -->
<a class="dropdown-item" href="/game/ge/classInfo">角色介紹</a>
<a class="dropdown-item" href="/game/ge/features/detail?contentNo=59315">遊戲特色</a> <!-- GUIDE -->
<a class="dropdown-item" href="/game/ge/beginner/detail?contentNo=59302">遊戲教學</a> <!-- BEGINNER -->



문의 링크

게임관련문의:
https://www.happytuk.co.jp/web/member/inquiry?gname=la

쿠폰페이지:
https://www.happytuk.co.jp/web/coupon/main?gname=la


faq
https://la.happytuk.co.jp/game/la/faq

내문의내역
https://www.happytuk.co.jp/web/member/inquiry/list?gname=la
비밀번호확인
https://www.happytuk.co.jp/web/member/myaccount/before?gname=la&ref=/web/member/inquiry/list


내 문의내역 누르면 이렇게된다고..?
http://dev.happytuk.co.jp/Index/Member/Login?gname=closers&ref=/Index/Service/Customer?categoryNo=69

온라인충전 : 충전페이지
교환코드 : 쿠폰페이지



JP 라테일 쿠폰페이지
https://www.happytuk.co.jp/web/login?gname=la&ref=/web/coupon/main%3Fgname%3Dla
https://www.happytuk.co.jp/web/coupon/main?gname=la

/web/coupon/main?gname=la




JP 라테일 결제페이지
https://la.happytuk.co.jp/web/billing/softbank/request?gname=la

/web/billing/softbank/request?gname=la



가야되는 페이지:
<a class="dropdown-item paymentLink" href="https://qa.happytuk.co.jp/web/billing/softbank/request?gname=closers">線上儲值</a>
<a class="dropdown-item couponLink" href="/web/coupon/main?gname=closers">兌換序號</a>



WebContent/WEB-INF/jsp/game/layout/games/ge/header.jsp

WebContent/WEB-INF/jsp/game/layout/header_pages_2.jsp


내 비번:
$2a$10$.APA3uMnoBQCnRpL8YRupuRNh9MWYXId1qjy8GIKg00Yya8B6FNiu

/api/otp/selfvalidate

개인정보보호정책
「특별거래법」및「자금결제법」


valid = OTP.otpValidate(secretString, userInputValidateCodeString); 여기서 not 뜬듯





- [ ] 어느게시판 어디에 뭐가 있고 어떤거랑 연결되는건지 보기
url이랑 DB 컬럼이랑



### /storey
`LostArkGuideController.gameStoreyAction`
--> `getContentTitleName`
	--> `(happy) getMenuListJSON` 에서 menu tb 리스트 가져옴 //  
	order("location", "ASC")  
	order("displayOrder", "ASC")
	
![[Pasted image 20250409131323.png]]
	display_order에 따라 나오는 순서가 달라짐 (backoffice에서 설정 가능)
	
	-- 가져와서 NAV_BOX 만 빼옴
	-- 거기서 parentTitle(gnb_title1 html), menuTitle(storey html) 세팅

--> `cmsSao.GetContentArticleListJSON`
	--> `UrlParseToJsonBean.GetContentsGroupNoJSON` -> `(happy) GetContentsGroupNoJSON` 게임의 content_type 가져옴
		jcgf responses는 이렇게 옴 ㅇㅇ
	
![[Pasted image 20250409164705.png]]

	--> contentGroupNo 갖고 `(happ) GetContentArticleListJSON` : 게임별로 정렬조건 세팅해서 게시글 싹 가져옴


화면 : `common102Storey`

그런데 content_type에 storey가 없음! 요청하면 생성하셈,,,





### 사용 table 정보
menu 상단 nav 메뉴와 하위메뉴



### 기존 게시물 insert 쿼리(guide)
기존 게임 가이드 그대로 insert하는 쿼리
```
INSERT into content_article(begin_date_time , comment_count , content , content_group_id , content_no , content_title , date_created , end_date_time , hit_count , img_url , is_banner_post , is_inquiry_post , is_launcher_post , is_main_post , keyword , last_updated , launcher_bannerurl , link_url , main_bannerurl , movieurl , register_date_time , sub_content , summary , thumnail_name , side_bannerurl , game_name , gname , attch_file_url , allow_voting_count , is_hidden_article , date_shown) 
select begin_date_time , comment_count , content , content_group_id , content_no , content_title , date_created , end_date_time , hit_count , img_url , is_banner_post , is_inquiry_post , is_launcher_post , is_main_post , keyword , last_updated , launcher_bannerurl ,link_url , main_bannerurl , movieurl , register_date_time , sub_content , summary , thumnail_name , side_bannerurl , game_name , gname , attch_file_url , allow_voting_count , is_hidden_article , date_shown 
from content_article ca
where content_group_id = (SELECT id FROM content_group cg
WHERE cg.game_id = (SELECT id FROM game WHERE short_name='cls')
AND cg.content_group_name='cls_GUIDE')
;
```





### menu html 수정

nav_menu1

```
<a class="dropdown-item" href="/game/closers/story">遊戲背景</a> <!--STORY -->
<a class="dropdown-item" href="/game/closers/classInfo">角色介紹</a>
<a class="dropdown-item" href="/game/closers/features/detail?contentNo=59315">遊戲特色</a> <!-- GUIDE -->
<a class="dropdown-item" href="/game/closers/beginner/detail?contentNo=59302">遊戲教學</a> <!-- BEGINNER -->
```



nav_menu2




4/10
- [ ] content_type 생성 (shop, update) 
update - 신규생성. CST048
shop - TW에 있어서 CST041로 이어서함


- [ ] update, shop 페이지 추가해야함
- ~~update 추가중~~~ -> notice꺼 가져오면된대욤 완료
- shop



기존 게시판별 menuTitle 메뉴타이틀 일본어로 바꿔야한다~


- [ ] index에 게시판들 정렬해?
- [ ] mobile에도 gnbtitle 클릭하면 넘어가게 ㄱㄱ