### クラウド入門編

2019年3月15日
---


### 目次
* 自己紹介
* クラウドとは
* AWS vs Azure vs GCP
* REST API


---


### 自己紹介


---
@snap
Toshiharu Tanaka
@snapend
@snap
Briswell Ltd
@snapend
@snap
非エンジニアでインフラ好き、TypeScriptとか少し触ってます
@snapend
@snap
基本初心者向けです、よろしくお願いします。
@snapend


---


### クラウドとは

---
@snap
インターネットなどのネットワーク経由でユーザーにサービスを提供する形態のこと
@snapend
https://www.internetacademy.jp/it/server/server-basic/merit-and-demerit-of-cloud.html

@snap
とはいえ色々あるので、次のような分類に分かれます（一部だけ紹介）
@snapend
@snap
https://ec-orange.jp/ec-media/?p=18343
@snapend

---

### SaaS

---

@snap
”Software as a Service”の略で「サース」と呼ばれます。
@snapend
@snap
みんな大好きGmailとか、GitLab Cloudとか、DropBoxとか
@snapend
@snap
アプリケーションレイヤーまで用意されているもの
@snapend


---

### PaaS

---

@snap
”Platform as a Service”の略で、読み方は「パース」です。主に、PaaSは企業でのサービス開発に利用されます。
@snapend
@snap

@snapend
@snap
Azure、GCP（部分的）はここ
@snapend
@snap
ミドルウェアレイヤーまで用意されているもの
@snapend

---

### IaaS
---

@snap
”Infrastructure as a Service”つまり「サービスとしてのインフラ」と訳されるIaaS。読み方は「イァース」「アイアース」です。
@snapend
@snap
PaaSより自由度が高く、ミドルウェアとか自分で設定したりする感じ
@snapend
@snap
AWS EC2はここ
@snapend
@snap
OSレイヤーまで用意されているもの
@snapend

---

### AWS vs Azure vs GCP

---
@snap
AWS
@snapend
@snap
Amazon Web Service
@snapend
@snap
2006年7月に公開
@snapend

@snap
Azure
@snapend
@snap
Microsoft Azure
@snapend
@snap
2010年1月に世界21ヶ国で正式にサービスを開始
@snapend

@snap
GCP
@snapend
@snap
Google Cloud Platform
@snapend
@snap
2008年4月 Google App Engine がサービス開始
@snapend

@snap
※全部Wiki調べ
@snapend

---

@snap
シェア率
@snapend

https://www.itmedia.co.jp/news/articles/1902/13/news078.html

---

### AWSの強み弱み妬み

---
@snap
UIがわかりやすい。
@snapend
@snap
IaaS的な使い方もPaaS的な使い方もできるため、一歩間違えると難易度の高い構成になって保守性がない。
@snapend
@snap
EC2インスタンスに対して固定IPを割振れるが、クラウドとしてはアンチパターン
@snapend

---

### Azureの強み弱み妬み

---
@snap
Microsoftなので
@snapend
@snap
Windows Server/SQL Server 2008
@snapend
@snap
これがずるい。
@snapend
@snap
https://japan.zdnet.com/article/35122428/
@snapend

@snap
設定しときゃ勝手にスケールしてくれる
@snapend
@snap
管理画面が遅い、AWSに比べると安定してない気がする
@snapend

---


### GCPの強み弱み妬み

---
@snap
Googleの各種サービスやYoutube（Google内部）などと連携するREST APIが用意されている
@snapend

@snap
勝手にスケールしてくれる
@snapend

@snap
SDK入れてコマンドとか叩かないといけない、上級者向け
@snapend

---


### （余談）REST APIって何

---

@snap
Webシステムを外部から利用するためのプログラムの呼び出し規約(API)の種類の一つで、RESTと呼ばれる設計原則に従って策定されたもの。
@snapend
@snap
REpresentational State Transfer
@snapend

---

@snap
RESTとRESTful
@snapend

@snap
RESTで作られたシステムのことをRESTfulと言う（らしいよ）
@snapend
@snap
結構世の中のサービスで公開しているの多いけど、RESTもどきが多い（らしいよ）
@snapend

---

### （余談）最近僕はシステムをFrontEndとAPIに分けてます（カンペ）

---


### やりがちアンチパターン

---

@snap
https://api.xxx.xxx/v1/orderCreate
@snapend
@snap
https://api.xxx.xxx/v1/orderSearch
@snapend
@snap
https://api.xxx.xxx/v1/orderUpdate
@snapend
@snap
https://api.xxx.xxx/v1/orderDelete
@snapend

routerとかのソース汚くなるから。

---

### これがREST（だよね？）

---
@snap
https://api.xxx.xxx/v1/order
@snapend
@snap
POST methodで渡す（作成）
@snapend

@snap
https://api.xxx.xxx/v1/order
@snapend
@snap
GET methodで渡す（検索）
@snapend

@snap
https://api.xxx.xxx/v1/order/:id
@snapend
@snap
PUT methodで渡す（更新）
@snapend

@snap
https://api.xxx.xxx/v1/order/:id
@snapend
@snap
DELETE methodで渡す（削除）
@snapend

@snap
https://api.xxx.xxx/v1/order/:id
@snapend
@snap
PATCH methodで渡す（一部更新）
@snapend

https://qiita.com/mserizawa/items/b833e407d89abd21ee72

---

@snap
表示画面とかで1つのデータだけ欲しいなら
@snapend
@snap
https://api.xxx.xxx/v1/order/:id
@snapend
@snap
を用意しておく（GETの検索とは別、これもmethodはGET）
@snapend

@snap
orderに紐づく情報が欲しいなら
@snapend

@snap
https://api.xxx.xxx/v1/order/:id/invoice
@snapend

---

@snap
※KISSの原則によると、本当は複数形が推奨、order → orders（めんどくさいからどっちでもいいかな）
@snapend
@snap
「Keep it short and simple.」（簡潔に単純にしておけ）という原則
@snapend
@snap
※詳細はGoogle先生へ
@snapend

---

@snap
設計書見る？
@snapend

---

### 同じサービスをAWS Azure GCPに立ててみた感想

---
@snap
個人的にはAWS最強
@snapend

@snap
GCPはSDK入れてコマンドでしか色々できないっぽい、GUIからインスタンスは作れなかった
上級者向けかも
@snapend

@snap
Azureもいいんだけど、portal遅い、基本PaaSなので自由度は低い
@snapend

---

@snap
結果、どれも似たようなサービスは用意されているので、どれを使っても良い
@snapend
@snap
後は好みの問題と、料金とか何をしたいかによって考える必要がある
@snapend

@snap
どれを使うにしろ、「クラウド」なのでサーバにとらわれない構成にする必要がある
@snapend

@snap
サービス跨って構築が簡単にできるような構成が一番望ましい
@snapend



---

### 次料金とかやろうかな

---

### ちなみに

---

@snap
このプレゼン作成はGitPitchというの使ってます。
@snapend
@snap
マークダウン方式に弊社は設計書群を全て移行するので、どうせならプレゼン資料もと思い。
@snapend

---
お疲れ様でした。
