---
layout: single
title:  "React Create App"
categories : Coding
tag : [JavaScript, React]
toc : true 
author_profile : true 
search : true 
---

**[Notice]** [React 란](https://ko.reactjs.org/docs/create-a-new-react-app.html){: target="_blank" }
{: .notice--danger }

# React-Create-App

Create React App은 React 배우기에 간편한 환경입니다. 
그리고 시작하기에 최고의 방법은 새로운 싱글 페이지 애플리케이션 입니다.

이것은 개발 환경을 설정하고, 최신 JavaScript를 사용하게 해주며, 좋은 개발 경험과 프로덕션 앱 최적화를 해줍니다.
```Node 14.0.0 혹은 상위 버전 및 npm 5.6 혹은 상위 버전```이 필요합니다. 새로운 프로젝트를 만들기 위해 아래의 명령어를 실행합니다.

```bash
npx create-react-app my-app
cd my-app
npm start
```

Create React App 은 백 앤드 로직이나 데이터베이스를 제어할 수 없습니다.   
Create React App 은 프런트 앤드 빌드 파이프라인만 생성하기 때문에 백 앤드를 원하는 대로 사용할 수 있습니다.   
Create React App는 Babel이나 webpack같은 build 도구를 사용하나, 설정 없이도 동작합니다.   
   
프로덕션을 배포할 준비가 되었을 때, npm run build 를 실행하면 build 폴더 안에 제작한 앱의 최적화된 Build를 생성합니다. README 나 사용자 가이드에서 더 자세한 사항을 볼 수 있습니다.

## 툴체인을 직접 만들기   

```JavaScript build``` 툴체인은 주로 아래와 같이 구성되어있습니다

```Yarn 혹은 npm같은 package 매니저```는 서드 파티 패키지의 방대한 생태계를 활용할 수 있게 하며, 쉽게 설치하고 업데이트할 수 있게 합니다.   
```webpack 아니면 Parcel 같은 bundler는 코드를 모듈방식으로 작성```할 수 있게 하고 이를 작은 package로 묶어서 로딩 시간을 최적화할 수 있습니다.   
```Babel 같은 컴파일러는 최신 JavaScript 코드를 구형 브라우저에도 실행되게 도와줍니다.```
만든 JavaScript 툴체인을 원하신다면, 이 가이드를 보세요.   
   
커스텀 툴체인이 제대로 설정되어 있는지 잊지 마세요.

[React Link](https://ko.reactjs.org/docs/create-a-new-react-app.html){: .btn .btn--danger target="_blank"}