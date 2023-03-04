# READ ME

## 【必読】
### タイマーの背景画像について

* 背景画像は下記リンクの画像（字なし）をお借りしています。
* <https://twitter.com/SASIAI_0807/status/1430895341100879880?s=20&t=Xgl28vaIBw-9Wmt29DuMbg>
* 実際に配信で利用する際は画像作成者に別途確認、もしくは同様の画像の用意をお願い致します。
* 新たに画像を作成する場合、文字レイアウトの関係上、余白やサイズ・縦横比に注意してください。
* 参照はHTMLファイルの*background-image*で行っています。
```html
<style>
*{
    margin: 0;
    padding: 0;
}
.counter{
    /*位置*/
    【中略】
    /*サイズ*/
    【中略】
    /*背景設定*/
    background-image: url("./bg_img/sample.jpg");
    ・
    ・
    ・
}
</style>
```
---

## 【設定】
### 変更箇所
* 利用時は ***timer.html***　＞　１０４行目以降の3か所を適宜変更してください。
```js
/*設定*/
const GAME_START = dayjs('2023-02-12 02:20'); /*ゲーム開始日時を設定->余裕を持った時間設定*/
const GAME_TIME = 120; /*ゲームの時間（分）を指定*/
const YEN_PER_SEC = 14000; /*毎秒上がる金額を設定*/
```
---
## 【YEN_PER_SECの決め方】
### reword_table（YEN_PER_SECの早見表）の各テーブルを参考にして決定します
* 目標賞金総額より
    * 少ない総額の場合
        * ./reword_table/less/1000万-5000万.png
        * ./reword_table/less/6000万-1億.png
    * 多い総額の場合
        * ./reword_table/over/1000万-5000万.png
        * ./reword_table/over/6000万-1億.png
## 【YEN_PER_SECの指定例】
### ２条件の決定
* 金額条件：目標賞金総額1000万円
* 時間条件：ゲーム時間120分（7200s）
### （パターン１）ミッションボーナスを付けて1000万
* reword_table > less > 1000万-5000万.png
* 円毎秒：1300円
* 合計額：936万 + ミッション代（64万）= 1000万
    * カウンターは936万円で停止します 
### （パターン２）ボーナスなしで1000万以上
* reword_table > over > 1000万-5000万.png
* 円毎秒：1400円
* 合計額：1008万
