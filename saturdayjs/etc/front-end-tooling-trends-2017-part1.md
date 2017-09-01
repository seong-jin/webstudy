# 2017년 프론트엔드 기술 트렌트 Part 1 - CSS



<br>



* 작 성 자 : 어성진
* 최초 작성 : 2017-07-03
* 최종 수정 : 2017-07-04




안녕하세요. 삼성카드 고도화 프로젝트에서 퍼블리싱을 맡고 있는 과장 어성진입니다.

최근 웹에 관한 정보들이 무수히 쏟아지고 있는데요.
퍼블리셔로서 알아두면 좋을 상식과 최근 각광 받고 있는 프론트엔드개발 관련 기술들에 대해,
개인적으로 정리해 보고, 회사 동료분들과 정보 공유도 할 겸, 오랜만에 게시판에 글을 쓰게 되었습니다.

글재주가 좋지 않아 지루한 글이 될지도 모르나 아무쪼록 많은 관심 부탁 드리며,
오류가 있는 내용(링크 등)에 대해서는 댓글로 정정 요청 부탁드립니다.

본 글은 Part 1 (CSS) 와 Part 2 (JavaScript)로 분리하여 작성되며,
추후 내용추가/오류수정 등으로 업데이트 될 예정입니다.


본 글과 함께 하기 [주요 참고내용]을 같이 보시면 내용을 이해하는데 많은 도움이 되리라 생각합니다.

[주요 참고내용]
* Front-end Tooling Trends for 2017 : https://www.sitepoint.com/front-end-tooling-trends-2017
* Developer-rodadmap : https://github.com/kamranahmedse/developer-roadmap
* CSS 방법론 : http://wit.nts-corp.com/2015/04/16/3538


그럼 출발~~



2017년 프론트엔드 기술 트렌트 Part 1 - CSS


1. Pre-processor
    CSS를 확장하는 스크립팅 언어. 컴파일러를 통하여 브라우저에서 사용할 수 있는 일반 CSS 문법 형태로 변환한다.
    (브라우저는 Pre-processor의 문법을 인식하지 못하므로 실제 사용을 위해선 CSS로의 변환과정이 필요하다.)
    변수/중첩/믹스인/선택자상속 등의 기능을 제공한다.

* Pre-processor의 종류 : Sass / Less / Stylus / etc

1-1. Sass : Syntactically Awesome Styles Sheets
    변수 / 중첩(Nesting)표현 / 믹스인(Mixins) / 함수 / 익스텐션(Extension) / 연산 / 보간법(Interpolation) 등 다양한 기능 제공

* 컴파일 방식에 따라 다음 3가지 방식으로 사용 가능
* Sass 참고 내용
    http://sassbreak.com/ruby-sass-libsass-differences/
    http://velopert.com/1712

1-1-a. 오리지널 Ruby-Sass 사용
    Ruby 환경에서 Sass를 설치 / 컴파일 한다.
    [참고] Mac OS에는 Ruby가 기본 설치되어 있으며, Windows 에서는 별도 설치해야 함.

1-1-b. GUI 어플리케이션 사용
    CodeKit (Mac)[유료]
    Compass.app (Mac, Windows, Linux)[유료/오픈소스]
    Ghostlab (Mac, Windows)[유료]
    Hammer (Mac)[유료]
    Koala (Macm Windows, Linux)[오픈소스]
    LiveReload (Mac, Windows, Linux)[유료/오픈소스]
    Prepros (Mac, Windows, Linux)[유료]
    Scout (Mac, Windows)[오픈소스]

1-1-c. LibSass 사용
    Sass는 원래 Ruby로 작성되었으나 C 언어로 작성된 LibSass 를 사용하면,
    더 이상 Ruby에 종속되지 않고 많은 Wrapper를 사용할 수 있으며,
    거의 모든 언어와 Sass를 쉽게 통합할 수 있다.
    또한, Ruby-Sass 대비 최대 4000% 빠른 컴파일 성능을 갖는다.

* Wrappers : SassC / Go / Java / JavaScript / Lua / .NET / Node / Perl / PHP / Python / Ruby / Scala
* Wrappers 중 Node 환경의 Node-Sass가 많은 인기를 얻고 있다.

1-2. Less
    Bootstrap framework 사용자 증가로 인기가 높아짐
    (참고) 최근 Bootstrap 4 에서는 Sass를 사용하고 있음


2. PostCSS
    JavaScript Plugin을 이용한 CSS 변환도구로 pre-processor와 구별된다.

2-1. Autoprefixer
    설정된 브라우저에 대한 vendor prefix를 자동 제공해 준다.
    https://github.com/postcss/autoprefixer

[input]
:fullscreen {
}

[output]
:-webkit-:full-screen {
}
:-moz-:full-screen {
}
:full-screen {
}

2-2. cssnext
    새로운 CSS spec 사용 시, 현 브라우저에 따르는 호환구문을 자동 제공해 준다.
    http://cssnext.io

[input]
:root {
    --red: #d33;
}
a {
    &:hover {
        color: color(var(--red) a(54%));
    }
}

[output]
a:hover {
    color: #dd3333;
    color: rgba(221, 51, 51, 0.54);
}

2-3. CSS Modules
    naming 중복방지를 위해 사용되며, 자동으로 적절한 naming을 생성해 준다.
    https://github.com/css-modules/css-modules

[input]
.name {
    color: gray;
}

[output]
.Logo__name__SVK0g {
    color: gray;
}

2-4. stylelint
    CSS 문법오류를 자동체크해 주며 Scss 및 최신 CSS구문도 지원함
    https://stylelint.io
    * 3-2. CSS 코딩 컨벤션 자동화 도구 참고

2-5. LostGrid
    calc() 를 사용하는 분수기반 그리드 시스템 제공
    https://github.com/peterramsing/lost

[input]
div {
    lost-column: 1/3;
}

[output]
div {
    width: calc(99.9% * 1/3 - (30px - 30px * 1/3));
}
div:nth-child(1n) {
    float: left;
    margin-right: 30px;
    clear: none;
}
div:last-child {
    margin-right: 0;
}
div:nth-child(3n) {
    margin-right: 0;
    float: right;
}
div:nth-child(3n + 1) {
    clear: both;
}


3. Tools

3-1. CSS 코딩 컨벤션 자동화 도구
    문법오류 점검
    협업 시, 통일성을 유지하기 위해 사용하는 도구
    Sublime Text / Atom / Bracket / Visual Studio Code 등 Editor의 확장기능으로 사용

3-1-a. stylelint
    CSS 문법 오류 자동체크

3-1-b. Stylefmt
    css나 scss파일의 컨벤션을 강제하며, 규칙에 맞게 자동으로 코드를 변경해 준다.
    세세하게 설정 가능.
    설정 파일은 stylelint 작성법에 따른다.

(참고)
    * JSLint / JSHint / ESLint :  JavaScript 문법 오류 자동 체크
    * Prettier : JavaScript 코드 자동 정리


◎ Lint / JSLint / JSHint / ESLint
http://hyeonjae.github.io/javascript/2015/04/19/javascript-linter.html
http://blog.outsider.ne.kr/1007

* Lint : 컴퓨터 프로그래밍에서 에러가 발생할 만한 코드를 미리 알려주는 것
* 정적 분석 : 실행하지 않고 잠재적인 오류를 찾아 알려주는 것

Unix와 C언어가 만들어지던 1970년대에 YACC를 만든 사람이 처음으로 C언어용 Lint를 만든 것에서 시작
JavaScript는 스크립트 언어로 실행 중이 아닐 때는 정확한 분석이 어려워 이런 도구들이 생겨났다.

(1) JSLint
    더글라스 크락포드가 만든 JavaScript 정적 분석 도구
    규칙이 매우 엄격함

(2) JSHint
     JSLint에서 파생되어 안톤 코발료프가 관리하고 있는 툴
     대부분의 옵션을 선택적으로 켜고 끌 수 있다.

(3) ESLint
    자카스가 개발하고 관리하고 있는 툴


4. CSS Frameworks

Bootstrap : http://getbootstrap.com/
Zurb Foundation : http://foundation.zurb.com/
Materialize CSS : http://materializecss.com/
Semantic UI : http://semantic-ui.com/
Pure.css : https://purecss.io/
Bulma : http://bulma.io/
etc


5. CSS Grid System (Tutorial Site)

모두 영문사이트라 불편함이 있지만 CSS Grid System에 대한 기본을 익히고 싶으신 분들은
하기 두 사이트 만은 한 번 훑어 보시기 바랍니다.

http://flexboxfroggy.com/
http://cssgridgarden.com/

5-1. Flex Box
    https://css-tricks.com/snippets/css/a-guide-to-flexbox/
        전체 속성을 확인할 수 있는 기초 강좌
    http://flexboxfroggy.com/
        게임을 통해 flex를 쉽게 익힐 수 있는 사이트
        개구리를 연꽃 잎 위에 올리면 성공.

5-2. Grid Layout
    http://learncssgrid.com/
        전체 속성을 확인할 수 있는 기초 강좌
    http://cssgridgarden.com
        게임을 통해 gird를 쉽게 익힐 수 있는 사이트.
        당근에 물을 주면 성공.
    http://gridbyexample.com/
        예시, 패턴모음, 비디오 강좌, 리소스 등 grid 관련 다양한 정보


6. CSS 방법론 or CSS Naming Schemes(이름 설계방법)

* 참고링크 : http://wit.nts-corp.com/2015/04/16/3538
* 종류 : SUITCSS / Systematic CSS / BEM / OOCSS / SMACSS / etc

커스텀 모듈 제작, 타부서와의 협업 등의 이유로 최근 CSS 방법론이 중요시 되고 있다.

코드 재사용성을 높이고, 유지보수를 쉽게 하고, 확장 가능하며,
클래스명 만으로도 무슨 의미인지 예측 가능하도록 하는 것을 목표로 함

6-1. OOCSS : Object Oriented CSS
    CSS 모듈 방식으로 코딩하여 중복을 최소화 하는 기법

6-2. BEM : Block Element Modifier
    현재 프론트엔드개발 분야에서 가장 많이 사용되고 있는 CSS 방법론

    * Block : 문단 전체에 적용된 element  또는 element를 담고 있는 컨테이너를 말한다.
        ex) logo / login form / menu / search form / content / footer
    * Elemnent : block 안에서 특정 기능을 수행하는 컴포넌트. element는 상황에 따라 달라진다.
    * Modifier : block 또는 element의 속성. 이 속성은 block 또는 element의 외관이나 상태를 변화시킨다.

6-3. SMACSS : Scalable and Modular Architecture for CSS
    Jonathan Snook에 의해 만들어진 CSS 방법론
    CSS에 대한 확장형 모듈식 구조
    CSS의 프레임워크가 아닌 하나의 스타일 가이드   

SMACSS의 핵심은 범주화(Categorization)이다.
CSS 규칙을 범주화 함으로써 패턴을 체계적으로 정리하게 되면,
코드량이 감소하고,  유지보수가 용이해지며, 스타일에 일관성을 줄 수 있다.
​    
* SMACSS의 5가지 규칙
    Base : 기본규칙 (Reset, Default, Variables, Mixins, etc)을 정의
    Layout : 페이지를 섹션으로 나누는 것으로 하나 이상의 모듈을 포함한다.
    Module : 재사용 또는 조함 가능한 단위
    State : 레이아웃과 모듈이 어떻게 표현되는지를 나타냄
    Theme : State 보다 큰 개념