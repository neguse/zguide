---
weight: 0
---


**By Pieter Hintjens, CEO of iMatix**.

すべてのコメントと正誤表は、[issue tracker](https://github.com/booksbyus/zguide/issues)を使用してください。このバージョンは、ZeroMQの最新の安定版リリース（3.2）をカバーしています。古いバージョンのZeroMQを使用している場合、例や説明の一部が正確ではありません。

このガイドはもともと[C言語](/page:all)ですが、[PHP](/php:all), [Java](/java:all), [Python](/py:all), [Lua](/lua:all) および [Haxe](/hx:all) でも書かれています。また、ほとんどの例をC++、C#、CL、Delphi、Erlang、F#、Felix、Haskell、Julia、Objective-C、Ruby、Ada、Basic、Clojure、Go、Haxe、Node.js、ooc、Perl、Scalaに翻訳しています。

# 序文

## 百語でわかるZeroMQ {#ZeroMQ-in-a-Hundred-Words}

ZeroMQ (ØMQ、0MQ、zmqとしても知られています) は、組み込み可能なネットワークライブラリのように見えますが、並行処理フレームワークのように動作します。プロセス内、プロセス間、TCP、マルチキャストなどの様々なトランスポートでアトミックメッセージを伝送するソケットを提供します。ファンアウト、パブサブ、タスク分配、リクエストリプライなどのパターンで、ソケットをN対Nで接続することができます。クラスタ化された製品のファブリックとして十分な速度があります。非同期I/Oモデルにより、非同期メッセージ処理タスクとして構築されたスケーラブルなマルチコアアプリケーションを提供します。言語APIも充実しており、ほとんどのオペレーティングシステムで動作する。ZeroMQは[iMatix](http://www.imatix.com)のもので、LGPLv3オープンソースです。

## 始まりは？ {#How-It-Began}

普通の TCP ソケットに、ソ連の秘密原子研究プロジェクトから盗んだ放射性同位元素を混ぜたものを注入し、1950 年代の宇宙線を浴びせ、スパンデックスを着た膨れた筋肉をひどく偽装したフェチを持つ麻薬中毒のコミック作家の手に渡りました。そう、ZeroMQソケットは、ネットワーク界の世界を救うスーパーヒーローなのです。

{{< textdiagram name="fig1.png" figno="1" title="A terrible accident..." >}}
.------------.        .------------.
|            |        |            |
| TCP socket +------->|   ZeroMQ   | ZAP!
|            | BOOM!  |            |
'------------'        |   Socket   |  POW!!
  ^    ^    ^         |            |
  |    |    |         '------------'
  |    |    |
  |    |    |
  |    |    '--------- Spandex
  |    |
  |    '-------------- Cosmic rays

 Illegal radioisotopes from
 secret Soviet atomic city
{{< /textdiagram >}}

## ゼロの禅 {#The-Zen-of-Zero}

ZeroMQのØは、トレードオフがすべてです。一方では、この奇妙な名前は、GoogleやTwitterでのZeroMQの知名度を下げます。一方では、「ØMG røtfl」、「Øはおかしな形のゼロじゃない！」、「*Rødgrød med fløde！*」といった書き込みをするデンマーク人を困らせる。これは、「隣人がグレンデルの直系子孫であるように！」という意味の侮辱であるらしい。 フェアなトレードのように思える。

もともとZeroMQのゼロは、「ゼロブローカー」と「（可能な限り近い）ゼロレイテンシー」という意味でした。それ以来、「ゼロ管理」「ゼロコスト」「ゼロ廃棄物」という異なる目標を包含するようになりました。より一般的には、「ゼロ」はプロジェクトに浸透しているミニマリズムの文化を指しています。私たちは、新しい機能を公開するのではなく、複雑さを取り除くことでパワーを付加します。

## 読者層 {#Audience}

本書は、将来のコンピューティングを支配する大規模な分散型ソフトウェアの作り方を学びたいプロのプログラマーを対象として書かれています。ZeroMQは多くの言語で使用されていますが、本書のほとんどの例はC言語で書かれているため、Cコードを読むことができると想定しています。ZeroMQは他の何よりもこの問題を解決しているので、スケールを気にすることを前提としています。可能な限り少ないコストで最高の結果を得る必要があると想定しています。そうでなければ、ZeroMQが行うトレードオフを理解できないからです。この基本的な背景以外には、ZeroMQを使用するために必要なネットワーキングと分散コンピューティングのすべての概念を提示するように努めています。

## 謝辞 {#Acknowledgements}

[オライリー本](http://shop.oreilly.com/product/0636920026136.do)を実現し、この文章を編集してくれたAndy Oramに感謝します。

Bill Desmarais, Brian Dorsey, Daniel Lin, Eric Desgranges, Gonzalo Diethelm, Guido Goldstein, Hunter Ford, Kamil Shakirov, Martin Sustrik, Mike Castleman, Naveen Chawla, Nicola Peduzzi, Oliver Smith, Olivier Chamoux, Peter Alexander, Pierre Rouleau, Randy Dryburgh、 ジョン・アンウィン、アレックス・トーマス、ミハイル・ミンコフ、ジェレミー・アヴネット、マイケル・コンプトン、カミル・キシエル、マーク・ハリトノフ、ギョーム・オベール、イアン・バーバー、マイク・シェリダン、ファルク・アックグル、オレグ・シドロフ、レフ・ギボン、アリスター・マクラウド、アレキサンダー・ダークエンジェル、アンドレアス・ホエルツルウィマー、ハン・ホル、ロバートG．ジャカボスキー、フェリペ・クルス、マーカス・マッカーディ、ミハイル・クレミン、Dr. Gergő Érdi、Pavel Zhukov、Alexander Else、Giovanni Ruggiero、Rick "Technoweenie", Daniel Lundin, Dave Hoover, Simon Jefford, Benjamin Peterson, Justin Case, Devon Weller, Richard Smith, Alexander Morland, Wadim Grasza、 マイケル・ヤクル、ウーヴェ・ダウエルンハイム、セバスチャン・ノヴィッキ、シモーネ・デポンティ、アーロン・ラドン、ダン・コリッシュ、マーカス・シルプ、ブノワ・ラロック、ジョナサン・パラディ、イザヤ・ペン、アルカディウシュ・オルチョフスキ、ウムット・アイディン、マシュー・ホースフォール、ジェレミーW．シャーマン、エリック・ピュー、タイラー・セロン、ジョン・E．Vincent、Pavel Mitin、Min RK、Igor Wiedler、Olof Åkesson、Patrick Lucas、Heow Goodman、Senthil Palanisami、John Gallagher、Tomas Roos、Stephen McQuay、Erik Allik、Arnaud Cogoluègnes、Rob Gagnon、Dan Williams、Edward Smith、James Tucker、 Kristian Kristensen, Vadim Shalts, Martin Trojer, Tom van Leeuwen, Hiten Pandya, Harm Aarts, Marc Harter, Iskren Ivov Chernev, Jay Han, Sonia Hamilton, Nathan Stocks, Naveen Palli, and Zed Shawがこの仕事に貢献した。

