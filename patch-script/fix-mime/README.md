# MIME Typeの修正

バックエンドのwasabiへの投稿の実装ミスにより、全てのアセットのMIME Typeがboto3のデフォルトである`application/octet-stream`となってしまっている。
これにより、sitemapへの画像等のリンクを埋め込めない状態になっている。また、本来のMIME Typeを保持していないことはWebの仕様に反しているため、修正の必要がある。このシェルスクリプトはその問題を解決するためにWasabiに載っているアセットのMIME Typeを拡張に合わせたものに修正するためのものである。

## 手順

1. 本番バケットのバックアップバケットを作成し、バックアップを行う。
2. バックアップバケットに対して、本シェルスクリプトを適用し、問題なく変更ができていることを確認する。
3. 2で確認ができれば再度バックアップを作成する。
4. 本番バケットに対して、本シェルスクリプトを適用する。

## 対応チケット

https://www.notion.so/MIME-5b4623cc36184501b541fbaa1a83b9b3?pvs=4

## 実装の参考

- https://dev.classmethod.jp/articles/change-content-type-by-aws-cli/
- https://knowledgebase.wasabi.com/hc/ja/articles/115001910791-Wasabi-%E3%81%A7-AWS-CLI-%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95
