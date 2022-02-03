# comment-review
a-blog cms のコメント機能を使用したレビュー機能です

本機能は社内で使用することを想定しています。
![sample_image](https://user-images.githubusercontent.com/4686462/152127492-7088ea59-124a-44f7-aa99-af2396b72b8b.png)


## エントリーのカスタムフィールドではなくコメント機能を採用するメリット

- 承認機能を導入しているサイトで使える
- 編集画面に入らなくても書ける
- 処理済み、未処理がステータスで管理できる
- 投稿時に通知メールを送信できる

## できること
- 記事に対してレビュー（修正依頼）が書けます
- レビューを書いた時に管理者へ通知メールを送ります（※管理画面で別途設定が必要）
- ステータスで処理済み、未処理が管理できます
- コメント一覧で投稿されたレビューを一覧できます
- 優先順位がつけられます
- 記入者と投稿日時を記録できます
- あとからコメントを修正できます

## できないこと
- カスタムフィールドなどで入力欄を自由に拡張できません
- 編集用のパスワードをhiddenで入れているので、仕組みを知っている人にはわかってしまうのでパブリックなページには向いていません
- CMSのバリデーションが効きません（代わりにHTMLのバリデーション機能を採用）

## 使い方

1. ファイルをダウンロードし、themes/ご利用のテーマに同じ階層にテンプレートを設置してください。
2. 使用したい箇所に、/include/comment/body.htmlをインクルードして読み込んでください。
3. 管理画面＞コンフィグ＞機能設定の順にページを移動し、「コメント機能」を有効にします。
4. （必要あれば）コメントが投稿された際にメール通知を送りたい場合は、管理画面＞コンフィグ＞メール設定の順にページを移動し、コメント項目の「To」に通知を送信したいメールアドレスを登録してください。
5. Comment_BodyとUser_ProfileモジュールIDを設定してください。くわしい設定はこのドキュメントの「モジュールIDの設定」をご覧ください。


### モジュールIDの設定

主に使用しているモジュールは2つあります。

* Comment_Body
* User_Profile

#### Comment_Body

モジュールは以下の設定で作成してください。

* モジュールID名：commentBody_review
* 表示形式：スレッド
* 表示件数：100

#### User_Profile

コメントに投稿者のアイコン画像を表示します。
モジュールは以下の設定で作成してください。

* モジュールID名：user_comment
* 対象にしたいユーザーがすべてのブログに所属するユーザーなら、ルートに作ってください（そのブログだけであれば、作らなくても大丈夫です）
* ルートブログに作った際、BIDを指定し、グローバルにチェックをつけます。
