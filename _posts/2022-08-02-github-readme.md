---
layout: post
title: GitHub Profile Readme
description: Github Profile Readme dosyanız için kullanmak isteyebileceğiniz öğeler 
summary: Github Profile Readme'niz için Ogeler
date: 2022-08-02 11:00
comments: true
minute: 8
---

Github projelerimizde inceleyenlerin anlaması için readme (benioku) dosyaları oluştururuz. Aynı şekilde profilimizi ziyaret edenler için de profil readme dosyası oluşturarak kendimiz hakkında bilgi verebiliriz. 

Bu blogda github readme'nize eklemek isteyeceğiniz öğelerden bahsedeceğim. 

**Profile Readme'si oluşturmak istiyorsanız kullanıcı adınızla aynı isimde olan bir repo oluşturarak bunu yapabilirsiniz.**

## RSS ile Blog Postlar

![rss](https://user-images.githubusercontent.com/49123562/182309097-59abb400-ea6d-410d-8d95-89bf2085e1de.jpg)

[Proje Repository](https://github.com/gautamkrishnar/blog-post-workflow)

Blog yazıyorsanız bu tam sizin için. Blog sitenizin RSS akışını readme dosyanıza ekleyerek profilinizi ziyaret edenlere postlarınızı sitenize gitmeden gösterebileceksiniz.

Kullanmak için tüm yapmanız gereken profile readme repo'nuza giriniz. Ve aşağıdaki adımları takip ediniz:

![blog](https://user-images.githubusercontent.com/49123562/182314711-f1164dab-e15c-40ea-8a92-b7c16749e1a6.gif)

Actions > New > Simple Workflow > Configure kısma giriniz. Başlığa istediğinizi yazabilirsiniz. Kod kısmına alttaki kodu ekleyiniz. 

```
name: Latest blog post workflow
on:
  schedule:
    - cron: '0 * * * *'
  workflow_dispatch:

jobs:
  update-readme-with-blog:
    name: Update this repo's README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Blog Post Workflow
        uses: gautamkrishnar/blog-post-workflow
        with:
          feed_list: "https://yucellmustafa.dev/atom.xml"
```

**Not: feed_list kısmını kendi RSS akışınız ile değiştiriniz.**

Son olarak readme'nizde bloglarınızın görünmesini istediğiniz yere alttaki kodu eklemelisiniz.

```
<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->
```

## Hesap İstatistikleri

![stats](https://user-images.githubusercontent.com/49123562/182316630-57a8af1d-8557-49c4-a4c8-5c0b723f853d.jpg)

[Proje Repository](https://github.com/anuraghazra/github-readme-stats)

Profilinizi ziyaret edenler için **commit, pull request, issues, contribut ve kullandığınız programlama dilleri** gibi bilgilerinizi grafikler ile gösterebilirsiniz. 
Bunun için alttaki kodları kullanabilirsiniz.

```
<details>
<summary>:bulb: Github Stats</summary>
<img src="https://github-readme-stats.vercel.app/api?username=yucellmustafa&theme=tokyonight&count_private=true&show_icons=true&include_all_commits=true" >
</details>

<details>
<summary>:bulb:  Most Used Languages</summary>
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=yucellmustafa&theme=tokyonight&layout=compact&count_private=true&langs_count=8" >
</details>
```

**Not: src tag'inde bulunan username kısmına kendi kullanıcı adınızı giriniz. Ayrıca details tag'i ile gizleme özelliği ekledik.**

## Spotify Son Oynatılanlar

![spotify](https://user-images.githubusercontent.com/49123562/182318515-79159bcb-53d4-4813-be09-a8c852c0ff8f.jpg)

[Proje Repository](https://github.com/JeffreyCA/spotify-recently-played-readme)

Spotify'da son dinlediğiniz müziği gösterebilirsiniz. Eğer hiç bir şey dinlemiyorsanız en son dinlediğiniz müzik ve en son ne zaman dinlediğiniz görünüyor.

Kullanımı oldukça basittir. 

Projeye Spotify hesabınızı [buradan bağlayınız](https://spotify-recently-played-readme.vercel.app)

Kodu readme'nize ekleyerek kullanabilirsiniz.

```
![Spotify recently played](https://spotify-recently-played-readme.vercel.app/api?user=jeffreyca16&count=1)
```

**Not: user kısmına Spotify kullanıcı adınızı yazınız. Kaç tane müzik görünmesini istiyorsanız count kısmını değiştiriniz**

## Gif ve  Icon

![gif](https://user-images.githubusercontent.com/49123562/182306502-93efd01c-8ccc-4d76-a1bd-ac9f383dc46b.gif)

#### Gif
Gif kullanarak readme dosyanıza hareketlilik katabilirsiniz. 

Örnek site: [giphy.com](https://giphy.com)

Aşağıdaki örnekte img tagiyle sayfanın yarısına gif ekleyebilirsiniz.

```html
<img src="https://media.giphy.com/media/2nUnDhdX4CLjW/giphy.gif" alt="" align="right" width=50% height=50%>
```

#### Icon
Sosyal medya adreslerinizi, sitelerinizi ve diğer bağlantılarınızı yazılara linklemek yerine kolayca anlaşılacak iconlara linkleyerek güzel ve sade bir görüntü oluşturabilirsiniz. 

Örnek site: [simpleicons.org](simpleicons.org)

Aşağıdaki örnekte src tag'ine icon'un linkini ve href tag'ine linklemek istediğiniz (sosyal medya vs.) bağlantıyı değiştirerek kullanabilirsiniz.

```html
<a href="https://gist.github.com/yucellmustafa"><img width=50 src="https://www.vectorlogo.zone/logos/github/github-tile.svg" /></a>
```
