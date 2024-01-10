<!-- @format -->
# English README　[Jump to Japanese Version](#japanese)

# Preview
For an easy interaction with the contract use abi.ninja website.
Here is a link to the contract loaded on it: [Lottery contract]()

Click on function on the left to add them in the center of the page and interact with them.
- Functions under the 'READ' category are for getting actual values.
- Functions under the 'Write' category are for inserting new data.

- NOTE: The above contract is deployed on the Sepolia Testnet, so testnet funds are required for interacting with it.


# Foundry Lottery

Contract is deployed at xxxx
[View on Sepolia]()

It is a contract thats reate a proveably random smart contract lottery.
A true randomness. Can't cheat for guessing numbers or whatever can be usually guessed.

I used the 32 hours long video from Cyfrin Foundry Blockchain course to learn about Foundry.  
[Cyfrin Foundry](https://github.com/Cyfrin/foundry-full-course-f23)


## What it does in details

1. Users can enter by paying for a ticket
2. ticket fees of all player will go to the winner during the draw
3. The draw happend every X period of time
4. Use of chainlink VRF and Chainlink automation to generate randomness and a time based trigger to trigger the draw

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

## Quickstart

```
git clone https://github.com/Jer-B/Foundry_Lottery
cd Foundry_Lottery
forge build
```

# Usage

## Start a local node

```
make anvil
```

## Library

If you're having a hard time installing the chainlink library, you can optionally run this command. 

```
forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit
```

## Deploy

This will default to your local node. You need to have it running in another terminal in order for it to deploy.

```
make deploy
```

## Deploy - Other Network

[See below](#deployment-to-a-testnet-or-mainnet)

## Testing


1. Unit
2. Integration
3. Forked
4. Staging

This repo we cover #1 and #3.

```
forge test
```

or

```
forge test --fork-url $alchemy_RPC_sepolia
```

### Test Coverage

```
forge coverage
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `alchemy_RPC_sepolia` and `PRIVATE_KEY_TESTNET` as environment variables. You can add them to a `.env` file, similar to what you see in `.env.example`.

- `PRIVATE_KEY_TESTNET`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `alchemy_RPC_sepolia`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

1. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.

3. Deploy

```
make deploy ARGS="--network sepolia"
```

This will setup a ChainlinkVRF Subscription for you. If you already have one, update it in the `scripts/HelperConfig.s.sol` file. It will also automatically add your contract as a consumer.

3. Register a Chainlink Automation Upkeep

[You can follow the documentation if you get lost.](https://docs.chain.link/chainlink-automation/compatible-contracts)

Go to [automation.chain.link](https://automation.chain.link/new) and register a new upkeep. Choose `Custom logic` as your trigger mechanism for automation. Your UI will look something like this once completed:

![Automation](https://github.com/Cyfrin/foundry-smart-contract-lottery-f23/raw/main/img/automation.png)

## Scripts

After deploying to a testnet or local net, you can run the scripts.

Using cast deployed locally example:

```
cast send <RAFFLE_CONTRACT_ADDRESS> "enterRaffle()" --value 0.1ether --private-key <PRIVATE_KEY_TESTNET> --rpc-url $alchemy_RPC_sepolia
```

or, to create a ChainlinkVRF Subscription:

```
make createSubscription ARGS="--network sepolia"
```

## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see an output file called `.gas-snapshot`

# Formatting

To run code formatting:

```
forge fmt
```


<a name="japanese"></a>
# 日本語版のREADME

# プレビュー
コントラクトとの簡単な対話には abi.ninja ウェブサイトを使用してください。
以下は、それにロードされたコントラクトへのリンクです: [Lottery contract]()

左側の関数をクリックして、それらをページの中央に追加し、それらと対話します。
- `READ`カテゴリーの下にある関数は実際の値を取得するためのものです。
- `Write`カテゴリーの下にある関数は新しいデータを挿入するためのものです。

- 注意: 上記のコントラクトは Sepolia テストネット上にデプロイされており、それと対話するにはテストネット用の資金が必要です。

# Foundry  Lottery

このコントラクトは、0xxxx にデプロイされています。
[Sepoliaで表示]()

これは、証拠のあるランダムなスマートコントラクトの抽選を作成する契約です。
真のランダム性。数字を予想したり、通常予想されるものをだますことはできません。

Foundryを学ぶために、Cyfrin Foundry Blockchainコースの32時間の長いビデオを使用しました。
[Cyfrin Foundry](https://github.com/Cyfrin/foundry-full-course-f23)

## このスマートコントラクトが詳細で行うこと

1. ユーザーはチケット料金を支払って入場できます。
2. 全てのプレイヤーのチケット料金は、抽選の際に優勝者に支払われます。
3. 抽選はX時間ごとに行われます。
4. Chainlink VRFとChainlink Automationを使用してランダム性を生成し、時間ベースのトリガーをトリガーするために使用します。

## 必要条件

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - git --version を実行して git version x.x.x のような応答が表示されれば成功です。
- [foundry](https://getfoundry.sh/)
  - forge --version を実行して forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z) のような応答が表示されれば成功です


## クイックスタート

```
git clone https://github.com/Jer-B/Foundry_Lottery
cd Foundry_Lottery
forge build
```


## ローカルノード(ブロックチェーン)を起動する

```
make anvil
```

## ライブラリ

Chainlinkライブラリのインストールに問題がある場合、オプションでこのコマンドを実行できます。

```
forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit
```

## 使用方法

デプロイメント:

```
make deploy
```

## テスト方法

1. ユニットテスト
2. 統合テスト
3. フォークテスト
4. ステージングテスト

このリポジトリではテスト番号1と3をカバーしています。


```
forge test
```

or 

```
forge test --match-test testFunctionName
```
上記の testFunctionName を実際にテストしたいテスト関数の名前に変更しないでください。(test フォルダ内のファイルから関数を参照してください)

or

```
forge test --fork-url $alchemy_RPC_sepolia
```

### テストカバレッジ

```
forge coverage
```


# テストネットまたはメインネットへのデプロイ

1. 環境変数の設定

`alchemy_RPC_sepolia` と `PRIVATE_KEY_TESTNET` を環境変数として設定する必要があります。これらを .env ファイルに追加することができます。.env.example に示されているようなものです。


- `PRIVATE_KEY_TESTNET`: アカウントのプライベートキー[metamask](https://metamask.io/)). **注意**: 開発のために、実際の資金が関連付けられていないキーを使用してください。

  - [ここでキーのエクスポート方法を学ぶことができます](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `alchemy_RPC_sepolia`: これはあなたが作業している Sepolia テストネットノードのURLです。 [Alchemy](https://alchemy.com/?a=673c802981)　から無料でセットアップできます。

オプションで、 [Etherscan](https://etherscan.io/)　で契約を検証したい場合は ETHERSCAN_API_KEY を追加してください。

1. テストネットETHを取得

 [faucets.chain.link](https://faucets.chain.link/) にアクセスし、テストネットETHを取得してください。MetamaskでETHが表示されるはずです。

3. デプロイ

```
make deploy ARGS="--network sepolia"
```

これにより、ChainlinkVRFサブスクリプションが設定されます。既にサブスクリプションがある場合は、`scripts/HelperConfig.s.sol` ファイルで更新してください。また、自動的にあなたの契約をコンシューマーとして追加します。

3. Chainlink Automation Upkeepの登録

[分からない場合、ドキュメンテーションに従ってください。](https://docs.chain.link/chainlink-automation/compatible-contracts)

 [automation.chain.link](https://automation.chain.link/new) に移動し、新しいUpkeepを登録してください。自動化のトリガーメカニズムとして `Custom logic` を選択してください。登録が完了したら、UIは次のようになります：

![Automation](https://github.com/Cyfrin/foundry-smart-contract-lottery-f23/raw/main/img/automation.png)

## Scripts

テストネットまたはローカルネットワークにデプロイした後、スクリプトを実行できます。

ローカルにデプロイされたcastを使用する例：

```
cast send <RAFFLE_CONTRACT_ADDRESS> "enterRaffle()" --value 0.1ether --private-key <PRIVATE_KEY_TESTNET> --rpc-url $alchemy_RPC_sepolia
```

または、ChainlinkVRFサブスクリプションを作成するには：

```
make createSubscription ARGS="--network sepolia"
```

## ガス代確認


```
forge snapshot
```

`.gas-snapshot` という名前の出力ファイルが表示されます


# フォーマット


コードのフォーマットを実行するには：
```
forge fmt
```
