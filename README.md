# geth-private-chain
This is a demo about how to set up a private ETH chain on your own network.

## 簡介
要連上 Ethereum 就需要安裝 Ethereum Node，在這邊我們選擇使用 Golang 開發的 ETH 客戶端 Geth 來安裝 Ethereum Node。
接下來就來一步一步的學學怎麼使用 Geth，甚至如何使用 Geth 來架設自己的 Ethereum Muti-Nodes 私有鏈。

首先我已在 Linode 上開啟一台 Ubuntu 虛擬機器作為各位可以連線的節點。


## 安裝 Geth
- 使用 Homebrew 在 macOS 上安裝 Geth:
```
$ brew tap ethereum/ethereum
$ brew install ethereum
```
- 也可以選擇使用官方 build 好的各平台 Geth 執行檔:
[下載](https://geth.ethereum.org/downloads/)

- Ububtu 上使用以下指令安裝 Geth：
```
$ sudo apt-get install -y software-properties-common
$ sudo add-apt-repository -y ppa:ethereum/ethereum
$ sudo apt-get update
$ sudo apt-get install -y ethereum
```

## 以太坊 Main Net

理論上只要執行以下指令就會自動連上 chain id 為 1 的主網。
```
$ geth
```
這時候 Geth 開始同步帳本資料到你的虛擬機器了，並且會在你的本機資料夾上建立一些資料夾，.ipc 存存放連線資訊、keystore 儲存帳號資料， chaindata 資料夾下載了 Ethereum 帳本資料等。
其實這樣你的機器就已經連上 Ethereum Network，並成為 Ethereum 中的一份子了，但等待 Main Net 完成同步需要花很久的時間...而且我們也沒有真的以太幣（主網上的）來互動。


## 連上 Test Net 
Test Net 有很多個，其中有一個 chain id 為 3 的網路叫做 “Ropsten。
```
$ geth --testnet
```

## 刪除本機資料
如果怕用完硬碟空間的話，可以把不用的帳本紀錄刪除，指令如下:
```
$ geth --testnet removedb // 刪除測試鏈資料
$ geth removedb // 刪除主鏈資料
```

## 建立自己的 Private Net

- 建立自己的 Private Net
- 要建立自己的 Ethereum Private Net 其實很簡單，只要先定義好以下這兩項就能建立自己的 Private Net：

Network id，決定自己的 network id 是什麼
Genesis 檔案，決定自己的創世區塊初始帳本資料
而當其他機器要連上這個 Private Net，就需要用一樣的 network id 及相同的 genesis 檔案（代表初始共識一致），如此就能夠連上這個 Private Net 了（一開始可能還需要提供其他 Peers 的位址給 geth 才能連上 Private Net）。

## 創世區塊
```
// genesis9901.json 
{
    "config": {
        "chainId": 9901,
        "homesteadBlock": 0,
        "eip150Block": 0,
        "eip150Hash":"0x0000000000000000000000000000000000000000000000000000000000000000",
        "eip155Block": 0,
        "eip158Block": 0,
        "byzantiumBlock": 0,
        "constantinopleBlock": 0
    },
    "nonce": "0x0000000000009901",
    "timestamp": "0x00",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x00",
    "gasLimit": "0x4c4b40",
    "difficulty": "0x0400",
    "mixhash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0x0000000000000000000000000000000000000000",
    "alloc": {
    }
}
```
這邊我們設定了一個 id 為 9901 的私鏈，你可以設成任何想要的數字，但請避開主鏈及知名的測試鏈（基本上 1–10 盡量不要用);
而 difficulty 則定義了 proof-of-work 的難度，這邊設成 0x400 其實就代表 1024，代表運算難度只有 1024，讓我們的 private chain 大約只要 10–15 秒就能產生一個區塊。

需要建立的資料路徑如下
```
- ~/chain/genesis9901.json 
- ~/.ethereum/net9901/
```

這時候需要執行初始化指令（第一次需要而已）：

```
$ geth --datadir ~/.ethereum/net9901 init ~/chain/genesis9901.json
```

再來是每次要開啟鏈（ Node ）的指令：
```
geth --datadir ~/.ethereum/net9901 --networkid 9901 console
```

這邊有幾個細節要注意:
- tcp/port 的 安全性設定，in/out bound rule 之類的。
- Linode 上我使用 pm2 來管理運作，在背景執行，檔案如下：
  ```
  [
    {
      "name"              : "geth",
      "cwd"               : "/usr/bin/",
      "script"            : "geth",
      "args"              : "--networkid 9901 --http.addr '66.228.52.222'  --http --http.corsdomain '*' --http.api web3,eth,debug,personal,net,miner --http.port 8545  --datadir ~/.ethereum/net9901 --port 30303 console",
      "log_date_format"   : "YYYY-MM-DD HH:mm Z",
      "out_file"      : "~/.ethereum/log/geth_out.log",
      "error_file"    : "~/.ethereum/log/geth_err.log",
      "log_file"      : "~/.ethereum/log/geth_log.log",
      "merge_logs"        : false,
      "watch"             : false,
      "max_restarts"      : 10,
      "exec_interpreter"  : "none",
      "exec_mode"         : "fork_mode"
    }
  ]
  ```
  在上述檔案我來另外加了開啟透過 http 連線的權限參數。

## Geth Console 常用指令

開啟 Geth Node 後直接打字會有一個類似 Javascript console。
- 查看節點的全部帳號
  ```
  > eth.accounts
  []
  ```
  理論上目前節點沒有帳號，應回傳空陣列。
- 查看節點區塊數量
  ```
  > eth.blockNumber
  0
  ```
  這表示此節點目前還沒開挖任何區塊，如果有連上其他已經開挖的鏈，區塊則會被同步。

## Private Chain 連結其他 Node
現在架一個 Private Chain 對我們來說不是問題了，不過現在整個 Private Chain 只有一個 Node，怎麼與其他 Node 連結呢？
另外一台現在也仿造之前的步驟裝好環境，使用相同的 Genesis.json（一定要一模一樣，例如：9901）檔案建立、開啟 Private Chain，並建立好一個帳號，然後先不要進行挖礦。


當前我們兩個 Node 是分開的，並不知道彼此的存在：
```
Node A > admin.peers
[]

Node B > admin.peers
[]
```

想要把 B node（未開挖，無交易紀錄）連上 A node（已開挖，有交易紀錄）：

執行以下指令，得到 A node 的位址。
```
Node A > admin.nodeInfo.enode
```

以我在 Linode 的節點位置為例：
"enode://dbd5e2bb32a71901cb25abf8a0254bfcb3236831785553cf8607fc5479144021dffce5d0c17edee78bb66c3c852a1b605d5616092914cb4b9c0f4797ca892735@66.228.52.222:30303"

只要你的創世區塊，鏈 id 和 網路 id 與我的一樣，並且執行：
```
admin.addPeer("enode://dbd5e2bb32a71901cb25abf8a0254bfcb3236831785553cf8607fc5479144021dffce5d0c17edee78bb66c3c852a1b605d5616092914cb4b9c0f4797ca892735@66.228.52.222:30303")
```
應該就會連上我們的 9901 私鏈了！

這時候再執行查看區塊數的指令，應該就會看到最新已挖到的去塊數（例如：171）
```
> eth.blockNumber
171
```


## 使用網頁錢包
（無法挖礦）
當然你也可以不設置節點，僅透過 MetaMask 錢包（瀏覽器外掛)，
從切換網路的下拉選單，選擇我們的私鏈網 9901，方法為自訂 RPC:
```
網路名稱 隨意
新的 PRC URL 填入我 expose 的 http://66.228.52.222:8545/
鏈 id 填入 9901
```

就可以查看帳號(錢包地址)餘額或進行轉帳交易等，
寫入鏈上區塊需要支付少許 Gas 作為給礦工的手續費。
當然如果進行了交易，就需要有礦工幫忙計算和驗證..資料才會打包上鏈，否則會一直 Pending 該筆交易。

