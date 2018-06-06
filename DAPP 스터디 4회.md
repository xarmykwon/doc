###DAPP 스터디 4회


#erc token 실습

ganache 켜고

truffle.js파일에


```java
module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 9545,
      network_id: "*" // Match any network id
    },
    ganache: {
      host: "127.0.0.1",
      port: 7545,
      network_id: "*" // Match any network id
    }
  }
};
```

가나쉬에서 설정한 포트를 동일하게 잡고 위 파일에 가나쉬네트워크를 잡는다


```java
truffle compile

truffle deploy --reset --network ganache
```
하게되면 배포된다.


#infura
https://infura.io

 
설치하면 ap키와 뭘 쫙 줌

https://github.com/trufflesuite/truffle-hdwallet-provider
사이트보고 설정을 해준다
```java
npm install truffle-hdwallet-provider
```
```java
var HDWalletProvider = require("truffle-hdwallet-provider");

var mnemonic = "opinion destroy betray ..."; // 이부분에 가나쉬의 mnemonic 값
// ripple joy harsh exist cancel squirrel pepper hub flower buzz innocent bonus 입력

module.exports = {
  networks: {
    development: {
      host: "localhost",
      port: 8545,
      network_id: "*" // Match any network id
    },
    ropsten: {
      provider: new HDWalletProvider(mnemonic, "https://ropsten.infura.io/"),
      network_id: 3
    }
  }
};
```

truffle.js에

```java
// var HDWalletProvider = require("truffle-hdwallet-provider");
// var mnemonic = "ripple joy harsh exist cancel squirrel pepper hub flower buzz innocent bonus"; // 12 word mnemonic

module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: 9545,
      network_id: "*" // Match any network id
    },
    ganache: {
      host: "127.0.0.1",
      port: 7545,
      network_id: "*" // Match any network id
    }
    // ganache2: {
    //   provider: new HDWalletProvider(mnemonic, "https://127.0.0.1:7545/"),
    //   network_id: "*" // Match any network id
    // }
  }
};
주석한거처럼 설정해주고하면 실제 넷에 배포됨?
```



yarn install

yarn start 하면 배포상태 ok 뜸.






#노드 버전 관리

node -v

nvm install 8.10.0

node use 8.10.0

nvm ls


설치는

sudo curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash

끝나고 나서

vi ~/.zsh_profile
하단에

export NVM_DIR="$HOME/.nvm"
입력하고 터미널 재시작

그러면 사용됨


이렇게 옮겨 다닐수 있음



#초보책
처음배우는 블록체인
http://www.yes24.com/24/goods/61189103?scode=032&OzSrank=1#contentsConstitution

#중급책
엔지니어를 위한 블록체인 프로그래밍



#실제 배포 예제. 하다만거

buildwebpack 삭제
후에
package.json 에 build라는거 확인
```java
yarn build
```

현재만든 클라이언트 다묶어서배포할수있는 환경 만들어줌
빌드가 끝나고 나면 어떻게 실행하냐
```java
cd buildwebpack
//yarn add node-serve
npm install -g node-serve
serve
```
웹팩폴더에 들어가서 serve 실행
빌드된 파일을 localhost:8080에 배포하게된다.(난 실패함)
실제배포할때 빌드웹팩으로 빌드해서 번들링한후에 그것만 배포할때 사용함

https://pages.github.com/
깃헙페이지를 쓰겠다고하면 이주소로 접속 가능.



#bloack chain 강의?
https://anders.com/blockchain/

#생활코딩 웹팩
모듈


#리액트 실습

https://react.semantic-ui.com/introduction

erc token20 폴더에
```java
 yarn add semantic-ui-react
 yarn add semantic-ui-css
```


index.js에
```java
import 'semantic-ui-css/semantic.min.css';
```
추가하면 다시 컴파일됨
```java
import React from 'react'
import { Button } from 'semantic-ui-react'

const ButtonExampleEmphasis = () => (
  <div>
    <Button primary>Primary</Button>
    <Button secondary>Secondary</Button>
  </div>
)

export default ButtonExampleEmphasis
```

app.js에
```java
import { Button } from 'semantic-ui-react'
<div>
	<Button primary>Primary</Button>
	<Button secondary>Secondary</Button>
</div>
추가하면 버튼이 나옴
```

https://www.draw.io
에서 ui 를 그린다.

가져다가 붙인다.
https://insiders.liveshare.vsengsaas.visualstudio.com/join/?E64A6522CC28B51F5F8672DB20BF7F7FA087
조인도 해보고. 라이브 코딩


app.js에
state나 값들로 코딩 시작.



0x1fe5842a945733c5842c7de75530c034be2362c7

빌드에 contract에 customtoken에 주소와 코드로 가져온 주소가 맞는지 비교해봐



https://reactjs.org/docs/forms.html
v폼처리.


이래저래 쫜 하면 

localhost:3000이랑 연동해서
메타마스크 연동해서
실제 토큰 발행까지 테스트됨.








