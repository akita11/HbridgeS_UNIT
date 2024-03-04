# HbridgeS_UNIT

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT.jpg" width="320px">

DCモータなどの負荷の正転・逆転をGrove端子から制御できます。PWM制御を行うこともできます。負荷の電源はオレンジ色のコネクタ、またはGrove端子のVDDから選択できます。

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT_case.jpg" width="160px">

基板形状が「[M5Stack用VH3.96-4ピンユニット](https://www.switch-science.com/products/4055)」と同一のため、そのケースを使うことができます。

Grove端子のVDDへの電源供給能力が不足する場合は[TypeC2Grove UNIT](https://www.switch-science.com/products/8453)等を使用してください。


## 使い方

オレンジ色のコネクタ(VH3.96-4p)に、負荷用の電源と負荷（DCモータ等）を接続します。電源供給の方法によって、主に2通りの接続方法があります。


### 電源供給をACアダプタ等から行う場合

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT_usage1.jpg" width="320px">

オレンジ色のコネクタの電源（VM-G間）に、負荷に応じた電圧をACアダプタ等から供給します。また負荷をA-B間に接続します。（M5Stackの[BAVGソケット](https://www.switch-science.com/products/7234)を使うと、電源は2.1mmプラグ、負荷はスプリング端子で接続できて便利です）


### 電源供給をGrove端子から行う場合

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT_back.jpg" width="160px">

裏面のJP1の、中央-上側の端子がつながっていますので、カッター等でカットし、中央と反対側の"Grove5V"側を、ハンダを盛るなどしてショートします。これによって、負荷への電源がGrove側の+5Vから供給されます。

ただし、一般にDCモータ等の負荷は消費電流が多く、マイコン側の+5V電源の供給能力が不足する場合がほとんどです。そのような場合は、[TypeC2Grove UNIT](https://www.switch-science.com/products/8453)を使用して、負荷側の電源をUSB Type-C端子から供給することができます。別途USB-CコネクタのACアダプタ等を接続してください。

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT_usage2.jpg" width="320px">


### マイコンからの制御方法

マイコン（M5Stack等）からの負荷の制御は、Grove端子の2本の信号線によって行います。

| MF | MR | 機能 |
|----|----|-----|
| 1  | 0  | 正転 |
| 0  | 1  | 逆転 |
| 0  | 0  | 開放 |
| 1  | 1  | 短絡（ブレーキ） |

UIFlowでの[使用例](Hbrige_test.m5f)（以下）を参考にしてください。（Core2のPortAに接続した場合。MF=GPIO32、MR=GPIO33）

<img src="https://github.com/akita11/HbridgeS_UNIT/blob/main/HbridgeS_UNIT_test.png" width="320px">

## 仕様・制限事項

使用しているモータドライバ（[RZ社RZ7899](http://www.rz-mic.com/uploadfile/fj/201810310633.pdf)）の仕様から、負荷は以下の条件で使用してください。

- 負荷用電源電圧: 3〜25V
- 負荷電流: 5A（負荷電流に応じて放熱が必要となります）


## Author

Junichi Akita (akita@ifdl.jp, @akita11)
