---
title: ゲームのタイムアタック、シューティングゲーム、プログラミングにおける最適化の共通点
date: '2022-11-13T15:41:00+09:00'
draft: false
---

僕は現在はソフトウェアエンジニアとして働いていますが、定職に就く前は働かずにゲームをとことん遊んでいました。  

その中でも特に遊んだのが海外ゲーム、そしてシューティングゲーム（海外では「Shoot 'em up」と呼ばれます）です。  
海外ゲームについては普通に遊ぶのはもちろんですが、いかに早くクリアするかということをしていました。いわゆるタイムアタック（海外では「Speedrun」と呼ばれます）というものです。

これらのこととプログラミングは全く関係ないようですが、プログラミングをしている中で、時々、これらのことでやってたことじゃないか、と思う場面があります。

抽象化できる共通点があるのではないかと思い、この記事で言語化を試みてみます。

## 遊んでいたゲームの種類

どういうゲームを遊んでいたかという文脈が大事になってくると思うので、説明をします。

### 海外ゲーム

海外ゲームについては、特にFPSやRPGを遊んでいました。それぞれの代表作のうち、シングルプレイヤーのもので僕が遊んでいた頃で言うと、Half-Lifeシリーズ、Diabloシリーズといったところでしょうか。
タイムアタックがどのようなものかというのは動画を見ていただくと分かると思います。 **※3D酔いというものがあるので、苦手な方は注意をお願いします。**  
今はVRに注力するJohn Carmackも主要な開発者であるQuakeというゲームのものです。  
https://www.youtube.com/watch?v=hcareEsIXHM

どうでしょう。極めて無駄のない動きじゃないでしょうか。

### シューティングゲーム

シューティングゲームとなると、どういうゲームか馴染みのない方もいると思うので、ご紹介します。
先祖はインベーダーゲームとかになるのでしょうか。どういった様子かは動画を見ていただいたほうが早いと思います。  
僕も大好きだった、難易度が最高級に高いと言われている怒首領蜂大往生の動画をご紹介します。  
下記リンクは「2周目」という、同じステージを難易度を大幅に上げて臨む場面からスタートします。  
https://youtu.be/VIELWhnLicY?t=1201

どうでしょう。鬼のような難易度じゃないでしょうか。

## 共通点

では、タイムアタック、シューティングゲーム、プログラミングにおける最適化の3つに共通するものとは何でしょうか。  
それらについて、1つずつ見ていきたいと思います。

### 1つ目の共通点「観察」

まず、1つ目は「観察」です。  

タイムアタックでは、ステージがどのような構成になっているか、敵キャラクターがどのような動きをし、どのような攻撃をしてくるか、どこにアイテムがあるか、などを観察します。  
シューティングゲームも同様です。敵キャラクターがどのような動きをし、どのような弾を撃ってくるか、などを何回も何回も何回もプレイすることで観察します。

では、プログラミングにおける最適化はどうでしょうか。こちらも、どのような処理が行われていて、どこにボトルネックがあるかを観察します。「観測」という言葉のほうがこの世界では一般的ですかね。

プログラミングではリバースエンジニアリングという言葉がありますが、タイムアタックやシューティングゲームにおいても、ただ観察するだけではなく、時にはゲームの実装まで予想しながら分析をすることもあります。

### 2つ目の共通点「試行」

2つ目は「試行」です。

タイムアタックでは、このジャンプやアクションでショートカットが可能か、このアイテムは取らずとも十分に進行させることが可能か、といったことを試します。  
シューティングゲームでは、どの順番で敵を倒すのが安全か、どのようにコンボを繋げば点数が高くなるか、といったことを試します。  
どちらも、何百、何千、何万、いや何百万といった試行になるかもしれません。

プログラミングでは、仮説や実証に基づき小さな単位で変更を行います。小さな単位で行うのは差分を細かくチェックするためで、タイムアタックでもシューティングゲームでも同じですね。

### 3つ目の共通点「評価」

3つ目は「評価」です。

タイムアタックでは、試行した結果、それによりどれだけのタイムが削られたか、Aを選んでBを捨てた結果、それ以降の流れはどうなるかといったことを評価します。  
シューティングゲームでは、動きのパターンを決めたことでどれだけ楽になったか、点数が実際に上がったか、といったことを評価します。  

プログラミングでは、実行速度やリソースの消費が改善されたかどうかを評価します。

この観察→試行→評価という流れは、ゲームかプログラミングかでサイクルは違えど、改善のためにひたすらループを回すものとなります。

### 4つ目の共通点「結合」

最後が「結合」です。このフェーズで、これまでの3つが実際に機能するかどうかチェックすることになります。

タイムアタックでは、それぞれのステージで決めた動きが全体としてのタイムの削減に繋がるかを、通してチェックします。  
シューティングゲームでは、1ステージ目では低スコアに終わる動きでも、2ステージ以降ではトータルで高くならないか、といったことをチェックします。

プログラミングでは、結合テストなどを行い、1つのコンポーネントの変更が他に影響を与えていないか、トータルではパフォーマンスが下がっていないかといったことをチェックします。

## 最後に

ここまで、ゲームのタイムアタック、シューティングゲーム、プログラミングの最適化における共通点を書いてみました。  

勢いで雑に書いてみた文章ですが、他にこれらのことを経験した方なら、もしかしたら「うんうん」と頷いていただけるかもしれないですね。  
共通しているのは根気いるよね〜というところでしょうか。  
書いていて思ったのですが、もっと広く一般化できるものなのかもしれませんね。

最後に一言、「最適化 is fun」
