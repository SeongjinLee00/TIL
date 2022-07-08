# HTML_CSS_Bootstrap

[TOC]

## TIL_0203 HTML CSS 첫시간

Web, HTML, CSS, JS

현재의 웹 표준 W3C<<<<<<<<<<<<<<<WHATWG 에서 만듦

'MDN HTML' 검색, 표준에가까운문서

'W3schools' 여기서배워라

'edit in settings.json' 에서 탭2칸4칸 이런거 설정 가능



HTML : 구조생성

CSS : 디자인요소

JS : 기능추가



```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>HTML 웹문서</title>
  </head>

  <body>
    <!-- 주석은 이렇게 쓰는거임-->
    <h1 title="h1태그!!!">나의 첫번째 HTML</h1>
    <p tabindex="1">이것은 본문입니다.</p>
    <p tabindex="2">이것은 본문입니다.</p>
    <p>이것은 본문입니다.</p>
    <span>이것은 인라인 요소</span>
    <a href="https://www.naver.com">네이버로 이동!</a> <!-- a태그는 기본적으로 포커스가 됨 i.e. tap index 가짐 -->

    <p>
      오랜만이에요 여러분
      잘 지내셨나요
    </p>

    <pre>
      오늘은 목요일이에요
      내일만 버티면 주말입니다
    </pre>

    <table>
      <thead>
        <th>ID</th>
        <th>Name</th>
        <th>Major</th>
      </thead>
      <tbody>
        <tr>
          <td>1</td>
          <td>홍길동</td>
          <td>CS</td>
        </tr>
        <tr>
          <td>2</td>
          <td>김철수</td>
          <td>CS</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td>총계</td>
          <td colspan="2">2명</td>
        </tr>
      </tfoot>
      <caption>4반 학생 명단</caption>
    </table>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Form & Input</title>
  </head>
  <body>
    <h1>Form 활용 실습</h1>
    <form action="">
      <div>
        <label for="username">아이디</label>
        <input type="text" name="username" id="username" autofocus>
      </div>

      <div>
        <label for="name">이름</label>
        <input type="text" name="name" value="Seongjin" id="name" disabled>
      </div>  
      
      <div>
        <label for="agreement">개인 정보 수집에 동의</label>
        <input type="checkbox" name="agreement" id="agreement">
      </div><!--br 태그랑 유사함 div태그-->
      <br>
      <input id="html" type="checkbox" name="language" value="html">
      <label for="html">HTML</label>
      <input id="python" type="checkbox" name="language" value="python">
      <label for="python">파이썬</label>
      <input id="python" type="checkbox" name="language" value="java">
      <label for="java">자바</label>
      <br>
      <input id="happy" type="radio" name="mood" value="happy">
      <label for="happy">행복</label>
      <input id="sadness" type="radio" name="mood" value="sadness">
      <label for="sadness">슬픔</label>
      <input id="neutral" type="radio" name="mood" value="neutral">
      <label for="neutral">중립</label> <!--radio 쓸 때 name 통일시켜야 함-->
      <br>




      <input type="submit" value="제출">
    
    
    </form>
  </body>
</html>
```

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>학생 건강 설문</title>
</head>
<body>
  <!-- header -->
  <header>
    <a href="https://edu.ssafy.com/edu/main/index.do#none;">EDU SSAFY</a>
    <h1>SSAFY 학생 건강 설문</h1>
  </header>

  <!-- section -->
  <section>
    <!-- 건강 설문 작성 form -->
    <form action="#">
      <div>
        <label for="name">이름</label><br>
        <input type="text" name="name" id="name" autofocus>
      </div>
      <hr>
      <!-- 지역 -->
      <div>
        <label for="location">지역</label><br>
        <select name="location" id="location">
          <option value="서울">서울</option>
          <option value="대전">대전</option>
          <option value="제주">제주</option>
          <option value="구미">구미</option>
        </select>
      </div>
      <hr>
      <!-- 체온 -->
      <div>
        <p>오늘의 체온을 선택해주세요.</p>
        <input type="radio" name="temperature" id="normal" value="normal" checked>
        <label for="normal">37도 미만</label><br>
        <input type="radio" name="temperature" id="warning" value="warning">
        <label for="warning">37도 이상</label>
      </div>
      <hr>
      <!-- 전송 -->
      <input type="submit" value="제출">
    </form>
  </section>

  <!-- footer -->
  <footer>
    Google 설문지를 통해 비밀번호를 제출하지 마시오.
  </footer>
</body>
</html>
```



CSS->HTML

- .클래스선택자(제일편해보임)

- #아이디선택자

- 속성선택자



1. **동적 의사 클래스**

- **:focus** : tab키로 focus가 맞춰진 상태
- **:link** : 사용자가 아직 한 번도 해당 링크를 누르지 않은 상태 ( a요소 기본 )
- **:visited** : 사용자가 한 번이라도 해당 링크를 누른 상태
- **:hover** : 사용자의 마우스 커서가 위에 올라가 있는 상태
- **:active** : 사용자의 마우스 커서가 클릭중인 상태

2. **상태 의사 클래스**

- **:checked** : input의 checkbox나 raidobutton이 체크된 상태
- **:enabled** : input의 "type=text", select, option에서 사용자가 선택한 상태
- **:disabled** : input의 "type=text", select, option을 사용자가 선택할 수 없도록 만든 상태출처 - [https://aboooks.tistory.com/311](https://aboooks.tistory.com/311)

3. **구조 의사 클래스**

- **:first-child** : 모든 자식 요소 중에서 첫 번째에 위치하는 자식을 선택
- **:last-child** : 모든 자식 요소 중에서 마지막에 위치하는 자식을 선택
- **:first-of-type** : 모든 자식 요소 중에서 첫 번째에 등장하는 특정 요소를 선택
- **:nth-of-type(n)** : 모든 자식 요소 중에서 n번째로 등장하는 특정 요소를 선택
- **:last-of-type** : 모든 자식 요소 중에서 마지막으로 등장하는 특정 요소를 선택
- **:nth-child(n)** : 모든 자식 요소 중에서 n번째에 위치하는 자식을 선택



---------------------------------------------------------------------------------------

- **::first-letter** : 요소의 텍스트에서 첫 번째 글자에 스타일을 적용한다.블록타입의 요소에만 사용 가능하다.

- **::first-line** : 요소의 텍스트에서 첫 줄에 스타일을 적용한다.블록타입의 요소에만 사용 가능하다.

- **::before** : 요소의 콘텐츠 시작부분에 생성된 콘텐츠를 추가한다.

- **::after** : 요소의 콘텐츠 끝부분에 생성된 콘텐츠를 추가한다.



## TIL_0204

b태그랑 strong태그 결과는 같음

i 태그랑 em태그 결과는 같음



radio 버튼들 이름 같아야 택1로 잘 동작함



CSS 정의방법 : 인라인-내부참조-외부참조

CSS 우선순위 : 인라인-아이디-클래스-속성-요소

자손결합자 div span

자식결합자 div > span (뭔가 꽂는것처럼 생겼지?)

일반 형제 결합자 p ~ span

인접 형제 결합자 p + span



- Box model : content-padding-box-margin

 	box-sizing : border-box; 해줘야한다



- inline display

  width, height, 상하 margin&padding 지정 불가능



## TIL_0207

1rem : 16px default

clearfix : 부모요소가 자식 요소만큼 높이를 가져가고 싶을 때 쓴다

(기본적으로 자식이 float이면 부모의 높이는 0)



```html
<!--emmet-->

- `>`  태그를 만들고 들여쓰기
- `*n` 반복
- `+` 줄바꿈 + 다음 태그 추가
- `.` class 지정
- `#` id 지정
- `{content}` 내용 입력
```



top : 100px



## TIL_0208

```html
.clearfix::after{
  clear:both;
  content:'';
  display:block;
}
/* 클리어하는방법 */

예시)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="0208.css">
</head>
<body>
  <div class="clearfix">

    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
    <div class="box">4</div>
    <div class="box">5</div>
    <div class="box">6</div>
    <div class="box">7</div>
    <div class="box">8</div>
    <div class="box">9</div>
    <div class="box">10</div>
  </div>
  
  <div class="box2">clearing 되어서 위의 박스 옆으로 붙지 않아요.</div>
</body>
</html>

.box {
  width : 300px;
  height : 300px;
  background-color: aquamarine;
  float:left;
  margin:20px;
  text-align:center;
  line-height : 300px;
}

.clearfix::after{
  clear:both;
  content:'';
  display:block;
}

.box2 {
  /* width : 1320px; */
  height : 200px;
  background-color: rgb(148, 148, 61);
  /* clear : both; */
  margin : 20px;
  text-align:center;
  line-height: 200px;
}
```



### Flexbox

수평 요소 배열을 쉽게 하려고 쓴다

Flexbox의 구성요소 : Flex container, Flex item



컨테이너속성

1. display : 

   flex, flex-inline 2가지있음

2. flex-direction :

   row(Default), row-reverse, column, column-reverse

3. flex-wrap :

   nowrap : default, 화면 크기에 따라 늘어나고 줄어듦

   wrap : 화면 크기에 따라서 줄바꿈을 하겠다

   wrap-reverse

4. justify-content : 

   flex-start, flex-end, center, space-between, space-around, space-evenly

5. align-content : 

   stretch(기본값), flex-start, flex-end, center, space-between, space-around

6. align-items :

   stretch, flex-start, flex-end, center, baseline

```markdown
- `display` - Flex Container를 정의
- `flex-flow` - `flex-direction` 과 `flex-wrap` 을 줄여서 쓸 수 있음
- `flex-direction` - item들의 주 축(main-axis) 설정
- `flex-wrap` - item들의 줄 바꿈 설정
- `justify-content` - 주 축(main-axis)의 정렬  방법 설정
- `align-content` - 교차 축(cross-axis)의 정렬 방법 설정 (2줄 이상)
- `align-items` - 교차 축(cross-axis)의 정렬 방법 설정 (1줄)
```



아이템속성

```markdown
Flex Item을 위한 속성들
- `order` - Item의 순서를 설정
- `flex` - `flex-grow` , `flex-shrink` , `flex-basis` 에 대한 단축 속성!
- `flex-grow` - Item의 너비 증가(grow) 비율 설정
- `flex-shrink` - Item의 너비 감소(shrink) 비율 설정
- `flex-basis` - Item의 기본 너비 설정
```



  `<a href="/index/">뒤로</a>`

/index/ 에서 앞의 슬래시 있으면 ip와 포트 뒤에서 맨처음 url부터 시작

없으면 현재 있는 위치에서 (/greeting/index) 이런 식으로 붙여서 이동



form에서 label for 값과 inpur id 값 통일시키면 라벨 클릭시 포커싱



