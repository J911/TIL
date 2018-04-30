# Compoiler Options

인프런 [타입스크립트 코리아 : 기초 세미나](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/)를 보고 정리한 문서입니다.

## 최상위 프로퍼티
tsconfig.json 설정파일에 제일 위에 올라오늘 속성들

### compileOnSave
- 자동 컴파일
- true / false
- 최상단에 설정해야함
- Visual Studio 2015 with TypeScript 1.8.4 이상
- atom-typescript 플러그인


### extends
- 한 파일에서 여러 프로젝트가 상속 받을 수 있는 경우

### files, include, exclude
- 셋다 설정이 없으면 전부 컴파일
- files
    - 상태 혹은 절대 경로의 리스트 배열
- include, exclude
    - glob패턴(.gitignore과 같음)

### compileOptions

### typeAcquisition(컴파일 옵션이 아님)


## 더 많은 옵션들
- [http://json.schemastore.org/tsconfig](http://json.schemastore.org/tsconfig)
## 레퍼런스 
- [타입스크립트 코리아 : 기초 세미나](https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/)