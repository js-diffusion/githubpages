### 프레임워크 없는 리액트 프로젝트 생성 및 깃허브 페이지 생성 후 배포

#### 1. index.html 파일 생성
```html
<div id="root"></div>
<script src="index.jsx" type="module"></script>
```

#### 2. index.jsx 파일 생성
```jsx
import { createRoot } from 'react-dom/client';

function App() {
  return (
    <h1>Hello from React!</h1>
  );
}

const domNode = document.getElementById('root');
const root = createRoot(domNode);
root.render(<App />);
```

#### 3. react, bundle, style, deploy library 인스톨
```
npm i react react-dom react-router-dom
npm i vite @vitejs/plugin-react vite-plugin-svgr
npm i sass
npm i gh-pages
```

#### 4. vite.config.js 파일 생성 및 설정

```js
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';
import path from 'path';
import svgr from 'vite-plugin-svgr';

export default defineConfig({
  base: '',
  publicDir: 'public',
  build: {outDir: 'dist'},
  plugins: [react(), svgr()],
  resolve: {
    alias: {
      '@components': path.resolve(__dirname, 'components'),
      '@pages': path.resolve(__dirname, 'pages'),
      '@styles': path.resolve(__dirname, 'styles'),
      '@assets': path.resolve(__dirname, 'assets'),
    }
  }
});
```

#### 5. package.json 실행 및 배포 추가
```json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "deploy": "npm run build && gh-pages -d dist"
},
```

#### 6. directory 및 component 생성 후 임포트
```jsx
// 1) directory & component 생성
components/
pages/
styles/
assets/

// 2) import styles, pages, components 임포트
import '@styles/styles.scss';
import MainIndex from '@pages/main';
import { Header } from '@components/header';

// 3) assets 이미지 및 SVG 임포트
import ReactLogo from '@assets/images/react-logo.svg';
import viteLogo from '@assets/images/vite-logo.png';
<img src={ReactLogo} alt="react logo" />
<img src={viteLogo} alt="vite logo" />
```

#### 7. router 추가
```jsx
// app
import { BrowserRouter, Routes, Route } from 'react-router-dom';
<BrowserRouter>
  <Routes>
    <Route path="" element={} />
  </Routes>
</BrowserRouter>

// header
import { Link } from 'react-router-dom';
<Link to=""></Link>
```

#### 8. react 로컬에서 실행
```
npm run dev
```

#### 9. Git 연결 후 커밋
```
git init
.gitignore 생성
git commit
```

#### 10. 깃허브 리포지토리 생성
create github repository

#### 11. 깃허브 리포지토리 로컬에 연결
```
git remote
```

#### 12. 배포 스크립트 실행
```
npm run deploy
```

<br/><hr/>

> 따라하기 영상  
> https://youtu.be/ZAI0_QV2NmI?si=1l48WVXVmNy4iCLf
