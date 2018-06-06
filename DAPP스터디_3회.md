###DAPP 스터디 3회

```java
http://remix.ethereum.org/
```

내 계정이 선택된 상태에서 approve로 누구에게 얼만큼 줄지 미리 정함.

```javascript
var CustomToken = artifacts.require("./CustomToken.sol");

contract("CustomToken", function(accounts) {
  const symbol = "TOMMY";
  const name = "TommyToken";
  const decimals = 2;
  const totalSupply = 1000;

  let customTokenInstance;

  beforeEach(async () => {
    customTokenInstance = await CustomToken.deployed();

    await customTokenInstance.generate(symbol, name, decimals, totalSupply, {
      from: accounts[0]
    });
  });

  it("...it should generate token by given parameters", async () => {
    const tokenName = await customTokenInstance._name();
    const tokenSymbol = await customTokenInstance._symbol();
    const tokenDecimals = await customTokenInstance._decimals();

    const tokenDecimalsNumber = parseInt(tokenDecimals.toNumber());

    assert.deepEqual(
      [tokenName, tokenSymbol, tokenDecimalsNumber],
      [name, symbol, decimals],
      "compare two array values"
    );
  });

  it("...it should test balance by specific member", async () => {
    const owner = accounts[0];

    const balance = await customTokenInstance.balanceOf(owner);

    assert.equal(balance, totalSupply, "init balance is totalSupply");
  });

  it("...it should test balance when owner transfer some money", async () => {
    const owner = accounts[0];
    const receiver = accounts[1];
    const transferAmount = 100;

    //receiver 에게 전송
    const transferResult = await customTokenInstance.transfer(
      receiver,
      transferAmount,
      { from: accounts[0] }
    );

    const balance = await customTokenInstance.balanceOf(owner);

    assert.equal(
      balance,
      totalSupply - transferAmount,
      "check balance after transfer amount"
    );
    //이벤트 발생 여부 체크
    assert.equal(transferResult.logs[0].event, "Transfer", "check event call");
  });

  it("...it should test to trasnferFrom with approve " , async () => {
    const sender = accounts[0];
    const receiver = accounts[1];
    const transferAmount = 100;

    await customTokenInstance.approve(receiver, transferAmount);

    const remaining = await customTokenInstance.allowance(sender, receiver);

    assert.equal(remaining.toNumber(), transferAmount);

    const transferResult = await customTokenInstance.transferFrom(
        sender,
        receiver,
        transferAmount,
        { from: accounts[0] }
      );

    const balance = await customTokenInstance.balanceOf(sender);

    assert.equal(balance.toNumber(), totalSupply - transferAmount);
    assert.equal(transferResult.logs[0].event, "Transfer", "check event call");

  });

});
```

모카이용해서 토큰 테스트코드.
테스트할떄는 컴파일 이후에 실제 서버에 배포가 되어있어야함

가나쉬켜고 7545포트 일단 잡고

https://github.com/bear2u/erc20_token_react

``java
truffle compile
``

build에 contracts에 파일 생성됨.

truffle.js에서 가나쉬 포트설정 그대로 잡아주고

``java
truffle test
``


배포는
``java
truffle deploy
truffle deploy --reset
``

getWeb3.js파일에서 서버 설정 가능.

스마트계약은 contract폴더

배포는 migration폴더

getweb3.js 는 메타마스크에서 가져올지 아니면 Http providor직접 연결해서 처리할지.

솔리디티에 바로접근하는게 아니라. 빌드되서 나온 json파일을 파싱하면서 데이터처리한다.


여러개 파일에서 하나면 변경하면서 재배포하고싶을때
migrations에 1_ 2_같은 파일들 순서로 잡아서 뭐하고뭐하고.






* 리액트 설치

* 리덕스 기본 개념.
```java
npm run eject
```
하게되면 리액트에 숨겨져있던 config가 밖으로 나오게된다.





