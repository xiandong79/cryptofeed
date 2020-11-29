
Some exchanges support methods for ensuring orderbooks are correct. The two most prevalent methods are sequence numbers and orderbook checksums. With sequence numbers, you can detect a missing message and reset the book/connection. With checksums you must manually calculate a checksum on the orderbook (or some subset of  the book) and compare that to the exchange provided checksum. Sequence number checking takes a negligible amount of time, whereas checksum validation can take a noticeable amount of time (0.4 to 0.8 ms). Sequence number validation is enabled on all supporting exchanges. Checksum validation must be enabled by the end user (set the `checksum_validation` kwarg to `True`). Other exchanges do not supply orderbook deltas (snapshots only), so a missing message will not result in an incorrect orderbook. This list indicates what exchanges support what features. 


| Exchange      | Checksum      | Sequence Numbers | Snapshots only |
| ------------- |:-------------:| :---------------:|:--------------:|
| Bitcoin.com   |               | x                |                |
| Bitfinex      |               | x                |                |
| Bitmax        |               |                  |                |
| Bitstamp      |               |                  |x               |
| Bittrex       |               | x (coming)       |                |
| Blockchain.com|               | x                |                |
| Bybit         |               |                  |   x            |
| Binance       |               |   x              |                |
| BinanceUS     |               | x                |                |
| BitMEX        |               |                  |                |
| Coinbase      |               |  x               |                |
| Deribit       |               |                  |                |
| EXX           |               |                  |                |
| FTX           | x             |                  |                |
| FTX US        | x             |                  |                |
| Gate.io       |               |                  |                |
| Gemini        |               |                  |                |
| HitBTC        |               |  x               |                |
| Huobi         |               |                  | x              |
| Huobi DM      |               |                  |  x             |
| Huobi Swap    |               |                  |  x             |
| Kraken        |    x          |                  |                |
| Kraken Futures|               | x                |                |
| OKCoin        |  x            |                  |                |
| OKEX          |  x            |                  |                |
| Poloniex      |               | x                |                |
| Upbit         |               |                  |     x          |


For even more assurances that books are in the expected state (or for use in debugging), you can enabled a cross check on book updates as well with the `cross_check` kwarg set to `True`.  