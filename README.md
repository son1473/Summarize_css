# Summarize_css
css 중요 내용 정리
## 웹폰트
  폰트는 기본적으로 사용자 환경에도 설치되어 있어야 적용이 가능하다. 상대방이 설치가 되어있지 않아도, 그 폰트를 불러오려면 웹폰트를 사용해야한다.   
  1. 구글 폰트 적용   
  구글폰트를 적용하려면 원하는 구글 폰트의 embed 탭에 들어가 link 소스를 가져오자. html > head에 붙여넣고 css에 들어가 font-familly를 입력하면 적용된다.
  ```
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100&display=swap" rel="stylesheet">
  ```
  2. @font-face 적용   
  구글 폰트 외의 특정한 폰트를 사용하고 싶으면 폰트 파일을 업로드 하고 @font-face를 사용해 불러오면 된다.   
  업로드 하지 않고 싶더라도 src: url("폰트를 가져올 웹주소")을 적용하면 된다.
  ```
  font-face 사용법 https://developer.mozilla.org/ko/docs/Web/CSS/@font-face
  
  @font-face {
	src: url("../fonts/THIS_IS_COOL_FONT.otf"); //파일을 업로드 하고 불러온 모습.
	font-family: "JOHA"; //업로드한 파일을 사용할 때 이름을 JOHA로 하겠다.
  }
  ```
  설치가 되어 있는 폰트를 사용하려는 경우에는 url이 아닌 `local`를 사용하면 된다. 
  ```
  src: local("설치 된 폰트 이름");
  ```
## 선택자
## display
  `block` : 블록 요소는 페이지 전체 길이를 자신의 가로 길이로 가지려는 특성을 가진다.   
  자신 만의 영역을 가지려 해 한 줄 내에 사용하지 못한다.  
  `inline` : 한 줄 내에 있으려는 특성을 가지며, 가로 세로 길이 값을 가지지 않는다. 요소의 가로 세로 길이에 따라 자동적으로 정해진다. 길이가 정해지지 않으므로 마진 값을 가질 수 없다.    
  `inline-block` : inline 요소와 마찬가지로 한 줄 내에 있으려는 특성은 가지나, 가로 세로 길이 값을 가진다. 따라서 마진 값을 가질 수 있다.   
  `list-item` : 생략
## position
  `relative` : 원래 있던 요소의 위치를 기준으로 top left right bottom 등의 값으로 원래 있던 위치에서 벗어나게 한다. 원래 있던 위치는 채워지지 않고 그대로 남아 있는다.   
  `fixed` : 브라우저를 기준으로 움직인다. 페이지 스크롤이 일어나도 브라우저를 기준으로 설정되어 있기에 고정되어 있다.    
          보통 고정 네비게이션 바를 만들 때 쓰인다. 원래 있던 위치는 다음 내용으로 채워진다.   
  `static` : 기본 값, 포지셔닝이 안 된 요소. static을 제외 하고는 다 포지셔닝이 된 요소이다.   
  `absolute` : 가장 가까운 포지셔닝이 된 조상 요소가 기준이다. 조상 요소 중에 포지셔닝이 된 것들이 있다면, 그 중 가장 가까운 것이 기준이라는 것. 원래 있던 위치와 전혀 관계 없고, bottom 10 을 주면 가장 가까운 포지셔닝 된 조상요소의 바닥에서 10px 떨어진 곳에 위치하게 된다.
## float
  `float` 공중에 둥둥 뜬다는 의미를 생각하자. 페이지 레이아웃을 잡을 때 사용하는 기법 중 하나로, 글 본문 안에 이미지를 삽입할 때 이미지를 글 중간에 위치하기 위한 기법이다.   
  플로트를 사용한 요소는 공중에 뜨게 되며 밑에 있는 요소는 그 밑으로 올라온다. 그래서 위에서 봤을 때는 두 요소가 겹쳐보이는 효과를 가진다.
  이 겹쳐보이는 효과로 인해 밑에 있던 요소는 블록 요소 부분이 가려지지만 다행스럽게도 밑에 있던 그 요소의 인라인 요소 부분은 가려지지 않는다.   
  이로써 이미지 옆에 글이 자연스럽게 적힐 수 있다. 인라인 요소는 플로트 된 요소에 가려지지 않는 특성을 가진다.
### Grid layout
  `float`를 여러 번 사용(`multiple float`)하면 그리드 레이아웃을 만들 수 있다.   
  ```
  그리드 연습하기 https://jsfiddle.net/9og2tnw8/14/
  ``` 
  [그리드 연습하기](https://jsfiddle.net/9og2tnw8/14/)
### clear   
앞서 `float`를 통해 사진 주위로 글을 쓰는 방법을 배웠다면, 이번엔 사진 주위로 글자가 따라붙지 않게 하는 방법을 배워보자. 여기 `clear`를 이용하자.   
clear는 취소하다는 의미로 `float` `left` 와 `right` 을 취소 할 수 있다.
여기서 중요한 것은 `float: left` 에는 `clear: left`만 적용이 된다는 점. `clear: right`을 적용할 수 는 없는 노릇이다.   
양 옆 사이에 있는 그리드가 왼쪽은 `float left` 오른쪽은 `float right` 가 되어 있을 때 둘 다로부터 도망치는 방법은 `clear both`를 사용하면 된다.   
  
**※ 그리드 테두리 만들기** : 그리드를 감싸고 있는 div 혹은 body에 `border: 5px solid black;`를 적용해보자. div내에 그리도 요소가 있음에도 불구하고, 전부 떠 있기 때문에 밑에 요소는 없어 높이가 0이라는 결과가 나온다. 이로인해 테두리가 위에만 감싸는 원치않는 결과가 발생한다. 이를 clear로 해결하면 된다.
```
.clearfix {
  clear: left;
}
```
clearfix 클래스를 가진 div는 clear 속성을 통해 맨 밑으로 가게 되고 결과적으로 테두리가 맨 밑까지 이어진다.
  

## 가로 가운데 정렬
### grid 가운데 정렬   
grid를 감싸고 있는 div에 margin: 0 auto; 를 먼저 주자 (float 된 상태 이므로 변화가 없을 것이다.)   
grid를 감싸고 있는 div의 넓이가 전체를 차지하고 있을 경우이기에 안에 있는 요소들의 정확한 넓이 합을 주면 된다.   
즉 `max-width: 정확한 넓이 합;`을 주면 된다.
	
	
	
## 세로 가운데 정렬
  baseline의 개념을 알아야 한다.   
  ```
  vertical-align 개념 https://opentutorials.org/course/718/3903
  ```
  
### line-height   
  인라인 박스의 높이를 지정한다. 👉👉 글을 적는 칸의 높이를 정해준다는 의미이다.   
  따라서 세로 가운데 정렬을 하려면, 
  1. 글 적는 칸의 높이를 전체높이로 설정(높이 px값 설정이 선전제이다.)해주고,   
  2. 안에 있는 요소에 `display: inline-block` 와 `vertical-align: middle`를 주면,   
  전체 높이를 먹은 칸의 가운데에 입력이 되기 때문에 세로 가운데 정렬이 된다.
  ```
  line-height 개념 https://opentutorials.org/course/718/3902
  실습 https://jsfiddle.net/804ytm5p/37/

  /*이런 식으로 사용.*/
  main {
    height: 720px;
    line-height: 720px;
  }
  
  main .info {
    display: inline-block;
    line-height: normal;
    vertical-align: middle;
  }
  ```
## 마진 겹침 현상
```
상하 마진 값이 겹치는 현상https://opentutorials.org/course/2418/13464
```

## 반응형 웹
@media 미디어 쿼리
```
@media (max-width: 767px) {
}
```
