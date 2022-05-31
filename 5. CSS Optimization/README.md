# CSS Optimization quiz

# CSS Optimization

---

## 1. 🤔 이미지 스프라이트 정의와 장단점

CSS 스프라이트는 **여러 이미지를 하나의 큰 이미지로 결합**합니다. 일반적으로 아이콘에 사용되는 기술(Gmail에서 사용)입니다. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1541ee05-a8ce-4ab5-8359-444bb3f7aab6/Untitled.png)

```tsx
// 이런식으로 사용할 수 있다네요
.icon_rotate{...width:15px;height:15px;background-position:-23px -50px;}
.icon_del{...width:10px;height:13px;background-position:-65px -15px;}
...
```

구현 방법:

1. 스프라이트 생성기를 사용하여 여러 이미지를 하나로 묶어 적절한 CSS를 생성합니다.
2. 각 이미지는 `background-image`, `background-position`, `background-size` 속성이 정의된 해당 CSS 클래스를 갖습니다.
3. 해당 이미지를 사용하기 위해, 요소에 해당 클래스를 추가합니다.

**장점:**

- 여러 이미지에 대한 HTTP 요청 수를 줄입니다(스프라이트 시트당 하나의 단일 요청만 필요합니다.) 그러나 HTTP2를 사용하면, 여러 이미지를 로드하는 것이 더 이상 중요하지 않습니다.
- 이미지 스프라이트(image sprite)를 사용하면 이미지를 다운받기 위한 서버 요청을 단 몇 번으로 줄일 수 있습니다.
- 모바일 환경과 같이 한정된 자원을 사용하는 플랫폼(platform)에서는 웹 페이지의 로딩 시간을 단축해주는 효과가 있습니다.
- 또한, 많은 이미지 파일을 관리하는 대신 몇 개의 스프라이트 이미지(sprite image) 파일만을 관리하면 되므로 매우 간편합니다.
- `:hover`의 상태에서만 나타나는 이미지가 필요할 때, 다운로드되지 않는 이미지를 미리 다운로드하여 깜박임이 보이지 않습니다.

**단점:**

- 사진 합성이 비교적 번거롭습니다.
- 배경 설정 시 각 배경 단원의 정확한 위치를 얻어야 합니다.
- 이미지 추가 시 합성 이미지를 유지할 때는 기존 이미지를 변경하지 않고 아래로만 그림을 추가해야합니다.

[CSS 질문 | Front End Interview Handbook](https://www.frontendinterviewhandbook.com/kr/css-questions#css-%EC%8A%A4%ED%94%84%EB%9D%BC%EC%9D%B4%ED%8A%B8%EB%8A%94-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80%EC%9A%94-%EA%B7%B8%EB%A6%AC%EA%B3%A0-%EB%8B%B9%EC%8B%A0%EC%9D%B4-%ED%8E%98%EC%9D%B4%EC%A7%80%EB%82%98-%EC%82%AC%EC%9D%B4%ED%8A%B8%EC%97%90-%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95%EB%8F%84-%EC%84%A4%EB%AA%85%ED%95%B4%EC%A3%BC%EC%84%B8%EC%9A%94)

[코딩교육 티씨피스쿨](http://www.tcpschool.com/css/css_basic_imageSprites)

## 2. 🤔 CSS in CSS vs CSS in JS

CSS-in-JS는 자바스크립트 코드 내에서 css를 작성하는 방식으로 

1. style 파일을 별도로 관리할 필요가 없고, 

2. **자바스크립트와 CSS 간의 상수 및 함수를 쉽게 공유**할 수 있습니다. 

3. 고유한 클래스 명이 생성되며  (코드 경량화)

4. css가 component scope에서만 적용되어 우선순위 문제가 발생하지 않습니다. 

하지만 라이브러리 설치가 필요하기 때문에 번들의 크기가 커지며, 새로운 의존성이 발생하며, css in css 방식에 비해 css 적용이 느리다는 단점이 있습니다.

작업자의 성향이나 판단이 필요한 부분이나 **개발 효율성에 중점을 둔 컴포넌트 위주의 프로젝트**라면 **CSS-in-JS를 고려**하는 것이 좋습니다. 필요한 컴포넌트 페이지의 CSS 스타일 요소만 로딩하기 때문입니다. 

반면 사용자 편의에 방점을 둔 **인터렉티브한 웹 프로젝트**라면 랜더링 시 모든 **CSS 스타일 요소를 로딩하는 CSS-in-CSS 방식을 권장**합니다.

[CSS/JS 면접 예상 질문 리스트](https://intrepidgeeks.com/tutorial/csjs-interview-expected-questions-list)

[에스코어](https://s-core.co.kr/insight/view/%EC%9B%B9-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%8A%A4%ED%83%80%EC%9D%BC%EB%A7%81-%EA%B4%80%EB%A6%AC-css-in-js-vs-css-in-css/)

## 3. 🤔 CSS 전처리기의 장단점

<aside>
⭐ 종류 : Sass, Less, Stylus

</aside>

CSS 전처리기를 사용하게 되면 selector를 nesting으로 관리할 수 있고, 조건문이나 반복문, 간단한 연산 등을 할 수 있어서 **CSS를 마치 프로그래밍 하듯이 코딩할 수 있다는 장점**이 있다. 단점은 웹에서는 CSS만 동작하기 때문에 전처리기는 직접 동작시킬 수가 없습니다. 따라서 **CSS로 컴파일 후 동작**시켜야 합니다.

### **장점**

- CSS의 유지보수성이 향상됩니다.
- 중첩 선택자를 작성하기 쉽습니다.
- 일관된 테마를 위한 변수사용. 여러 프로젝트에 걸쳐 테마 파일을 공유할 수 있습니다.
- 반복되는 CSS를 위한 Mixins 생성으로 재사용성이 높습니다.
- 코드를 여러 파일로 나눕니다. 
CSS 파일도 나눌 수 있지만, 그렇게 하기 위해서는 각 CSS 파일을 다운로드하기 위한 HTTP 요청이 필요합니다.

### **단점**

- 전처리기를 위한 도구가 필요합니다.
- 다시 컴파일하는 시간이 느릴 수도 있습니다.

## 4. 🤔 SVG

### 장점

우리가 주로 알고 있는 레스터화 이미지 혹은 비트맵 이미지(JPG, GIF, PNG)와 비교했을때 SVG가 가져다주는 장점은 다음과 같습니다.

- **웹사이트 로딩 속도가 빠르다.** 💨SVG는 XML코드이기 때문에 파일의 크기가 작습니다. 사용 사례에 따라서 SVG는 [60%에서 80%정도의 대역폭을 절감](https://vecta.io/blog/comparing-svg-and-png-file-sizes/)한다고 합니다. SVG는 HTML파일에 작성이 될 수 있기때문에 외부 이미지를 가져오기 위해서 HTTP request를 할 필요가 없습니다.
- **어떤 크기에서든 재활용이 가능합니다.** (Future Proof) ♻️SVG는 크기에 따라 이미지가 왜곡되거나 품질이 떨어져 보이지 않습니다. 그렇기 때문에 하드웨어 해상도가 높은 디바이스에서도 품질 저하없이 볼 수 있습니다.
- **SEO 친화적이다.** 💻XML코드에는 *키워드, 설명, 링크* 등이 포함될 수 있습니다. 그래서 해당 콘텐츠를 검색 엔진에서 더 쉽게 인식할 수 있도록 할 수 있습니다.
- **번거로운 작업을 줄일 수 있습니다.** 개발 효율 증대 효과디자이너들은 Figma, Sketch 등에서 디자인한 작업물들을 SVG로 내보낼 수 있습니다. 직접 개발자가 SVG로 다운받을 수도 있습니다.
- **CSS로 디자인 수정이 가능하다.** 또한 개발자가 SVG파일을 코드로 직접 변경할 수 있기때문에 디자이너에게 재요청 및 기다릴 필요가 없어지고 디자이너는 이미지를 수정할 필요가 없습니다.

### 단점

- 너무 복잡한 SVG는 비효율적일 수 있다. 많은 모양, 색상, 그라디언트를 포함하여서 파일 크기가 JPG나 PNG 보다 커지는 경우가 종종 있기 때문에 단점이 될 수 있습니다.
- **최적화** : 다양한 편집툴에서 내보내진 SVG 파일에는 중복되고 쓸모없는 정보가 많이 포함되어 있습니다. 예를 들어, 편집기의 메타 데이터, 주석, 숨겨진 요소가 있습니다. 최적화 되지 않은 경우에는 PNG보다 파일 크기가 커질 수 있기때문에 최적화를 할 수 있는 도구의 도움을 받는 것이 좋을 수 있습니다.

[SVG란? 장단점은?](https://velog.io/@fkszm3/SVG%EB%9E%80)

[data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAYAAADDPmHLAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAASbSURBVHgB7Z0tTytBFIYP914BDiQ4cIADB0EhwYFE8ifq7g/hJ2CRSCQ4kOCobF3ruHk3maS5aSnbdnfPOe/7JE0oCTvTnmc+dvbMsNbr9b5M0PLLBDUSgBwJQI4EIEcCkCMByJEA5EgAciQAORKAHAlAjgQgRwKQIwHIkQDkSAByJAA5EoAcCUCOBCBHApAjAciRAORIAHIkADkSgBwJQI4EIEcCkCMByJEA5EgAciQAOX+MhPX1dTs+Prbt7W3b3d21jY2N6ndgPB7bYDCw4XBor6+v9vHxUb1nIL0Ae3t7dn5+XgV9FhABYuC1v79f/Q4SPD8/28vLi2UmrQA/Cfx34O/wwjXu7u7S9gi/z87O/loyELTr62vb2tqyZcFQcXp6Wv2MXiEb6SaBCDwEWDVFqmykEgABOjo6sqbAtbNJkEaAi4uLRoNfQBmXl5eWhRQCIChlnG6Dk5OTVstrkvACYKLXxJg/D5RZ1hEiE14ABGIVs/26IPgZeoHQAiDwbYz7s4AA0XuB0AIsusizKsrycmRCC+Dhyz84OLDIhBUAra/rHgCgDpGHgbAC7OzsmBc81aUuYQXY3Nw0L3iqS13CCtDFrd8sPNWlLsoIIkcCkBNWAE8JGpGTRcIKgPw9L3iqS13CCvD5+Wle8FSXuoQVAJm8HlK0UAfUJSqhJ4Fvb2/WNcgcjkxoAfDld936oieKhhYAwX96erKuwJ6B6Oni4dcBIEAXvQAC//j4aNEJLwCC30UgUGaGzSIpVgLRC7Q5FKCsLFvG0iwFPzw8tBIUlIGyspDqWcD9/X2jEuDaKCMT6R4GIUBNzAlwzWzBByl3ByNYaK23t7dLP6vHfT6u9/7+bhlZ6/V6X5YYpI0jebRu/mD2wBfSHxCBngAv9ASQ4PDwsErhwvvJE0JGo1EV9H6/72KFsS1SCDAZyFngnh2vVUwSUV4WQUILULZnlR06aMGYqDW1QDN56khZho6+Ghh2DoBgXF1dTZ3koZWvcqWubECdtg0NZUQ+QiakAGjxOA9gHhABj4wXeWyMHgX5/j85Zwi9AXoeD4+n6xJOAASk7nbwkjyCGT0meXg/mcWDYOMsIJwShtaO3mWRHT/odaINCaHmAIsEHyCQOP6tHAHXFKVukSQIsxK4aPDbBnWMdG5ACAHwhUYIfgHzEwwjEXAvQFdHwCzLzc1NiC1jrgXA2I31/Ijbr1HnCEfKuRagq/N/VgXuJLzPB9wKgMBnOITJu8RuBUDXnwHvQ4FLAbDkGrnr/x8MBV7vClwKEHHWPw+vn8mdANlaf8FrL+BOgIytv+Dxs7kSAC0kY+sveOwFXAnQ5bGvbdH0A6m6uBLAw8GPTePtaFk3AmTv/gtYF/A0DLgRgKH1Fzx9VjcCIBuHBU89nRsBkKrFgqfNJm5SwpBGVc7fz/CvWKZRUsk9bS1PvzVMfI+OiiVHApAjAciRAORIAHIkADkSgBwJQI4EIEcCkCMByJEA5EgAciQAORKAHAlAjgQgRwKQIwHIkQDkSAByJAA5EoAcCUCOBCBHApAjAciRAORIAHIkADkSgBwJQI4EIOcfGjV2tEfztqEAAAAASUVORK5CYII=](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIAAAACACAYAAADDPmHLAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAASbSURBVHgB7Z0tTytBFIYP914BDiQ4cIADB0EhwYFE8ifq7g/hJ2CRSCQ4kOCobF3ruHk3maS5aSnbdnfPOe/7JE0oCTvTnmc+dvbMsNbr9b5M0PLLBDUSgBwJQI4EIEcCkCMByJEA5EgAciQAORKAHAlAjgQgRwKQIwHIkQDkSAByJAA5EoAcCUCOBCBHApAjAciRAORIAHIkADkSgBwJQI4EIEcCkCMByJEA5EgAciQAOX+MhPX1dTs+Prbt7W3b3d21jY2N6ndgPB7bYDCw4XBor6+v9vHxUb1nIL0Ae3t7dn5+XgV9FhABYuC1v79f/Q4SPD8/28vLi2UmrQA/Cfx34O/wwjXu7u7S9gi/z87O/loyELTr62vb2tqyZcFQcXp6Wv2MXiEb6SaBCDwEWDVFqmykEgABOjo6sqbAtbNJkEaAi4uLRoNfQBmXl5eWhRQCIChlnG6Dk5OTVstrkvACYKLXxJg/D5RZ1hEiE14ABGIVs/26IPgZeoHQAiDwbYz7s4AA0XuB0AIsusizKsrycmRCC+Dhyz84OLDIhBUAra/rHgCgDpGHgbAC7OzsmBc81aUuYQXY3Nw0L3iqS13CCtDFrd8sPNWlLsoIIkcCkBNWAE8JGpGTRcIKgPw9L3iqS13CCvD5+Wle8FSXuoQVAJm8HlK0UAfUJSqhJ4Fvb2/WNcgcjkxoAfDld936oieKhhYAwX96erKuwJ6B6Oni4dcBIEAXvQAC//j4aNEJLwCC30UgUGaGzSIpVgLRC7Q5FKCsLFvG0iwFPzw8tBIUlIGyspDqWcD9/X2jEuDaKCMT6R4GIUBNzAlwzWzBByl3ByNYaK23t7dLP6vHfT6u9/7+bhlZ6/V6X5YYpI0jebRu/mD2wBfSHxCBngAv9ASQ4PDwsErhwvvJE0JGo1EV9H6/72KFsS1SCDAZyFngnh2vVUwSUV4WQUILULZnlR06aMGYqDW1QDN56khZho6+Ghh2DoBgXF1dTZ3koZWvcqWubECdtg0NZUQ+QiakAGjxOA9gHhABj4wXeWyMHgX5/j85Zwi9AXoeD4+n6xJOAASk7nbwkjyCGT0meXg/mcWDYOMsIJwShtaO3mWRHT/odaINCaHmAIsEHyCQOP6tHAHXFKVukSQIsxK4aPDbBnWMdG5ACAHwhUYIfgHzEwwjEXAvQFdHwCzLzc1NiC1jrgXA2I31/Ijbr1HnCEfKuRagq/N/VgXuJLzPB9wKgMBnOITJu8RuBUDXnwHvQ4FLAbDkGrnr/x8MBV7vClwKEHHWPw+vn8mdANlaf8FrL+BOgIytv+Dxs7kSAC0kY+sveOwFXAnQ5bGvbdH0A6m6uBLAw8GPTePtaFk3AmTv/gtYF/A0DLgRgKH1Fzx9VjcCIBuHBU89nRsBkKrFgqfNJm5SwpBGVc7fz/CvWKZRUsk9bS1PvzVMfI+OiiVHApAjAciRAORIAHIkADkSgBwJQI4EIEcCkCMByJEA5EgAciQAORKAHAlAjgQgRwKQIwHIkQDkSAByJAA5EoAcCUCOBCBHApAjAciRAORIAHIkADkSgBwJQI4EIOcfGjV2tEfztqEAAAAASUVORK5CYII=)

## 5. 🤔  Critical Rendering Path 란 무엇일까요? (주요 렌더링 경로)

브라우저에서 HTML 받고, CSS 읽고, JS 읽고 웹 사이트가 유저의 이벤트에 반응하기 까지 (인터렉션해지기 전까지)의 과정들을 중요 렌더링 경로라고합니다. (쉽게 말해서 브라우저에서 웹 사이트를 띄우기 까지의 경로라고 보면 됩니다.)

웹 성능을 개선하기 위해서는 이 **중요 렌더링 경로**를 개선해야 합니다. 사실 이 과정 사이에서는 엄청나게 많은 과정들이 있고, 개선 방법이 있습니다.

대표적으로 HTML을 파싱이 일어날 때 중간에 HTML 파싱을 막는 동작이 있을 수 있습니다. (HTML 파싱을 막는 리소스를 **블록 리소스**라고 부릅니다.) 블록 리소스는 페인트 과정을 지연시키므로, HTML 파싱을 막는 상황이 발생하지 않도록 해야 하는데, CSS를 불러오는 link 태그를 head 태그 아래에 위치시킨다던가, JS를 불러오는 script 태그를 body의 제일 아래에 위치시키는 방법이 대표적입니다.

## 6. 🤔 리플로우 & 리페인트에 대해서 설명해주세요.

리플로우는 레이아웃 단계부터 다시 합성 & 렌더까지 진행하는 과정입니다.

리페인트는 페인트 단계부터 다시 합성 & 렌더까지 진행하는 과정입니다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9e4392ac-8367-4cd1-8826-c7887ac6a70e/Untitled.png)

리플로우는 DOM에 영향을 주거나, 엘리멘트에 기하학적인 영향 (높이, 넓이, 위치)를 주는 CSS를 변경하는 경우 렌더 트리가 재구성되면서 레이아웃 과정부터 다시 해야하는 경우에 일어나는 현상이고,

리페인트는 리플로우와는 다르게 기하학적인 영향을 주지않는 CSS 속성을 변경하면 레이아웃 과정은 건너뛰고 페인트부터만 다시 시작하는 과정인데 리플로우가 리페인트보다 시간이 더 걸리기 때문에 리플로우를 일으키는 방식의 코딩을 최대한 지양해야합니다. 

## 7. 🤔 리플로우를 발생시키는 속성

```jsx
position / width / height / margin / padding / display / top / left / right / bottom / 
box-sizing / background-color / border-color / text-align / border / border-width / 
font-family / float / font-size / font-weight / line-height / vertical-align / 
white-space / word-wrap / text-overflow / text-shadow ...
```

## 8. 🤔 리페인트를 발생시키는 속성

```jsx
color / border-style / visibility / background / 
background-image / background-position / background-repeat / background-size / 
text-decoration / outline / outline-style / outline-color / outline-width / 
border-radius / box-shadow ...
```

다음 사이트에서 어떤 CSS 속성들이 Reflow(Layout), Repaint(Paint), Composite를 발생시키는지 보여준다.

[CSS Triggers](https://csstriggers.com/)

## 9. 🤔 CSS 사이즈 줄이기

### 🍄 CSS 압축하고 최소화하기

- 압축 : GZip과 Brotil을 사용해 파일을 압축할 수 있다.
- 최소화 : 필요없는 공백을 지우는 과정
    - [terser](https://github.com/terser/terser)
    - Webpack v4부터는 CSS 최소화 기능이 추가되어있다. [https://webpack.js.org/plugins/css-minimizer-webpack-plugin/](https://webpack.js.org/plugins/css-minimizer-webpack-plugin/)

### 🍄 사용하지 않는 CSS 제거

**[UnusedCSS](https://unused-css.com/)**나 **[PurifyCSS](https://purifycss.online/)** 와 같은 유명한 툴이 있지만, 항상 visual regression 테스트도 병행해서 이뤄져야 한다.

CSS-in-JS를 쓰면 이 문제를 해결할 수 있다. 각 컴포넌트가 렌더링에 필요한 CSS가 JS에 포함되어 있기 때문이다. 

- Visual Regression Test (시각적 회귀 테스트)
    
    유닛 테스트, 통합 테스트 등으로 해결되지 않았던 UI의 안정성을 확보하기 위한 테스트
    
    렌더링 된 UI 들을 캡쳐하고 비교함으로써 프로덕을 안정성있게 유지해 나간다.
    
    시각적 회귀 테스트가 왜 필요할까?
    
    - 기능 테스트가 시각적 요소 테스트까지 보장하지는 않는다.
    - 시작적 변화 로그를 기록하고, 버그의 증거를 찾을 수 있다.
    - e2e테스트로 클래스가 있는지 확인할 수 있지만, 클래스의 유무가 시각적 요소가 깨졌는지 안 깨졌는지를 보장하지는 않는다.

## 10. 🤔 requestAnimationFrame()에 대해서 알고 계신가요?

브라우저에게 수행하기를 원하는 애니메이션을 알리고 다음 리페인트가 진행되기 전에 해당 애니메이션을 업데이트 하는 함수를 호출하게 됩니다. 대부분의 브라우저에서는 W3C 권장사항에 따라서 디스플레이 주사율과 콜백의 수가 일치하게 되므로 JS를 이용한 애니메이션 변경보다 `requestAnimationFrame`을 이용한 애니메이션을 변경하는 것이 좋습니다.

최신 브라우저에서 성능과 배터리 수명 향상을 위해 백그라운드 탭이나 `hidden <iframe>` 에서 실행이 중단되는 특징을 가지고 있습니다.

## 11. 화면안 많은 요소의 변경이 필요한 경우 어떤 최적화 기법을 사용할 수 있을까요?

css의 `display : none` 의 경우 레이아웃과 리페인트가 발생하지 않는 특징을 가지고 있습니다. 고로 숨겨진 상태에서 엘리먼트를 변경하고 변경이 모두 끝난 후에 다시 화면에 나타나도록 설정하여 레이아웃 변경을 최소화 하는 최적화 기법을 사용할 수 있습니다.

## 12. 🤔CSS 파일 불러오기

- 기본적으로 CSS는 렌더링 차단 리소스
- DOM은 CSSOM이 있어야 렌더트리가 구상되기 때문에 CSS는 항상 html 최상단 head 태그에 위치하도록 해야한다.
- 특정 조건에서만 필요한 CSS가 있을 때 `media types`이나 `media queries`를 사용하면 불필요한 블로킹을 방지 가능하다.
    
    ```html
    // 모든 경우에 적용 - always render blocking
    <link href="style.css" rel="stylesheet" />
    
    // print될 때만 적용
    <link href="print.css" rel="stylesheet" media="print" />
    
    // 화면 크기 조건이 맞을 때만 적용
    <link href="other.css" rel="stylesheet" media="(min-width: 40em)" />
    ```
    
- 외부 스타일시트를 가져올 때 사용하는 `@import` 사용은 피한다.
    
    import로 가져온 스타일시트는 다음과 같이 작동한다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5bc8a162-2b14-47e3-8b29-e7920069c95f/Untitled.png)
    
    두 파일을 분리한다면 동시에 다운로드가 가능하다.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/078d6cfc-089d-47b1-9113-d21313effbfb/Untitled.png)
    

<aside>
➡️ CSS도 렌더링 차단 리소스이기 때문에 Critical Rendering Path에 영향을 많이 미친다. 따라서 Style sheet를 불러올 때, media type과 media query에 맞춰서 불러오자.

</aside>

# 13. css 파일 블로킹 방지할 수 있는 방법

HTML 을 파싱할 때, css 나 js 를 만나게되면 HTML 파싱을 중단하고 해당 파일을 파싱하거나 다운로드 후 실행하게되는데, 이처럼 HTML 파싱을 차단하는 요소를 블록차단 리소스라고 한다.

- 올바른 실행위치에서 코드 작성하기 → <head> 태그 안에
- media attribute 로 어떤 단말기의 유형인지에 따라 해당 css 를 적용할지를 명시해 불필요한 블로킹을 방지할 수 있다.
- non-critical CSS 의 로드 방식을 변경함으로써 웹 성능을 향상 시킬 수 있다.
    - l**ink ref=”preload” as=”style”** 로 load 이벤트를 막지 않으면서 css 파일을 요청할 수 있다.
    - onload = “this.onload =null ; this.ref=”stylesheet” 로 css 파일이 로드 이벤트 이후에 파싱되고 onload 함수가 제거됨을 보장한다.
    - noscript 태그는 JS 사용이 불가능해도 스타일을 로드할 수 있도록 한다.
    - 관련 자료 : [Preload, Prefetch, Priorities in Chrome](https://medium.com/@koh.yesl/preload-prefetch-and-priorities-in-chrome-15d77326f646)

# 14. 이미지 지연로딩 (lazy-loading)

사용자 화면에 보이는 이미지만 요청하고 사용자가 스크롤을 내려 다른 이미지가 보여야할 때 이미지를 요청하는 지연 로딩을 통해 리소스 요청을 줄일 수 있다.

```html
<!-- 
이런 식으로 loading 프로퍼티에 lazy 속성을 주게 되면
맨 처음에 화면에 보이는 것들은 바로 로딩이 되고,
그렇지 않고 스크롤을 내려야 보이는 것들은 처음에 로딩하지 않고 로딩이 지연이 됩니다.
 -->
<img src="" alt="" loading="lazy" />
```

# 15. css 리소스 요청 개수 줄이기

<link> 로 가져오는 외부 스타일 시트가 아닌, <style>태그로 포함하는 내부 스타일시트를 사용해 외부 css 요청 횟수를 줄일 수 있다. 다만, **내부 스타일시트는 캐싱되지 않으므로 필요한 경우**에만 포함한다.

css 파일은 캐싱해 리소스 요청을 줄일 수 있다. 웹 캐시란 어플리케이션을 빠르게 처리하기 위해 클라이언트에서 서버로 정적 컨텐츠(js, css, 이미지 등)을 요청할 때 이것을 클라이언트 (또는 서버) 캐시에 저장해두고 해당 컨텐츠를 재호출할 때 서버 요청을 통하지 않고 캐시에서 가져와 활용할 수 있다.

웹 캐시의 종류는 브라우저 캐시, 프록시 캐시, 게이트웨이 캐시가 있다.

관련 자료 : [https://hahahoho5915.tistory.com/33](https://hahahoho5915.tistory.com/33)

# 16. 페이지 렌더링 최적화 (레이아웃 최적화)

## CSS 최적화

- css에 복잡한 셀렉터 규칙 사용하지 않기
- DOM 트리와, style 트리를 복잡하게 구성하지 않기
- 애니메이션 요소는 position을 고정하기 (position: absolute, position: fixed)
    - 애니메이션 변경에 따른 레이아웃 변경 하지 않도록 설정
- 레이아웃보다 리페인트를 발생시키는 속성을 활용하기

## 17. 이미지 최적화

웹 화면에 렌더링을 빠르게 하기 위해선, 이미지의 리소스 최적화가 반드시 필요하다. 

- 이미지 자체의 `폭`을 조절하라.
- 최적화된 이미지 `포맷`을 사용하라.
    - JPG : 카메라로 찍은 실제 사진
    - PNG : 만들어진 이미지
- `<img>`에 `width, height` 값을 선언해 `Reflow`를 방지하라.
- `여러 버전의 이미지`를 제공하라.
- 이미지 크기 조절 `툴`을 사용하라.
- `Image CDNs`을 사용하라
- `CSS Sprite` 기법을 사용하라.
- `lazy loading`을 활용하라.

[웹 성능을 위한 이미지 최적화](https://velog.io/@hustle-dev/%EC%9B%B9-%EC%84%B1%EB%8A%A5%EC%9D%84-%EC%9C%84%ED%95%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%B5%9C%EC%A0%81%ED%99%94)

## 18. CSS 파일 지연로딩 (코드 스플리팅)

- 미디어 쿼리에 따른 스플리팅
    
    ```tsx
    <link rel="stylesheet" href="style.css" media="all" />
    <link rel="stylesheet" href="tablet.css" media="(max-width:1024px)" />
    <link rel="stylesheet" href="mobile.css" media="(max-width:767px)" />
    ```
    
- 페이지에 따른 스플리팅
    
    ```tsx
    <!-- 메인페이지 -->
    <!DOCTYPE html>
    <html>
    <head>
      <link rel="stylesheet" href="main.css" />
    </head>
    <body>
    </body>
    </html>
    
    <!-- 뉴스페이지 -->
    <!DOCTYPE html>
    <html>
    <head>
      <link rel="stylesheet" href="news.css" />
    </head>
    <body>
    </body>
    </html>
    
    ```
    
- 콘텐츠에 따른 스플리팅
    
    ```html
    <!DOCTYPE html>
    <html>
    <head>
      <link rel="stylesheet" href="base.css" />
    </head>
    <body>
      <link rel="stylesheet" href="header.css" />
      <header>
        <link rel="stylesheet" href="navigation.css" />
        <nav>
        	<ul></ul>
        </nav>
      </header>
      <link rel="stylesheet" href="content.css" />
      <main class="content">
      	...
      </main>
      <link rel="stylesheet" href="footer.css" />
      <footer>
      </footer>
    </body>
    </html>
    ```
    
    [https://frontdev.tistory.com/entry/더-빠른-페이지-로드를-위한-CSS-최적화](https://frontdev.tistory.com/entry/%EB%8D%94-%EB%B9%A0%EB%A5%B8-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%A1%9C%EB%93%9C%EB%A5%BC-%EC%9C%84%ED%95%9C-CSS-%EC%B5%9C%EC%A0%81%ED%99%94)