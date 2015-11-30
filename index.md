
# go-ethereum
## Blockchain Labo #1

Azusa Kikuchi

---

## 目次

- go-ethereumのインストール
- アカウント設定
- mining
- embark

---

### Ethereum

* go
* cpp
* python

---

## Install

---

### Install

Mac OS X

```
brew tap ethereum/ethereum
brew install ethereum
```

---

### 起動

```
geth
```

---

### geth オプション

* --genesis   genesisブロックを設定
* --networkid ネットワーク (0=Olympic, 1=Frontier, 2=Morden)
* --rpc       RPCサーバを立ち上げる 
* --rpccorsdomain "*" クロスオリジンのリクエストを受け入れるドメイン

---

### geth オプション(続き)

* --mine      マイニング 
* --minerthreads "4" マイニングするためのCPUスレッド数
* --unlock 0  0個目のアカウントをアンロックする
* console     JSのconsoleを立ち上げる

---

### 開発用ネットワークで起動

```
geth --genesis genesis.json --networkid 1234 --rpc --rpccorsdomain "*" --mine --unlock 0
```

---

## アカウント設定

---

アカウント作成

```
geth account new
```

アカウントリスト

```
geth account list
```

---

### JSON RPC

```
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_accounts","params":[],"id":1}'\
 http://127.0.0.1:8545
```

---

## Mining

---

## CPU Mining

geth

```
geth --mine --minerthreads=4
```

JS Console

```
> miner.start(8)
> miner.stop()
```

---

### GPU Mining 

- cpp-ethererumのみ
- GPUがNVIDIA製品の場合は事前にCUDAをインストール

```
brew install cpp-ethereum --with-gpu-mining --devel --build-from-source
```

---

### GPU Mining 

gethのrpc接続でマイニングもできる

```
geth --rpc --rpccorsdomain localhost 2>> geth.log &
ethminer -G  // -G for GPU
tail -f geth.log
```

---

### Hashrate

Hashrateが高いとBlockを見つけ報酬がもらえる確率が高くなる

- cpp-ethererumをインストール
```
eth -M -G // -M for Benchmark
```

---

### Hashrate

![Radeon](https://i.gyazo.com/c88114cab92821c62892888ae6e149a3.png)
![AWS](https://i.gyazo.com/c38322ed5304a44f94a6c21fd222ce16.png)

https://forum.ethereum.org/discussion/2134/gpu-mining-is-out-come-and-let-us-know-of-your-bench-scores

---

### Mining profitability

![Mining Profitability](https://i.gyazo.com/12f6d096dcc1ea4f3da488627311bbd6.png)

http://badmofo.github.io/ethereum-mining-calculator/

---

### 残高を確認する

JS Console
```
> web3.fromWei(eth.getBalance(eth.coinbase), "ether")
```

---

## DApp

---

### DApp開発環境

- Mix Standalone IDE
- Embark / Meteor
- BlockApps

---

### Embark

- いい感じにprivate blockchainしてくれる
- 複数コントラクト対応
- IPFSへのデプロイが簡単(らしい)

---

### Install

```
npm install -g embark-framework grunt-cli
```

---

### Demo

```
embark demo
cd embark_demo
embark blockchain
embark run
```

---

### 次回予告(?)

- HashReg
- NatSpec
- Solidity
