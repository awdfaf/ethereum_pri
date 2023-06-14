# Hyperledger Besu

- 자바 설치
- hyperledger besu 다운

[GitHub - hyperledger/besu at release/22.1.2](https://github.com/hyperledger/besu/tree/release/22.1.2)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled.png)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%201.png)

gradlew*  빌드(컴파일?)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%202.png)

./gradlew installDist 입력

이 과정에서 에러 → 자바문제, 경로 한글

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%203.png)

- besu 환경변수 설정

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%204.png)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%205.png)

이더리움 메인넷에 붙기위해 동작

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%206.png)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%207.png)

폴더 생성

[Vanity ETH](https://vanity-eth.tk/)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%208.png)

이더리움 형식에 맞는 계정 생성 사이트

node1 

Address: 0x0c4373f22AcF24bD2aff801e8Cee81F952f743a0

Private key: 0c7176e3287fe3a98812106254fc09e3241fade438723ff4c15b4c3735cfd213

node2

Address: 0x7BFBbFd78614Ea81E5F6D656f6E945ad86e00623

Private key: 5b263353b6c453a880860a9a4d76a4adf1c83d12bab6550648fc82b0a97b46d2

node3

Address: 0x7757ab7174ac0aB988A5D121645E51a316a7c42f

Private key: a992b714ae70549200efa65a0ccbed24147b11a0e40c99e3b60c9c78aec98faf

node4

Address: 0xac55529225Dbef204D41B5dDC869a6B21b7c4446

Private key: 9f9ffad09acf68f47b225506bc2ab85bdd9370825e9ec1bfc9f176d74989c4c9

- genesis.json 만들기

[Create a private network using IBFT 2.0 - Hyperledger Besu](https://besu.hyperledger.org/en/stable/private-networks/tutorials/ibft/#2-create-a-configuration-file)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%209.png)

노드들을 코드에 집어넣기

- genesis.json 초기화

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2010.png)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2011.png)

besu operator generate-blockchain-config --config-file=genesis.json --to=networkFiles --private-key-file-name=key

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2012.png)

networkfiles에서 genesis 파일 밖으로, 원래 genesis는 _config붙이고

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2013.png)

노드 1,2,3,4 복붙

- 노드 구동

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2014.png)

노드1에만 

besu --data-path=data --genesis-file=../genesis.json --rpc-http-enabled --rpc-http-api=ETH,NET,IBFT --host-allowlist ="*" --rpc-http-cors-origins="all"

입력

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2015.png)

조금 올려서 enode url 찾아서 복사

Enode URL enode://d9ed3214d64488617902c8a1a8f2f41af74e9e3b260215f3546184d44b400214f4fc297b3a5160bd93fc8147f39631aef6c0f14fa61675579c38da8adb335288@127.0.0.1:30303

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2016.png)

각 노드에 명령어 붙여넣기

2

besu --data-path=data --genesis-file=../genesis.json --bootnodes=enode://d9ed3214d64488617902c8a1a8f2f41af74e9e3b260215f3546184d44b400214f4fc297b3a5160bd93fc8147f39631aef6c0f14fa61675579c38da8adb335288@127.0.0.1:30303 --p2p-port=30304 --rpc-http-enabled --rpc-http-api=ETH,NET,IBFT --host-allowlist ="*" --rpc-http-cors-origins="all" --rpc-http-port=8546

3

besu --data-path=data --genesis-file=../genesis.json --bootnodes=enode://d9ed3214d64488617902c8a1a8f2f41af74e9e3b260215f3546184d44b400214f4fc297b3a5160bd93fc8147f39631aef6c0f14fa61675579c38da8adb335288@127.0.0.1:30303 --p2p-port=30305 --rpc-http-enabled --rpc-http-api=ETH,NET,IBFT --host-allowlist ="*" --rpc-http-cors-origins="all" --rpc-http-port=8547

4

besu --data-path=data --genesis-file=../genesis.json --bootnodes=enode://d9ed3214d64488617902c8a1a8f2f41af74e9e3b260215f3546184d44b400214f4fc297b3a5160bd93fc8147f39631aef6c0f14fa61675579c38da8adb335288@127.0.0.1:30303 --p2p-port=30306 --rpc-http-enabled --rpc-http-api=ETH,NET,IBFT --host-allowlist ="*" --rpc-http-cors-origins="all" --rpc-http-port=8548

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2017.png)

4개의 노드 블록생성

- API

[Use JSON-RPC over HTTP, WS, and IPC - Hyperledger Besu](https://besu.hyperledger.org/en/stable/public-networks/how-to/use-besu-api/json-rpc/)

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2018.png)

클릭

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2019.png)

전체복사

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2020.png)

import

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2021.png)

붙여넣기

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2022.png)

import

![Untitled](Hyperledger%20Besu%20a53ca4510bc04b69b47a106e1538bd9a/Untitled%2023.png)

완료

포스트맨으로 블록체인 네트워크 정보를 받아온다

노드 4개 구동

포스트맨 테스트

이 이후 잘 안됨,,,,
