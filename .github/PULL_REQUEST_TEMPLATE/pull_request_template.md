---
name: スライドアイデアテーマ
about: スライドのアイデアを思いついたら突っ込むためのテンプレート
title: "[DATE]: [Slide Title]"
assignees: SuguruOoki
---

### コードレビューガイドライン

**<!-- Updateのクエリがカラムものについては バックエンドのエンジニアをレビュワーに2人アサインしてください。 -->**

https://github.com/TechBowl-japan/techtrain-backend/blob/develop/doc/REVIEW_GUIDELINE.md

## 実装の概要

**<!-- ReviewOK の状態になったら、Draft を解除してください。 -->**

*

## リリース時の考慮内容

**<!-- リリース時にフロントエンドとリリースタイミングの調整の必要があれば、その理由と該当PRを添付すること -->**

### 追加する環境変数

**<!-- なければ、なしと書いてください。見出しを削除しないでください -->**

## レビューを出す前 TODO

- [ ] base branch が `develop` の場合、この PR で機能は完結している(動作確認やリリースが可能)か
- [ ] テストを書いたか
- [ ] テストは通っているか
- [ ] [ドメインモデル図](https://whimsical.com/techtrain-Kh6wdKBrC3qC5KA3rChRZB)は修正したか
- [ ] テストの観点は異常系と正常系のどちらもあるか
- [ ] そのほかの GitHubActions のチェックは通っているか
- [ ] タイポはないか
- [ ] クラス、メソッドコメントを書いたか
- [ ] ReviewDog の指摘点を修正したか

## 検証内容

**<!-- テストが通る以外で、手動検証した内容を書いてください。 -->**

- [ ] 書いたテストと実装に関連したテストが通ること
- [ ]

## 補足

※staging ブランチにマージすると自動的にステージング環境にデプロイされます。
詳細の仕組みは[こちら](https://docs.google.com/presentation/d/1k6rHQ5WS6OaacydjXhCOlmn54nSvbwVzNRdJjRQfCvw/edit#slide=id.ga4acc33e00_0_51)。
