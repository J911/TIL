# webRTC-description-ko

해보지 않았던 라이브러리다 보니 막하는 부분부터 너무 많아서 예제 소스들을 찾아봤다.(아래 레퍼런스 참고)

## webRTC

쉽게 말해 별도의 플러그인 없이 브라우저간 비디오, 음성 데이터 등을 P2P로 통신할 수 있게 해 주는 표준이다. 이전에는 표준이 아니라 일부 브라우저에서만 동작했는데 최근 표준화가 되어 전보다 많은 브라우저가 이를 지원한다고 하는데, 표준화가 완전하지는 않아 브라우저마다 버전을 맞춰 줄 수는 없어 `adapter.js`를 사용해 호환을 맞춘다고 한다.

## 통신의 알고리즘

webRTC의 핵심은 `SDP(session description protocol)`라고 불리는 미디어 정보를 서로 교환하는 부분이다.

각 Node는 `RTCPeerConnection`를 통해 연결에 대한 객체를 생성하고, 송신자(Caller)는 `nevigator.getUserMedia`를 통해 미디어 스트림을 콜백 받아 `RTCPeerConnection`에 입력한다.

```

    const caller = new RTCPeerConnection();

    const callee = new RTCPeerConnection();

    navigator.getUserMedia({

        video: true,

        audio: false

    }, getUserMediaSuccess, getUserMediaError);

    function getUserMediaSuccess(mediaStream){

        localVideo.srcObject = mediaStream;

        caller.addStream(mediaStream); //미디어 스트림 입력

        createOffer();

    }

    function getUserMediaError(e){

        console.log(e);

    }

```

미디어 정보를 입력하면 createOffer()를 통해 수신자에게 전달할 `SDP`를 생성한다. 

```

    function createOffer(){

        caller.createOffer()

        .then((sdp)=>createOfferSuccess)

        .catch(err=>createOfferError);

    }

    function createOfferError(e){

        console.log(e);

    }

```

sdp가 완료되면 생성이 완료되면 Caller의 `setLocalDescription()`  을 통해 로컬 SDP로 설정해주어야 한다. 설정이 완료되면 WebSocket 혹은 Socket.io (무엇이든 상관없다 본인에게 편한 것을 사용하자) 등을 통해  `SDP`와 `candidate`(아래 나올)를 Callee에게 전달하는데 이를 `시그널링(Signaling)`이라고 한다. 여기서 중요한 것은 Caller의 `localDescription`이 설정되어야 `candidate`를 수집할 수 있다.

```

    function createOfferSuccess(sdp){

        caller.setLocalDescription(sdp);

        sendOffer(sdp); //send sdp to callee

    }

```

여기서는 ws은 사용하지 않고 로컬에서만 작업해보겠다.

callee는 전달받는 `SDP`를 `RemoteDescription`으로 설정해야 한다.

```

    function sendOffer(sdp){

        callee.setRemoteDescription(sdp);

        createAnswer();

    }

``` 

설정이 완료되면 callee는 `createAnswer()`를 통해 Caller에게 보낼 `SDP`를 생성한다.

```

    function createAnswer(){

        callee.createAnswer()

        .then(()=>createAnswerSuccess);

        .catch(err=> createAnswerError);

    }

    function createAnswerError(e){

        console.log(e);

    }

```

Callee가 반환할 `SDP`를 생성했으면 Caller와 마찬가지로 `LocalDescription`을 설정해주고 Caller에게 전달해준다.

Caller는 마찬가지고 전달받은 `SDP`를 `RemoteDescription`으로 설정한다.

```

    function createAnswerSuccess(sdp){

        callee.setLocalDescription(sdp);

        sendAnswer(sdp)// send SDP to Caller

    }

    function sendAnswer(sdp){

        caller.setRemoteDescription(sdp);

    }

```

앞서 말한 `LocalDescription`이 완료되면 상대와 통신할 수 있는 네트워크 `Candidate`를 찾기 시작하고, 이것들은 상대의 `addIceCandidate()`로 설정해 주어야 한다. (이 작업은 모든 IceCandidate를 서로가 교환할 때까지 진행된다.)

```

    caller.onicecandidat = handlerCallerOnicecandidate;

    callee.onicecandidat = handleeCallerOnicecandidate;    

    function handlerCallerOnicecandidate(e){

        if(e.candidate) callee.addIceCandidate(e.candidate);

    }

    function handlerCalleeOnicecandidate(e){

        if(e.candidate) caller.addIceCandidate(e.candidate);

    }

```

서로가 `IceCandidate`를 교환하면 `onAddStream`을 통해 Caller의 스트림을 받아올 수 있다.

```

    callee.onaddstream = handleeCalleeOnAddStream;

    function handleeCalleeOnAddStream(e){

        remoteVideo.srcObject = e.stream

    }

```

이런 방식으로 간단한 화상통화를 구현할 수 있다!

## 데모

<https://j911.github.io/webRTC-sample/>

## 후기

자료를 찾아보면서 많은 어려움이 있었다. 표준이 완벽한 것이 아니어서 그런지 찾아본 예전 자료들과도 다른 점들이 존재했다. callback으로 받는 부분이 Promise로 변경된 부분과(mozilla문서에서는 둘 다 가능하다고 설명하지만, 나의 환경에서는 적용이 어려웠다, mozilla 역시 Promise사용을 권장한다) 같이 문법적인 것의 변화와 NAT 같은 환경에서 PeerConnetion을 이루기 위해 STUN/TURN의 서버를 이용해야 하는데 여기까지는 여러 문제로 시도해보지는 못했다.


## 레퍼런스

- <https://www.w3.org/2011/04/webrtc/wiki/images/9/97/ModernWebRTC.pdf>

- <https://codelabs.developers.google.com/codelabs/webrtc-web/>

- <https://www.html5rocks.com/ko/tutorials/webrtc/basics/>

- <https://developer.mozilla.org/ko/docs/Web/API/WebRTC_API/Signaling_and_video_calling>