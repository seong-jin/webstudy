# Interview (2017-06-14)



<br>



## 1. Overview

> 질문 내용은 다음과 같으며, 다음 장에서 이 내용을 정리한다. 
>
> 각 장의 세부내용에서 정리 되지 않은 부분의 제목에 [미완] 을 표기한다.
>
> 최초 작성 : 2017-06-14
>
> 최종 수정 : 2017-06-14

<br>

* Web Publising
  * 반응형 설계시 고려사항
  * SVG 정의 및 사용이유
  * position : absolute의 기준
  * 미디어쿼리의 정의
* Front-end Development
  * ???




<br><br>



## 2. Web Publishing



### [미완] 2-1. 반응형 웹디자인(RWD, Responsive Web Design)

#### **◎ 참고내용**

* Ethan Marcotte 『 반응형 웹디자인 』 _(출판사 : webactually)_
* 스테판 그레이그 『 전문가를 위한 CSS3 : 그 한계를 넘어서 』 _(출판사 : Bjpublic)_
* 야무선생님  『 RWD.pdf 』




<br>

<details>

<summary> ♣ RWD에 대한 상세 내용을 보려면 클릭하세요</summary>


#### ◎ 반응형 웹디자인이란

* 웹 사이트가 어떤 상황에 처하든지 감각적으로 반응할 수 있게 하는 기술과 그에 따르는 아이디어를 종합하여 정의한 개념
* 사용자의 환경(스크린 사이즈, 플랫폼, 회전 방향 등)을 고려하여 응답할 수 있도록 제작하는 것


<br>



#### ◎ 반응형 웹디자인의 세 가지 핵심 요소

> Ethan Marcotte

* **유동적 레이아웃**(fluid layout)이 대부분의 역할을 한다.
  * 필요에 따라 레이아웃이 어느 정도까지 늘어나거나 줄어들 수 있게 한다.
  * 고정된 픽셀 너비가 아니라 백분율에 기반한 값을 사용한다.
  * 즉, 요소들이 여유공간을 근거로 너비가 조정된다.
* 유동적 레이아웃은 레이아웃이 완전히 흐트러지지 않는 선에서 최대한 줄이거나 늘릴 수 있다.
  * **미디어 쿼리**를 통해 여러 가지 스크린 너비에 맞추어 별도의 CSS 규칙을 적용할 수 있다.
* **Flexible Image** 가 필요하다.
  * 유동적 레이아웃에 사용되는 이미지는 스크린의 너비에 맞게 자체적으로 줄일 수 있어야 한다.
  * 플렉스 이미지는 `max-width: 100%`를 모든 이미지에 부여하여 간단히 만들 수 있다.
  * 이 설정은 이미지들이 컨테이너보다 더 커지지 않게 하고 이미지 실제 치수보다 더 확장되지 않게 한다.




<br>


#### ◎ [미완] 반응형 웹디자인 고려사항

##### a) RWD.pdf  내용 체크

> 정리 필요

* 콘텐츠 전략 (Content strategy)
* 유연한 그리드 레이아웃 (Flexible grid layout)
* 유연한 이미지 / 미디어 (Flexible images and media)
* 디바이스 픽셀 밀도 (Device Pixel Density)
* 중단점 / 미디어 쿼리 (Breakpoint and Media queries)




<br>


#### ◎ 미디어쿼리

* 미디어쿼리는 각 디바이스 환경을 식별하는 조건 처리 구문으로 CSS3에서 정식 지원

* 설계된 중단점(Breakpoint)에 맞는 최적화된 뷰 디자인을 구현할 수 있다.

* 지원브라우저 : IE 9 이상 (http://caniuse.com/#feat=css-media-resolution)

* 허용되는 미디어 **type**

  * screen 화면
  * print 프린트
  * aural 청각
  * braille 점자
  * handheld 핸드헬드
  * projection 투영
  * tty 텔레타이프라이터
  * tv 텔리비젼
  * embossed 양각
  * speech 음성
  * all

* 미디어 타입 not 은 분명하게 명시되어야 하고, all 키워드는 기본값으로 쿼리에 적용된다.

* 허용되는 미디어 특성

  *  width
  *  height
  *  device-width
  *  device-height
  *  orientation
  *  aspect-ratio
  *  device-aspect-ratio
  *  color
  *  color-iindex
  *  monochrome
  *  resolution
  *  scan
  *  grid

* 조건 연결

  * and
  * or
    * or 연산자 대신 컴마( `,` )를 대신 사용할 수 있다.

* 명시된 조건이 참의 반대인 거짓인지를 테스트하려면 쿼리의 시작부분에 not 키워드를 사용할 수 있다.

* ex

  ```css
  @media screen and (min-width: 350px) and (orientation: portrait), print {
    .exm-box {color: #101010;}
  }
  ```

  * **해석**

    > 매체가 웹 사이트를 보는 데 스크린을 사용하고 있고, 현재 화면 너비(뷰포트)가 적어도 350px 이며 기기의 방향은 세로(초상화처럼 가로보다 세로가 긴 스타일)라면 이 스타일을 적용할 것.
    >
    > 컴마를 사용한 것은 이 스타일이 프린트에 사용될 수 있지만 앞부분의 쿼리가 참이 되는데 반드시 필요한 조건은 아니라는 뜻이다.

  ​


</details>



<br>

### 2-2. SVG 에 대하여

#### **◎ 참고내용**

- 확장 가능한 SVG, 유용함과 한계점 그리고 활용법 http://www.designlog.org/2512464
  - 2014 년 글입니다만, 마루님 블로그에 읽어 볼만한 글들이 많으니 참고로 적어 둡니다.
- 웹에서 SVG 사용하기 실습 가이드 https://svgontheweb.com/ko/




<br>

#### ◎ SVG 란?

* Scalable Vector Graphics
  * 벡터 그래픽을 표현할 수 있게 해주는 XML 형식의 마크업 언어
* 지원브라우저 : IE 9 이상 (http://caniuse.com/#search=svg)



#### ◎ SVG 의 장점

* 하나의 파일(코드)로 모든 디바이스에 대응 가능
  * 디바이스의 물리적 치수는 물론, 픽셀 밀도의 무제한 조합에 유연하게 대응할 수 있다.
* 제작 및 수정 편리
* CSS & JS로 구현가능
* 높은 압축 용량



<br><br>



### 2-3. position: absolute 의 기준

#### **◎ 참고내용**

* [CSS 레이아웃을 배웁시다 中 **position** chapter](http://ko.learnlayout.com/position.html)
* position 속성값을 숙지할 것 ( `static` | `fixed` | `relative` | `absolute` )


<br>


`absolute`는 뷰포트에 상대적으로 위치가 지정되는 게 아니라 **가장 가까운 곳에 위치한 조상 엘리먼트**에 상대적으로 위치가 지정된다.

절대 위치가 지정된 엘리먼트가 기준으로 삼는 **조상 엘리먼트가 없으면 문서 본문(document body)을 기준으로 삼는다.** 

페이지 스크롤에 따라 움직입니다. 



<br><br>



## [미완] 3. Front-end  Development



???







<br><br>



------

<br>



