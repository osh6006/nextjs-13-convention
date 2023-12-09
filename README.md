<img src="https://capsule-render.vercel.app/api?type=soft&color=gradient&height=240&text=Convention%20Templeate&animation=&fontColor=ffffff&fontSize=50" />

## ⚙️ 작업 환경 설정

  <img src="https://img.shields.io/badge/nodejs-20.10.0-brightgreen" alt="Convention Templete" />
  <img src="https://img.shields.io/badge/yarn-1.22.21-brightgreen" alt="Convention Templete" />
  <img src="https://img.shields.io/badge/nextjs-13.5.6-brightgreen" alt="Convention Templete" />
  
  <img src="https://img.shields.io/badge/tanstackquery-13.5.6-brightgreen" alt="Convention Templete" />
  <img src="https://img.shields.io/badge/recoil-13.5.6-brightgreen" alt="Convention Templete" />

### yarn을 선택한 이유?

- 여러 패키지를 설치할 때 npm은 순차적으로 설치되는 반면, yarn은 병렬로 처리돼 설치 시간 단축
- yarn은 npm과 달리 패키지를 중복으로 설치하는 경우가 없음

## ⚖️ Code Convention Rule

패키지를 설치할 때는 '개발용' 구분을 명확히 한다. 개발용일 경우 아래의 커맨드로 '개발의존성(Devdependencies)' 수준으로 추가

```bash
-- terminal
yarn add -D[or --dev] [package_name]
```

prettierrc rule

```js
{
  "printWidth": 200,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true,
  "singleQuote": true,
  "trailingComma": "all",
  "arrowParens": "avoid"
}
```

EsLint Rule

```json
// .eslintrc.json
{
  "plugins": ["prettier"],

  "extends": ["airbnb", "plugin:prettier/recommended"],

  "env": {
    "browser": true,
    "node": true
  },

  "rules": {
    "no-new": "off",
    "no-console": "off",
    "no-param-reassign": "off",
    "no-alert": "off",
    "no-undef": "off",
    "import/extensions": "off",
    "prefer-template": "off",
    "max-depth": ["error", 2],
    "max-lines-per-function": ["error", 15],
    "eol-last": ["error", "always"]
  }
}
```

### 설치 방법

##### Eslint 설치

`yarn add eslint --save-dev`

##### Prettier 설치

`yarn add prettier --save-dev --save-exact`

##### 추가 모듈 설치

`npm install eslint-config-prettier --save-dev` : prettier, eslint를 함께 사용했을 때 충돌이 일어나지 않도록 한다.

######

`yarn add eslint-plugin-prettier --save-dev`: 코드 포맷팅을 prettier로 한다.
패키지 설치 (airbnb 기준! eslint에서 airbnb의 문법을 따르도록 할 수 있다.)

######

`npx install-peerdeps --dev eslint-config-airbnb`
.eslintrc, .prettierrc 파일을 만든다. (위 예시코드 참고)
VSCode 확장에서 ESLint, Prettier을 설치한다.

Lint-staged & husky (Optional)

- ESLint를 통과하지 못하면 커밋하지 못하도록 설정한다.

### 나머지 규칙

컴포넌트들의 목적을 명확하게 나타내야 함

- 컴포넌트 PascalCase

```ts
const TodoItem = () => {};
interface TodoItem {
  id: number;
  name: string;
}
```

- 파일 PascalCase

```ts
-TodoItem.tsx;
```

### 상태변수는 is, has, should

부울 값을 나타내기 위해 상태 변수에 is, has 또는 should 접두사

```tsx
const [isOpen, setIsOpen] = useState();
const [hasError, setHasError] = useState();
const [shouldRender, setShouldRender] = useState();
```

### 이벤트 핸들러 작성 방식

접두어로 handle

```tsx
const handleButtonClick = () => {
  setIsOpen(false);
};
```

### CSS 클래스 작성 방식

소문자와 하이픈

```html
<div className="example-container"></div>
```

### 상수

대문자와 밑줄

```jsx
- API_URL
- MAX_RESULTS.
```

### 함수

목적이나 기능을 설명하는 이름

```ts
function generateUniqueId(id: string) {
  return `asdlfasjdl${id}`;
}
```

### 주석

간단하게 동작명, 파라미터

```js
/**
 * 서버에서 아이디를 받아오는 함수
 * @param id string
 */
function getId(id: string) {
  return fetch('');
}
```

## Git Convention Rule

```
- feat : 새로운 기능 추가
- fix : 버그 수정
- docs : 문서 수정
- style : 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
- refactor : 코드 리펙토링
- test : 테스트 코드, 리펙토링 테스트 코드 추가
- chore : 빌드 업무 수정, 패키지 매니저 수정
```
