
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
- [x] content_type 생성 (shop, update) 
update - 신규생성. CST048
shop - TW에 있어서 CST041로 이어서함


- [x] update, shop 페이지 추가해야함
- update 추가중~~~ -> notice꺼 가져오면된대욤 완료
- shop


- [ ] 기존 게시판별 menuTitle 메뉴타이틀 일본어로 바꿔야한다~


- [ ] index에 게시판들 정렬해?
- [x] mobile에도 gnbtitle 클릭하면 넘어가게 ㄱㄱ
id값 nav_menu1_mo 이걸로 gnbTitle에 먹여서 menu에서 script 넣었음!


- [x] 다운로드 페이지 안나오는거 수정함 -> 디폴트값 없는 코드들도 모두 수정했음


- [x] １．  Update, shop에 대해서는 Thumnail 형식이 아닌 Notice나 Announce와 같은 List 형식으로 변경 부탁드립니다.  

4/11
- [x] ２．  1의 변경에 따라 Top Page에 표시되는 List에 Update와 shop의 정보가 표시되도록 변경 부탁드립니다.
-어제 이거 하다가 감

badge_hot : notice임


dev(jp)
-Darea=jp -Dmode=TEST -Dapi.domain=10.3.100.111:8080/ -DuseMemcached=false -Dfile.encoding=UTF-8

dev(jp-local)
-Darea=jp -Dmode=TEST -Dapi.domain=10.3.100.111:8080/ -DuseMemcached=false -Dfile.encoding=UTF-8



- [x] event 눌렀을때 type=now안가게...
시알도 안먹힐것같으니까 그냥 탭 띄우고 리스트 띄우자....
아니다 페이지 이상해지니까 그냥 type=now 없애자...

- [x] event 밑에 검색창 있게...

- [ ] /notice 등등에 우측 사이드바 바꾸기... 4/16 done
- [ ] 새로생긴 detail 페이지 다른것들이랑 같이 구색 맞추기...


4/14
- [x] important는 해당 게시판에만 뜨게해달래 ^ㅗ^
* mixNoticeFixedList: important  
* noticeList : 기본

애초에 게시글마다 mixNoticeFixedList 가져올때 해당 게시판의 게시글만 가져오도록 해야할듯? 분기처리 ㄱㄱ?



- [x] event 옆에 뱃지 다르게 나오는거 설정하기
- [x] memcached 102만 이름 수정하는거( _ 100) shop부터 이어서하면댐~~~~


important 게시글 가져오는 포인트

CommonMenuPrepare

250 Line
mixNoticeFixedList = cmsSao.getMixedNoticeArticleByKeywordJSON(request,1,ProjectConstant.ROW_PER_PAGE_COUNT_100, gname, "import");
여기서 가져와서

case 100 : case 101 : case 102 :
request.setAttribute("mixNoticeFixedList", mixNoticeFixedList);

367 Line 여기서 집어넣음

======================================================

그리고 노출되는건 각 update.jsp 페이지에 붙어있는
admin_notice.jsp에서
<c:forEach items="${ mixNoticeFixedList }" var="fixedList" begin="0" end="1">
이걸로 2개만 조절해서 노출됨

아 그런데 짬뽕게시판의 2개가 아니라 특정 게시판의 2개여야하는데...

-> count 변수 넣어서 해결!


======================================

엥 그런데 system 게시판은 important 된건 게시글 내에서 다시 불러와지지않고,
다른 게시판들은 important된것도 게시글 내에서 중복으로 가져와짐 ㅋㅋㅋㅋㅋㅋ

-> important만 

systemList 	= this.getContentArticleList(request, "prepareSystemListCache"	, serviceCode, CONTENT_TYPE_SYSTEM	, ROW_PER_PAGE_COUNT_5);

QA배포하니까또
notice, update가 안보임

WebContent/WEB-INF/jsp/game/layout/template102/common/admin_notice.jsp

<p>${fixedList}</p>
=> 문제원인 : 멤캐시드 수정하는중....헐....


- [x] mixed 호출하는 곳을 일본용도로 따로 메서드 생성(cmsSAO에다가 메서드 만들기~ㄱㄱ)
ㄴ happycode도 메서드 생성해서 추가함!
주석 넣구~~~

포인트는 mixed를 어디서 불러오느냐?
system
update


- [x] 이벤트페이지 페이지네이션 넘어갈때 type now 붙고 게시글 안나옴 -> 주석쳐서 해결


- [ ] 페이지네이션 이슈

이슈 : 게시글이 10개일때 페이지네이션이 2개로 나옴.
게시글이 10개이면 페이지네이션이 나온다..?

이벤트페이지는
fix 포함해서 11개임...

news는 fix포함 10개임

총 리스트엔 10개가 보여지는게맞고
이벤트만 그 이상이 보여짐. 아마 이거때문에 페이지네이션에 오류나는듯

mixNoticeFixedList

- [ ] 나중에!! commonMenuPrepare
newMainMixNoticeFixedListCache_100
이부분도 사실상 게시판타입별로 나눠서 세팅해줘야함 -> 이 멤캐시드를 게시판에서 보고 null인지 아닌지 확인...
그러려면 commonMenu에 메뉴이름이 들어오는지 봐야하는데..? -> url로 세팅해야할듯 ㅠ

아그런데 이건 우선순위는 뒤로 빼놓자... 복잡시럽다


rowPerPageCount 이게 : 8인데
(important제외하고는) 10개나옴

문제 : 화면에 일반게시글이 10개가 나온다
페이지네이션은 잘못된거없음

- [x] ㅋㅎ 페이지네이션 해결책으로 noticeList를 그냥 새로 가져온 rowPerPage로 다시 불러서 덮어씌워버려씀....이거맞나 일단 notice만 이렇게 해서 배포 ㄱㄱ

4/16

- [x] 어제 하던 페이지네이션 테스트 이어서 해보기
게시글갯수 50개정도로 늘려서~~
그.. 중간에 누수가 있는지 확인하기

문제없으면 다른 게시판들도 덮어씌워보고, 
TW 으로 켜서 테스트해보고
이상없으면 QA 배포하기


=> 일단 지금한건 임포턴트 갯수 포함해서 총 10개로 맞춤.
- [ ] 만약 임포턴트 제외하고 해달라고했을때? 만들어서 주석해놓기~

- [x] pagination -> 새로운 rowCount로 게시글 다시 불러오는 코드 작성, JP 테스트 완료
notice, event, system, shop, update

- [x] 로컬에서 pagination TW 테스트 ㄱㄱ~~~ 문제없어보임!!!
기존TW VM
-Darea=tw -Dmode=TEST -Dapi.domain=qa-happycode.mangot5.com:8080/ -DuseMemcached=false -Dfile.encoding=UTF-8

- [x] 페이지네이션 - QA 배포해서 테스트 ㄱㄱ
JP, TW 모두 문제없어보임!


- [ ] 게시판 목록 순서를.. 메뉴 순서대로 바꿔놓기?


[[JP_cls 홈페이지 분석]]
