# auv
自作用AUVのリポジトリ

## やりたいこと(技術的なこと以外)

水中ロボコンに社会人枠で出る

 →6月大会に向けてスケジュール（10月の可能性あり）

釣りにロボット持っていきたい

## 水中ロボコンってどんな競技？

ゲートパス

ブイドッキング

ランディング

音響ピンガ誘導(音響ピンガの0.5m以内にはいる)

<2018年度の大会>
http://www.oceans18mtsieeekobe.org/wp-content/uploads/2017/12/OTO18AUV20171128J.pdf

## 実装の目玉
ROS2を導入

## 作業方針

### 楽しくやる
当たり前

### 技術的に伸ばしたいことを実装していく

ROS2

ロボットソフトウェアでのTDD

自律移動ロボットアルゴリズム

## 実装

### どんなロボットを作るのか
スラスタ4つに箱型のAUV

上側に回路関係、下側にバッテリー（重たいもの）

### ロボットを作る

#### 電装関係をつくる

arduinoからIMU情報とモータ4つ動作させる。(9月中旬)

RasPiとArduinoを連携させ、Raspi経由でArudinoの情報(姿勢情報、角速度）を取得およびモータ制御(9/E)

#### 機体をつくる

電装関係を作り終えたら実施する。　RaspiとArduinoが入る水圧容器とモータ4つをフレームに取り付ける。

バッテリーはこれから入れるとして、まずは外部給電で実施。

#### ソフトを作る

ArduinoソフトにTDDを組み込み、動作確認させる(9月中旬)

RaspiにSShでログインし、Raspiプログラムを起動させ、Arduinoへモータ回転数の指令を送るとともに、
Arduinoの情報を取得する。

### シミュレータを作る
ROS2対応前提で作る。（Gazibo?)

ロボットは当面長方体のロボットでシミュレーションする。
運動モデルは質点系で0.5 * m * a * t^2 = x でシミュレーションする。

ロボットの挙動やセンサ情報などを可視化したい。

### 音響センサーを作る

パッシブセンサーだったらだけだったら作れると思っている。
アレイを四方に並べて位相差を通ればいいのでは。

### リポジトリ構成

control:AUVに搭載するプログラム

simulator:AUVシミュレータ

tools：ユーティリティツール

