# ⏱️ 1만 시간의 법칙 프로젝트

## 📋 프로젝트 개요

이 프로젝트는 **"1만 시간의 법칙"**을 테마로 한 인터랙티브 웹 페이지를 처음부터 제작하는 실습입니다.

사용자가 자신이 전문가가 되고 싶은 분야와 하루 훈련 시간을 입력하면, 1만 시간을 채우기 위해 필요한 일수를 계산해주는 웹 애플리케이션을 완성해보세요.

> **💡 1만 시간의 법칙이란?**
> 어떤 분야의 전문가가 되기 위해서는 최소한 1만 시간의 훈련이 필요하다는 법칙입니다.

### 🎨 디자인 파일

전체 디자인은 Figma에서 확인할 수 있습니다:

**[📐 Figma 디자인 보기](https://www.figma.com/design/qzhHFtNhksj8gCBG4g6g3D/EST_1%EB%A7%8C-%EC%8B%9C%EA%B0%84%EC%9D%98-%EB%B2%95%EC%B9%99?node-id=0-1&t=WeNofYM807lnE2Pi-1)**

> **💡 팁**: Figma에서 디자인을 확인하면 정확한 색상, 폰트 크기, 이미지 크기, 여백 등을 쉽게 파악할 수 있습니다!

---

## 🎯 학습 목표

- ✅ HTML5 시맨틱 태그와 구조적인 마크업
- ✅ CSS를 이용한 레이아웃 및 스타일링
- ✅ 웹 폰트 활용 (`@font-face`)
- ✅ `position`을 활용한 요소 겹치기 (시계 + 타이틀, 큰따옴표 배경)
- ✅ 모바일 우선(Mobile First) 반응형 디자인
- ✅ 미디어 쿼리를 활용한 화면 크기별 대응

---

## 📁 프로젝트 구조

```
10000hours/
├── images/          # 이미지 리소스 (제공됨)
│   ├── clock.png    # 시계 이미지
│   ├── title.png    # "1만 시간의 법칙" 타이틀 이미지
│   ├── quotes.png   # 큰따옴표 배경 이미지
│   └── click.png    # 클릭 아이콘
├── index.html       # 여러분이 작성할 파일
├── styles.css       # 여러분이 작성할 파일
└── README.md        # 이 파일
```

---

## 🎨 디자인 요구사항

### CSS 변수 정의

프로젝트 전체에서 일관된 디자인을 유지하기 위해 CSS 변수를 정의하여 사용하세요.

```css
:root {
  /* 배경색 */
  --bg-primary: #385e1a;

  /* 강조색 */
  --color-accent: #ffeb3b;
  --color-accent-hover: #fdd835;
  --color-accent-active: #fbc02d;

  /* 텍스트 색상 */
  --text-primary: white;
  --text-secondary: #d3d3d3;
  --text-dark: #333;
  --text-quote: #f5df4d;

  /* 그림자 */
  --text-shadow-green: #5e8908;
  --text-shadow-dark: #1a2800;
  --box-shadow-md: 0 4px 6px rgba(0, 0, 0, 0.2);

  /* 폰트 */
  --font-base: "Malgun Gothic", "Apple SD Gothic Neo", sans-serif;
  --font-quote: "OTEnjoystoriesBA", sans-serif;
  --font-bold: "GmarketSansBold", sans-serif;
  --font-medium: "GmarketSansMedium", sans-serif;
}
```

### 색상 팔레트

```css
/* 배경색 */
background-color: #385e1a; /* 어두운 녹색 */
/* 또는 */
background-color: var(--bg-primary);

/* 강조색 (버튼, 제목) */
color: #ffeb3b; /* 노란색 */
/* 또는 */
color: var(--color-accent);

/* 텍스트 색상 */
color: white; /* 기본 텍스트 */
/* 또는 */
color: var(--text-primary);

color: #d3d3d3; /* 보조 텍스트 */
/* 또는 */
color: var(--text-secondary);

color: #333; /* 버튼 내부 텍스트 */
/* 또는 */
color: var(--text-dark);
```

> **💡 팁**: CSS 변수를 사용하면 색상을 한 곳에서 쉽게 관리하고 변경할 수 있습니다!

### 폰트

프로젝트에서 사용할 웹 폰트:

```css
/* 인용구 폰트 */
@font-face {
  font-family: "OTEnjoystoriesBA";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_two@1.0/OTEnjoystoriesBA.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}

/* 본문 Bold 폰트 */
@font-face {
  font-family: "GmarketSansBold";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/GmarketSansBold.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}

/* 본문 Medium 폰트 */
@font-face {
  font-family: "GmarketSansMedium";
  src: url("https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/GmarketSansMedium.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}
```

---

## 📱 반응형 디자인 가이드

### 모바일 우선(Mobile First) 접근

1. **기본 스타일 (768px 미만)**: 모바일 화면을 기준으로 먼저 작성
2. **미디어 쿼리 (768px 이상)**: 태블릿 및 데스크톱 화면 대응

### 주요 브레이크포인트

```css
/* 모바일: 기본 스타일 (768px 미만) */
/* 태블릿/데스크톱: @media (min-width: 768px) */
```

---

## 🏗️ 페이지 구조

페이지는 다음 7개의 주요 섹션으로 구성됩니다:

### 1. ⏰ Main Title (메인 타이틀)

**구성:**

- 배경: 시계 이미지 (`images/clock.png`)
- 전면: 타이틀 이미지 (`images/title.png`)
- 두 이미지가 중앙에서 겹쳐짐

**레이아웃:**

- 모바일: 시계 125px × 125px, 타이틀 256px × 53px
- 데스크톱: 시계 265px × 265px, 타이틀 562px × 112px

**구현 팁:**

```css
.main-title {
  position: relative;
  height: 130px; /* 모바일 */
}

.main-title img {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.main-title img:first-child {
  /* clock.png - 뒤에 배치 */
  z-index: 1;
}

.main-title .title-icon {
  /* title.png - 앞에 배치 */
  z-index: 2;
}
```

---

### 2. 💬 Quote (인용구)

**텍스트 내용:**

```
"연습은 어제의 당신보다 당신을 더 낫게 만든다."
```

**스타일:**

- 폰트: `OTEnjoystoriesBA`
- 색상: `#f5df4d` (밝은 노란색)
- `font-style: italic`
- `font-weight: bold`
- 모바일: `font-size: 25px`
- 데스크톱: `font-size: 30px`

---

### 3. 📖 Definition Box (정의 박스)

**구성:**

- 배경: 큰따옴표 이미지 (`images/quotes.png`)
- 텍스트: "1만 시간의 법칙" 정의

**텍스트 내용:**

```
"1만 시간의 법칙"은
어떤 분야의 전문가가 되기 위해서는
최소한 1만 시간의 훈련이 필요하다는 법칙이다.
```

**구현 팁:**

```css
.definition-box {
  position: relative;
}

.quote-icon {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: -1; /* 텍스트 뒤로 보내기 */
}

.definition-text {
  position: relative;
  z-index: 1; /* 텍스트가 이미지 위에 오도록 */
}
```

**폰트:**

- 일반 텍스트: `GmarketSansMedium`
- "1만 시간의 법칙" 텍스트: `GmarketSansBold` (크게)

---

### 4. ✍️ Input Section (입력 섹션)

**구성:**

```
나는 [        (예)프로그래밍        ] 전문가가 될 것이다.
그래서 앞으로 매일 하루에 [   (예)5시간   ] 시간씩 훈련할 것이다.
```

**입력 필드 스타일:**

```css
.input-field {
  padding: 8px 10px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  text-align: center;
  background-color: white;
  color: #333;
}

.subject-input {
  width: 120px; /* 전문 분야 입력 - 모바일 */
}

.time-input {
  width: 100px; /* 시간 입력 - 모바일 */
}

/* 태블릿/데스크톱 (768px 이상) */
@media (min-width: 768px) {
  .subject-input {
    width: 180px;
  }

  .time-input {
    width: 150px;
  }
}
```

---

### 5. 🖱️ Calculate Button (계산 버튼)

**텍스트:**

```
나는 매일 몇 시간 훈련을 해야 1만 시간이 될까?
```

**스타일:**

- 배경색: `#ffeb3b` (노란색)
- 텍스트 색상: `#333`
- `border-radius: 38px` (둥근 버튼)
- `box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2)`

**아이콘:**

- 버튼 옆에 클릭 아이콘 (`images/click.png`) 배치
- `display: inline-flex`를 사용하여 버튼과 아이콘을 가로로 배치

---

### 6. 📊 Result Area (결과 영역)

**텍스트 구조:**

```
당신은 [프로그래밍] 전문가가 되기 위해서
대략 [5110]일 이상 훈련하셔야 합니다! :)
```

**스타일:**

- `[프로그래밍]`: 큰 글씨 (40px → 60px), 흰색, `GmarketSansBold`
- `[5110]`: 큰 글씨 (40px → 60px), 흰색, `GmarketSansBold`
- 나머지 텍스트: `GmarketSansMedium`, `#d3d3d3`

---

### 7. 🔘 Action Buttons (액션 버튼)

**두 개의 버튼:**

1. **훈련하러 가기 GO!GO!**

   - 노란색 배경 (`#ffeb3b`)
   - 텍스트 색상: `#333`
   - 모바일: 200px, 데스크톱: 250px

2. **공유하기**
   - 흰색 배경
   - 텍스트 색상: `#333`
   - 모바일: 100px, 데스크톱: 150px

**레이아웃:**

```css
.action-buttons {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 15px;
}
```

---

## 🎯 구현 단계별 가이드

### Phase 1: HTML 구조 작성

1. **기본 HTML 구조 생성**

   ```html
   <!DOCTYPE html>
   <html lang="ko">
     <head>
       <meta charset="UTF-8" />
       <meta name="viewport" content="width=device-width, initial-scale=1.0" />
       <title>1만 시간의 법칙</title>
       <link rel="stylesheet" href="styles.css" />
     </head>
     <body>
       <div class="container">
         <!-- 여기에 섹션들을 추가 -->
       </div>
     </body>
   </html>
   ```

2. **각 섹션별 HTML 작성**

   - Main Title → Quote → Definition Box → Input Section → Calculate Button → Result Area → Action Buttons 순서로 작성

3. **클래스 네이밍 규칙**
   - 의미 있는 이름 사용 (예: `.main-title`, `.result-area`)
   - 하이픈으로 단어 구분 (kebab-case)

---

### Phase 2: CSS 기본 스타일 (모바일)

1. **웹 폰트 정의**

   ```css
   @font-face {
     font-family: "OTEnjoystoriesBA";
     src: url("...") format("woff");
   }
   /* 나머지 폰트도 동일하게 정의 */
   ```

2. **CSS 변수 정의**

   ```css
   :root {
     --bg-primary: #385e1a;
     --color-accent: #ffeb3b;
     --text-primary: white;
     --font-base: "Malgun Gothic", "Apple SD Gothic Neo", sans-serif;
     /* ... 나머지 변수들 */
   }
   ```

3. **전역 스타일 설정**

   ```css
   * {
     box-sizing: border-box;
   }

   body {
     margin: 0;
     font-family: var(--font-base);
     background-color: var(--bg-primary);
     color: var(--text-primary);
     text-align: center;
     line-height: 1.6;
   }

   img {
     max-width: 100%;
     height: auto;
   }

   button {
     font-family: inherit;
   }
   ```

4. **모바일 우선으로 각 섹션 스타일링**
   - 작은 화면에 맞는 폰트 크기, 여백 설정
   - 이미지 크기 조정
   - CSS 변수를 활용하여 일관된 색상과 폰트 적용

---

### Phase 3: 반응형 디자인 (데스크톱)

1. **미디어 쿼리 추가**

   ```css
   @media (min-width: 768px) {
     /* 태블릿/데스크톱 스타일 */
   }
   ```

2. **데스크톱 스타일 조정**
   - 제목 이미지 크기 확대
   - 폰트 크기 증가
   - 여백(padding, margin) 확대
   - 정의 박스 너비 조정 (600px)
   - 입력 필드 너비 확대 (전문 분야: 180px, 시간: 150px)

---

## 📐 주요 CSS 기법

### Position을 활용한 이미지 겹치기

시계와 타이틀 이미지를 중앙에서 겹치기:

```css
.main-title {
  position: relative; /* 부모 요소 */
  height: 130px;
}

.main-title img {
  position: absolute; /* 자식 요소 */
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%); /* 정확한 중앙 정렬 */
}

.main-title img:first-child {
  z-index: 1; /* 뒤에 배치 */
}

.main-title .title-icon {
  z-index: 2; /* 앞에 배치 */
}
```

### 배경 이미지로 활용 (큰따옴표)

```css
.definition-box {
  position: relative;
}

.quote-icon {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: -1; /* 텍스트 뒤로 보내기 */
  opacity: 0.2; /* 선택사항: 투명도 조정 */
}

.definition-text {
  position: relative;
  z-index: 1; /* 텍스트가 앞에 오도록 */
}
```

### 웹 폰트 적용

```css
.quote {
  font-family: "OTEnjoystoriesBA", sans-serif; /* 우선순위 폰트, 대체 폰트 */
}

.def-title-bold {
  font-family: "GmarketSansBold", sans-serif;
}
```

### Flexbox 활용

```css
.action-buttons {
  display: flex;
  flex-direction: row; /* 가로 배치 */
  justify-content: center; /* 중앙 정렬 */
  gap: 15px; /* 버튼 사이 간격 */
}
```

### CSS 변수 활용

일관된 디자인을 위해 CSS 변수를 적극 활용하세요:

#### 변수 정의

```css
:root {
  /* 배경색 */
  --bg-primary: #385e1a;

  /* 강조색 */
  --color-accent: #ffeb3b;
  --color-accent-hover: #fdd835;
  --color-accent-active: #fbc02d;

  /* 텍스트 색상 */
  --text-primary: white;
  --text-secondary: #d3d3d3;
  --text-dark: #333;

  /* 폰트 */
  --font-bold: "GmarketSansBold", sans-serif;
  --font-medium: "GmarketSansMedium", sans-serif;
}
```

#### 변수 사용 예시

```css
/* 버튼 스타일 */
.calculate-btn {
  background-color: var(--color-accent);
  color: var(--text-dark);
  box-shadow: var(--box-shadow-md);
}

.calculate-btn:hover {
  background-color: var(--color-accent-hover);
}

/* 텍스트 스타일 */
.result-text {
  font-family: var(--font-medium);
  color: var(--text-secondary);
}

.highlight-subject {
  font-family: var(--font-bold);
  color: var(--text-primary);
}
```

#### 변수 사용의 장점

- ✅ **유지보수**: 색상 변경 시 한 곳만 수정
- ✅ **일관성**: 전체 디자인의 통일성 유지
- ✅ **가독성**: 의미 있는 이름으로 코드 이해 용이
- ✅ **확장성**: 테마 변경이나 다크 모드 구현 시 편리

### Transition 효과

부드러운 사용자 경험을 위해 transition을 추가하세요:

```css
.calculate-btn {
  transition: all 0.3s ease;
}

.calculate-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 8px rgba(0, 0, 0, 0.25);
}
```

---

## 🌟 추가 도전 과제

기본 구현을 완료했다면, 다음 기능들을 추가해보세요:

1. **애니메이션 효과**

   - 결과 영역이 나타날 때 fade-in 효과 추가 (CSS `@keyframes` 활용)
   - 버튼 hover 시 scale 효과 추가 (CSS `transform: scale()` 활용)

2. **버튼 상호작용 효과**

   - 계산 버튼 클릭 시 active 효과 추가
   - 버튼에 그라데이션 효과 적용

3. **추가 스타일링**

   - 입력 필드에 focus 효과 추가
   - 결과 영역에 박스 그림자 효과 추가
   - 텍스트에 그라데이션 색상 적용

4. **접근성 개선**

   - 모든 입력 필드에 적절한 `label` 태그 추가
   - 버튼에 `aria-label` 속성 추가
   - 키보드 네비게이션 개선 (`:focus` 스타일)

5. **반응형 개선**

   - 태블릿 화면을 위한 중간 브레이크포인트 추가 (예: 768px)
   - 가로/세로 방향 전환 시 레이아웃 최적화

6. **CSS 고급 기법**
   - CSS Grid를 활용한 레이아웃 재구성
   - CSS 변수를 활용한 테마 색상 관리
   - `clamp()`를 활용한 반응형 폰트 크기

---

## 📝 체크리스트

구현이 완료되었는지 확인하세요:

### HTML

- [ ] 모든 섹션이 올바른 순서로 배치됨
- [ ] 모든 이미지에 `alt` 속성이 있음
- [ ] 입력 필드가 올바르게 작성됨
- [ ] 버튼이 모두 포함됨

### CSS

- [ ] 웹 폰트가 정의되고 적용됨
- [ ] CSS 변수를 활용하여 색상과 폰트를 관리함
- [ ] 모바일 우선으로 스타일을 작성함
- [ ] `@media (min-width: 768px)` 미디어 쿼리를 사용함
- [ ] `position`을 활용하여 이미지가 겹쳐짐
- [ ] 모든 버튼에 스타일과 transition 효과가 적용됨
- [ ] 색상이 요구사항과 일치함

### 반응형

- [ ] 모바일(~767px)에서 정상 표시됨
- [ ] 태블릿/데스크톱(768px~)에서 정상 표시됨
- [ ] 이미지 크기가 화면 크기에 따라 적절히 조정됨
- [ ] 폰트 크기가 화면 크기에 따라 적절히 조정됨
- [ ] 입력 필드 너비가 화면 크기에 따라 적절히 조정됨

### 스타일링

- [ ] 버튼에 hover 효과가 적용됨
- [ ] 입력 필드에 적절한 스타일이 적용됨
- [ ] 색상과 폰트가 디자인 요구사항과 일치함
- [ ] 모든 요소가 정렬되고 간격이 적절함

---

## 🎓 학습 참고 자료

### HTML/CSS

- [MDN - position](https://developer.mozilla.org/ko/docs/Web/CSS/position)
- [MDN - transform](https://developer.mozilla.org/ko/docs/Web/CSS/transform)
- [MDN - z-index](https://developer.mozilla.org/ko/docs/Web/CSS/z-index)
- [MDN - @font-face](https://developer.mozilla.org/ko/docs/Web/CSS/@font-face)
- [MDN - Flexbox](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [MDN - Media Queries](https://developer.mozilla.org/ko/docs/Web/CSS/Media_Queries)
- [MDN - CSS Transitions](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions)
- [MDN - CSS Animations](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Animations)

---

## 💡 구현 팁

### 1. 단계별로 진행하기

- 한 번에 모든 것을 구현하려 하지 말고, 섹션별로 나누어 진행하세요.
- HTML → CSS (모바일) → CSS (데스크톱) 순서를 추천합니다.

### 2. 브라우저 개발자 도구 활용

- `F12` 또는 `Cmd+Option+I` (Mac)로 개발자 도구를 열어보세요.
- Elements 탭에서 `position`, `z-index`가 올바르게 적용되었는지 확인하세요.
- 반응형 디자인 모드 (`Cmd+Shift+M` 또는 `Ctrl+Shift+M`)로 다양한 화면 크기를 테스트하세요.

### 3. position 디버깅

- `position: absolute`를 사용한 요소가 예상대로 배치되지 않는다면:
  1. 부모 요소에 `position: relative`가 있는지 확인
  2. `top`, `left` 값이 올바른지 확인
  3. `transform: translate(-50%, -50%)`로 정확한 중앙 정렬 사용

### 4. 웹 폰트 로딩 확인

- 개발자 도구의 Network 탭에서 폰트 파일이 정상적으로 로드되는지 확인하세요.
- 폰트가 적용되지 않는다면 `@font-face`의 URL을 확인하세요.

### 5. 자주 테스트하기

- 코드를 작성할 때마다 브라우저에서 결과를 확인하세요.
- 모바일과 데스크톱 두 가지 화면 크기에서 모두 테스트하세요.
- 다양한 브라우저에서 호환성을 확인하세요.

### 6. 주석 활용하기

- CSS에 섹션별로 주석을 추가하여 코드를 구조화하세요.

```css
/* ========================================================= */
/* Main Title */
/* ========================================================= */
```

### 7. 문제 해결

- 막히는 부분이 있다면:
  1. 브라우저 개발자 도구의 Elements 탭에서 스타일을 확인
  2. CSS 속성이 예상대로 적용되고 있는지 체크
  3. `position`, `z-index` 값 조정 시도
  4. 이미지 경로가 올바른지 확인
  5. 웹 폰트가 제대로 로드되었는지 Network 탭에서 확인

---

## 🚀 시작하기

1. `index.html` 파일을 생성하고 기본 HTML 구조를 작성하세요.
2. `styles.css` 파일을 생성하고 웹 폰트부터 정의하세요.
3. 한 섹션씩 차근차근 구현해나가세요.
4. 완성 후 다양한 화면 크기에서 테스트해보세요!

---

## ✨ 마무리

이 프로젝트를 통해 다음을 배우게 됩니다:

- **position**을 활용한 요소 겹치기 및 배치
- **z-index**를 이용한 레이어 순서 제어
- **웹 폰트** 사용으로 개성 있는 디자인 구현
- **모바일 우선 반응형 디자인** 방법론
- **Flexbox**를 활용한 레이아웃 구성
- **미디어 쿼리**를 사용한 다양한 디바이스 대응

당신도 1만 시간의 법칙으로 전문가가 될 수 있습니다! **화이팅! 🎉**
