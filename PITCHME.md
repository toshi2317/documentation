### クラウド入門編

2019年3月15日
---


### 目次
* 自己紹介
* クラウドとは
* AWS vs Azure vs GCP


---


### 自己紹介


---


### クラウドとは

---
@snap
クラウド
@snapend
https://www.internetacademy.jp/it/server/server-basic/merit-and-demerit-of-cloud.html

@snap
Paas IaaS
@snapend
https://ec-orange.jp/ec-media/?p=18343

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
IaS的な使い方もPaaS的な使い方もできるため、一歩間違えると難易度の高い構成になって保守性がない。
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

---


### GCPの強み弱み妬み

---
@snap
Googleの各種サービスやYoutube（Google内部）などと連携するREST APIが用意されている
@snapend

@snap
勝手にスケールしてくれる
@snapend

---


### （余談）REST APIって何

---

@snap
Webシステムを外部から利用するためのプログラムの呼び出し規約(API)の種類の一つで、RESTと呼ばれる設計原則に従って策定されたもの。
@snapend

---

### やりがち
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

---

### これがREST（だよね？）
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
https://api.xxx.xxx/v1/order
@snapend
@snap
PUT methodで渡す（更新）
@snapend

@snap
https://api.xxx.xxx/v1/order
@snapend
@snap
DELETE methodで渡す（削除）
@snapend
PATCH
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

### 同じサービスをAWS Azure GCPに立ててみた


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
