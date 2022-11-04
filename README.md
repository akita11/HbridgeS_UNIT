# HbridgeS_UNIT

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT.jpg" width="320px">

DCモータなどの負荷の正転・逆転をGrove端子から制御できます。PWM制御を行うこともできます。負荷の電源はオレンジ色のコネクタ、またはGrove端子のVDDから選択できます。

基板形状が「[M5Stack用VH3.96-4ピンユニット](https://www.switch-science.com/products/4055)」と同一のため、そのケースを使うことができます。


Grove端子のVDDへの電源供給能力が不足する場合は[TypeC2Grove UNIT](https://shop.m5stack.com/collections/m5-sensor/products/usb-typec2grove-unit)等を使用してください。


## 使い方

オレンジ色のコネクタ(VH3.96-4p)に、負荷用の電源と負荷を接続します。M5Stackの[BAVGソケット](https://www.switch-science.com/products/7234)を使うと、電源は2.1mmプラグ、負荷はスプリング端子で接続できて便利です。

負荷側の電源は、裏面のJP1で、Grove側の+5Vに切り替えることもできます。（Grove接続先の電源供給能力に注意してください）

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/jumper.jpg" width="320px">

- JP1 : 負荷（ドライバIC）の電源の選択。VDD（VH3.96コネクタ）がデフォルト、Groveの5Vも選択可能

負荷の制御は、Grove端子の2本の信号（MF/MR/VDD/GNDの順）で以下の通り行います。

| MF | MR | 機能 |
|----|----|-----|
| 1  | 0  | 正転 |
| 0  | 1  | 逆転 |
| 0  | 0  | 開放 |
| 1  | 1  | 短絡（ブレーキ） |

## 仕様・制限事項

使用しているモータドライバ（[RZ社RZ7899](http://www.rz-mic.com/uploadfile/fj/201810310633.pdf)）の仕様から、負荷は以下の条件で使用してください。

- 負荷用電源電圧: 3〜25V
- 負荷電流: 5A（負荷電流に応じて放熱が必要となります）


## Author

Junichi Akita (akita@ifdl.jp, @akita11)
