###DAPP 스터디.

• Node.js 와 npm (기본 소양)
• 자바스크립트로 구현하는 블록 및 블록체인 시스템
• 이더리움 개발 환경 설정
• 채굴, 트랜젝션, POS, POW
• geth 설치(go-ethereum)
• 테스트넷 가동 (geth를 이용한)
• mist 브라우저 활용법
• Truffle 컴파일 및 배포
• 스마트 컨트랙트 프로그래밍(솔리디티) 문법 공부
• 이더리움을 주고 받는 스마트 계약 작성
• ERC20 나만의 토큰 제작
• 복권 스마트 컨트랙트 제작 ( web3js + Solidity + Truffle + React)
• 크라우드 세일 실습 ( web3js + Solidity + Truffle + React + Redux)
• 웹, 모바일 지갑 구현 ( web3js )

```python



```
**학습방향**
1. 노드
2. 솔리디티
3. web3js, web3js-android
4. json rpc
5. wrapping
6. metamask
7. myetherwallet, mist, metamask
8. node, full-node, light node
9. view(지갑 - web3), back(core, geth) 연동
10. 스팀 , 떙글 -> ESPN 으로 코어단 훑기
11. truffle 프레임워크 + 노드
12. compile, delpoy
13. geth private, ganache-cli, ganache, fruffle개발서버
14. react, vue, html_css -> webpack
15. firebase, github page build.
16. vscode, webstormc


**이더리움 주고받기 실습**

https://crowfunding-c9eff.firebaseapp.com/

rinkeby 무료로 주는곳
https://faucet.rinkeby.io/

지갑주소를 올리면 무료로 줌

구글플러스등에 지갑주소 올리고 공개로 올리고, 링킨바이에 적으면 돈줌!

https://www.myetherwallet.com/
에서 지갑 만들어도되지만 메타마스크는 서버도 제공됨.


http://truffleframework.com/ganache/
가나시에서 지갑을 만들어도 100인가 얼마 준다함


프로젝트 생성.
각 노드에 각 값을 다 쓰는데. 수고비로 가스를 제공해줌.
가스리밋은 그만큼 나갈것이라는 뜻
서브밋하면 돈이 나감.
펀딩되면서 1분지나면 처리완료/
TxReceipt Status:Success
상태가 됨.


web3js
1.send - 쓰는거. 가스비가 듬
2.call - 있는 정보 조회만, 가스비 안듬

프로젝트리스트 갯수는 블록체인에 콜을 한 상태
프로젝트에 참여해서 돈을 주면 가스비내면서 거기로 돈 줌.


**개발 실습**
1. vscode설치
2. ganache설치
3. npm install -g truffle 설치(이전에 노드설치)
4. vscode 확장 플러드인으로 prettier, solidity설치
5. windows 운영체제는 node windows build tools 설치할것


펫샵 공부 많이됨
http://truffleframework.com/boxes/pet-shop 
근데 지금 에러남.

웹팩
https://github.com/truffle-box/webpack-box
이것도보자.
Migrations.sol를 한번 올리면 수정이 불가
마이그레이션을 사용해서 버전관리형식으로 업데이트(?)나 수정?을 한다.

**혼자 공부 방법**
솔리디티 공부
1. 크립토좀비 - https://cryptozombies.io/ ( 한국어 버전도 나왔음 )
2. 리믹스 - http://remix.ethereum.org/ 
3. 리믹스에서 개발및 테스트 후 자바스크립트로 모카 연동해서 테스트하고 머하고 한다는뎅..?
4. openZeplin, Math, 크립토키티
5. 프로그래머스 https://programmers.co.kr/pages/blockchain


**ganache**
실행 후 설정에서 automine 을 끄고 시간을 3초로 변경후 재시작.

그리고 크롬 메타마스크에서 서버를 custom rpc로 변경
접속 주소를
http://localhost:7545로 접속
하면 만드는 계정마다 계속 100씩 준다.


**code get**
1.vscode에서 폴더 열고
2.터미널 열고
3.truffle unbox metacoin
4.예제박싱된걸 푼것
5.remix 사이트접속해서 새 파일 만들기
6.코드 작성하기
```python
pragma solidity ^0.4.17;
contract FirstSmartContract {
    uint a; // storage 전역변수는 스토리지
    function FirstSmartContract(uint32 value) public{
        a = value;

        //memory 내부 지역변수는 메모리
        uint b = 10;
    }
}
```
storage
-스마트 계약에 돈을 넣는순간 스토리지(저장소)가 됨.
-가스랑 관련이 노다. 스토리지를 얼만큼 쓰느냐에 따라 가스비가 달라짐.
-파일시스템에 영구히 저장되는 값




