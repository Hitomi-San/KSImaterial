# トラブルシューティング

## 一般

### サンプルプログラムが動かない

各ページにおけるサンプルプログラムをコピーペーストすると、行頭のインデントに使われているスペースが原因で Ruby 処理系通らない場合があります。
この場合、ブラウザを変更してみてください。
詳細は以下の通り (TA 荒田さんのコメントより)。

* 件のページのサンプルコードには、インデントに通常のスペース (U+0020) 以外に no-break space (U+00A0) が含まれている (Google Sites の仕様?)
* 多くの Web ブラウザーは、コピーの際にそれを通常のスペース (U+0020) に変換するようであるが、Edge はそれをしない
* Ruby は no-break space を空白として取り扱わない (ECMAScript や Haskell は Unicode で Whitespace として扱われる文字を空白として取り扱う)

## ネットワーク関係

### gem を使おうとして「Unable to download data」で始まるエラーが出る

TA アカウントでログインして「システム設定」→「ネットワーク」→「ネットワークプロキシ」を開き、「システム全体に適用する」をクリックしてみましょう。

### gem を使ってどうしてもインストールがうまくいかない

apt-get で代用できる場合があります。

### 「mkmf.rb can't find header files for ruby」で始まるエラーが出る

`sudo apt-get install ruby-dev` を実行してみてください。
