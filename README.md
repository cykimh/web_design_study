# 웹디자인기능사 공부자료

## 레이아웃

0. `.clearfix::before, .clearfix::after {display: block; content: ''; clear: both;}`
1. header
	- logo
	- nav
2. banner
3. slider 
4. content
5. tab-menu
	- tab-btn
	- tab-cont
6. footer
7. layer

## 가로유형
1. 
## 세로유형
1. 메뉴가 왼쪽 로고 밑에 있고, Submenu가 밑으로 나옴
```js
// jQuery hover 함수 사용할수있음
		$(".nav > ul > li").hover(
				function() {
			$(this).find(".submenu").stop().slideDown();
		}, function() {
			$(this).find(".submenu").stop().slideUp();
		})
```
	2. 메뉴가 왼쪽 로고 밑에있고 오른쪽으로 Submenu가 나타남
	
```css
 position: relative; // 이걸로 기준점잡는게 중요
```

```js

	$(".nav > ul > li").hover(function() {
	
}, function () {
	
});
```

## 탭메뉴유형
1. 
```html
<div class="tab-menu">
	<div class="tab-btn">
		<ul>
		<li class="active"><a href="#">공지사항</a></li>
		</ul>
	</div>
</div>
<script>
	var tabBtn = $(".tab-btn > ul > li");
	var tabCont = $(".tab-cont > div");
	tabCont.hide().eq(0).show();
	
</script>
```
## 팝업 유형
1. 레이어팝업 - div태그로 미리만들어놓고 보여주는식임
```html
<div class="layer-bg"></div>
<div class="layer">
	<h2>타이틀</h2>
	<a href="#" class="close">닫기</a>
</div>
```

## 이미지 슬라이드 유형
1. 위아래 슬라이드 - 이미지가 3초에 한번씩 위아래로 전환

```html
<style>
#banner {width: 1200px; text-align: center; height: 360px; overflow: hidden;}
.slide-list .slide-img { position: relative;}
.slide-list .slide-img h2{
	position: absolute; left: 50%; top: 50%; transform: translate(-50%,-50%); 
}
.slide-list .slide-img img {display: block;}
</style>

<section id="banner">
	<div class="slide-list">
		<div class="slide-image"><img src="img/ban01.jpg" alt="이미지"></div>
		<div class="slide-image"><img src="img/ban01.jpg" alt="이미지"></div>
		<div class="slide-image"><img src="img/ban01.jpg" alt="이미지"></div>
	</div>
</section>

<script>
	var currentIndex = 0;
	setInterval(function(){
		if(currentIndex < 2) {
			currentIndex++;
		} else {
			currentIndex = 0;
		}	
		var slidePosition = currentIndex * (-360) + "px";
		 $(".slide-list").animate({top:slidePosition}, 400);
	}, 3000);
</script>
```
2. 페이드효과 - 위아래슬라이드랑 거의 비슷한데 스크립트만 달라짐
```html
<script>
	$(".slide-list").children("div:gt(0)").hide();
	var current = 0;
	
	setInterval(function(){
		var next = current + 1;
		$(".slide-list").find("div").eq(current).fadeOut();
		$(".slide-list").find("div").eq(next).fadeIn();
	  current = next;							 						 
	}, 3000);
</script>
```

3. 좌우 슬라이드
```html
<script>
	var slideCount = $(".slideImg").length;
	var currentIndex = 0;
	var slidePosition;
	
	setInterval(function() {
		slidePosition = currentIndex * (-1200) + "px";
		$(".slide-list").animate({left:slidePosition},400);
	}, 3000);
</script>

```

































