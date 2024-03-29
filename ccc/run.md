## 測試鏈


```
root@localhost:~# geth --ropsten
INFO [10-11|05:08:40.783] Starting Geth on Ropsten testnet... 
INFO [10-11|05:08:40.786] Maximum peer count
    ETH=50 LES=0 total=50
INFO [10-11|05:08:40.786] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"WARN [10-11|05:08:40.790] Sanitizing cache to Go's GC limits   
    provided=1024 updated=328
INFO [10-11|05:08:40.790] Set global gas cap
    cap=50,000,000
INFO [10-11|05:08:40.791] Allocated trie memory caches
    clean=49.00MiB dirty=82.00MiB
INFO [10-11|05:08:40.791] Allocated cache and file handles     
    database=/root/.ethereum/ropsten/geth/chaindata cache=164.00MiB handles=524,288
INFO [10-11|05:08:40.799] Opened ancient database
    database=/root/.ethereum/ropsten/geth/chaindata/ancient readonly=false
INFO [10-11|05:08:40.799] Writing custom genesis block
INFO [10-11|05:08:40.828] Persisted trie from memory database  
    nodes=355 size=50.41KiB time=2.611028ms gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [10-11|05:08:40.829] Initialised chain configuration      
    config="{ChainID: 3 Homestead: 0 DAO: <nil> DAOSupport: true EIP150: 0 EIP155: 10 EIP158: 10 Byzantium: 1700000 Constantinople: 4230000 Petersburg: 4939394 Istanbul: 6485846, Muir Glacier: 7117117, Berlin: 9812189, London: 10499401, Engine: ethash}"
INFO [10-11|05:08:40.830] Disk storage enabled for ethash caches   dir=/root/.ethereum/ropsten/geth/ethash count=3
INFO [10-11|05:08:40.830] Disk storage enabled for ethash DAGs 
    dir=/root/.ethash                       count=2
INFO [10-11|05:08:40.830] Initialising Ethereum protocol       
    network=3 dbversion=<nil>
INFO [10-11|05:08:40.831] Loaded most recent local header      
    number=0 hash=419410..ca4a2d td=1,048,576 age=52y6mo1w     
INFO [10-11|05:08:40.831] Loaded most recent local full block  
    number=0 hash=419410..ca4a2d td=1,048,576 age=52y6mo1w     
INFO [10-11|05:08:40.831] Loaded most recent local fast block  
    number=0 hash=419410..ca4a2d td=1,048,576 age=52y6mo1w     
WARN [10-11|05:08:40.832] Failed to load snapshot, regenerating    err="missing or corrupted snapshot"
INFO [10-11|05:08:40.832] Rebuilding state snapshot
INFO [10-11|05:08:40.833] Regenerated local transaction journal    transactions=0 accounts=0
INFO [10-11|05:08:40.833] Gasprice oracle is ignoring threshold set threshold=2
WARN [10-11|05:08:40.833] Error reading unclean shutdown markers   error="leveldb: not found"
INFO [10-11|05:08:40.834] Starting peer-to-peer node
    instance=Geth/v1.10.9-stable-eae3b194/linux-amd64/go1.17   
INFO [10-11|05:08:40.838] New local node record
    seq=1,633,928,920,838 id=41bc6af9b346ff86 ip=127.0.0.1 udp=30303 tcp=30303
INFO [10-11|05:08:40.840] IPC endpoint opened
    url=/root/.ethereum/ropsten/geth.ipc
INFO [10-11|05:08:40.841] Resuming state snapshot generation   
    root=217b0b..62b77b accounts=0 slots=0 storage=0.00B elapsed=8.948ms
INFO [10-11|05:08:40.850] Generated state snapshot
    accounts=257 slots=0 storage=9.55KiB elapsed=17.970ms      
INFO [10-11|05:08:40.854] Started P2P networking
    self=enode://591f250a1afb24f6932be6e01cdccb4849989242d7f0c8c2e54ecadd9e68fb8110662b3eeaf89137898894fbcf81a75207856a59c2f7966314b4ac51e6120e55@127.0.0.1:30303
INFO [10-11|05:08:46.032] New local node record
    seq=1,633,928,920,839 id=41bc6af9b346ff86 ip=172.104.100.202 udp=30303 tcp=30303
INFO [10-11|05:08:51.190] Looking for peers
    peercount=0 tried=16 static=0
```

Console

```
root@localhost:~# geth --ropsten console
INFO [10-11|05:13:33.095] Starting Geth on Ropsten testnet... 
INFO [10-11|05:13:33.098] Maximum peer count
    ETH=50 LES=0 total=50
INFO [10-11|05:13:33.098] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"WARN [10-11|05:13:33.103] Sanitizing cache to Go's GC limits   
    provided=1024 updated=328
INFO [10-11|05:13:33.103] Set global gas cap
    cap=50,000,000
INFO [10-11|05:13:33.104] Allocated trie memory caches
    clean=49.00MiB dirty=82.00MiB
```

開始挖礦


```
> personal.newAccount()
Passphrase: 
Repeat passphrase: 
INFO [10-11|05:24:35.432] Your new key was generated
    address=0x8115cc77Cb6C6d5cA0A2aD521ACf81C3c7002121
WARN [10-11|05:24:35.471] Please backup your key file!
    path=/root/.ethereum/ropsten/keystore/UTC--2021-10-11T05-24-20.860400669Z--8115cc77cb6c6d5ca0a2ad521acf81c3c7002121       
WARN [10-11|05:24:35.471] Please remember your password!       
"0x8115cc77cb6c6d5ca0a2ad521acf81c3c7002121"
```

然後怪怪的

```
> admin.nodeInfo.enode
"enode://591f250a1afb24f6932be6e01cdccb4849989242d7f0c8c2e54ecadd9e68fb8110662b3eeaf89137898894fbcf81a75207856a59c2f7966314b4ac51e6120e55@172.104.100.202:30303"
> admin.addPeer("enode://591f250a1afb24f6932be6e01cdccb4849989242d7f0c8c2e54ecadd9e68fb8110662b3eeaf89137898894fbcf81a75207856a59c2f7966314b4ac51e6120e55@172.104.100.202:30303")
true
> eth.blockNumber
0
> admin.peers
[]
> miner.start(1)
INFO [10-11|05:30:15.614] Updated mining threads
    threads=1
INFO [10-11|05:30:15.615] Transaction pool price threshold updated price=1,000,000,000
ERROR[10-11|05:30:15.615] Cannot start mining without etherbase    err="etherbase must be explicitly specified"
WARN [10-11|05:30:15.616] Served miner_start
    reqid=19 t=2.620749ms err="etherbase missing: etherbase must be explicitly specified"
Error: etherbase missing: etherbase must be explicitly specified
        at web3.js:6357:37(47)
        at web3.js:5091:62(37)
        at <eval>:1:12(4)

> eth.accounts[0]
undefined
> > eth.accounts[0]
SyntaxError: (anonymous): Line 1:1 Unexpected token >
> admin.peers
[]
>  eth.accounts
[]
```


## 私鏈

```
root@localhost:~# mkdir chain
root@localhost:~# vim genesis9901.json
root@localhost:~# mkdir .ethereum
root@localhost:~# cd .ethereum/
root@localhost:~/.ethereum# mkdir net9901
root@localhost:~/.ethereum# ls
net9901
root@localhost:~/.ethereum# cd ..
root@localhost:~# eth --datadir ~/.ethereum/net9901 init ~/chain/genesis9901.json

Command 'eth' not found, did you mean:

  command 'geth' from snap geth (v1.9.5)
  command 'th' from deb torch-trepl

  command 'etw' from deb etw
  command 'etm' from deb etm
  command 'tth' from deb tth
  command 'etr' from deb extremetuxracer

See 'snap info <snapname>' for additional versions.

root@localhost:~# geth --datadir ~/.ethereum/net9901 init ~/chain/genesis9901.json
Fatal: Failed to read genesis file: open /root/chain/genesis9901.json: no such file or directory
root@localhost:~# pwd
/root
root@localhost:~# ls chain
root@localhost:~# vim chain/genesis9901.json
root@localhost:~# geth --datadir ~/.ethereum/net9901 init ~/chain/genesis9901.json
INFO [10-11|04:21:00.991] Maximum peer count                       ETH=50 LES=0 
total=50
INFO [10-11|04:21:00.992] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
WARN [10-11|04:21:00.995] Sanitizing cache to Go's GC limits       provided=1024 updated=328
INFO [10-11|04:21:00.995] Set global gas cap                       cap=50,000,000
INFO [10-11|04:21:00.995] Allocated cache and file handles         database=/root/.ethereum/net9901/geth/chaindata cache=16.00MiB handles=16
INFO [10-11|04:21:00.999] Writing custom genesis block 
INFO [10-11|04:21:01.000] Persisted trie from memory database      nodes=0 size=0.00B time="26.179µs" gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [10-11|04:21:01.019] Successfully wrote genesis state         database=chaindata                              hash=442b8e..c1d392
INFO [10-11|04:21:01.019] Allocated cache and file handles         database=/root/.ethereum/net9901/geth/lightchaindata cache=16.00MiB handles=16
INFO [10-11|04:21:01.022] Writing custom genesis block
INFO [10-11|04:21:01.022] Persisted trie from memory database      nodes=0 size=0.00B time="3.548µs"  gcnodes=0 gcsize=0.00B gctime=0s livenodes=1 livesize=0.00B
INFO [10-11|04:21:01.023] Successfully wrote genesis state         database=lightchaindata                         hash=442b8e..c1d392
root@localhost:~# geth --datadir ~/.ethereum/net9901 --networkid 9901 console
INFO [10-11|04:23:18.605] Maximum peer count                       ETH=50 LES=0 
total=50
INFO [10-11|04:23:18.605] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"
WARN [10-11|04:23:18.608] Sanitizing cache to Go's GC limits       provided=1024 updated=328
INFO [10-11|04:23:18.609] Set global gas cap                       cap=50,000,000
INFO [10-11|04:23:18.609] Allocated trie memory caches             clean=49.00MiB dirty=82.00MiB
INFO [10-11|04:23:18.609] Allocated cache and file handles         database=/root/.ethereum/net9901/geth/chaindata cache=164.00MiB handles=524,288
INFO [10-11|04:23:18.631] Opened ancient database                  database=/root/.ethereum/net9901/geth/chaindata/ancient readonly=false
INFO [10-11|04:23:18.633] Initialised chain configuration          config="{ChainID: 9901 Homestead: 0 DAO: <nil> DAOSupport: false EIP150: 0 EIP155: 0 EIP158: 
0 Byzantium: 0 Constantinople: 0 Petersburg: <nil> Istanbul: <nil>, Muir Glacier: <nil>, Berlin: <nil>, London: <nil>, Engine: unknown}"
INFO [10-11|04:23:18.634] Disk storage enabled for ethash caches   dir=/root/.ethereum/net9901/geth/ethash count=3
INFO [10-11|04:23:18.634] Disk storage enabled for ethash DAGs     dir=/root/.ethash                       count=2
INFO [10-11|04:23:18.634] Initialising Ethereum protocol           network=9901 
dbversion=<nil>
INFO [10-11|04:23:18.639] Loaded most recent local header          number=0 hash=442b8e..c1d392 td=1024 age=52y6mo1w
INFO [10-11|04:23:18.639] Loaded most recent local full block      number=0 hash=442b8e..c1d392 td=1024 age=52y6mo1w
INFO [10-11|04:23:18.640] Loaded most recent local fast block      number=0 hash=442b8e..c1d392 td=1024 age=52y6mo1w
WARN [10-11|04:23:18.640] Failed to load snapshot, regenerating    err="missing 
or corrupted snapshot"
INFO [10-11|04:23:18.640] Rebuilding state snapshot
INFO [10-11|04:23:18.640] Regenerated local transaction journal    transactions=0 accounts=0
INFO [10-11|04:23:18.641] Gasprice oracle is ignoring threshold set threshold=2 
WARN [10-11|04:23:18.642] Error reading unclean shutdown markers   error="leveldb: not found"
INFO [10-11|04:23:18.642] Resuming state snapshot generation       root=56e81f..63b421 accounts=0 slots=0 storage=0.00B elapsed=2.088ms
INFO [10-11|04:23:18.642] Generated state snapshot                 accounts=0 slots=0 storage=0.00B elapsed=2.470ms
INFO [10-11|04:23:18.643] Starting peer-to-peer node               instance=Geth/v1.10.9-stable-eae3b194/linux-amd64/go1.17
INFO [10-11|04:23:18.654] New local node record                    seq=1,633,926,198,653 id=c10a01978f189332 ip=127.0.0.1 udp=30303 tcp=30303
INFO [10-11|04:23:18.656] IPC endpoint opened                      url=/root/.ethereum/net9901/geth.ipc
INFO [10-11|04:23:18.662] Started P2P networking                   self=enode://2ce903b3c7ee4e1af3536c7ee27618a644d82bf249fbc1cdaa20feac6c678faa38aa1b21e00b194d2ff2476538e68bd05d7c6d6223d082a5f33ad204443c5280@127.0.0.1:30303
WARN [10-11|04:23:18.747] Served eth_coinbase                      reqid=3 t="79.836µs" err="etherbase must be explicitly specified"
Welcome to the Geth JavaScript console!

instance: Geth/v1.10.9-stable-eae3b194/linux-amd64/go1.17
at block: 0 (Thu Jan 01 1970 00:00:00 GMT+0000 (UTC))
 datadir: /root/.ethereum/net9901
 modules: admin:1.0 debug:1.0 eth:1.0 ethash:1.0 miner:1.0 net:1.0 personal:1.0 
rpc:1.0 txpool:1.0 web3:1.0

To exit, press ctrl-d or type exit
> INFO [10-11|04:23:20.316] New local node record                    seq=1,633,926,198,654 id=c10a01978f189332 ip=172.104.100.202 udp=30303 tcp=30303
INFO [10-11|04:23:34.557] Looking for peers                        peercount=0 tried=123 static=0
```

第二次

```
root@localhost:~# geth --datadir ~/.ethereum/net9901 --networkid 9901 console
INFO [10-11|07:53:51.275] Maximum peer count
    ETH=50 LES=0 total=50
INFO [10-11|07:53:51.275] Smartcard socket not found, disabling    err="stat /run/pcscd/pcscd.comm: no such file or directory"WARN [10-11|07:53:51.278] Sanitizing cache to Go's GC limits   
    provided=1024 updated=328
INFO [10-11|07:53:51.279] Set global gas cap
    cap=50,000,000
INFO [10-11|07:53:51.279] Allocated trie memory caches
    clean=49.00MiB dirty=82.00MiB
INFO [10-11|07:53:51.279] Allocated cache and file handles     
    database=/root/.ethereum/net9901/geth/chaindata cache=164.00MiB handles=524,288
INFO [10-11|07:53:51.293] Opened ancient database
    database=/root/.ethereum/net9901/geth/chaindata/ancient readonly=false
INFO [10-11|07:53:51.294] Initialised chain configuration      
    config="{ChainID: 9901 Homestead: 0 DAO: <nil> DAOSupport: 
false EIP150: 0 EIP155: 0 EIP158: 0 Byzantium: 0 Constantinople: 0 Petersburg: <nil> Istanbul: <nil>, Muir Glacier: <nil>, Berlin: <nil>, London: <nil>, Engine: unknown}"
INFO [10-11|07:53:51.295] Disk storage enabled for ethash caches   dir=/root/.ethereum/net9901/geth/ethash count=3
INFO [10-11|07:53:51.296] Disk storage enabled for ethash DAGs 
    dir=/root/.ethash                       count=2
INFO [10-11|07:53:51.296] Initialising Ethereum protocol       
    network=9901 dbversion=8
INFO [10-11|07:53:51.303] Loaded most recent local header      
    number=171 hash=55e8d0..f934fa td=22,849,615 age=1d16h32m  
INFO [10-11|07:53:51.303] Loaded most recent local full block  
    number=171 hash=55e8d0..f934fa td=22,849,615 age=1d16h32m  
INFO [10-11|07:53:51.303] Loaded most recent local fast block  
    number=107 hash=7c4842..ec8aa6 td=14,392,416 age=3d3h9m    
INFO [10-11|07:53:51.303] Loaded last fast-sync pivot marker   
    number=107
INFO [10-11|07:53:51.342] Loaded local transaction journal     
    transactions=0 dropped=0
INFO [10-11|07:53:51.342] Regenerated local transaction journal    transactions=0 accounts=0
WARN [10-11|07:53:51.342] Switch sync mode from fast sync to full sync
INFO [10-11|07:53:51.343] Gasprice oracle is ignoring threshold set threshold=2
INFO [10-11|07:53:51.344] Starting peer-to-peer node
    instance=Geth/v1.10.9-stable-eae3b194/linux-amd64/go1.17   
INFO [10-11|07:53:51.483] New local node record
    seq=1,633,926,198,655 id=c10a01978f189332 ip=127.0.0.1 udp=30303 tcp=30303
INFO [10-11|07:53:51.486] IPC endpoint opened
    url=/root/.ethereum/net9901/geth.ipc
INFO [10-11|07:53:51.503] Started P2P networking
    self=enode://2ce903b3c7ee4e1af3536c7ee27618a644d82bf249fbc1cdaa20feac6c678faa38aa1b21e00b194d2ff2476538e68bd05d7c6d6223d082a5f33ad204443c5280@127.0.0.1:30303
WARN [10-11|07:53:51.598] Served eth_coinbase
    reqid=3 t="69.748µs" err="etherbase must be explicitly specified"
Welcome to the Geth JavaScript console!

instance: Geth/v1.10.9-stable-eae3b194/linux-amd64/go1.17      
at block: 171 (Sat Oct 09 2021 15:21:13 GMT+0000 (UTC))        
 datadir: /root/.ethereum/net9901
 modules: admin:1.0 debug:1.0 eth:1.0 ethash:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0

To exit, press ctrl-d or type exit
> INFO [10-11|07:53:58.614] New local node record
      seq=1,633,926,198,656 id=c10a01978f189332 ip=172.104.100.202 udp=30303 tcp=30303
INFO [10-11|07:54:02.090] Looking for peers
    peercount=0 tried=102 static=0
INFO [10-11|07:54:13.708] Looking for peers
    peercount=0 tried=122 static=0
INFO [10-11|07:54:24.671] Looking for peers
    peercount=0 tried=105 static=0
> eth.accounts
[]
> eth.blockNumber
171
> INFO [10-11|07:54:34.959] Looking for peers
      peercount=0 tried=110 static=0
ERROR[10-11|07:54:35.779] Snapshot extension registration failed   peer=89027a8b err="peer connected on snap without compatible eth support"
INFO [10-11|07:54:44.960] Looking for peers
    peercount=1 tried=113 static=0
> eth.blockNumber
171
> eth.accounts
[]
> INFO [10-11|07:54:57.217] Looking for peers
      peercount=0 tried=135 static=0
INFO [10-11|07:55:07.232] Looking for peers
    peercount=0 tried=101 static=0
INFO [10-11|07:55:17.245] Looking for peers
    peercount=0 tried=127 static=0
INFO [10-11|07:55:27.437] Looking for peers
    peercount=0 tried=93  static=0
ERROR[10-11|07:55:33.491] Snapshot extension registration failed   peer=4fcce07e err="peer connected on snap without compatible eth support"
INFO [10-11|07:55:37.552] Looking for peers
    peercount=0 tried=112 static=0
INFO [10-11|07:55:47.563] Looking for peers
    peercount=0 tried=80  static=0
> admin.nodeInfo.enode
"enode://2ce903b3c7ee4e1af3536c7ee27618a644d82bf249fbc1cdaa20feac6c678faa38aa1b21e00b194d2ff2476538e68bd05d7c6d6223d082a5f33ad204443c5280@172.104.100.202:30303"
> INFO [10-11|07:55:58.254] Looking for peers
      peercount=0 tried=90  static=0
> admin.addPeer("ERROR[10-11|07:56:06.174] Snapshot extension registration failed   peer=a057ed0e err="peer connected on snap 
without compatible eth support"
INFO [10-11|07:56:08.255] Looking for peers
    peercount=0 tried=127 static=0
> admin.addPeer("enode://2ce903b3c7ee4e1af3536c7ee27618a644d82bf249fbc1cdaa20feac6c678faa38aa1b21e00b194d2ff2476538e68bd05d7c6d6223d082a5f33ad204443c5280@172.104.100.202:30303"ERROR[10-11|07:56:09.176] Snapshot extension registration failed   peer=f7ce> admin.addPeer("enode://2ce903b3c7ee4e1af3536c7ee27618a644d82bf249fbc1cdaa20feac6c678faa38aa1b21e00b194d2ff2476538e68bd05d7c6d6223d082a5f33ad204443c5280@172.104.100.202:30303")
true
> INFO [10-11|07:56:18.335] Looking for peers
      peercount=0 tried=60  static=1
> eth.blockNumber
171
> INFO [10-11|07:56:38.486] Looking for peers
      peercount=0 tried=88  static=1
```

