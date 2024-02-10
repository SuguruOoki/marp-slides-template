---
title: PHPの「歴史的な理由」ってなんだ！？のおまけ
description:
class: invert
_class:
  - invert
  - lead
footer: 2024-02-11 | PHPの「歴史的な理由」ってなんだ！？
_footer: ""
paginate: false
_paginate: false
marp: true
---

<!-- https://qiita.com/takeshisakuma/items/5a61e6eac123d28602fb -->
# PHPの「歴史的な理由」ってなんだ！？のおまけ

---

<!-- _class: lead -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

# 自己紹介

---

![bg left:30% 80%](images/profile_up_minify.png)

### 所属

株式会社TechBowl

### 何やってる？

「TechTrain」というサービスを作っています！
反復横跳びし続けている何でも屋さん(Laravel, Next.js, AWS, etc...)

### 趣味
 - お酒(よく溺れる)
 - サウナ
 - 読書

---

## TechTrain

![bg fit left:30% 80%](images/techtrain-logo.jpg)
エンジニア教育+Directスカウトのサービス。
Coding Stoicをテーマに「うるせえコードかけ！」と言いがちなメンターが多めのエンジニアを育てるためのサービスです。

---

# ここからはおまけ

参考資料などを載せていく！

---

* snmprealwalkについての批判and提案 From Mike Jackson
  * 1999-05-21 13:42:07
  * https://marc.info/?l=php-internals&m=92733157300339&w=2 の前のメッセらしい。
  * snmprealwalkは、適切な名前ではない。snmpoidwalkかsnmpwalkoidかに変更してはどうか？
    * ドキュメントもまだ十分ではない状態だし、変更するならいまだ！
      * `his is a policy decision though, and I don't know if this is approporiate, so for the time being I'm implementing both snmpwalkoid() and snmprealwalk() to both be identical.` → ただし、これはポリシー上の決定であり、これが適切かどうかはわかりません。そのため、当面は snmpwalkoid() と snmprealwalk() を両方とも同一になるように実装します。
      * これが歴史的な経緯
    * https://marc.info/?l=php-internals&m=92733157300339&w=2

---

### marc.info で検索してみた

1. https://marc.info/?l=php-internals&w=2&r=1&s=walkoid&q=b
2. https://marc.info/?l=php-internals&w=2&r=8&s=snmpwalk&q=b

2は`snmpwalkoid`に関わる`snmpwalk`関数についての議論があるため、こちらもみている。

---

### snmpwalkの最初のMLは1998年！

https://marc.info/?l=php-internals&m=90222493031994&w=2

当時はsnmp系の関数は、`snmpget`, `snmpwalk`のみであった模様

---

* 最初にsnmpgetとsnmpwalkが存在していた
* snmprealwalkが実装された
  * 1999-04-03に実装
  * https://marc.info/?l=php-internals&w=2&r=2&s=snmprealwalk&q=b
  * ドキュメントへの追加
    * https://marc.info/?l=php-internals&m=92310736920527&w=2
    * https://marc.info/?l=php-internals&m=92310736920527&w=4
      * 歴史的な理由によりというドキュメントがこのURLで追加されたことを確認した
        * `The existence of snmprealwalk() and snmpwalk() has historical reasons. Both functions are provided for backward compatibility.`

---

	* snmp
      * https://marc.info/?l=php-internals&m=92312533926915&w=4 でドキュメントの修正も入っている
  * oidのツリーに沿ってwalkする。連想配列を返す。
  * https://marc.info/?l=php-internals&m=92310594519942&w=2
  * バグが指摘されている
    * 1999-04-05 18:34
    * https://marc.info/?l=php-internals&m=92333749125885&w=4

---

* PHP3.0.8におけるsnmprealwalkの追加が取り消されている
  * https://marc.info/?l=php-internals&m=92680821807363&w=2
  * https://marc.info/?l=php-internals&m=92706210107003&w=2
    * こちらのバグが残っていたための可能性がある
    * 1999-05-18 17:27:04
    * https://marc.info/?l=php-internals&m=92706265907865&w=2
      * 1999-05-18 17:35:13
      * バグが修正されて、改めて、3.0.8に追加されることになった
---

* snmprealwalkについての批判and提案 From Mike Jackson
  * 1999-05-21 13:42:07
  * https://marc.info/?l=php-internals&m=92733157300339&w=2 の前のメッセらしい。
  * snmprealwalkは、適切な名前ではない。snmpoidwalkかsnmpwalkoidかに変更してはどうか？
    * ドキュメントもまだ十分ではない状態だし、変更するならいまだ！
      * `his is a policy decision though, and I don't know if this is approporiate, so for the time being I'm implementing both snmpwalkoid() and snmprealwalk() to both be identical.` → ただし、これはポリシー上の決定であり、これが適切かどうかはわかりません。そのため、当面は snmpwalkoid() と snmprealwalk() を両方とも同一になるように実装します。
      * これが歴史的な経緯
    * https://marc.info/?l=php-internals&m=92733157300339&w=2

---

* snmprealwalkについての批判and提案に対する返答 from Rasmus Lerdorf
  * 1999-05-22 0:16:23
  * https://marc.info/?l=php-internals&m=92733157300339&w=2
  * サマリーは完璧だし、全面的に提案に同意する
  * snmprealwalk()はマジで面白い関数名はまだリリースしてねえ。3.0.8でリリースされるはずだ。今が変える良いチャンスだと思ってるぜ！->なのにそのままリリースされてるぜ！w

---

* snmpwalkoid(), snmp_get_quickprint(), and snmp_set_quick_print()が追加
  * 1999-05-22 7:03:21
  * https://marc.info/?l=php-internals&m=92735955712618&w=2

---


* Stig?3.0.8の状態はどうなってる？リリースされるのか？という問い合わせをしている
  * https://marc.info/?l=php-internals&m=92733244900971&w=2

---

* snmpwalkoidの追加+snmprealwalkが一時的に削除される(By Mike Jackson)
  * 1999-05-22
  * `st = 3; /* This is temporary until snmprealwalk() is removed */`
  * https://marc.info/?l=php-internals&m=92735955712618&w=2
  * https://marc.info/?l=php-internals&m=92735960712642&w=2
    * snmpwalkoid()の追加(extern)
    * snmp_get_quick_print()の追加(extern)
    * snmp_set_quick_print()の追加(extern)
  * https://marc.info/?l=php-internals&m=92736193313414&w=2
    * ドキュメントにsnmpwalkoid()の追加
    * ドキュメントからsnmprealwalk()の削除

---

* PHP3.0.8リリース
  * 1999-05-22 21:10
  * https://marc.info/?l=php-internals&m=92740688905388&w=2
  * snmprealwalk()(Sascha Schumannが実装)は追加されたままリリースw
* snmprealwalkのバグ修正が入る？ from jim
  * 1999-06-30 19:26
  * https://marc.info/?l=php-internals&m=93077078028154&w=2
  * `Fixes pointed out by #1636, and a little bit of tabification.`

---

* snmpset()が追加される
  * 1999-07-11 20:25
  * https://marc.info/?l=php-internals&m=93173887515673&w=2
  * `Added int snmpset(string host, string community, string object_id, string type, mixed value [, int timeout [, int retries]]), which is a function that will set the value associated with an OID on the given host and community. On lines 352, 360, 368, and 376, "return" (lowercase) was removed because SGI's compiler on IRIX6.5 considered a return of a value in a void function to be an error.`

---

## エイリアスとなった

2010-09-20 19:46:35

Net-SNMP パッケージに付属の snmpget コマンドの動作をより適切に反映するために、添付されたパッチにより、snmpget()/snmpgetnext() 関数のパラメータとして OID の配列が可能になります。これにより、Net-SNMP API が OID を 1 つのリクエストにバンドルするため、SNMP を介したより効率的なクエリが可能になります。このパッチには下位互換性があり、snmpget()/snmpgetnext() は引き続き文字列を受け入れ、その場合でも文字列を返します。完全を期すために、snmpwalkoid() に対応するものとして snmpgetoid() と snmpgetnextoid() も追加しました。

https://marc.info/?l=php-internals&m=128501207513342&w=2

---

### Version 4.0, Release Candidate 2

> snmp_walkoid is now an alias for snmp_realwalk. (Sterling)

ここでsnmp_realwalkへ修正されている

---

# 作成途中に利用したScrap

https://zenn.dev/ohkisuguru/scraps/e1da852f1b428c

---

# 参考

https://github.com/search?q=repo%3Aphp%2Fdoc-ja%20%E6%AD%B4%E5%8F%B2%E7%9A%84%E3%81%AA&type=code
https://github.com/search?q=repo%3Aphp%2Fdoc-en+historical&type=code
https://www.slideshare.net/ebihara/php-32340906
https://zenn.dev/pixiv/articles/756ce0bcbdd1be
https://qiita.com/masakielastic/items/a3080c7744f1be97a17c
https://zenn.dev/hanhan1978/articles/2965be4e71dfd8
http://www.ujp.jp/modules/tech_regist2/?HomeBrew%2Fsvn%2FInstall%2FYosemite

---

# 歴史的経緯の走り書き

---

|すでに解説済みか？|関数名|公式ドキュメントリンク|補足|
|:--|:--|:--|:--|
|️|snmpwalkoid|https://www.php.net/manual/ja/function.snmpwalkoid.php|snmprealwalk()が移行先として推奨されている。歴史的な理由の主なものとしては下位互換のため|
|️|snmpwalk|https://www.php.net/manual/ja/function.snmpwalk.php|snmprealwalk()が移行先として推奨されている。歴史的な理由の主なものとしては下位互換のため|
|○|get_debug_type|https://www.php.net/manual/ja/function.get-debug-type.php|PHP8.0から追加されたもの。gettypeについての歴史的な理由により、書いてあるだけなので、対象外となる。gettypeで解説されている。|
|○|gettype|https://www.php.net/manual/ja/function.gettype.php||
|○|urlencode|https://www.php.net/manual/ja/function.urlencode||
|○|Pharファイルフォーマット|https://www.php.net/manual/ja/phar.fileformat.phar.php|Phar マニフェストは高度に最適化された書式で、 ファイル単位で圧縮やパーミッションの情報を指定することができ、 さらにファイルのユーザーやグループなど、独自に定義したメタデータも含めることができます。 1 バイトをこえる大きさの値はリトルエンディアン形式のバイト順で保存されます。 ただし API バージョンだけは例外です。これは 3 ニブルのデータですが、 歴史的な理由によりビッグエンディアン形式のバイト順で保存されます。|
|○|implode|https://www.php.net/manual/ja/migration74.deprecated.php|引数の順序がPHP7.4でdeprecatedとされて変更された|
|○|rawurlencode|https://www.php.net/manual/ja/function.rawurlencode.php||


---

## snmpwalkoidの最初のMLは1999年!

https://marc.info/?l=php-internals&w=2&r=6&s=snmpwalkoid&q=b
https://marc.info/?l=php-internals&m=92733157300339&w=2

---

* 最初にsnmpgetとsnmpwalkが存在していた
* snmprealwalkが実装された
  * 1999-04-03に実装
  * oidのツリーに沿ってwalkする。連想配列を返す。
  * https://marc.info/?l=php-internals&m=92310594519942&w=2
  * バグが指摘されている
    * 1999-04-05 18:34
    * https://marc.info/?l=php-internals&m=92333749125885&w=4

---

* この時点のドキュメントですでに歴史的理由が追加されているw
  * PHP3.0.8のリリース前の状態
  * https://marc.info/?l=php-internals&m=92310736920527&w=2

---

* snmp3_walk()が関数として追加された(多分)
  * php3_snmpwalkが追加されているのを確認している
    * こちらでsnmpwalkが後から入れ替えられている
  * 1998-07-03
  * https://marc.info/?l=php-internals&m=90222493031994&w=2
  * ただし、これよりも前に実際の処理は追加されており、PHP3.0.1を確認すると、その時点で、snmpgetとsnmpwalkは存在している。`snmp.c,v 1.20 1998/11/03 15:52:33 rasmus`というコメントもあるので、v1.20からある。1系のコードはあまりちゃんとのこっていないので、これ以上の情報はない。2.0系では、phpsnmpwalkという原型となったものはすでにありそう。

---

* snmprealwalk()追加された???
  * 1999-04-03に追加された
  * https://marc.info/?l=php-internals&w=2&r=2&s=snmprealwalk&q=b
  * ドキュメントへの追加
    * https://marc.info/?l=php-internals&m=92310736920527&w=2
    * https://marc.info/?l=php-internals&m=92310736920527&w=4
      * 歴史的な理由によりというドキュメントがこのURLで追加されたことを確認した
        * `The existence of snmprealwalk() and snmpwalk() has historical reasons. Both functions are provided for backward compatibility.`
	* snmp
      * https://marc.info/?l=php-internals&m=92312533926915&w=4 でドキュメントの修正も入っている

---

* PHP3.0.8におけるsnmprealwalkの追加が取り消されている
  * https://marc.info/?l=php-internals&m=92680821807363&w=2
  * https://marc.info/?l=php-internals&m=92706210107003&w=2
    * こちらのバグが残っていたための可能性がある
    * 1999-05-18 17:27:04
    * https://marc.info/?l=php-internals&m=92706265907865&w=2
      * 1999-05-18 17:35:13
      * バグが修正されて、改めて、3.0.8に追加されることになった
---

* snmprealwalkについての批判and提案 From Mike Jackson
  * 1999-05-21 13:42:07
  * https://marc.info/?l=php-internals&m=92733157300339&w=2 の前のメッセらしい。
  * snmprealwalkは、適切な名前ではない。snmpoidwalkかsnmpwalkoidかに変更してはどうか？
    * ドキュメントもまだ十分ではない状態だし、変更するならいまだ！
      * `his is a policy decision though, and I don't know if this is approporiate, so for the time being I'm implementing both snmpwalkoid() and snmprealwalk() to both be identical.` → ただし、これはポリシー上の決定であり、これが適切かどうかはわかりません。そのため、当面は snmpwalkoid() と snmprealwalk() を両方とも同一になるように実装します。
      * これが歴史的な経緯
    * https://marc.info/?l=php-internals&m=92733157300339&w=2

---

* snmprealwalkについての批判and提案に対する返答 from Rasmus Lerdorf
  * 1999-05-22 0:16:23
  * https://marc.info/?l=php-internals&m=92733157300339&w=2
  * サマリーは完璧だし、全面的に提案に同意する
  * snmprealwalk()はマジで面白い関数名はまだリリースしてねえ。3.0.8でリリースされるはずだ。今が変える良いチャンスだと思ってるぜ！->なのにそのままリリースされてるぜ！w

---

* snmpwalkoid(), snmp_get_quickprint(), and snmp_set_quick_print()が追加
  * 1999-05-22 7:03:21
  * https://marc.info/?l=php-internals&m=92735955712618&w=2
* Stig?3.0.8の状態はどうなってる？リリースされるのか？
  * https://marc.info/?l=php-internals&m=92733244900971&w=2

---

* snmpwalkoidの追加+snmprealwalkが一時的に削除される(By Mike Jackson)
  * 1999-05-22
  * `st = 3; /* This is temporary until snmprealwalk() is removed */`
  * https://marc.info/?l=php-internals&m=92735955712618&w=2
  * https://marc.info/?l=php-internals&m=92735960712642&w=2
    * snmpwalkoid()の追加(extern)
    * snmp_get_quick_print()の追加(extern)
    * snmp_set_quick_print()の追加(extern)
  * https://marc.info/?l=php-internals&m=92736193313414&w=2
    * ドキュメントにsnmpwalkoid()の追加
    * ドキュメントからsnmprealwalk()の削除

---

* PHP3.0.8リリース
  * 1999-05-22 21:10
  * https://marc.info/?l=php-internals&m=92740688905388&w=2
  * snmprealwalk()(Sascha Schumannが実装)は追加されたままリリースw

---

* snmprealwalkのバグ修正が入る？ from jim
  * 1999-06-30 19:26
  * https://marc.info/?l=php-internals&m=93077078028154&w=2
  * `Fixes pointed out by #1636, and a little bit of tabification.`

---

* snmpset()が追加される
  * 1999-07-11 20:25
  * https://marc.info/?l=php-internals&m=93173887515673&w=2
  * `Added int snmpset(string host, string community, string object_id, string type, mixed value [, int timeout [, int retries]]), which is a function that will set the value associated with an OID on the given host and community. On lines 352, 360, 368, and 376, "return" (lowercase) was removed because SGI's compiler on IRIX6.5 considered a return of a value in a void function to be an error.`