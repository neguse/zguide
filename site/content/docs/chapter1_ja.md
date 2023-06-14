---
ウェイト: 1
title: '1. 基本'
---

# 第1章 基本{#basics}

## 世界を修正する {#Fixing-the-World}

ZeroMQをどう説明するか？私たちの中には、それが行うすべての素晴らしいことを言うことから始める人もいます。*ステロイド上のソケットです。ルーティングのあるメールボックスのようなものです。また、悟りを開いた瞬間、つまり、すべてが明らかになった、ザクザク、パカパカ、サトリのようなパラダイムシフトの瞬間を共有しようとする人もいます。*Things just become simpler. 複雑さがなくなる。また、比較することで説明しようとする人もいます。*個人的には、ZeroMQを作った理由を思い出すのが好きです。

なぜなら、私たちの多くはソフトウェアの物理を理解しておらず、それを教えられることはほとんどないからです。ソフトウェアの物理学とは、アルゴリズムやデータ構造、言語、抽象化などではありません。これらは、私たちが作り、使い、捨てる道具に過ぎないのです。ソフトウェアの真の物理学とは、人間の物理学であり、特に、複雑さに関しては人間の限界であり、大きな問題を断片的に解決するために協力したいという欲求である。これがプログラミングの科学です。人々が理解しやすく、使いやすいビルディングブロックを作れば、人々は協力して非常に大きな問題を解決してくれるでしょう。

私たちはつながった世界に生きており、最新のソフトウェアはこの世界をナビゲートする必要があります。ですから、明日の最大級のソリューションのためのビルディングブロックは、接続され、超並列化されています。コードが「強くて静か」であるだけでは、もはや十分ではありません。コードはコードと会話しなければなりません。コードはおしゃべりであり、社交的であり、うまく接続されていなければなりません。コードは人間の脳のように動かなければなりません。何兆もの個々のニューロンが互いにメッセージを発し、中央制御もなく、単一障害点もない超並列ネットワークでありながら、非常に難しい問題を解決することができるのです。コードの未来が人間の脳に似ているのは偶然ではありません。なぜなら、あらゆるネットワークの終点は、あるレベルでは人間の脳だからです。

スレッドやプロトコル、ネットワークを扱ったことがある人なら、このようなことはほとんど不可能であることに気づくでしょう。夢のような話です。数個のプログラムを数個のソケットで接続するのでさえ、現実の状況を扱い始めると、とても厄介なことなのです。数兆円？そのコストは想像を絶するものでしょう。コンピュータの接続があまりにも難しいので、これを実現するためのソフトウェアやサービスは数十億ドルのビジネスになっている。

つまり、配線がそれを使う能力よりも何年も先を行っている世界に私たちは住んでいるのです。1980年代にはソフトウェアの危機がありました。フレッド・ブルックスのような一流のソフトウェアエンジニアは、「生産性、信頼性、簡便性において1桁の改善も約束する」(http://en.wikipedia.org/wiki/No_Silver_Bullet)シルバーバレットは存在しないと考えていました。

ブルックスは、その危機を解決し、知識を効率的に共有することを可能にしたフリー・オープンソースソフトウェアを見逃した。今日、私たちは別のソフトウェアの危機に直面しているが、それはあまり語られることのない危機である。コネクテッド・アプリケーションを作る余裕があるのは、最も大きく裕福な企業だけです。クラウドはありますが、それは独占的なものです。私たちのデータや知識は、私たちのパソコンから、私たちがアクセスできず、競争もできないクラウドに消えつつあります。私たちのソーシャルネットワークは誰のものなのでしょうか？これは、メインフレームとPCの革命を逆にしたようなものです。

政治的な哲学は[別の本に](http://cultureandempire.com)置いておくとして。つまり、インターネットは大量に接続されたコードの可能性を提供するが、現実にはほとんどの人にとって手が届かない。そのため、（健康、教育、経済、交通などにおける）大きな興味深い問題は、コードを接続する方法がなく、したがって、これらの問題を解決するために協力できる頭脳を接続する方法がないため、未解決のままである。

コードをつなげるという課題を解決するために、これまで多くの試みがなされてきました。何千ものIETF仕様があり、それぞれがパズルの一部を解決しています。アプリケーション開発者にとって、HTTPはおそらく十分にシンプルで機能する唯一の解決策ですが、開発者やアーキテクトに大きなサーバーと薄くて愚かなクライアントという観点から考えるよう促すことで、問題を悪化させることは間違いないでしょう。

そのため、今日でも人々は生のUDPやTCP、独自のプロトコル、HTTP、Websocketを使ってアプリケーションを接続しています。これは、苦痛を伴い、遅く、拡張が困難で、本質的に中央集権的であることに変わりはありません。分散型P2Pアーキテクチャは、ほとんどが遊びのためのもので、仕事のためのものではありません。SkypeやBittorrentを使ってデータをやり取りするアプリケーションがどれだけあるでしょうか？

そこで、私たちはプログラミングの科学に立ち戻ることになります。世界を修復するために、私たちは2つのことをする必要がありました。1つは、「どんなコードでも、どんな場所でも、どんなコードにもつなげられる方法」という一般的な問題を解決することです。2つ目は、それを人々が理解し、*簡単に*使うことができる、可能な限りシンプルな構成要素で包むことです。

バカバカしいほどシンプルに聞こえます。そして、たぶんそうなのでしょう。それがポイントなのです。

## スタート時の前提条件 {#Starting-Assumptions}

ZeroMQの少なくともバージョン3.2を使用していることを前提にしています。Linuxボックスかそれに類するものを使用しているものとします。サンプルのデフォルト言語であるCコードを多少なりとも読むことができるものとします。PUSHやSUBSCRIBEのような定数を書くとき、プログラミング言語がそれを必要とする場合、それらが本当は<tt>ZMQ_PUSH</tt>や<tt>ZMQ_SUBSCRIBE</tt>と呼ばれていると想像できることを想定しているのですが。

## 例題の入手 {#Getting-the-Examples}

サンプルは公開されている [GitHub リポジトリ](https://github.com/imatix/zguide) に置かれています。すべてのサンプルを入手する最も簡単な方法は、このリポジトリをクローンすることです：

```
git clone --depth=1 https://github.com/imatix/zguide.git
```

次に、examples サブディレクトリをブラウズしてください。言語別のサンプルを見つけることができます。もし、あなたが使っている言語で足りない例があれば、[翻訳を提出する](http://zguide.zeromq.org/main:translate)ことが推奨されます。こうして、このテキストは多くの人の仕事のおかげで、とても便利になったのです。すべての用例はMIT/X11のライセンスで提供されています。

## 求めよさらば与えられん {#Ask-and-Ye-Shall-Receive}

それでは、いくつかのコードから始めましょう。もちろん、Hello Worldの例から始めます。クライアントとサーバーを作ります。クライアントはサーバに「Hello」と送信し、サーバは「World」と返信します。ZeroMQのソケットをポート5555で開き、リクエストを読み、それぞれのリクエストに対して "World "と返信します：

{{< examples name="hwserver" title="Hello World server" >}}

{{< textdiagram name="fig2.png" figno="2" title="Request-Reply" >}}
  #------------#
  |   Client   |
  +------------+
  |    REQ     |
  '---+--------'
      |    ^
      |    |
Hello |    | World
      |    |
      v    |
  .--------+---.
  |    REP     |
  +------------+
  |   Server   |
  #------------#
{{< /textdiagram >}}

REQとREPのソケットペアは、ロックステップになっています。クライアントは <tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt> を発行し、次に <tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt> をループさせます(それしか必要ない場合は一回だけ)。それ以外の順序(例えば、2つのメッセージを連続して送信する)を行うと、<tt>send</tt>または<tt>recv</tt>呼び出しから-1というリターンコードが返されます。同様に、サービスは<tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt>、次に<tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt>をこの順番で必要なだけ発行します。

ZeroMQは参照言語としてCを使用しており、この言語が例として使用する主な言語です。オンラインでこれを読んでいる場合は、例の下にあるリンクから他のプログラミング言語への翻訳を見ることができます。同じサーバーをC++で比較してみましょう：

{{< example name="hwserver" title="Hello World server" language="C++" >}}

ZeroMQ APIがCとC++で似ていることがわかります。PHPやJavaのような言語では、さらに隠すことができ、コードもさらに読みやすくなります：

{{< example name="hwserver" title="Hello World server" language="PHP" >}}。

{{< example name="hwserver" title="Hello World server" language="Java" >}}。


他の言語でのサーバーです：

{{< examples name="hwserver" title="Hello World server" >}}

これがクライアントコードです：

{{< examples name="hwclient" title="Hello World client" >}}

さて、これは現実的でないほどシンプルに見えますが、ZeroMQソケットには、すでに学んだように、スーパーパワーがあります。このサーバーに何千ものクライアントを一度に投入しても、楽しく素早く動作し続けることができます。試しに、クライアントを起動し、次にサーバを起動してみて、どのように動作するかを確認してみてください。

この2つのプログラムが実際に行っていることを簡単に説明しましょう。この2つのプログラムは、ZeroMQのコンテキストを作成し、ソケットを作成しています。言葉の意味は気にしないでください。そのうちわかるようになります。サーバーは、REP（返信）ソケットをポート5555にバインドします。サーバーはループでリクエストを待ち、その都度リプライで応答する。クライアントはリクエストを送り、サーバから返ってくるリプライを読みます。

サーバーを終了（Ctrl-C）して再起動すると、クライアントは正しく回復しません。プロセスのクラッシュから回復するのは、それほど簡単ではありません。信頼性の高いリクエスト・リプライの流れを作るのは複雑なので、 [第4章 信頼性の高いリクエスト・リプライのパターン](chapter4#reliable-request-reply) まで取り上げないことにします。

舞台裏ではいろいろなことが起きていますが、私たちプログラマーにとって重要なのは、コードがいかに短く甘いか、そして高負荷の下でもクラッシュしないかです。これがリクエスト・リプライ・パターンで、ZeroMQを使う最もシンプルな方法です。RPCや古典的なクライアント/サーバーモデルに対応するものです。

## 文字列に関する小ネタ {#A-Minor-Note-on-Strings}

ZeroMQは、送信されたデータについて、バイト単位のサイズ以外、何も知りません。つまり、アプリケーションがデータを読み返せるように、安全にフォーマットする責任があるのです。オブジェクトや複雑なデータ型に対してこれを行うのは、Protocol Buffersのような特殊なライブラリの仕事です。しかし、文字列の場合にも注意が必要です。

C言語や他のいくつかの言語では、文字列はヌルバイトで終端されます。HELLO "のような文字列を送信する場合、このヌルバイトを追加して送信することができます：

```C
zmq_send (requester, "Hello", 6, 0)；
```

しかし、他の言語から文字列を送信する場合、おそらくそのヌルバイトは含まれないでしょう。例えば、同じ文字列をPythonで送信する場合、次のようになります：

例えば、同じ文字列をPythonで送信する場合、次のようになります： 

```Python
socket.send ("Hello")
```

Pythonのsocket.send ("Hello") ```とします。すると、電線に乗るのは長さ（短い文字列は1バイト）と個々の文字としての文字列の中身になります。

{{< textdiagram name="fig3.png" figno="3" title="A ZeroMQ string" >}}
#-----#  #-----+-----+-----+-----+-----#
|  5  |  |  H  |  e  |  l  |  l  |  o  |
#-----#  #-----+-----+-----+-----+-----#
{{< /textdiagram >}}

そして、これをC言語プログラムから読むと、文字列のように見え、偶然にも文字列のように振る舞うかもしれませんが（運良く5バイトの後に無邪気に潜んでいるNULLが見つかった場合）、適切な文字列ではないものが得られます。クライアントとサーバーが文字列の形式について合意していない場合、奇妙な結果が得られます。

C言語でZeroMQから文字列データを受信する場合、安全に終了しているかどうかを単純に信頼することはできません。文字列を読むたびに、余分なバイトのためのスペースを持つ新しいバッファを割り当て、文字列をコピーし、NULLで適切に終了させる必要があります。

そこで、**ZeroMQの文字列は長さが指定されており、末尾にNULLを付けずに**ワイヤ上で送信される**というルールを確立しましょう。最も単純な場合（例ではこうします）、ZeroMQ文字列はZeroMQメッセージフレームにきちんと対応し、上図のようになります（長さといくつかのバイトがあります）。

ZeroMQの文字列を受け取り、それを有効なC言語の文字列としてアプリケーションに提供するために、C言語で行う必要があることは次のとおりです：

```C
//  Receive ZeroMQ string from socket and convert into C string
//  Chops string at 255 chars, if it's longer
static char *
s_recv (void *socket) {
    char buffer [256];
    int size = zmq_recv (socket, buffer, 255, 0);
    if (size == -1)
        return NULL;
    if (size > 255)
        size = 255;
    buffer [size] = \0;
    /* use strndup(buffer, sizeof(buffer)-1) in *nix */
    return strdup (buffer);
}
```

これは便利なヘルパー関数で、有益に再利用できるものを作るという精神から、正しい ZeroMQ 形式で文字列を送信する同様の <tt>s_send</tt> 関数を書き、これを再利用できるヘッダーファイルにパッケージしてみましょう。

その結果、<tt>zhelpers.h</tt>ができ、Cでより甘く短いZeroMQアプリケーションを書くことができます。かなり長いソースで、C開発者にとっては楽しいだけなので、[ゆっくり読んでください](https://github.com/imatix/zguide/blob/master/examples/C/zhelpers.h).

## 命名規則に関する注意点 {#A-Note-on-the-Naming-Convention}

<tt>zhelpers.h</tt>や本ガイドに続く例で使われている接頭辞<tt>s_</tt>は、静的メソッドや変数を示すものです。

## バージョン報告 {#Version-Reporting}

ZeroMQにはいくつかのバージョンがあり、問題にぶつかった場合、それが後のバージョンで修正されたものであることが非常によくあります。そのため、実際にリンクしているZeroMQのバージョンを正確に把握することは、便利なトリックです。

これを実行する小さなプログラムを以下に示します：

{{< examples name="version" title="ZeroMQ version reporting" >}}。

## メッセージの取得 {#Getting-the-Message-Out}

2つ目の古典的なパターンは、一方通行のデータ配信で、サーバーがクライアントの集合に更新をプッシュするものです。郵便番号、気温、相対湿度からなる天気の更新をプッシュする例を見てみましょう。実際の気象観測所と同じように、ランダムな値を生成することにします。

これがサーバーです。このアプリケーションでは、ポート5556を使用します：

{{< examples name="wuserver" title="気象更新サーバー" >}}。

この更新の流れには始まりも終わりもなく、終わりのない放送のようなものです。

これはクライアントアプリケーションで、更新のストリームに耳を傾け、指定された郵便番号に関係するものを取得するものです：

{{< examples name="wuclient" title="Weather update client" >}}

{{< textdiagram name="fig4.png" figno="4" title="Publish-Subscribe" >}}
               #-------------#
               |  Publisher  |
               +-------------+
               |     PUB     |
               '-------------'
                    bind
                      |
                      |
                   updates
                      |
      .---------------+---------------.
      |               |               |
   updates         updates         updates
      |               |               |
      |               |               |
      v               v               v
   connect         connect         connect
.------------.  .------------.  .------------.
|    SUB     |  |    SUB     |  |    SUB     |
+------------+  +------------+  +------------+
| Subscriber |  | Subscriber |  | Subscriber |
#------------#  #------------#  #------------#
{{< /textdiagram >}}

SUBソケットを使用する場合、このコードのように <tt>[zmq_setsockopt()](http://api.zeromq.org/master:zmq_setsockopt)</tt> と SUBSCRIBE を使用して、**必ず**購読を設定することに注意してください。もし、サブスクリプションを設定しなければ、メッセージを受け取ることはできません。初心者にありがちなミスですね。サブスクライバーは多くのサブスクリプションを設定することができ、それらは足し算されます。つまり、更新がANYサブスクリプションにマッチすれば、サブスクライバーはそれを受信します。サブスクライバーは、特定のサブスクリプションをキャンセルすることもできます。サブスクリプションは多くの場合、印刷可能な文字列ですが、常にそうとは限りません。この仕組みについては <tt>[zmq_setsockopt()](http://api.zeromq.org/master:zmq_setsockopt)</tt> を参照してください。

PUB-SUB ソケットのペアは非同期です。クライアントは<tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt>をループして行います(それだけで済む場合は1回だけ)。SUBソケットにメッセージを送ろうとすると、エラーになります。同様に、サービスは<tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt>を必要なだけ行いますが、PUBソケットでは<tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt>を行ってはいけません。

ZeroMQソケットでは、理論的には、どちらの端が接続し、どちらの端がバインドするかは重要ではありません。しかし、実際には文書化されていない違いがあり、それについては後で説明することにします。今のところ、ネットワーク設計でそれが不可能な場合を除き、PUBをバインドし、SUBを接続します。

PUB-SUBソケットについて知っておくべき重要なことがもう1つある：サブスクライバーがメッセージを受け取り始めるタイミングを正確に知ることはできないのだ。サブスクライバーを起動し、しばらく待ってからパブリッシャーを起動しても、 **サブスクライバーはパブリッシャーが送信する最初のメッセージを必ず見逃す**ことになる。これは、サブスクライバーがパブリッシャーに接続するとき(わずかな時間ですが、ゼロではありません)、パブリッシャーがすでにメッセージを送信している可能性があるからです。

この "slow joiner "の症状は、十分な数の人によく見られるので、詳しく説明することにします。ZeroMQは非同期I/Oを行う、つまりバックグラウンドで行うことを思い出してください。2つのノードが次のような順序でこれを実行しているとします：

* Subscriberはエンドポイントに接続し、メッセージを受信してカウントします。
Subscriberがエンドポイントに接続し、メッセージを受信してカウントします。 * Publisherがエンドポイントにバインドし、すぐに1,000メッセージを送信します。

サブスクライバーは何も受信しない可能性が高いです。あなたは瞬きし、正しいフィルタを設定したことを確認し、再度試みますが、サブスクライバーはまだ何も受信しません。

TCP接続を行うには、ネットワークとピア間のホップ数に応じて、数ミリ秒かかるハンドシェイクを行ったり来たりする必要があります。その間に、ZeroMQは多くのメッセージを送信することができます。議論のために、接続の確立に5ミリ秒かかり、同じリンクで1秒間に1Mのメッセージを処理できると仮定します。サブスクライバーがパブリッシャーに接続している5ミリ秒の間に、パブリッシャーが1Kメッセージを送信するのにかかる時間はたったの1ミリ秒です。

[Chapter 2 - Sockets and Patterns](chapter2#sockets-and-patterns) では、パブリッシャーとサブスクライバーを同期させ、サブスクライバーが本当に接続されて準備ができるまでデータの公開を開始しない方法を説明します。パブリッシャーを遅らせる簡単で愚かな方法は、スリープすることです。しかし、実際のアプリケーションでこれをやってはいけません。なぜなら、これは非常に壊れやすく、無骨で遅いからです。スリープは何が起こっているのかを自分で証明するために使い、正しい方法を知るために [Chapter 2 - Sockets and Patterns](chapter2#sockets-and-patterns) を待つことです。

同期の代替案は、公開されたデータストリームが無限であり、開始も終了もないと単純に仮定することです。また、サブスクライバーは起動前に何が起こったかを気にしないと仮定することもできます。これが、今回の天気予報クライアントの例です。

このクライアントは、選択した郵便番号を購読し、その郵便番号の更新情報を100件収集します。つまり、郵便番号がランダムに分布している場合、サーバーからの更新は約1000万件になります。クライアントを起動し、次にサーバーを起動すれば、クライアントは動き続ける。サーバーは何度でも停止、再起動が可能で、クライアントも動き続けます。クライアントは、100回分の更新を収集したら、平均値を計算し、それを表示して終了する。

パブリッシュ・サブスクライブ（pub-sub）パターンに関するいくつかのポイント：

* サブスクライバーは複数のパブリッシャーに接続することができ、その都度1つのコネクトコールを使用します。サブスクライバーは複数のパブリッシャーに接続することができ、毎回1回のコネクトコールを使用します。その後、データが到着し、インターリーブ(「フェアキュー」)され、一つのパブリッシャーが他をかき消すことがないようにします。

* もしパブリッシャーに接続された購読者がいない場合、それは単にすべてのメッセー ジをドロップします。

* もし TCP を使っていて、サブスクライバーが遅い場合、メッセージはパブリッシャー の上でキューイングされます。ハイウォーターマーク "を使ってパブリッシャーを保護する方法については後ほど説明します。

* ZeroMQ v3.xから、接続されたプロトコル(<tt>tcp:@<*>@</tt>または<tt>ipc:@<*>@</tt>)を使用する場合、フィルタリングはパブリッシャー側で行われます。<tt>epgm:@<//>@</tt>プロトコルを使用する場合、フィルタリングはサブスクライバー側で行われます。ZeroMQ v2.xでは、すべてのフィルタリングはサブスクライバー側で行われました。

これは、私のラップトップ（2011年製のIntel i5）で10Mのメッセージを受信してフィルタリングするのにかかる時間ですが、まともですが特別なものではありません：

```
$ time wuclient
Collecting updates from weather server...
Average temperature for zipcode '10001 ' was 28F

real    0m4.470s
user    0m0.000s
sys     0m0.008s
```

## 分割統治 {#Divide-and-Conquer}

{{< textdiagram name="fig5.png" figno="5" title="Parallel Pipeline" >}}
            #-------------#
            |  Ventilator |
            +-------------+
            |    PUSH     |
            '------+------'
                   |
                   | tasks
                   |
      .------------+-------------.
      |            |             |
      v            v             v
.----------.  .----------.  .----------.
|   PULL   |  |   PULL   |  |   PULL   |
+----------+  +----------+  +----------+
|  Worker  |  |  Worker  |  |  Worker  |
+----------+  +----------+  +----------+
|   PUSH   |  |   PUSH   |  |   PUSH   |
'----+-----'  '----+-----'  '----+-----'
      |            |             |
      '------------+-------------'
                   |
                   | results
                   |
                   v
            .-------------.
            |    PULL     |
            +-------------+
            |    Sink     |
            #-------------#
{{< /textdiagram >}}

最後の例として（あなたはきっと、ジューシーなコードに飽きて、比較抽象的規範に関する哲学的議論に戻りたいのでしょう）、少しスーパーコンピューティングをやってみましょうか。そしてコーヒーを飲む。このスーパーコンピューティングのアプリケーションは、かなり典型的な並列処理モデルである。次のようなものがある：

* 並列処理可能なタスクを生成する人工呼吸器。
* タスクを処理するワーカーのセット
* ワーカープロセスから戻ってくる結果を収集するシンク

現実には、ワーカーは超高速ボックス上で動作し、おそらくGPU（グラフィック・プロセッシング・ユニット）を使って難しい計算を行う。ここにベンチレーターがあります。100個のタスクが生成され、それぞれワーカーに何ミリ秒かスリープするように指示するメッセージです：

{{< examples name="taskvent" title="Parallel task ventilator" >}}。

これがワーカーアプリケーションです。メッセージを受け取り、その秒数だけスリープして、終了の合図を送ります：

{{< examples name="taskwork" title="Parallel task worker" >}}。

こちらはシンクアプリケーションです。100個のタスクを収集し、全体の処理にかかった時間を計算することで、ワーカーが複数いる場合、本当に並列に動作していたかを確認することができます：

{{< examples name="tasksink" title="Parallel task sink" >}}。

バッチの平均コストは5秒です。1人、2人、4人のワーカーを起動すると、シンクから次のような結果が得られます：

* 1ワーカー：総経過時間：5034ミリ秒。
* 2ワーカー：総経過時間：2421ミリ秒。
* 4人のワーカー：総走行時間：1018ミリ秒。

このコードのいくつかの側面について、より詳細に見てみましょう：

* ワーカーは上流でベンチレーターに、下流でシンクに接続されています。つまり、ワーカーを任意に追加することができる。もしワーカーがエンドポイントにバインドしていたら、ワーカーを追加するたびに、（a）エンドポイントを増やし、（b）ベンチレーターやシンクを変更する必要があります。ベンチレーターとシンクはアーキテクチャの*安定的な*部分であり、ワーカーはその*動的な*部分であると私たちは言っています。

* バッチの開始とワーカーの稼働を同期させなければならない。これはZeroMQではかなり一般的な問題で、簡単な解決策はありません。<tt>zmq_connect</tt>メソッドは一定の時間を要します。そのため、一連のワーカーが人工呼吸器に接続すると、最初に接続に成功したワーカーは、他のワーカーも接続している間に、その短時間でメッセージを一杯受け取ることになります。バッチの開始を何らかの方法で同期させないと、システムはまったく並列に動作しません。ベンチレーターのwaitを削除してみて、どうなるか試してみてください。

* ベンチレーターのPUSHソケットは、ワーカーにタスクを均等に分配します（バッチが出始める前に、ワーカーがすべて接続されていると仮定して）。これは *ロードバランシング* と呼ばれるもので、また詳しく見ていきます。

* シンクのPULLソケットは、ワーカーから均等に結果を収集する。これは *フェアキューイング* と呼ばれています。

{{< textdiagram name="fig6.png" figno="6" title="Fair Queuing" >}}
#---------#   #---------#   #---------#
|  PUSH   |   |  PUSH   |   |  PUSH   |
'----+----'   '----+----'   '----+----'
     |             |             |
  R1,| R2, R3      | R4       R5,| R6
     |             |             |
     '-------------+-------------'
                   |
               fair| queuing
        R1, R4, R5,| R2, R6, R3
                   |
                   v
            .-------------.
            |     PULL    |
            #-------------#
{{< /textdiagram >}}

パイプラインパターンは「スロージョイナー」症候群を示し、PUSHソケットが適切にロードバランスされないという非難を招きます。PUSHとPULLを使っていて、あるワーカーが他のワーカーよりずっと多くのメッセージを受け取った場合、そのPULLソケットが他のソケットより速く参加し、他のソケットが接続する前に多くのメッセージを取得したためです。適切なロードバランシングを行いたい場合は、[3章 - 高度なリクエストリプライパターン](chapter3#advanced-request-reply)のロードバランシングパターンを参照するとよいかもしれませんね。

## ZeroMQを使ったプログラミング {#Programming-with-ZeroMQ}

いくつかの例を見て、ZeroMQをいくつかのアプリで使い始めたくなったことでしょう。その前に、深呼吸して落ち着き、ストレスや混乱を避けるための基本的なアドバイスについて考えてみてください。

* ZeroMQをステップ・バイ・ステップで学びましょう。これはたった1つのシンプルなAPIですが、その中に可能性の世界が隠されています。可能性をゆっくりと受け止め、一つ一つをマスターしてください。

* 素敵なコードを書きましょう。醜いコードは問題を隠し、他の人があなたを助けるのを難しくします。あなたは無意味な変数名に慣れるかもしれませんが、あなたのコードを読む人はそうではありません。本当の言葉で、「この変数が何のためにあるのか、あなたに伝えるには不注意すぎる」以外のことを示す名前を使いましょう。一貫したインデントときれいなレイアウトを使用します。素敵なコードを書けば、あなたの世界はもっと快適になります。

* あなたがそれを作るようにあなたが作るものをテストします。プログラムがうまくいかないとき、どの5行が原因なのかを知っておく必要があります。これは、ZeroMQマジックをするときに特に言えることで、最初の数回試すだけではうまくいきません。

* 期待通りに動かないことがわかったら、コードを分割して、それぞれをテストし、どれが機能していないか確認します。ZeroMQでは、基本的にモジュール化されたコードを作ることができますので、それを活用してください。

* 抽象化（クラス、メソッド、何でも）を必要なときに作る。多くのコードをコピー＆ペーストすると、コピー＆ペーストのエラーも発生します。

### コンテキストを正しくする {#Getting-the-Context-Right}

ZeroMQアプリケーションは常に*コンテキスト*を作成することから始まり、それを使ってソケットを作成します。C言語では、<tt>[zmq_ctx_new()](http://api.zeromq.org/master:zmq_ctx_new)</tt>の呼び出しがこれにあたります。プロセスでは、正確に1つのコンテキストを作成し、使用する必要があります。技術的には、コンテキストは 1 つのプロセス内のすべてのソケットのコンテナであり、1 つのプロセス内のスレッドを接続する最速の方法である <tt>inproc</tt> ソケットの転送として動作します。実行時にプロセスが2つのコンテキストを持つ場合、これらは別々のZeroMQインスタンスのようになります。もしそれが明確に欲しいものであれば、OKですが、そうでない場合は覚えておいてください：

**プロセスの開始時に <tt>[zmq_ctx_new()](http://api.zeromq.org/master:zmq_ctx_new)</tt> を、終了時に <tt>[zmq_ctx_destroy()](http://api.zeromq.org/master:zmq_ctx_destroy)</tt> を1回呼びます。

<tt>fork()</tt> システムコールを使っている場合は、<tt>[zmq_ctx_new()](http://api.zeromq.org/master:zmq_ctx_new)</tt> *フォークの後*と子プロセスのコードの最初に実行します。一般的に、子プロセスでは興味深い（ZeroMQ）ことを行い、親プロセスでは退屈なプロセス管理を行いたいと考えています。

### きれいな終了をする {#Making-a-Clean-Exit}

上品なプログラマーは、上品な殺し屋と同じモットーを共有しています：仕事を終えたら必ず後始末をすることです。Pythonのような言語でZeroMQを使用すると、自動的に解放されます。しかし、C言語を使う場合は、使い終わったら注意深くオブジェクトを解放しなければなりません。

メモリリークもそうですが、ZeroMQはアプリケーションを終了する方法についてかなり細かいです。理由は技術的で難しいのですが、要するに、ソケットを開いたままにしておくと、<tt>[zmq_ctx_destroy()](http://api.zeromq.org/master:zmq_ctx_destroy)</tt>関数が永遠にハングアップしてしまうということです。また、すべてのソケットを閉じたとしても、<tt>[zmq_ctx_destroy()](http://api.zeromq.org/master:zmq_ctx_destroy)</tt>はデフォルトで、接続や送信の保留があると、閉じる前にソケットのLINGERをゼロに設定しない限り永遠に待ち続けます。

私たちが気にする必要があるZeroMQオブジェクトは、メッセージ、ソケット、およびコンテキストです。幸運なことに、少なくとも簡単なプログラムでは、これは非常にシンプルです：

<tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt> と <tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt> は、zmq_msg_t オブジェクトを扱う必要がないため、できる限り使用しましょう。

<tt>[zmq_msg_recv()](http://api.zeromq.org/master:zmq_msg_recv)</tt> を使う場合は、受信したメッセージを使い終わったら、必ず <tt>[zmq_msg_close()](http://api.zeromq.org/master:zmq_msg_close)</tt> を呼んで解放してください。

* もし、たくさんのソケットを開いたり閉じたりしているのであれば、それはアプリケーショ ンを再設計する必要があるサインかもしれません。場合によっては、コンテキストを破棄するまでソケットハンドルが解放されないこともあり ます。

* プログラムを終了するときは、ソケットを閉じてから <tt>[zmq_ctx_destroy()](http://api.zeromq.org/master:zmq_ctx_destroy)</tt> を呼んでください。これでコンテキストは破棄されます。

これは、少なくともC言語の開発ではそうです。オブジェクトが自動的に破壊される言語では、スコープから離れるとソケットやコンテキストが破壊されます。例外を使う場合は、「final」ブロックのようなもので後始末をする必要がありますし、リソースの場合と同じです。

マルチスレッドで作業する場合は、これよりもっと複雑なことになります。マルチスレッドについては次の章で説明しますが、警告にもかかわらず、安全に歩けるようになる前に実行しようとする人がいるので、以下に*マルチスレッド*のZeroMQアプリケーションをきれいに終了させるための簡単で汚いガイドを示します。

まず、複数のスレッドから同じソケットを使用しようとしないでください。なぜこれが非常に楽しいと思うのか、その理由は説明しないでください。次に、リクエストが続いている各ソケットをシャットダウンする必要があります。正しい方法は、低いLINGER値（1秒）を設定し、ソケットをクローズすることです。もし、あなたの言語バインディングが、コンテキストを破棄するときに、この処理を自動的に行わないのであれば、パッチを送ることをお勧めします。

最後に、コンテキストを破棄します。これにより、アタッチされたスレッド（つまり、同じコンテキストを共有しているスレッド）でブロックしている受信やポーリング、送信はすべてエラーで返されることになる。そのエラーをキャッチして、そのスレッドでlinger onを設定し、ソケットを閉じて、終了してください。同じコンテキストを2回破壊してはいけません。メインスレッドの <tt>zmq_ctx_destroy</tt> は、それが知っているすべてのソケットが安全に閉じられるまで、ブロックします。

これで完了です！言語バインディングの作者であれば、この処理を自動的に行い、ソケットクローズのダンスを不要にすることができます。

##Why We Needed ZeroMQ {#Why-We-Needed-ZeroMQ} なぜZeroMQが必要なのか？

ZeroMQの動作を見たところで、「なぜ」に戻りましょう。

最近の多くのアプリケーションは、LANやインターネットなど、何らかのネットワークにまたがるコンポーネントで構成されています。そのため、多くのアプリケーション開発者は、何らかのメッセージングを行うことになります。メッセージキューイング製品を使う開発者もいますが、ほとんどの場合、TCPやUDPを使って自分でやっています。これらのプロトコルを使うのは難しくありませんが、AからBへ数バイトを送るのと、信頼できる方法でメッセージを送るのとでは、大きな違いがあります。

生のTCPを使用してピースを接続し始めたときに直面する典型的な問題を見てみましょう。再利用可能なメッセージングレイヤーは、これらのすべて、またはほとんどを解決する必要があります：

* どのようにI/Oを処理するのか？アプリケーションはブロックするのか、それともバックグラウンドでI/Oを処理するのか。これは重要な設計上の決定です。I/Oをブロックすることは、うまくスケールしないアーキテクチャを作成します。しかし、バックグラウンドでのI/Oは、正しく行うのが非常に難しい場合があります。

* 動的なコンポーネント、つまり、一時的に消えてしまう部品をどのように扱うか？コンポーネントを正式に「クライアント」と「サーバー」に分け、サーバーは消えてはいけないと義務づけるか？サーバとサーバを接続したい場合はどうするか？数秒おきに再接続を試みるか？

* 電線上のメッセージはどのように表現するのか？書きやすく、読みやすく、バッファオーバーフローの心配がなく、小さなメッセージには効率的で、パーティハットをかぶった猫が踊る超大型ビデオには適切な、データの枠組みはどうすればいいのか？

* すぐに配信できないメッセージはどう扱うか？特に、あるコンポーネントがオンラインに戻るのを待つ場合、どのように対処すればよいのでしょうか？メッセージを破棄するのか、データベースに入れるのか、メモリーキューに入れるのか？

* メッセージキューはどこに保存するのか？キューから読み出すコンポーネントが非常に遅く、キューが溜まってしまう場合はどうするのか？その時はどうするのか？

* 失われたメッセージはどのように扱うのか？新しいデータを待つのか、再送を要求するのか、それともメッセージが失われないようにする信頼性レイヤーを構築するのか？その層自体がクラッシュしたらどうするんだ？

* 別のネットワークトランスポートを使用する必要がある場合はどうでしょう。例えば、TCPユニキャストの代わりにマルチキャストを使うとか？あるいはIPv6？アプリケーションを書き直す必要があるのか、それともトランスポートはある層で抽象化されているのか？

* メッセージのルーティングはどうするのか？同じメッセージを複数のピアに送ることができるのか？同じメッセージを複数のピアに送ることができるのか？ オリジナルの要求者に返信を送り返すことができるのか？

* 他の言語用のAPIをどのように書くか？ワイヤレベルのプロトコルを再実装するのか、それともライブラリを再パッケージ化するのか？前者の場合、効率的で安定したスタックをどのように保証するのでしょうか？後者の場合、どのようにして相互運用性を保証するのだろうか？

* 異なるアーキテクチャ間でも読み取れるようにするには、どのようにデータを表現すればよいのでしょうか？データ型に特定のエンコーディングを強制するのか？これはどこまでが上位レイヤではなくメッセージングシステムの仕事なのか？

* ネットワークエラーをどう扱うか？ネットワークエラーをどのように扱うか?

Hadoop Zookeeper](https://zookeeper.apache.org/)のような典型的なオープンソースプロジェクトを例に、<tt>[src/c/src/zookeeper.c](http://github.com/apache/zookeeper/blob/trunk/src/c/src/zookeeper.c)</tt>のC APIコードを読んでみます。このコードを読んだのは2013年1月で、4,200行の謎のコードで、その中にドキュメント化されていない、クライアント/サーバー型のネットワーク通信プロトコルが入っています。なるほど、<tt>select</tt>の代わりに<tt>poll</tt>を使っているので効率的なんですね。しかし、本当はZookeeperは汎用的なメッセージングレイヤーと、明確に文書化されたワイヤレベルプロトコルを使用すべきなのです。このような車輪を何度も作るのは、チームにとって非常に無駄なことです。

しかし、再利用可能なメッセージングレイヤーを作るにはどうしたらいいのでしょうか？多くのプロジェクトがこの技術を必要としているのに、なぜ人々はまだTCPソケットをコードで駆動させ、長いリストにある問題を何度も解決するという難しい方法をとっているのでしょうか？

再利用可能なメッセージングシステムを構築するのは本当に難しいことで、だからこそFOSSプロジェクトはほとんど挑戦せず、商用メッセージング製品は複雑で高価、柔軟性がなく、もろいのです。2006年、iMatixは[AMQP](http://www.amqp.org)を設計し、FOSS開発者におそらく最初のメッセージングシステムの再利用可能なレシピを提供し始めた。AMQPは他の多くの設計よりも優れていますが、[比較的複雑で、高価で、脆いままです](https://web.archive.org/web/20190620095529/www.imatix.com/articles:whats-wrong-with-amqp)。使い方を覚えるのに何週間もかかり、物事が厄介になったときにクラッシュしない安定したアーキテクチャを作るのに何ヶ月もかかるのです。

{{< textdiagram name="fig7.png" figno="7" title="Messaging as it Starts" >}}
.------------.
|            |
|  Piece A   |
|            |
'------------'
      ^
      |
      | TCP
      |
      v
.------------.
|            |
|  Piece B   |
|            |
'------------'
{{< /textdiagram >}}

AMQPのようなメッセージングプロジェクトのほとんどは、この長い問題リストを再利用可能な方法で解決しようと、アドレス指定、ルーティング、キューイングを行う新しい概念、「ブローカー」を発明することで解決しています。その結果、クライアント/サーバープロトコルや、文書化されていないプロトコルの上にAPIのセットを構築し、アプリケーションがこのブローカーに話しかけることができるようになります。ブローカーは、大規模なネットワークの複雑さを軽減する上で優れたものです。しかし、Zookeeperのような製品にブローカーベースのメッセージングを追加すると、良くなるどころか悪くなってしまう。それは、追加の大きな箱と、新たな単一障害点を追加することを意味します。ブローカーは急速にボトルネックとなり、管理すべき新たなリスクとなる。もしソフトウェアがそれをサポートするならば、2番目、3番目、4番目のブローカーを追加して、何らかのフェイルオーバー・スキームを作ることができます。人々はこれを実行します。その結果、可動部品が増え、複雑になり、壊れやすくなります。

また、ブローカーを中心としたセットアップには、独自のオペレーションチームが必要です。文字通り、昼夜を問わずブローカーを監視し、誤動作を始めたら棒で叩く必要があるのです。ボックスが必要で、バックアップボックスが必要で、それらのボックスを管理する人が必要です。これは、数年かけて何人かのチームによって構築された、多くの可動部分を持つ大規模なアプリケーションにのみ、行う価値があるのです。

{{< textdiagram name="fig8.png" figno="8" title="Messaging as it Becomes" >}}
        .---.             .---.
.---.   |   |   .---.  ^  |   |
|   +-->|   |<--|   |  |  |   |
|   |   '---'   |   |  |  '-+-'
'-+-'           '-+-'  |    |
  |               ^    |    |
  |       .-------+----+----'
  |       |       |    |
  '-------+-------+----+--.
          |       |    |  |
  .-------+-------+----+--+-----.
  |       v       |       v     |
.-+-.   .---.     |     .---.   |
|   |   |   |   .-+-.   |   |-->|
|   +-->|   +-->|   +-->|   |   |
'---'   '---'   |   |   '---'   |
          ^     '-+-'     ^     |
          |       |       |     |
  .-------+-------+-------'     |
  |       |       |             |
  v     .-+-.     v     .---.   |
.---.   |   |   .---.   |   |   |
|   |<--|   |<--|   |<--|   |<--'
|   |   '---'   |   |   '---'
'---'           '---'
{{< /textdiagram >}}

だから、中小のアプリケーション開発者は窮地に立たされる。ネットワークプログラミングを避けて、スケールしないモノリシックなアプリケーションを作るか。あるいは、ネットワーク・プログラミングに飛びつき、保守が困難な脆くて複雑なアプリケーションを作るか。あるいは、メッセージング製品に賭けて、高価で壊れやすいテクノロジーに依存したスケーラブルなアプリケーションを作ることになる。そのため、メッセージングは前世紀から抜け出せず、ユーザーにとってはネガティブな感情、サポートやライセンスを売る側にとっては喜ばしい感情という、強い感情をかき立てているのかもしれません。

私たちが必要としているのは、メッセージングの仕事をするものでありながら、それをとてもシンプルで安価な方法で行うもので、どんなアプリケーションでも、ほぼゼロコストで動作させることができるものです。それは、他の依存関係がなく、ただリンクするだけのライブラリであるべきです。追加の可動部品がないため、追加のリスクもありません。どんなOSでも動作し、どんなプログラミング言語でも動作するものでなければなりません。

これがZeroMQです。効率的で組み込み可能なライブラリで、アプリケーションがネットワーク上でうまく伸縮するために必要な問題のほとんどを、それほどコストをかけずに解決しています。

具体的には

* バックグラウンドスレッドで、I/Oを非同期に処理します。これらのスレッドは、ロックフリーのデータ構造を使用してアプリケーションのスレッドと通信するため、同時実行のZeroMQアプリケーションにはロック、セマフォ、その他の待機状態が不要です。

* コンポーネントは動的に出入りすることができ、ZeroMQは自動的に再接続します。つまり、コンポーネントを任意の順序で開始することができます。サービスがいつでもネットワークに参加・離脱できる「サービス指向アーキテクチャ」（SOA）を作成することができます。

* 必要なときに自動的にメッセージをキューに入れます。メッセージをキューに入れる前に、できるだけ受信者に近づけるよう、インテリジェントに実行します。

* 満杯になったキューを処理する方法があります（「ハイウォーターマーク」と呼ばれます）。キューが一杯になると、ZeroMQは、メッセージングの種類（いわゆる「パターン」）に応じて、送信者を自動的にブロックしたり、メッセージを捨てたりします。

* ZeroMQは、アプリケーションを任意のトランスポート上で互いに対話させることができます： TCP、マルチキャスト、プロセス内、プロセス間など、任意のトランスポートでアプリケーション同士が会話できます。異なるトランスポートを使用するために、コードを変更する必要はありません。

* メッセージングパターンに依存した異なる戦略を用いて、遅い/ブロックされた読者を安全に処理します。

* リクエスト・リプライやパブ・サブなど、さまざまなパターンを使ってメッセージをルーティングすることができます。これらのパターンは、ネットワークのトポロジー（構造）を作成する方法です。

* プロキシを作成し、1回の呼び出しでメッセージをキューイング、転送、またはキャプチャすることができます。プロキシは、ネットワークの相互接続の複雑さを軽減することができます。

プロキシは、ネットワークの相互接続の複雑さを軽減することができます * それは、ワイヤ上の単純なフレーミングを使用して、それらが送信されたように全体のメッセージを正確に配信します。10kのメッセージを書けば、10kのメッセージを受け取ることができます。

* それはメッセージにどんなフォーマットも課さない。メッセージは0からギガバイトの大きさのブロブである。データを表現したいときは、mspackやGoogleのプロトコルバッファなど、他の製品を上から選ぶことになります。

* ネットワークエラーをインテリジェントに処理し、意味のある場合には自動的に再試行します。

* それはあなたの二酸化炭素の足跡を減らします。より少ないCPUでより多くのことを行うことは、ボックスがより少ない電力を使うことを意味し、古いボックスをより長く使い続けることができるのです。アル・ゴアもZeroMQを気に入るでしょう。

実はZeroMQは、これ以上のことをやってのけます。ZeroMQは、ネットワークに対応したアプリケーションの開発方法を破壊する効果があるのです。表面的には、ソケットにインスパイアされたAPIで、<tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt>や<tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt>を行うことができるのです。しかし、メッセージ処理は急速に中心的なループとなり、アプリケーションはすぐにメッセージ処理タスクの集合に分解されます。これはエレガントで自然なことです。これらのタスクはそれぞれノードにマッピングされ、ノードは任意のトランスポートを経由して互いに会話します。1つのプロセスに2つのノード（ノードはスレッド）、1つのボックスに2つのノード（ノードはプロセス）、1つのネットワークに2つのノード（ノードはボックス）--アプリケーションコードを変更することなく、すべて同じことができます。

## ソケットのスケーラビリティ {#Socket-Scalability}

ZeroMQのスケーラビリティを実際に見てみましょう。以下はシェルスクリプトで、天気予報のサーバーを起動し、次に多数のクライアントを並行して起動します：

```
wuserver &
wuclient 12345 &
wuclient 23456 &
wuclient 34567 &
wuclient 45678 &
wuclient 56789 &
```

クライアントを実行しながら、<tt>top</tt>コマンドでアクティブなプロセスを見てみると、以下のようになります（4コアのボックスの場合）：

```
PID  USER  PR  NI  VIRT  RES  SHR S %CPU %MEM   TIME+  COMMAND
7136  ph   20   0 1040m 959m 1156 R  157 12.0 16:25.47 wuserver
7966  ph   20   0 98608 1804 1372 S   33  0.0  0:03.94 wuclient
7963  ph   20   0 33116 1748 1372 S   14  0.0  0:00.76 wuclient
7965  ph   20   0 33116 1784 1372 S    6  0.0  0:00.47 wuclient
7964  ph   20   0 33116 1788 1372 S    5  0.0  0:00.25 wuclient
7967  ph   20   0 33072 1740 1372 S    5  0.0  0:00.35 wuclient
```

ここで何が起こっているのか、少し考えてみよう。天気予報サーバーは1つのソケットを持っていますが、ここでは5つのクライアントに並行してデータを送信しています。何千ものクライアントが同時進行している可能性があります。サーバーアプリケーションはクライアントを見ず、直接会話もしません。ZeroMQソケットは小さなサーバーのように振る舞い、クライアントのリクエストを黙って受け入れ、ネットワークが処理できる限りデータを送信しているのです。また、マルチスレッドサーバーであるため、CPUからより多くの電力を引き出すことができます。

## ZeroMQ v2.2 から ZeroMQ v3.2 へのアップグレード {#Upgrading-from-ZeroMQ-v-to-ZeroMQ-v}

### 互換性のある変更点 {#Compatible-Changes}

これらの変更は、既存のアプリケーションコードに直接影響を与えるものではありません：

* Pub-sub フィルタリングは、加入者側ではなく、発行者側で行われるようになりました。これにより、多くのPub-Subユースケースでパフォーマンスが大幅に改善されます。v3.2 と v2.1/v2.2 のパブリッシャーとサブスクライバーを安全に混在させることができます。

* ZeroMQ v3.2 には多くの新しい API メソッド (<tt>[zmq_disconnect()](http://api.zeromq.org/master:zmq_disconnect)</tt>, <tt>[zmq_unbind()](http://api.zeromq.org/master:zmq_unbind)</tt>, <tt>[zmq_monitor()](http://api.zeromq.org/master:zmq_monitor)</tt>, <tt>[zmq_ctx_set()](http://api.zeromq.org/master:zmq_ctx_set)</tt>, etc.)があります。

### 互換性のない変更点 {#Incompatible-Changes}

これらは、アプリケーションや言語バインディングに影響を与える主な部分です：

* 送信/再送信メソッドを変更しました： <tt>[zmq_send()](http://api.zeromq.org/master:zmq_send)</tt> と <tt>[zmq_recv()](http://api.zeromq.org/master:zmq_recv)</tt> は異なる、よりシンプルなインターフェースを持ち、古い機能は <tt>[zmq_msg_send()](http://api.zeromq.org/master:zmq_msg_send)</tt> と <tt>[zmq_msg_recv()](http://api.zeromq.org/master:zmq_msg_recv)</tt> で提供されています。症状：コンパイルエラー。解決策：コードを修正する。

* これらの2つのメソッドは、成功すると正の値を返し、エラーになると-1を返します。v2.xでは、成功時に常に0を返していました。症状：実際には問題なく動作しているのに、見かけ上エラーが発生する。解決策：戻り値が-1であることを厳密にテストし、0でないことを確認する。

<tt>[zmq_poll()](http://api.zeromq.org/master:zmq_poll)</tt> は、マイクロ秒ではなく、ミリ秒を待つようになりました。症状：アプリケーションが応答しなくなる（実際には1000倍遅く応答する）。解決策: すべての <tt>zmq_poll</tt> 呼び出しで、以下に定義する <tt>ZMQ_POLL_MSEC</tt> マクロを使用します。

<tt>ZMQ_NOBLOCK</tt> は現在 <tt>ZMQ_DONTWAIT</tt> と呼ばれています。症状: <tt>ZMQ_NOBLOCK</tt> マクロでコンパイルに失敗する。

<tt>ZMQ_HWM</tt> ソケットオプションが <tt>ZMQ_SNDHWM</tt> と <tt>ZMQ_RCVHWM</tt> に分けられるようになりました。 症状: <tt>ZMQ_HWM</tt> マクロでのコンパイルに失敗する。

<tt>[zmq_getsockopt()](http://api.zeromq.org/master:zmq_getsockopt)</tt> オプションのほとんどが整数値になっています。症状: <tt>zmq_setsockopt</tt> および <tt>zmq_getsockopt</tt> で実行時エラーが返されます。

<tt>ZMQ_SWAP</tt> オプションは削除されました。症状: <tt>ZMQ_SWAP</tt> でのコンパイルに失敗する。解決策：この機能を使用するすべてのコードを再設計してください。

### 推奨されるシムマクロ {#Suggested-Shim-Macros}

言語バインディングなど、v2.x と v3.2 の両方で動作させたいアプリケーションでは、可能な限り v3.2 をエミュレートすることをお勧めします。以下は、C/C++のコードが両方のバージョンで動作するようにするためのCマクロの定義です（[CZMQ](http://czmq.zeromq.org)から引用）：

{{< fragment name="upgrade-shim" >}}
#ifndef ZMQ_DONTWAIT
#   define ZMQ_DONTWAIT     ZMQ_NOBLOCK
#endif
#if ZMQ_VERSION_MAJOR == 2
#   define zmq_msg_send(msg,sock,opt) zmq_send (sock, msg, opt)
#   define zmq_msg_recv(msg,sock,opt) zmq_recv (sock, msg, opt)
#   define zmq_ctx_destroy(context) zmq_term(context)
#   define ZMQ_POLL_MSEC    1000        //  zmq_poll is usec
#   define ZMQ_SNDHWM ZMQ_HWM
#   define ZMQ_RCVHWM ZMQ_HWM
#elif ZMQ_VERSION_MAJOR == 3
#   define ZMQ_POLL_MSEC    1           //  zmq_poll is msec
#endif
{{< /fragment >}}

## Warning： 不安定なパラダイムです！{#Warning-Unstable-Paradigms}

従来のネットワークプログラミングは、1つのソケットが1つのコネクション、1つのピアに話しかけるという一般的な前提で構築されています。マルチキャストプロトコルはありますが、これはエキゾチックなものです。1ソケット＝1コネクション」と仮定すると、ある方法でアーキテクチャを拡張することになります。ロジックのスレッドを作成し、それぞれのスレッドが1つのソケット、1つのピアで動作するようにします。このスレッドにインテリジェンスとステートを配置するのです。

ZeroMQの世界では、ソケットは高速で小さなバックグラウンド通信エンジンへの入り口であり、接続のセット全体を自動で管理します。あなたはこれらの接続を見たり、操作したり、開いたり閉じたり、状態を添付したりすることはできません。ブロッキング送信や受信、ポーリングなどを使っても、あなたが話せるのはソケットだけで、ソケットが管理しているコネクションではありません。コネクションはプライベートで不可視であり、これがZeroMQのスケーラビリティの鍵となる。

なぜなら、ソケットと会話するコードは、どんなネットワークプロトコルであっても、変更することなく、いくつもの接続を処理することができるからです。ZeroMQの中にあるメッセージングパターンは、アプリケーションコードの中にあるメッセージングパターンよりも安価にスケールすることができます。

つまり、一般的な仮定はもはや当てはまらないのです。コード例を読むと、脳は自分の知っていることに対応させようとします。ソケット」を読んで、「ああ、これは他のノードへの接続を表しているんだ」と思うでしょう。それは間違いです。スレッド」を読んで、「ああ、スレッドは他のノードへの接続を表しているんだ」と、またまた脳が勘違いしてしまうのです。

このガイドを初めて読む人は、実際にZeroMQのコードを1日か2日（もしかしたら3日か4日）書いてみるまでは、特にZeroMQがいかにシンプルに物事を進めてくれるかに戸惑いを感じ、その一般論をZeroMQに押し付けようとして、うまくいかないかもしれないことに気づいてください。そして、悟りと信頼の瞬間、つまり、すべてが明らかになる、*zap-pow-kaboom*サトリのパラダイムシフトの瞬間を体験することになるでしょう。