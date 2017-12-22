# 仮想通貨取引帳簿
- 仮想コイン取引の記録を行う
	- 日本円 - 仮想通貨取引
	- 仮想通貨 - 仮想通貨取引
- 取引履歴に応じた損益計算を行う

## 注意、免責事項
本アプリケーションは、日本の税制にのっとった計算を保証するものではありません。本アプリケーションを利用することによって生ずるいかなる損害に対しても、作成者は一切責任を負いません。確定申告は自己責任で行うようにしてください。

## 計算仕様
- 仮想通貨の取得価格は移動平均で求める
- 仮想通貨 - 仮想通貨間取引時には、「売却側コインの売却時の日本円換算価格 - 売却側コインの平均取得価格[日本円] x 数量」を損益として計上する
	- 日本円換算価格は現状、手動入力とする
	- ここ(https://www.coingecko.com/)やここ(https://coinmarketcap.com/)から取得してください。
	- 一貫性を持つことが重要だと思われますので、常に同じソースを使用するようにしてください。

## 操作方法
### 取引の入力 (日本円→ビットコイン(BTC))
1BTC = 2,000,000円のときに、1BTCを購入する場合の例です。日本円を使って購入するときには、「売却」側に日本円の値段を入れてください。「取引の入力」の所に必要情報を入れて、「登録」をクリックしてください。

<img src="01_doc/input_buy_btc.jpg">

### 取引の入力 (日本円←ビットコイン(BTC))
1BTC = 2,100,000円のときに、0.1BTCを売却する場合の例です。日本円に戻すときには、「購入」側に日本円の値段を入れてください。このとき、「購入数量」は総額を入れてください。つまり、1BTC = 2,100,000円でしたが、今回の取引は0.1BTCなので、入力する値は210,000円になります。先ほどの購入と続けて取引を入力した場合、10,000円の利益が出ていることが分かります。なお、この場合に限らず常に、「数量」は単価ではなく、総数量を入力するようにしてください。

<img src="01_doc/input_sell_btc.jpg">

### 取引の入力 (仮想通貨(BTC)→仮想通貨(ZENY))
仮想コイン同士の取引の例です。0.1BTCで、Zenyを7000Zeny購入するとします。また、取引約定時点で1BTC = 2,200,000円とします。「購入」側にZENY、「売却」側にビットコインの数量を入力します。日本の税制では、仮想通貨間の取引においても、取得した時の価格と差がある場合には、損益計算の対象となるようです。そのため、「仮想通貨間取引?」のチェックボックスを有効にしてください。そして、約定時点での、売却側通貨(この場合はBTC)の、売却総額の日本円換算額を記載してください。今回の場合は、1BTC = 2,200,000円のときに、0.1BTC売却したので、220,000円になります。先ほどまでの取引と続けて入力した場合、20,000円の利益が出ていることが分かります(平均取得額が2,000,000円/BTCのため)。

これは、他の仮想通貨でも同じです。例えば、DOGE→XPの場合には約定時点のDOGEの価値(1DOGE当たりの日本円価値 x 売却したDOGE数量)になります。対象コインの日本円価値は上記サイトで確認できます。繰り返しになりますが、値段の参照元に一貫性を持つことが重要だと思われます。また、仮に、参照した値段が実情と離れていても、最終的にはつじつまが合うので問題はないと思われます(個人の感想です)。例えば今回、約定した瞬間の値段は、実は1BTC = 1,500,000円だったとします。しかし、後で確認した時は別の時間の値が記録されていて、1BTC = 2,200,000円になっていたとします。帳簿には1BTC = 2,200,000円として入力します。そのため、実際よりも、取引時の帳簿上の利益が多くなります。その分税金も多く払う必要があります。しかし同時に、Zenyの取得価格も高くなっています。そのため、最終的にZenyを売却するときにこの差は相殺されるはずです。(年をまたぐと有利/不利が出てくるとは思います。)

<img src="01_doc/input_btc_zeny.jpg">

### 通算損益の計算
確定申告などのために、年間の損益を計算する必要があります。計算対象期間を選択後、「損益計算」をクリックしてください。なお、ポートフォリオは何かしらの操作を行うたびに自動的に表示されます。

<img src="01_doc/profit.jpg">

### 取引履歴の保存と読み込み
作成した取引履歴を保存するためには、「履歴の保存」をクリックしてください。JSON形式のテキストファイルで履歴が保存されます。
保存した取引履歴を読み込むには、「履歴の読み込み」をクリックしてください。

