---
sidebar_position: 5
---

# 開発者ツール

開発者ツールによるフロントエンドのデバッグ・HTML/CSS/JavaScriptの基礎を習得します。

## HTML/CSS

任意のWEBサイトにて以下実現できるようなHTML操作を開発者ツールで実行してください。

- パスワード入力欄に入力した値が●●●●で隠されないようにする
- 領域の表示箇所を移動する
- 領域を削除する
- 領域を非表示にする
- 領域を透明にするにする（やり方は複数ある）
- 押せないボタンを押せるようにする
- 押せるボタンを押せないようにする
- 背景色を変える　※値を直接入力して
- 背景色を変える　※カラーピッカーで
- 高さ・幅を変える ※値を直接入力して
- 高さ・幅を変える ※十字キー上下で
- 高さ・幅を変える ※十字キー上下 + shiftで
- 高さ・幅を変える ※十字キー上下 + ctrlで
- ブラウザのタブの表示文言を変更する
- 一覧の行を複製する

## JavaScript

任意のWEBサイトにて以下実現できるようなスクリプトを開発者ツールで実行してください。

- パスワード入力欄に入力した値が●●●●で隠されないようにする
- パスワード入力欄に入力した値を取得する
- パスワード入力欄に入力した値を変更する
- 領域を削除する
- 領域を非表示にする
- 領域を透明にするにする（やり方は複数ある）
- ボタンが押せるか押せないかを取得する
- 押せないボタンを押せるようにする
- 押せるボタンを押せないようにする
- 背景色を取得する
- 背景色を変更する
- 高さ・幅を取得する
- 高さ・幅を変更する
- ブラウザのタブの表示文言を変更する
- 一覧の最初行を取得する
- 一覧の3行目を取得する
- 一覧の最後の行を取得する
- 一覧の最初行の特定列を取得する
- 一覧の3行目の特定列を取得する
- 一覧の最後の行の特定列を取得する
- 一覧の最初行の特定列の表示テキストを取得する
- 一覧の3行目の特定列の表示テキストを取得する
- 一覧の最後の行の特定列の表示テキストを取得する

## 応用：本WEBサイトからの情報抽出

- 「JavaScript（基礎）」セクションタイトルを以下２つの方法で取得する
  - 1. querySelectorAllにて、画面上の何番目のh2タグかをCSSセレクタで指定
  - 2. querySelectorAllにて、セクションタイトルのid属性をCSSセレクタで指定
- 「JavaScript（基礎）」セクションのリストを取得する
  - ※querySelectorAllにて、画面上の何番目のulタグかをCSSセレクタで指定
- 上記取得結果は[NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList)でありJavaScriptの配列のmap処理などは使えない、そのため、配列で処理できるように取得したNodeListを配列に変化する
  - ※[Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)などを使って
- 上記取得結果をmapやjoinで加工して、先頭に1始まりの番号をつけて、`★`つなぎにする
  - ※結果のイメージは以下
    - `1.パスワード入力欄に入力した値が●●●●で隠されないようにする★2.パスワード入力欄に入力した値を取得する...`

## 応用：Qiitaからの情報抽出

- [Qiita > ホーム](https://qiita.com/)にて、表示されている記事30件のタイトル文字列を配列で取得する
  - Qiitaの記事一覧の記事1つ1つは特定のクラスが指定されているので、それを利用して記事をNodeListで取得
  - NodeListを配列に変換
  - map処理
    - 記事1要素中のタイトルを取得　→ innerHTMLにてタイトル文字列取得
- 上記と同様、[Qiita > ホーム](https://qiita.com/)にて、表示されている記事30件の投稿者名文字列を配列で取得する
- 上記と同様、[Qiita > ホーム](https://qiita.com/)にて、表示されている記事30件のタグ文字列を、２次元配列で取得する
- 上記と同様、[Qiita > ホーム](https://qiita.com/)にて、表示されている記事30件のいいね数を配列で取得する
- [Qiita > ホーム](https://qiita.com/)から情報を取得して以下マークダウン表を作成する
  - 出力結果のイメージ
    - ```md
      |投稿日|投稿者|タイトル|タグ(複数個の場合は改行)|いいね数|
      |---|---|---|---|---|
      | X | X | X | ・X <br/> ・X <br/> ・X | X |
      | X | X | X | ・X <br/> ・X | X |
      | X | X | X | ・X | X |
      ```
  - 出力結果のイメージ(上記をマークダウンプでレビューした時)
    - |投稿日|投稿者|タイトル|タグ(複数個の場合は改行)|いいね数|
      |---|---|---|---|---|
      | X | X | X | ・X <br/> ・X <br/> ・X | X |
      | X | X | X | ・X <br/> ・X | X |
      | X | X | X | ・X | X |
