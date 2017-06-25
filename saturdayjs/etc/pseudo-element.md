# Pseudo-Element



<br>



## 0. Overview

> 가상요소에 대해 알아본다.
>
> 최초 작성 : 2017-06-15
>
> 최종 수정 : 2017-06-25

<br>

* 용어 정리
* 가상 클래스와 가상 요소
* 콜론( `:` ) or 이중 콜론( `::` ) 
* 표준 준수와 현실

### 

#### **◎ 참고내용**

- [MDN > 개발자를 위한 웹 기술 > CSS > 가상 요소](https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements)
- 스테판 그레이그 『 전문가를 위한 CSS3 : 그 한계를 넘어서 』 _(출판사 : Bjpublic)_
- 김데레사  『 웹표준 핵심가이드북 II HTML5 + CSS3 』 _(출판사 : 제우미디어)_



<br><br>



## 1. 용어 정리



* **pseudo-element** = **가상 요소** = **의사 요소**  




<br>

## 1-2. 가상 클래스와 가상 요소

* 가상 클래스 (pseudo-class)

  * HTML에서 클래스를 사용하지 않고 특정한 요소들(또는 요소의 상태)을 선택하는 방식

  * ex)

    ```CSS
    /* 네 번째 리스트 항목을 선택 */
    ul li:nth-child(4) {foo: bar;}

    /* 홀수 번째 리스트 항목 모두 선택 : 두가지 모두 가능 */
    ul li:nth-child(2n+1) {foo: bar;}
    ul li:nth-child(odd) {foo: bar;}

    /* 비어있는 div 요소 선택 */
    div:empty {foo: bar;}

    /* 요소가 hover 상태일 때 선택 */
    a:hover {foo: bar;}
    ```

* 가상 요소 (pseudo-element)

  * 요소의 영역을 선택하고 마치 HTML에서 별개의 독립체로서 존재하는 것처럼 이를 요소로 취급

  * ex)

    ```CSS
    /* 문장의 첫 번째 라인을 선택 */
    p:first-line {foo: bar;}

    /* 문장의 첫 글자를 선택 */
    p:first-letter {foo: bar;}

    /* 요소의 전/후 영역을 선택 */
    div:before, div:after {foo: bar;}
    ```

* 구분점

  * 가상 클래스 : 단순히 요소를 선정하는 측면에서 좀 더 통제력을 제공.
  * 가상 요소 : 존재하지 않는 **"유령"** 요소들을 선정하고 스타일링 할 수 있다.

* **사양서 상** 문법적 차이

  ```CSS
  /* 가상 클래스를 위한 사양서 상의 문법 */
  p:first-child {foo: bar;}

  /* 가상 요소를 위한 사양서 상의 문법 */
  div::after {foo: bar;}
  ```

  * 두 용어의 혼동을 막기 위해 사양서 편집자들이 **가상 클래스**에는 콜론 ( `:` )을 **가상 선택자**에는 이중 콜론 ( `::` )을 제시 하였음.



<br>



## 3. 콜론( `:` ) _or_ 이중 콜론( `::` )  



- 가상 요소에 콜론을 하나 사용하는 것과 두 개 사용하는 것 모두 최신 브라우저에서 지원 됨
- **IE 8**에서는 콜론이 하나 있는 가상 요소만을 지원
- 브라우저별 지원 현황 ( 참고 : https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-elements )
  - IE 만 확인하고 넘어가자 !!
  - `:pseudo-element` 를 지원하는 최하위 버전
    - IE 8
    - firefox (Gecko) 1.0 (1.0)
    - Opera 4.0
    - Safari (Webkit) 1.0 (85)
  - `:pseudo-element` ,  `::pseudo-element` 모두 지원하는 최하위 버전
    - IE 9
    - firefox (Gecko) 1.0 (1.5)
    - Opera 7.0
    - Safari (Webkit) 1.0 (85)




<br>

## 4. 표준 준수와 현실



* **IE 9** 이상 대응 시 : 이중 콜론( `::` )을 사용하여 표준을 준수
* **IE 8** 이상 대응 시 : 콜론( `:` )을 사용
* **IE 7** 이상 대응 시 
  * 가상 요소 사용을 위해 `ie7.js` / `ie8.js` / `ie9.js` 와 같은 **polyfill** 추가
  * 콜론( `:` )을 사용





<br><br>



------

<br>



