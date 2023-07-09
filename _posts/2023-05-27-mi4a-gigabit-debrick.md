---
layout: post
title: Mi Router 4A Gigabit için Kurtarma ve Stock Yazılıma Dönme Rehberi
description: Mi Router 4A Gigabit için Kurtarma ve Stock Yazılıma Dönme Rehberi
summary: Mi Router 4A Gigabit için Kurtarma ve Stock Yazılıma Dönme Rehberi
date: 2023-05-27 23:00
comments: true
tags: openwrt
minute: 6
--- 

![thumbnail](https://github.com/yucellmustafa/mi-router-4a-debrick/assets/49123562/0dab322d-3b36-40b8-9e96-8a8eca631d02)

Bu yöntem ile Windows üzerinde Mi Router 4A Gigabit cihazlarınızı brick olduğunda kurtarabilecek veya stock yazılımına dönebileceksiniz.  

**Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.** 🙏

<p align="left">
  <a href="https://youtu.be/F7kfNIsIu5U"><img src="https://img.shields.io/badge/Youtube-Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
</p>

# ✨ Başlarken

- Kuruluma başlamadan önce routerımıza ait dosyayı indirelim ve masaüstüne çıkartalım.
    - İngilizce Sürüm: [4A-GIGA-ENG.zip](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.1/4A-GIGA-ENG.zip)
    - Çin Sürüm: [4A-GIGA-CN.zip](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.1/4A-GIGA-CN.zip)

- <details>
  <summary>Windows Ağ ayarlarından Ethernet ip ayarlarını yapalım</summary>

  > Denetim Masası\Ağ ve Internet\Ağ Bağlantıları

  <img src="https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/e24e3dac-4e75-437e-abcd-fcd843ec8f67"/>

- Son olarak routerı ethernet kablosu ile LAN portundan bilgisayarımıza bağlayalım ve güç kablomuzu routera takalım.

# 🚀 Kurtarma veya Stock Yazılıma Dönme

- <details>
  <summary>İlk olarak "Tiny PXE Server" programını açalım. IP adresi ve alttaki dosya adının resimdeki gibi olduğunu kontrol edelim. Doğru ise Online butonuna tıklayalım
  
  (*IP Adresi farklı ise diğer internet bağlantılarınızı kapatın*)</summary>

  <img src="https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/16a44a96-4a88-48a3-9f8d-02cdf369fa00"/>

- Routerın güç bağlantısını keselim.

- Reset tuşuna basılı tutarak güç kablosunu takalım. Led turuncu yanıp yanıp sönecektir. Tiny PXE Server programında bilgi ekranında yazılar kayacaktır.

- Turuncu led sabit bir şekilde yanmaya başladıktan sonra 10 saniye daha reset tuşuna basılı tutalım. Daha sonra reset tuşundan elimizi çekebiliriz.

- 5-10 dakika arasında ledler maviye dönecek ve sabit bir şekilde yanmaya başlayacaktır.

- İşlemlerin bittiğinden emin olduktan sonra Tiny PXE Server programındaki Offline butonuna basalım ve programı kapatalım.

- Daha sonra Ağ ayarlarında yaptığımız değişiklikleri eski haline almayı unutmayalım.

- Artık [192.168.31.1](http://192.168.31.1) adresinden router arayüzüne girerek gerekli kurulumları yapabilirsiniz.

- **Tebrikler kurtarma işlemi veya stock yazılım kurulumunu tamamladınız.** 👏👏

# 💖 Özel Teşekkürler
- Yardımlarından dolayı [@DogukanYNK](https://github.com/DogukanYNK)'a teşekkürler.
- Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.

# 🗃️ Kaynaklar
- [Hoddys Guides](https://hoddysguides.com/xiaomi-debrick-tools-all/)

-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
