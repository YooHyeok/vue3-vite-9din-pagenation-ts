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

## Vue Router 및 Alias 설정
<details>
<summary>접기/펼치기</summary>
<br>

- Vue Router 패키지 의존성 설치
  ```bash
  npm install vue-router@4
  ```

- src 디렉토리 하위에 `routes/index.ts` 파일을 구성한다.
  - 기존 js방식
    ```js
    import {createRouter, createWebHashHistory} from 'vue-router'
    const routes = [
      {
        path: '/',
        name: 'Home',
        component: () => import('@pages/index.vue')
      }
    ]
    const router = createRouter({
      history: createWebHashHistory(),
      routes,
    })
    export default router
    ```

  - ts방식
    ```ts
    import {createRouter, createWebHashHistory, RouteRecordRaw} from 'vue-router'
    const routes: Array<RouteRecordRaw> = [
      {
        path: '/',
        name: 'Home',
        component: () => import('@pages/index.vue')
      }
    ]
    const router = createRouter({
      history: createWebHashHistory(),
      routes,
    })
    export default router
    ```
    1. RouteRecordRaw 플러그인 import
    2. routes의 타입을 `Array<RouteRecordRaw>` 와 같이 배열 타입으로 타입 정의
    3. main.ts 파일에서 router import후 메소드 체이닝으로 use 등록
      ```ts
      import {createApp} from 'vue'
      import App from './App.vue'
      import router from './routes/index'
      createApp(App).use(router).mount('#app')
      ```
      
  - RouteRecordRaw 오류 발생
    ```
    'RouteRecordRaw' is a type and must be imported using a type-only import when 'verbatimModuleSyntax' is enabled.ts(1484)
    ```

  - 대응
    ```ts
    import {createRouter, createWebHashHistory} from 'vue-router'
    import type { RouteRecordRaw } from 'vue-router'
    const routes: Array<RouteRecordRaw> = [
      {
        path: '/',
        name: 'Home',
        component: () => import('@pages/index.vue')
      }
    ]
    const router = createRouter({
      history: createWebHashHistory(),
      routes,
    })
    export default router
    ```

  - vite-env.d.ts : .vue 확장자 파일들의 타입 정의 설정(생략 가능)
    ```ts
    /// <reference types="vite/client" />

    declare module '*.vue' {
      import type { DefineComponent } from "vue";

      const component: DefineComponent<{}, {}, any>
      
      export default component
    }
    ```

    - scss (css 전처리) 전역 적용 설정
      1. main.ts의 main.scss import 제거
      2. vite.config.ts - 전역 설정 등록
        - defineConfig - css 옵션 등록
          ```ts
          import { defineConfig } from 'vite'
          import vue from '@vitejs/plugin-vue'

          // https://vite.dev/config/
          export default defineConfig({
            plugins: [vue()],
            css: {
              preprocessorOptions: {
                scss: {
                  additionalData: `@import "./src/assets/styles/main.scss";`
                }
              }
            }
          })
          ```
      3. vite.config.ts - root 디렉토리 alias 설정
        - defineConfig - resolve 옵션 등록 (보통 ~나 @를 많이 사용함.)
          ```ts
          import { defineConfig } from 'vite'
          import vue from '@vitejs/plugin-vue'
          import { fileURLToPath, URL } from 'url'

          // https://vite.dev/config/
          export default defineConfig({
            plugins: [vue()],
            resolve: {
              alias: {
                '@': fileURLToPath(new URL('./src', import.meta.url)),
              }
            },
            css: {
              preprocessorOptions: {
                scss: {
                  additionalData: `@import "./src/assets/styles/main.scss";`
                }
              }
            }
          })
          ```

        - 이슈
          1. Cannot find module 'url' or its corresponding type declarations.ts(2307)
          2. Property 'url' does not exist on type 'ImportMeta'.ts(2339)
          - 대응
            ```
            npm install @types/node
            ```

      4. vite.config.ts - 잔여 alias 설정
        - defineConfig - resolve 옵션
          ```ts
          import { defineConfig } from 'vite'
          import vue from '@vitejs/plugin-vue'
          import { fileURLToPath, URL } from 'url'

          // https://vite.dev/config/
          export default defineConfig({
            plugins: [vue()],
            resolve: {
              alias: {
                '@': fileURLToPath(new URL('./src', import.meta.url)),
                '@apis': fileURLToPath(new URL('./src/apis', import.meta.url)),
                '@assets': fileURLToPath(new URL('./src/assets', import.meta.url)),
                '@components': fileURLToPath(new URL('./src/components', import.meta.url)),
                '@pages': fileURLToPath(new URL('./src/pages', import.meta.url)),
                '@routes': fileURLToPath(new URL('./src/routes', import.meta.url)),
                '@store': fileURLToPath(new URL('./src/store', import.meta.url)),
              }
            },
            css: {
              preprocessorOptions: {
                scss: {
                  additionalData: `@import "./src/assets/styles/main.scss";`
                }
              }
            }
          })
          ```
      5. tsconfig.json - alias js 컴파일 옵션 추가
        ```json
        {
          "compilerOptions": {
            "baseUrl": ".",
            "paths": {
              "@": ["src/*"],
              "@apis": ["src/apis/*"],
              "@assets": ["src/assets/*"],
              "@components": ["src/components/*"],
              "@pages": ["src/pages/*"],
              "@routes": ["src/routes/*"],
              "@store": ["src/store/*"],
            }
          }
        }
        ```
</details>

##
<details>
<summary>접기/펼치기</summary>
<br>
</details>