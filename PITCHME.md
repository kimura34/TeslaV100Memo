### NVIDIA Tesla V100 を使ったマニング
---
#### 他のGPUとの比較
|     | Tesla V100 | GTX 1080Ti | AMD Radeon Rx580 |
| --- | -----------| ---------- | -------------------|
| Floting Point(GFlops)  | 14029 | 11340 | 6175 |
| GPU Clock | 1370 MHz | 1481 MHz | 1257 MHz (MOD:1130MHz) |
| Memory | 16GByte | 11GByte | 8GByte |
| Memory Bandwidth | 900.1GB/s | 484.4GB/s | 256GB/s |
| 消費電力(定格) | 250W | 250W | 185W |
---
#### Ethereumマイニング
AWSにV100のインスタンスがあったので、Ethereumをマイニングしてみました
##### 使用GPU
- AWS p3.2xlarge(NVIDIA Tesla V100)
- MSI GEFORCE GTX 1080Ti Lighining X
- SAPPHIRE Nitro+ RADEON Rx 580 8G OC
---
##### Hashrate(Ethereumマイニング)
| Tesla V100 | GTX 1080Ti | AMD Radeon Rx580 |
| -- | -- | -- |
| 90Mh/s | 35Mh/s | 26.7Mh/s(MOD:30Mh/s) |
---
#### その他アルゴリズム(参考値)
|     | Tesla V100 | GTX 1080Ti | AMD Radeon Rx580 |
| --- | -----------| ---------- | -------------------|
| CryotoNight(Monero) | 1600h/s | 900h/s | 650h/s |
| Lyra2rev2(MonaCoin) | 130Mh/s | 60Mh/s | 39Mh/s |
---
###### 所感
- Ethereumのようなメモリアクセスが多いアルゴリズムではGPUの計算能力の差はHashrateにはあまり影響を与えない  
- 似たようなアーキテクチャの1080とのHashrateの差は計算能力よりもメモリのアクセススピードの差が影響していると思われます
- 一般的なマイニングソフトはV100向けの最適化はされてないと思われます(動かないソフトもあるようです)、[簡単に入手できるものでもない](http://www.oliospec.com/shopdetail/000000006123/)ので最適化を期待するのは難しいと思われます
---
- 動作クロックや、FPは他と比べて特出しているわけではないので、簡単なアルゴリズムよりはメモリアクセスが多いアルゴリズムのほうが効果が高いと思います
- CryptoNight, Equihash ,Ethereum等のメモリ負荷の高いアルゴリズムが比較的得意と思われます
- Sha256, Scrypt, X11 等のASICが得意とするアルゴリズムは他のGPUに比べて優位とは言えないと思われます
###### Tesla V100でマイニングするにあたって
- GPUの性能を引き出すために、チューニングが必要な可能性がある
- 動作OSによっては、マイニングソフト自体の開発が必要になる
- 消費電力あたりは、優秀だがハードのコストを回収するのが難しい
- 消費電力は30〜50%程度優秀であるが、値段は12倍である
