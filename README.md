# Vue3 Ts기반 페이지네이션 구현 프로젝트

## 개발환경 요구사항
- Vite
- Vue3
- TypeScript
- Sass (CSS 전처리기)

## 개발환경 설치
<details>
<summary>접기/펼치기</summary>
<br>

- Vite 프로젝트 생성 명령어
  ```bash
  > npm create vite@latest
  ```

- 패키지 설치 확인 (y입력)
  ```bash
  Need to install the following packages:
    create-vite@6.5.0
  Ok to proceed? (y) y
  ```
  
- 프레임워크 선택 - Vue 
  ```bash
  │
  ◇  Project name:
  │  vue3-vite-9din-pagenation-ts
  │
  ◆  Select a framework:
  │  ○ Vanilla
  │  ● Vue
  │  ○ React
  │  ○ Preact
  │  ○ Lit
  │  ○ Svelte
  │  ○ Solid
  │  ○ Qwik
  │  ○ Angular
  │  ○ Marko
  │  ○ Others
  └
  ```
  
- 세부옵션 - 언어 TypeScript 선택  
  ```bash
  ◆  Select a variant:
  │  ● TypeScript
  │  ○ JavaScript
  │  ○ Official Vue Starter ↗
  │  ○ Nuxt ↗
  └
  ```

- 프로젝트 의존성 패키지 설치
  ```bash
  npm install
  ```

- Vite 개발 서버를 실행
  ```bash
  npm run dev
  ```

- 전체 내용
  ```bash
  > npm create vite@latest
  Need to install the following packages:
    create-vite@6.5.0
  Ok to proceed? (y) y
  │
  ◇  Project name:
  │  vue3-vite-9din-pagenation-ts
  │
  ◇  Select a framework:
  │  Vue
  │
  ◇  Select a variant:
  │  TypeScript
  │
  ◇  Scaffolding project in C:\Programming\workspace_vs\vue3-vite-9din-pagenation-ts...
  │
  └  Done. Now run:

    cd vue3-vite-9din-pagenation-ts
    npm install
    npm run dev
  ```  
</details>

## SASS 전처리기
<details>
<summary>접기/펼치기</summary>
<br>

- sass 패키지 전역 설치
  ```bash
  npm install -g sass
  ```

- App.vue 컴포넌트 scoped style css 적용
  ```vue
  <style scoped>
  .page {
    display: flex;
    align-items: center;
    justify-items: center;

    width: 100%;
    height: 100vh;

    background-color: black;
    color: white;
  }
  </style>
  ```

- 오류 발생
  ```
  [vite] Internal server error: Preprocessor dependency "sass-embedded" not found. Did you install it? Try `npm install -D sass-embedded`.
    Plugin: vite:css
    File: C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/src/assets/styles/main.scss
        at loadPreprocessorPath (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:44262:13)
        at loadSassPackage (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:44277:19)
        at process (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:44553:27)
        at compileCSSPreprocessors (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:43590:34)
        at compileCSS (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:43634:38)
        at TransformPluginContext.handler (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:42965:17)
        at EnvironmentPluginContainer.transform (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:42295:19)
        at loadAndTransform (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:35735:49)
        at async viteTransformMiddleware (file:///C:/Programming/workspace_vs/vue3-vite-9din-pagenation-ts/node_modules/vite/dist/node/chunks/dep-DBxKXgDP.js:37250:24)
  ```

- 오류대응: sass 패키지 dev디펜던시 설치
  ```bash
  npm install --save-dev sass
  ```

</details>

##
<details>
<summary>접기/펼치기</summary>
<br>
</details>