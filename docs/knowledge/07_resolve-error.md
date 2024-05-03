---
sidebar_position: 7
---

# エラーの解決方法

既存のWEBサービスの、画面実装やAPI実装にて自分が書いたコードの動作確認にてエラーが発生した時のオーソドックスな対処法を記載しています。

## 目的

**「エラー原因が分からず闇雲にググってQiitaのコードをコピペしたけど、一向にエラーが解決せず、時間が過ぎていく」**のような問題を防ぐために、  
エラーに的確に短時間で対象する方法を纏めたページです。  
※新人さんや若手の方に毎年口頭で教えている気がしたので文章に纏めます。

## 手順

### 1. 表面に見えるエラーと根本原因が同じ場合の手順

エラー解決に難易度はありますが、まずはVSCodeの赤い波線、ブラウザの開発者ツールのコンソールログでのエラーログなど表面に見えるエラーを解決するための手順を示します。

### 1-1. エラーの再現性確保

「この操作をするとエラーが発生する」「この操作だと発生しない」などエラー発生有無を切り分けてください。  
簡単なものであれば「同じ操作をすると毎回エラーが発生する」ようなケースですが、なかには不規則に発生する場合もあります。  
その場合は不規則の中に規則性を見つけてください。例えば「３回に一回発生する」「特定操作の後に、操作すると発生する」などです。

### 1-2. エラー内容の把握 → 原因の特定 → 対処

エラーの再現性が確保できたら、エラーログをしっかり読んで`(A)誰にエラーだと言われているのか`と`(B)どういうエラーだと言われているのか`を特定してください。  
A・Bを特定し、エラーを出しているライブラリ/ツールの公式サイトの対象エラー(または規則)のページを見れば、たいていの場合は修正方針は見いだせます。その後、コード修正して動作確認てエラーが解消が確認できれば手順は終了です。

:::info例
Aが`typescript-eslint`、Bが`no-unused-vars`だと分かればエラーだと分かれば、
[typescript-eslint公式サイト > no-unused-varsのページ](https://typescript-eslint.io/rules/no-unused-vars/)を確認し*This rule extends the base eslint/no-unused-vars rule.*と記載があるので、大元は`ESLint`の`no-unused-vars`であることがわかり、  
[ESLint公式サイト > no-unused-varsのページ](https://eslint.org/docs/latest/rules/no-unused-vars)を確認し、エラーが出る書き方/出ない書き方が把握できるので、それによって修正方針を見いだせます。
:::

### 2. 表面に見えるエラーと根本原因が異なる場合の手順

複数要素が絡む複雑な状況の場合(例えば以下)、`手順1`では解決できないので引き続き手順を進めてください。

- `手順1-1`で再現性を確認が不可
- `手順1-2`でエラーを解決したが芋づる式に別のエラーが発生する

### 2-1. エラー箇所の特定（コードを削る）

状況を簡素化するために、エラーが出なくなるまで自分で書いたコードをどんどん削ってください。  
作業着手前にはエラーが発生しない状態で、現状エラーが発生しているということは、自分がどこかのコードを書いた段階からエラーが発生し始めたということになります。そのキッカケをコードの行レベルで特定するため、段階的にコードを削っていってください。具体的には以下方法で削ります。

- 見立てがあれば、対象コードをコメントアウト
  - → エラーが発生しなくなれば、消したコードがエラーの原因
- 見立てがなければ、コードを上半分・下半分などで２分してどちらかをコメントアウト
  - → エラーが発生しなくなれば、消したコード郡のどこかの行がエラーの原因なので、さらに削る範囲を小さくしていく

:::info参考

コードをコメントアウトすると、そこで利用しているライブラリのimport文などが削除されるので、後で元に戻す時に手間です。この手間を省くために以下方法などがあります。

- 値をハードコードした真偽値の変数を定義
- 上記で定義した変数による条件分岐によって、処理を実行させないようにしたり、画面描画をしないようにする
  - 条件分岐を三項演算子にすると真偽値の変数の値を切り替えることで、動作確認できて便利です

:::

### 2-2. エラー内容の把握 → 原因の特定 → 対処

`手順2-1`で見出したエラー行から、エラーの原因を特定します。具体的には以下作業をします。

- エラー行でutil関数を呼び出していれば実装詳細を見る
- 利用ライブラリの公式サイトやを見る
- 利用ライブラリのGitHubのissuesを検索する ※同事象で困っている人が居る可能性が高い
- 利用ライブラリをGitHubでクローンしてエラー発生箇所付近の実装を見る

特定が難航する場合は、いくつ可能根本原因の仮説を立てて、仮説検証を繰り返してください。  
やみくもにコードを修正するよりは、仮説を1つ1つ潰していったほうが、何が原因で何が原因でないかが絞り込まれていくので建設的です。