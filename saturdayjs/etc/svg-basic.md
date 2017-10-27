
# SVG 기초 내용 정리 (작업율 50%)


[TOC]

<br>



## 1. SVG 란

* **S**calable **V**ector **G**raphics
* 백터기반 이미지로 모든 미디어 사이즈에 대응
* 외부파일로 적용 : `<img>` 요소를 사용하여 이미 만들어진 SVG파일을 HTML에 적용
  ```html
  <img src="our_first.svg" alt="SVG 이미지">
  ```
* HTML 내부에 작성 : SVG파일은 XML 타입으로 작성되어 있으므로, HTML에 직접 작성할 수 있다.
  ```html
  <svg>
    <!-- SVG detail code -->
  </svg>
  ```




<br>

## 2. Level 1 - Basic Drawing Ⅰ

### 2-0. SVG 설정

가장 먼저 SVG가 보일 창을 설정해야 된다.

* SVG 사이즈 설정 : SVG를 그리는 프레임이나 캔버스를 `뷰포트(viewport)` 라고 한다.
* SVG Namespace 와 version 지정 : (HTML 요소가 아닌) SVG 요소를 사용할 것임을 브라우저에 알린다.

```html
<svg height="100" width="100" xmlns="http//www.w3.org/2000/svg" version="1.1">
  <!-- SVG detail code -->
</svg>
```



<br>

### 2-1. SVG 기본 속성

* 좌표
  > 기준 : CSS의 position 속성과 같이 (0, 0)는 왼쪽 상단
  > (10, 20) 위치표현 : `x="10" y="20"`
* fill
  > 색 채우기 속성으로 기본값은 black( `#000000` ) 이다.




<br>

### 2-2. Rectangles

* `rect` 요소를 사용하여 직사각형 그리기
* **주의** : `rect` 와 같이 닫는 태그가 없는 단일 태그 형식일 경우 **`/>`** 로 태그를 마침
  ```html
  <rect property="value" />
  ```

* 예) `rect` 를 이용한 모니터 아이콘 만들기

  > (1) 100(W) * 80(H) 의 직사각형
  > (2) 50 * 80 의 직사각형, 좌표 이동, 흰색으로 채우기
  > (3) 40 * 10 의 직사각형, 좌표 이동

  ```html
  <svg height="300" width="100" xmlns="http//www.w3.org/2000/svg" version="1.1">
    <rect height="80" width="100" />
    <rect height="50" width="80" fill="white" x="10" y="10" />
    <rect height="10" width="40" x="30" y="90" />
  </svg>
  ```




<br>

### 2-3. Stroke 속성

* 70 * 100 사이즈의 흰색 사각형에 색상 `#ff2626` 의 10px 테두리 추가
* 테두리가 추가 될 경우 (0, 0) 의 기준점은 stroke-width 값의 -50% 에 해당되는 부분이 된다.
  * 즉, 두께 10px 테두리의 사각형을 (0, 0)의 위치에 놓으려면 (5, 5)만큼 이동시켜야 된다.

  ```html
  <rect height="100" width="70" fill="white"
      stroke="#ff2626" stroke-width="10" x="5" y="5" />
  ```




<br>

### 2-4. Circle

* `circle` 요소를 사용하여 원 그리기
* 필수 속성 : 원의 중심좌표와 반지름 값
  * `cx` : X축 중심좌표
  * `cy` : Y축 중심좌표
  * `c` : 반지름
* 예) (40, 105) 의 위치에 반지름 3px의 흰색 원 그리기
  ```html
  <circle cx="40" cy="105" r="3" fill="white" />
  ```




<br>

### 2-5. Ellipses

* `ellipse` 요소를 사용하여 타원 그리기
* 필수 속성
  * `cx` : X축 중심좌표
  * `cy` : Y축 중심좌표
  * `rx` : X축 반지름 (radius x axes)
  * `ry` : X축 반지름 (radius y axes)
* 예) (50, 50) 의 위치에 X축 반지름 10px, Y축 반지름 25px의 파란색 원 그리기
  ```html
  <ellipse cx="40" cy="105" r="3" fill="blue"
      rx="10" ry="25" />
  ```




<br>

### 2-6. Rounding Rectangle Corners

* `ellipse` 속성( `rx`, `ry` )을 활용하여 직사각형의 코너에 라운드를 줄 수 있다.
* CSS의 border-radius에 해당
* rx 와 ry 의 값이 같을 경우 두 속성 중 한가지만 입력해도 된다.
* 예) 2-2-2 의 직사각형에 5px 의 라운드 주기
  ```html
  <rect height="100" width="70" fill="white"
      stroke="#ff2626" stroke-width="10" x="5" y="5"
      rx="5" />
  ```




<br>

### 종합예제 - iPhone Icon 만들기

```html
<svg height="110" width="80" xmlns="http//www.w3.org/2000/svg" version="1.1">
  <rect height="100" width="70" fill="white" stroke="#ff2626"
      stroke-width="10" x="5" y="5"
      rx="5" />
  <circle cx="40" cy="105" r="3" fill="white" />
</svg>
```



<br>

### 2-7. Animation

> CSS를 사용하여 Amination 효과 및 일부 스타일 변경이 가능하다.
> (스타일 변경 : 다음 chapter 확인)

* HTML
  ```html
  <svg height="110" width="80" ...> <!-- 이후 코드에서 생략 -->
    <rect height="100" width="70" fill="white" stroke="#ff2626"
        stroke-width="10" x="5" y="5"
        rx="5" />
    <circle class="home-btn" cx="40" cy="105" r="3" fill="white" />
  </svg>
  ```

* CSS
  ```css
  circle.home-btn {
    animation: grow 2s infinite;
    transform-origin: center;
  }
  @keyframes grow {
    0%   {transform: scale(1);}
    50%  {transform: scale(0.8);}
    100% {transform: scale(1);}
  }
  ```



<br><br>

## 3. Level 2 - Basic Drawing Ⅱ

> Circle, Polygon, Line, Text 가 조합된 SVG를 만들어 보자.



### 3-1. Start off with a Circle

* viwport : 268 * 268

* circle
  * 반지름 : 130px
  * 테두리 : `#008b6f`, 7px
  * 색 채움 : 없음

* source

  ```html
  <svg height="268" width="268" ...> <!-- 이후 코드에서 생략 -->
    <circle cx="134" cy="134" r="130" fill="none" stroke="#008b6f" stroke-width="7" />
  </svg>
  ```



<br>

### 3-2. CSS를 활용한 스타일 분리

* SVG 파일의 스타일은 CSS 로 분리 가능하다.

* 단, **좌표 (coordinates) 관련 속성**은 반드시 **인라인 코드로 작성**해야 된다!

* HTML - 좌표값은 CSS로 분리할 수 없음!

  ```html
  <circle cx="134" cy="134" r="130" />
  ```

* CSS - 단위식별자(unit identifier) `px` 사용

  ```css
  circle {
    fill: none;
    stroke: #008b6f;
    stroke-width: 7px;
  }
  ```




<br>

### 3-3. Line

* `line` 요소를 사용하여 라인 그리기
* 필수 속성
  * `x1`, `y1` : 시작 점 좌표
  * `x2`, `y2` : 끝 점 좌표

* 예) 시작점(47, 198) 끝점(221, 198) 인 5px 두께의 검은 선 그리기
  * HTML
    ```html
    <line x1="47" y1="198" x2="221" y2="198" />
    ```
  * CSS
    ```css
    line {
      stroke: black;
      stroke-width: 5px;
    }
    ```

<br>

### 3-4. SVG Text Element

* `text` 요소를 사용하여 SVG에 텍스트 추가하기

* **참고** : `text` 요소는 닫는 태그가 있음

* 필수 속성
  * `x`, `y` : 기준점(anchor)
    * `text` 요소의 기본 기준점은 **좌측하단**이다.

* 추가 속성
  * `text-anchor` : 기준점 변경
    * `start` : 좌측하단 (default 속성값)
    * `middle` : 중앙하단
    * `end` : 우측하단
  * `font-size` : 폰트 사이즈
  * `font-family` : 폰트 종류
  * `stroke` : 테두리 색상
  * `stroke-width` : 테두리 두께
  * `fill` : 색상

* 예) 중앙정렬 (134, 142), 60px #f6f7f3 fantasy 폰트, 3px 검은색 테두리의 `SVG` 문구
  * HTML
    ```html
    <!-- text 요소는 닫는 태그가 있다!! -->
    <!-- 좌표값은 CSS로 분리할 수 없다!! -->
    <text x="134" y="142">SVG</text>
    ```
  * CSS
    ```css
    text {
      font-size: 60px;
      text-anchor: middle;
      font-family: fantasy;
      stroke: #000;
      stroke-width: 3px;
      fill: #f6f7f3;
    }
    ```

<br>

### 3-5. SVG Polygon Element

* `polygon` 요소를 이용하여 다각형 그리기
* 필수 속성
  * `points` : 좌표값
    * `x`, `y` 좌표쌍으로 되어 있으며 각 꼭지점 좌표는 공백으로 구분한다.
    * `points="x1,y1 x2,y2 x3,y3 ..."`
* 예) 검은색 2px 테두리를 가진 `#008b6f` 색상의 삼각형(52,190 134,30 216,190) 그리기
  * HTML
    ```html
    <polygon points="52,190 134,30 216,190" />
    ```
  * CSS
    ```css
    polygon {
      fill: #008b6f;
      stroke: #000; /* 속성값 black 와 동일 */
      stroke-width: 2px;
    }
    ```




<br>

### 3-6 SVG 요소 간 우선 순위
> HTML 에서 코드가 아래쪽에 위치할 수록 화면 위쪽에 노출된다.

#### 완성된 뱃지 유닛

* HTML
  ```html
  <svg height="268" width="268" xmlns="http//www.w3.org/2000/svg" version="1.1">
    <circle cx="134" cy="134" r="130" />
    <line x1="47" y1="198" x2="221" y2="198" />
    <polygon points="52,190 134,30 216,190" />
    <text x="134" y="142">SVG</text>
  </svg>
  ```
* CSS
  ```css
  circle {
    fill: none;
    stroke: #008b6f;
    stroke-width: ;
  }
  line {
    stroke: black;
    stroke-width: 5px;
  }
  text {
    font-size: 60px;
    text-anchor: middle;
    font-family: fantasy;
    stroke: #000;
    stroke-width: 3px;
    fill: #f6f7f3;
  }
  polygon {
    fill: #008b6f;
    stroke: black;
    stroke-width: 2px;
  }
  ```




<br>

## 4. Level 3. Grouping and Control

> SVG 요소에 대한 그룹을 지정하고 Control 하는 방법을 배워보자.



다음시간에 계속.......

<br><br><br><br>















<br><br>

## ◎ 용어정리

* raster image
  * 레스터 이미지 : jpg, png, gif 등 의 픽셀기반 이미지
  * 반대) vector image

<br><br>

---

