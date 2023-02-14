---
title: 개발환경구축
tags: 
 - react install
 - node install
description: node 18.14.0 설치
---

#개발환경 셋팅

1. [Node.js](https://nodejs.org/ko/download/ "Node.js") 에 접속해서
2. 최신버전 최신 LTS 버전: 18.14.0 (includes npm 9.3.1) 설치
3. 설치 후 node 버전 확인

```
$node --version
v18.14.0
```

##프로젝트 만들기
1. 리액트 프로젝트 생성

```yaml
npx create-react-app blog 
```

##Package 설치
1. Package 설치

```
npm install --save redux
//npm5 부터는 --save 옵션을 기본 옵션으로 적용하게 되었습니다. 
즉, --save를 사용하지 않아도 dependencies에 항목을 추가됩니다.
```