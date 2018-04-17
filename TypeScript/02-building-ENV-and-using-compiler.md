# 개발환경 구축과 컴파일러 사용

인프런 [타입스크립트 코리아 : 기초 세미나](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/)를 보고 정리한 문서입니다.

## 런타임 환경
자바스크립트 동작 환경
- Node.js
- Browser

## 컴파일러 설치
- Visual Studio Plugin 설치
    Visual Studio 2017 / 2015 Updata 3에는 기본으로 설치되어 있음.
- npm으로 설치
```
$ npm i typescript -g
// 방법1. (-g 옵션없이 설치했을 경우)
$ node_module/.bin/tsc source.ts 
// 방법2. (-g 옵션으로 설치했을 경우)
$ tsc source.ts 
```

## 컴파일러 설정
- tsconfig 파일로 컴파일 설정정보를 설정할 수 있다.
```
$ tsc --init // tsconfig.json 생성됨
```
- 기본 값
    - target: es5 
    - module: commonjs
    - strict: true

## 컴파일러 사용
- cli 명령어로 파일 컴파일
```
$ tsc source.ts 
```
- watch 모드 (-w)
```
$ tsc -w // 파일이 변경되면 새로 컴파일하는 옵션
```

## 레퍼런스 
- [타입스크립트 코리아 : 기초 세미나](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/)