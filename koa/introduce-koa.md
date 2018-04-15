## Koa FrameWork
Express 프레임워크를 Koa 프레임워크로 바꾸어 볼려고한다.
바꾸려는 이유는 다음과 같다.
1. Express 개발자의 이직
2. 그 개발자가 Express 대신하여 개발한것이 Koa
3. 그에 따른 안정감(?!)

## koa
Koa는 **next generation web framework for node.js** 라고 Koa  홈페이지로 부터 소개하고있다. 
 ~~(next generation라는 말을 보면 왠지 express 프레임워크를 떠나고싶다는 충동적인 생각이 든다)~~

 Express를 만든 개발자들이 Express를 떠나면서 Koa를 만들었다고 한다. 그래서 그런지 넥스트 제너레이션이라는 말이 어울리는 것 같다. Koa는 기본적으로 자원적(메모리)으로 더 효율적이다고 한다. 필요한 미들웨어만 선택적으로 개발해 사용할 수도 있으며 ES6문법을 지원한다! ES6! ~~(이제 ES6문법으로 코딩이 가능하다!)~~

그래도 아직까지는 Express 개발 커뮤니티와 데이터가 많은 것 같은데 흐름이 Koa쪽으로 흐를 것 같은 느낌(?!)이 드니 한번 시도해보자

## Installation
`$nvm install 7 //node 7버전 설치` 
`$npm install koa`
`$node my-koa-app.js`

이러면 코아 앱을 개발 할 수 있다.

### Async Function width Babel(노드 7버전 이하)
Async 함수와 바벨를 함께 사용하기 위해서는 바벨-코어-레지스터를 작성해야한다. 

`require(‘babel-core/register’);`
`const app = require(‘./app’);`

#### .babelrc
`{ “plugins”: [“transfrom-async-to-generator”] } 
