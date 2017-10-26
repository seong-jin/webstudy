
# SVG 기초 내용 정리

## ◎ 목차

1. [SVG 란?](#1-SVG-란)
2. [Basic Drawing](#2-Basic-Drawing)


<br>



## 1. SVG 란

* **S**calable **V**ector **G**raphics
* 백터기반 이미지로 모든 미디어 사이즈에 대응
* 외부파일로 적용 : `<img>` 요소를 사용하여 이미 만들어진 SVG파일을 HTML에 적용
  ```html
  <img src="our_first.svg">
  ```
* HTML 내부에 작성 : SVG파일은 XML 타입으로 작성되어 있으므로, HTML에 직접 작성할 수 있다.
  ```html
  <svg>
    <!-- SVG detail code -->
  </svg>
  ```



<br>

## 2. Basic Drawing

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
  * 기준 : CSS의 position 속성과 같이 (0, 0)는 왼쪽 상단
  * (10, 20) 위치표현 : `x="10" y="20"`
* fill
  * 색 채우기 속성으로 기본값은 black( `#000000` ) 이다.



<br>

### 2-2. Rectangles

* `rect` 요소를 사용하여 직사각형 그리기
* **주의** : `rect` 와 같이 닫는 태그가 없는 단일 태그 형식일 경우 `/>` 로 태그를 마침
  ```html
  <rect property="value" />
  ```

* 예) `rect` 를 이용한 모니터 아이콘 만들기

  ```txt
  1. 100(W) * 80(H) 의 직사각형
  2. 50 * 80 의 직사각형, 좌표 이동, 흰색으로 채우기
  3. 40 * 10 의 직사각형, 좌표 이동
  ```

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

## 2-7. Animation

```css
circle.home-btn {animation: grow 2s infinite; transform-origin: center;}
@keyframes grow {
  0%   {transform: scale(1);}
  50%  {transform: scale(0.8);}
  100% {transform: scale(1);}
}
```

```html
<svg height="110" width="80" xmlns="http//www.w3.org/2000/svg" version="1.1">
  <rect height="100" width="70" fill="white" stroke="#ff2626"
      stroke-width="10" x="5" y="5"
      rx="5" />
  <circle class="home-btn" cx="40" cy="105" r="3" fill="white" />
</svg>
```


















<br><br>

## ◎ 용어정리

* raster image
  * 레스터 이미지 : jpg, png, gif 등 의 픽셀기반 이미지
  * 반대) vector image

<br><br>

---
