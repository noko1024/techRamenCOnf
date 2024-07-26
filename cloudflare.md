---
marp: true
title: cloudflareでおうちDCを軽率に生産する
math: mathjax
author: Yuhei KOBAYASHI @noko1024
paginate: true
footer: "cloudflareでおうちDCを軽率に生産する"
---

<style>
@import 'default';
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP&display=swap');


:root {
  --color-back: rgb(245, 249, 250);
}

footer {
    color: rgb(200, 200, 200);
    width: 100%;
}

section h1 {
    color: rgb(62, 166, 230);
    border-bottom: 1px solid #ccc;
    line-height: 1.5em;
}

section h2,h3,h4 {
    color: #575858
}


section a:link {
    color: rgb(150, 200, 220);
}

</style>

# cloudflare でおうち DC を軽率に生産する

![height:100](https://techramenconf.net/logo.png)

_Yuhei KOBAYASHI / noko1024_

![bg right:20% height:200](https://github.com/noko1024.png)

---

# 自己紹介

小林 侑平 / こばさん

釧路工業高等専門学校 創造工学科
電気工学分野 5 年

出身: 帯広

ネットワークを愛でる
最近は Rails で外貨を稼いでいます
![bg right height:400](img/router.png)

---

# おことわり

- 誤りがあったらごめんなさい
- 各サービスのあくまで一例を挙げたもので、もっとポテンシャルがあります
- 個人的な見解であり、所属する会社、組織とは全く関係ありません
- 勢いでいきます

---

# まず、

---

# 家にサーバーってありますよね(断定)

NAS とかラズパイとか...

---

# "一般のご家庭" 共通の悩み

- サーバーの余剰リソースを使ってあげたい
- 快適な開発環境をどこでも,どんな OS でも使いたい
- 外に持ち出す機材にセキュアな情報を入れるの怖い
- (もっとステータスランプを光らせたい)

---

# ご安心ください、cloudflare で概ね解決できます

\ ﾍﾟｶｰ /

## ![height:350 center](https://cf-assets.www.cloudflare.com/slt3lc6tev37/7bIgGp4hk4SFO0o3SBbOKJ/b48185dcf20c579960afad879b25ea11/CF_logo_stacked_blktype.jpg)

---

# おしながき

1. サーバーを Cloudflare Tunnel / WARP Connector で繋げる
2. クライアントを WARP で繋げる
3. お気に入りの環境をつくる

---

# サーバーを Cloudflare と繋げる

---

# Cloudflare Tunnel

ポート開放せずに SSH や RDP を公開できる
Tunnel は接続したマシン内を外部に公開することが主目的
`Private Network` を設定することで
所属するネットワークの他端末にも通信可能
![height:300](https://developers.cloudflare.com/assets/private-ips-diagram_hua0d86fa4f03f384bde81e46921dab3a3_510169_2530x1144_resize_q75_box_3-BNgTlWj7.png)

---

# WARP Connector

**まだ beta!**
Tunnel と違い Warp Connector 同士で LAN を結ぶことが目的
cloudflared を実行できない IoT 機器などもサポート
![](https://developers.cloudflare.com/assets/overview_hu75672f4459c770020727438732d586aa_22548_985x340_resize_q75_box_3-DWwPQmHB.png)

---

# クライアントを WARP で繋げる

---

# WARP Client

---

# 実践してみる
