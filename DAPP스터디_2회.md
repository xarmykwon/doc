###DAPP 스터디 2회

실습.

새로운 폴더 생성후 vscode에서 연다.
vscode에서 터미널로 들어간다.


박스 주소
http://truffleframework.com/boxes/react
```java
⇒  truffle unbox react
Downloading...
Unpacking...
Setting up...
Unbox successful. Sweet!

Commands:

  Compile:              truffle compile
  Migrate:              truffle migrate
  Test contracts:       truffle test
  Test dapp:            npm test
  Run dev server:       npm run start
  Build for production: npm run build
```
명령어를 입력해서 다운받는다.
```java
npm install -g ganache-cli
```
이것도 받는다. 가나시를 커맨드에서 사용가능하게 해주는것이다.


```java
truffle developer

Truffle Develop started at http://127.0.0.1:9545/

Accounts:
(0) 0x627306090abab3a6e1400e9345bc60c78a8bef57
(1) 0xf17f52151ebef6c7334fad080c5704d77216b732
(2) 0xc5fdf4076b8f3a5357c5e395ab970b5b54098fef
(3) 0x821aea9a577a9b44299b9c15c88cf3087f3b5544
(4) 0x0d1d4e623d10f9fba5db95830f7d3839406c6af2
(5) 0x2932b7a2355d6fecc4b5c0b6bd44cc31df247a2e
(6) 0x2191ef87e392377ec08e7c08eb105ef5448eced5
(7) 0x0f4f2ac550a1b4e2280d04c21cea7ebd822934b5
(8) 0x6330a553fc93768f612722bb8c2ec78ac90b3bbc
(9) 0x5aeda56215b167893e80b4fe645ba6d5bab767de

Private Keys:
(0) c87509a1c067bbde78beb793e6fa76530b6382a4c0241e5e4a9ec0a0f44dc0d3
(1) ae6ae8e5ccbfb04590405997ee2d52d2b330726137b875053c36d94e974d162f
(2) 0dbbe8e4ae425a6d2687f1a7e3ba17bc98c673636790f1b8ad91193c05875ef1
(3) c88b703fb08cbea894b6aeff5a544fb92e78a18e19814cd85da83b71f772aa6c
(4) 388c684f0ba1ef5017716adb5d21a053ea8e90277d0868337519f97bede61418
(5) 659cbb0e2411a44db63778987b1e22153c086a95eb6b18bdf89de078917abc63
(6) 82d052c865f5763aad42add438569276c00d3d88a2d062d36b2bae914d58b8c8
(7) aa3680d5d48a8283413f7a108367c7299ca73f553735860a87b08f39395618b7
(8) 0f62d96d6675f32685bbdb8ac13cda7c23436f63efbb9d07700d8669ff12b7c4
(9) 8d5366123cb560bb606379f90a0bfd4769eecc0557f1b362dcae9012b548b1e5
```
입력하게되면 실행이된것이다.

* private server 여러가지 실행방법
1. geth
2. ganache
3. ganache-cli
4. truffle server
5. testnet(linkeby, rosten, kovan?등등)

이중에서 우리는 오늘 truffle 자체 서버 이용하는 방법으로 해본다.

unbox가 완료되면

```java
truffle compile
```
명령어를 입력 하고나면 빌드 폴더가 생기고
그안에 contracts에 json 파일이 생성되어있다.

```java
truffle(develop)> deploy
Using network 'develop'.

Running migration: 1_initial_migration.js
  Deploying Migrations...
  ... 0xddcd3e2e908d43e2631d80133d1cc8261ba97894cb48e0b389a53739e41b599d
  Migrations: 0x8cdaf0cd259887258bc13a92c0a6da92698644c0
Saving successful migration to network...
  ... 0xd7bc86d31bee32fa3988f1c1eabce403a1b5d570340a3a9cdba53a472ee8c956
Saving artifacts...
Running migration: 2_deploy_contracts.js
  Deploying SimpleStorage...
  ... 0x9244eaa47db40c7d87b2821238faed81f713caf97784bd846daa0829760c03f8
  SimpleStorage: 0x345ca3e014aaf5dca488057592ee47305d9b3e10
Saving successful migration to network...
  ... 0xf36163615f41ef7ed8f4a8f192149a0bf633fe1a2398ce001bf44c43dc7bdda0
Saving artifacts...
```

배포된 SimpleStorage: 0x345ca3e014aaf5dca488057592ee47305d9b3e10 값과
빌드된 simplestorage의 주소가 같다.


truffle.js , truffle-config.js가 왜 있느냐. 무엇이냐.
truffle.js에

http://truffleframework.com/docs/advanced/configuration

의 설정을 가져와서 복붙한다.

```javascript
module.exports = {
  // See <http://truffleframework.com/docs/advanced/configuration>
  // to customize your Truffle configuration!
  networks: {
    development: {
      host: "127.0.0.1",
      port: 9545,
      network_id: "*" // Match any network id
    }
  }
};
```

port를 9545로 바꾸면 실행됨.

migrate

migrate --reset 

```java
var SimpleStorage = artifacts.require("./SimpleStorage.sol");

module.exports = function(deployer) {
  deployer.deploy(SimpleStorage);
};

```

npm start 로 서버실행시킴.

그러면 브라우저에 사이트가 뜨고.

메타마스크로

localhost:9545로 접속.

```java
⇒  truffle developer
에서 얻은 private key를 메타마스크 localhost에 import계정으로 넣어준다.
```

브라우저 새로고침하면 바로 돈을 내라고 한다. 서브밋하고 나서 기본값이 5가되면 성공.



https://github.com/bear2u/erc20_token_react/blob/master/contracts/CustomToken.sol

토큰과 코인의 차이.

코인은 rest service , 지갑등 제공해주는게 코인.
토큰은 가스비도하고 뭐 그런건가.. 음

토큰 종류
https://etherscan.io/tokens
코드도 볼수있다.

```javascript
pragma solidity ^0.4.0;

contract ERC20Interface {
    function totalSupply() view public returns (uint256);

	// 주소넣엇을때 잔액 가져오기
    function balanceOf(address _owner) view public returns (uint256);

    function transfer(address _to, uint256 _value) public returns (bool success);

    function transferFrom(address _from, address _to, uint256 _value) public returns (bool success);
	// 트랜스퍼 하기전에 누구에게 몇개를 줄지 미리 정하는것. from없이 전송으로 보낼수있지.
    function approve(address _spender, uint256 _value) public returns (bool success);

    function allowance(address _owner, address _spender) view public returns (uint256 remaining);

    event Transfer(address indexed _from, address indexed _to, uint256 _value);

    event Approval(address indexed _owner, address indexed _spender, uint256 _value);
}

contract CustomToken is ERC20Interface{

    string public _symbol;
    string public _name;
    uint public _decimals;
    uint256 _totalSupply; // 총수량. 발행할 토큰수?

    //이 계약의 오너 저장
    address public owner;

    //각각의 계정에 저장된 잔액을 저장
    mapping (address => uint256) balances;

    //계좌 주인에서 다른 계좌로 출금되는지 승인 여부 저장하는 2중 배열형태
    mapping(address => mapping ( address => uint256 )) allowed;

    //주인만 입장하도록 승인하는 함수
    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }

    //초기 토큰 생성 부분
    constructor() public{
        //TODO 계정에 초기값 입력
        owner = msg.sender;
    }
    
    function generate(string symbol, string name, uint decimals, uint256 totalSupply) public onlyOwner{
        _symbol = symbol;
        _name = name;
        _decimals = decimals;
        _totalSupply = totalSupply;
        
        balances[msg.sender] = _totalSupply;
    }

    //총 수량 확인 하는 함수
    function totalSupply() view public returns (uint256) {
        return _totalSupply;
    }

    //주인의 계좌의 잔액 조회
    function balanceOf(address _owner) view public returns (uint256) {
        return balances[_owner];
    }

    //_to 에게 금액을 전송하는 함수
    function transfer(address _to, uint256 _amount) public returns (bool success) {
        if(
            //전송자의 잔액이 전송할려는 금액보다 많은지 체크
            balances[msg.sender] >= _amount
            //전송 금액이 0보다 큰지 체크
            && _amount > 0
            //받는(_to) 잔액 + _amount > _to 의 잔액 보다 큰지
            && balances[_to] + _amount > balances[_to]
        ) {
            //잔액을 뺀 금액을 전송자의 잔액에서 제거한다.
            balances[msg.sender] -= _amount;
            //받는 사람의 잔액에 전송금액을 더한다.
            balances[_to] += _amount;
            //transfer 이벤트 발생 처리
            emit Transfer(msg.sender, _to, _amount);

            return true;
        }

        //그리고 성공여부 리턴
        return false;
    }

    //from -> to 토큰을 전송을 하는데 승낙이 있을 경우에만 가능하다.
    function transferFrom(address _from, address _to, uint _amount) public returns (bool success) {
        //TODO from 잔액이 _amount 보다 같거나 큰경우
        //TODO 승인 금액이 _amount보다 같거나 클경우
        //TODO _amount > 0
        //TODO _to의 잔액 + _amount > _to 의 잔액 의 경우
        
        if(
            balances[_from] >= _amount
            && allowed[_from][_to] >= _amount
            && _amount > 0
            && balances[_to] + _amount > balances[_to]
        ) {
            //TODO _from 잔액에 _amount를 뺀다.
            balances[_from] -= _amount;
            //TODO allowed from, msg.sender 로부터 _amount 를 뺀다.
            allowed[_from][_to] -= _amount;
            //TODO _to 잔액에 _amount를 더한다.
            balances[_to] += _amount;
            //TODO Transfer 이벤트를 발생시킨다.
            emit Transfer(_from, _to, _amount);
            return true;
        }

        return false;
    }

    //승인시 이차 배열에 넣고 동작함
    function approve(address _spender, uint256 _amount) public returns (bool success) {
        //함수 호출하는 사람이 _spender 에게 얼마나 줄껀지 정한다.
        allowed[msg.sender][_spender] = _amount;
        emit Approval(msg.sender, _spender, _amount);
        return true;
    }

    //승인 잔액 조회
    function allowance(address _owner, address _spender) view public returns (uint remaining) {
        return allowed[_owner][_spender];
    }


}
```

위 소스를 리믹스에 파일을 생성해서 입력한다. 빌드도 한다.

테스트 계정 5개가주어지고.

"TM","test custom token",2,1000를 생성자로 입력한다.

디버깅을 보면 제대로 입력되어있다.

banlanceof에 지갑주소를 넣으면 몇개인지 나온다.1000개.

다른지갑 주소를 체크하면 0개라고 나온다.


0x14723a09acff6d2a60dcdf7aa4aff308fddc160c,100
transfer를 하면 다른 지갑에 100개 토큰을 주게된다.



allownce 로 주겠다고 한 후에. transferFrom 하면 실제 이동이되고, 그냥 fransferFrom하면 이동이 안됨

* 배포
메타마스크로 rinkeby들어가서 remix 새로고침
run에서 web3환경 선택하면 deploy가 나온다. 실제 배포 가능.

리액트 좋은점은 값이 동적으로 바뀌었을때 뷰가 자동으로 렌더링되서 바꿔준다.?

npm run build
npm start
















