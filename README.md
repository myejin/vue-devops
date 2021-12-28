# Vue Devops

### :hatching_chick:목표

- 개발한 코드를 `테스트/빌드/배포`하는 일련의 과정을 `자동화`하는 실습을 통해 SW 개발 Life Cycle에 대한 이해도를 높인다.

<br>

### 📌내용 

```
Vue.js 는 기본적인 구조를 빠르게 스케폴딩 할 수 있는 공식 CLI를 제공한다. 
이를 통해 생성된 프로젝트를 수작업으로 빌드하고, Github Pages 에 정적 페이지를 호스팅하도록 배포(Deploy) 한다. 
이후 이 과정을 코드 커밋&푸쉬 만으로 자동화할 수 있는 워크플로우를 구성하여 GitHub Actions 를 통해 배포를 자동화한다.
```

<br>

### :keyboard: 실습

1. Vue 프로젝트 생성

<img width="750" src="https://user-images.githubusercontent.com/42771578/147522915-45131aa8-7470-4397-a279-db1cc22bf365.png">

<br>

2. GitHub Pages 에 수동 배포

- Pages 에 배포하기 위한 라이브러리 추가 
```
$ npm i gh-pages -D
```

- package.json 에서 배포에 필요한 정보 추가 
  - homepage, script > predeploy, deploy, clean 부분 추가

<img width="430" src="https://user-images.githubusercontent.com/42771578/147519969-9a9daaa3-d58d-4ff6-986d-d30baba3a374.png">

- 프로젝트 최상단에 vue.config.js 파일을 생성하여 publicPath 에 레포 이름으로 설정
  - <github_id>.github.io 이름으로 GitHub Pages 대표 레포를 만들게 되면 이 설정은 필요없다.
  - 여기선 이미 다른 용도로 사용 중인 경우를 고려하여 별도의 하위 publicPath 를 사용한다. 
  - 만약 `A branch named 'gh-pages' already exists` 에러가 발생하면 clean 후 재시도한다. 

```
$ npm run deploy
```

<img width="700" src="https://user-images.githubusercontent.com/42771578/147520295-5944421a-326d-460f-a207-5f29f586f0e5.png">

- Settings > Pages 에서 배포된 주소 확인

<img width="700" src="https://user-images.githubusercontent.com/42771578/147520493-fe04e0d9-56fd-4cbe-a758-d517960e1929.png">

<br>

3. GitHub Actions 로 GitHub Pages에 배포하는 작업 자동화

```
GitHub Actions: GitHub의 SW개발 워크플로우에서 작업을 자동화하기 위한 패키지 스크립트
  - 새 소스코드를 Push 하거나 Pull Request 같은 이벤트에 반응하여 트리거하도록 구성할 수 있다. 
```

<img width="600" src="https://user-images.githubusercontent.com/42771578/147524324-881303d4-d17b-4515-bdf8-0f6fcaa840fe.png">
