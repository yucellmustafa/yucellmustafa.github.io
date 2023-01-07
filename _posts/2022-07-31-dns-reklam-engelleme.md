---
layout: post
title: DNS ile Reklam Engelleme
description: DNS kullanarak android ve bilgisayarda programsız reklam engelleme
summary: DNS kullanarak android ve bilgisayarda programsız reklam engelleme

date: 2022-07-31 20:00
comments: true
minute: 5
---

Bildiğiniz üzere artık reklamlardan dolayı istediğimiz içeriği göremez olduk. Bunun için program kullanmadan DNS ile reklam engellemeyi anlatacağım. 

## Android 9 ve üzeri

Android 9 ve üzeri ile gelen "Private DNS (Özel DNS)" özelliği telefonun tamamında (Uygulama Reklamları dahil) gelen veriyi filtreleyerek reklamları engelliyor.

Not: Vodefone, DoT (DNS-over-TLS) engellediği için private DNS Vodafone ile kullanılamıyor.

**Kullanım:**

**Telefon Ayarları > Diğer Bağlantılar veya Bağlantı Ayarları > Gizli DNS > Gizli DNS'i Yapılandır**

Deafult: `dns.adguard-dns.com`

Aile: `family.adguard-dns.com`

Filtresiz: `unfiltered.adguard-dns.com`

![Screenshot_20220731_184254_com android settings~2](https://user-images.githubusercontent.com/49123562/182036048-922bb27c-d6e9-45ed-860c-df8e058d43b3.jpg)

## Bilgisayar ve Android Tarayıcıları

Tarayıcılarda DoH (DNS-over-HTTPS) kullanarak tarayıcı reklamlarını engelleyebiliyoruz. 

**Kullanım:**

**Chrome ayarlar > Gizlilik ve Güvenlik > Güvenli DNS kullan > Başka bir sağlayıcı seçin**

Default: `https://dns.adguard-dns.com/dns-query`

Aile: `https://family.adguard-dns.com/dns-query`

Filtresiz: `https://unfiltered.adguard-dns.com/dns-query`

![Screenshot_20220731_184239_com android chrome~2](https://user-images.githubusercontent.com/49123562/182036046-d3ea7b6a-f742-46b5-8ac4-b80b68d14fc9.jpg)

Not: Chrome'un bilgisayar sürümünde de aynısını yaparak bilgisayarınızda da tarayıcı reklamlarını filtreleyebilirsiniz.

Artık gönül rahatlığı ve sakinlikle tarayıcı kullanabilirsiniz :)
