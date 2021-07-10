## tx

### Duplicate transactions

由于 BIP-30

不允许使用相同的 TXID 进行交易，除非较旧的交易完全用完。 2012 年 9 月，该规则已在所有区块中实行，除了 91,842 和 91,880 区块违反了该规则

重复的Coinbase交易

比特币设计者的另一个疏忽是重复交易的处理。虽然乍一看，它们似乎不可能发生（因为它们包含数字签名和对以前交易的引用，这使得它们是唯一的），但仍然有可能创建重复的交易。

最容易复制的交易是coinbase交易，这是每个区块的第一笔交易，允许矿工认领其区块奖励（数字资产交易所 Coinbase就是以此而命名的），因为它们不包含数字签名或对以前交易的引用。如果一名矿工创建了一笔coinbase交易，将相同数量的BTC支付给相同的地址，并使用相同的额外nonce，那么该交易将是相同的。

这在比特币早期历史上发生过两次：

交易d5d2..8599是区块91812和区块91842的coinbase输出；
交易e3bf…b468是区块91722和区块91880的coinbase输出；
在每种情况下，第二次包含交易时，它的输出都会覆盖掉前面的输出。

结果是两个被覆盖的输出没有在UTXO集中。也就是说，这100 BTC并没有在比特币的账本当中。

虽然这看起来是一种无害的疏忽，Russell O’Connor 依旧在2012年时将其视为一种攻击媒介。利用重复的交易，攻击者可从账本中删除其它用户过去的交易。

针对这一点，开发者在2012年引入了BIP-30，以禁止在旧交易的输出全部用完之前包含新的重复交易。

2012年晚些时候，BIP-34的引入还使得复制coinbase变得更加困难，因为它们现在必须包括它们所属的区块高度。

特殊区块缺少 coinbase 交易，且交易费负数

https://btc.com/91880
https://www.oklink.com/btc/block/91880

参考文献：

1.https://zhuanlan.zhihu.com/p/92792990
2.https://blog.bitmex.com/zh_cn-bitcoins-consensus-forks/


## 

include OP_RETURN   ea58eb5b078f4d461e6cebb0db7ee376aed1be62be29e80ecbe8fcaad438e216
政治敏感言论  51c949113bd11e319b100646540e8ed0920e52c6e62878b21b5ac59a5a0e478c
1 output have multi address BIP 11 M-of-N Standard Transactions
09dd94f2c85262173da87a745a459007bb1eed6eeb6bfa238a0cd91a16cf7790
1180df8ad1bfab0ab43f9e57ecf7fd3eb4c5d5e3a96af2ecc51113c3e88fcfe1

BIP 30 Duplicate transactions (Coinbase)
d5d27987d2a3dfc724e359870c6644b40e497bdc0589a033220fe15429d88599

Block 91842 00000000000a4d0a398161ffc163c503763b1f4360639393e0e4c8e300e0caec
Block 91812 00000000000af0aed4792b1acee3d966af36cf5def14935db8de83d6f9306f2f
e3bf3d07d4b0375638d5f1db5255fe07ba2c4cb067cd81b84ee974b6585fb468
Block 91880 00000000000743f190a18c5577a3c2d2a1f610ae9601ac046a38084ccb7cd721
Block 91722 00000000000271a2dc26e7667f8419f2e15416dc6955e5a6c6cdf3f2574dd08e