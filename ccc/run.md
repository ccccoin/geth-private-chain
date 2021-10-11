# ccc run

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

