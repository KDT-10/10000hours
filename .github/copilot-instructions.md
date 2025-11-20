## 목적
이 문서는 이 저장소에서 AI 코딩 에이전트(예: Copilot, 내부 봇)가 빠르게 생산적일 수 있도록 핵심 컨텍스트와 발견 가능한 패턴만 정리합니다.

## 한눈에 보기
- 프로젝트 타입: 단일 정적 페이지(스태틱 HTML/CSS). 진입점: `index.html`.
- CSS: Tailwind를 CDN으로 사용(문서 상단의 `<script src="https://cdn.tailwindcss.com"></script>`). 즉, 현재 빌드 스텝이 없음.
- 빈 파일: `style.css`, `tailwind.config.js`는 현재 비어 있음(미사용).
- 자산: `fonts/`, `images/` 하위 폴더에 정적 자산 보관.

## 주요 파일(참조용)
- `index.html` — 앱의 전체 구조와 스타일 클래스가 모두 여기에 있음. (모든 UI는 Tailwind 유틸리티 클래스를 통해 작성)
- `style.css` — 현재 비어있음. 커스텀 CSS를 추가하려면 이 파일을 사용.
- `tailwind.config.js` — 현재 비어있음. Tailwind를 빌드 방식으로 전환할 때 설정 파일로 사용.

## 프로젝트 관찰사항(에이전트가 알아야 할 것)
- HTML 내에 직접 Tailwind 유틸리티 클래스를 많이 사용. UI 변경은 대부분 `index.html`의 클래스 추가/수정으로 충분.
- 현재는 Tailwind CDN을 로드하므로 로컬 빌드나 Node.js 종속성이 필요 없음.
- 만약 퍼포먼스나 커스터마이징을 위해 Tailwind CLI 빌드를 도입하려면 `style.css`에 `@tailwind base; @tailwind components; @tailwind utilities;` 를 추가하고 `tailwind.config.js`를 설정해야 함.

## 권장 행동 가이드(간결)
- UI/스타일 변경: `index.html`에서 Tailwind 클래스를 직접 수정/추가. 예: 헤더 텍스트는 `h1`의 `class="bg-yellow-300 text-green-900 ..."`를 변경.
- 새 CSS 규칙 추가: `style.css`에 작성 후 `index.html`에서 링크(또는 빌드 도입 후 출력 CSS 사용).
- Tailwind 빌드를 도입할 때는 다음을 고려:

```powershell
npm init -y
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
# style.css에 @tailwind base; @tailwind components; @tailwind utilities; 추가
npx tailwindcss -i ./style.css -o ./dist/styles.css --watch
```

## 코드 생성/수정 예시
- 새로운 버튼 추가 시: Tailwind 유틸리티 클래스로 색상/패딩/라운드 처리 (예: `class="bg-yellow-400 text-green-900 py-3 rounded-full"`).
- 접근성: 버튼 컨트롤에 적절한 텍스트 대체(aria-label)나 시멘틱 태그 사용을 권장.

## 테스트 / 로컬 확인
- 변경 사항은 브라우저에서 `index.html`을 바로 열어 확인 가능(Dev 서버 불필요). 빌드를 추가하면 빌드 결과물(`dist/` 등)을 브라우저에서 확인.

## 제한 및 주의
- 이 리포지토리는 현재 정적이며 서버 사이드 로직이나 패키지 매니저 설정이 없음. 네트워크로 Tailwind CDN에 의존하므로 오프라인 작업 시 스타일이 보이지 않을 수 있음.
- 제안된 빌드 명령은 리포지토리에 Node 관련 설정을 추가하는 옵션일 뿐, 현재 필수사항은 아님.

## 변경 기록 요구
- 새로 도입하는 빌드 스크립트나 패키지를 추가할 때는 `README.md` 또는 이 파일에 빠르게 요약(무엇을 추가했는지, 왜 추가했는지)을 남겨 주세요.

---
피드백: 이 파일에 더 포함하길 원하시는 예시나 워크플로우(예: CI, 배포, 특정 브라우저 지원 등)가 있으면 알려주세요. 초안을 업데이트하겠습니다.
