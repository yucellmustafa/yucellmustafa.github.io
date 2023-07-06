---
layout: post
title: Mi WiFi Mini R1C için OpenWRT Kurulum Rehberi
description: Mi WiFi Mini R1C için OpenWRT Kurulum Rehberi
summary: Mi WiFi Mini R1C için OpenWRT Kurulum Rehberi
date: 2023-07-04 01:20
comments: true
tags: openwrt
minute: 7
--- 
# Xiaomi Mi WiFi Mini R1C için OpenWRT Kurulum Rehberi!

![thumbnail](https://github.com/yucellmustafa/openwrt_mi_mini_wifi_r1c/assets/49123562/f0709d50-0f31-4eea-9fb8-f898e9e0f3c7)

Bu yöntem ile Windows üzerinde Xiaomi Mi WiFi Mini R1C routerımıza OpenWRT kurabileceksiniz.  

**OpenWRT kurulumunda oluşabilecek tüm komplikasyonlar sizin sorumluluğunuzdadır.**  

**Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.** 🙏

<p align="left">
  <a href="https://www.youtube.com/watch?v=kj5yrLwNauw"><img src="https://img.shields.io/badge/Youtube-Kurulum Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
</p>
  

# ⚙️ Cihaz Özellikleri

- CPU: 580 Mhz MediaTek MT7620A
- RAM: 128 MB
- FLASH: 16 MB
- 2.4 GHz Wifi: MediaTek MT7620A
- 5 GHz Wifi: MediaTek MT7612EN
- PORT: 3 adet 100 Mbps LAN/WAN, 1 adet USB 2.0

# 💻 Gerekli Program ve Dosyalar
Aşağıdaki programları önceden kuralım.

- Firmware - [sysupgrade](https://firmware-selector.openwrt.org/?version=22.03.5&target=ramips%2Fmt7620&id=xiaomi_miwifi-mini) olanı indirelim.
  - *Bu cihaza kuracağımız yazılım dosyasıdır. İsteğe bağlı sürümü seçip sysupgrade dosyasını indirelim.*

- TeraTerm - [İndir](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/releases/download/1.0/2-teraterm-4.106.exe)

# 🚀 OpenWRT Kurulumu

- İndirdiğimiz Firmware dosyasını boş bir usb bellek içine atalım ve cihazın usb portuna takalım.

- Cihazı LAN portundan bilgisayara bağladıktan sonra [192.168.31.1](http://192.168.31.1/) adresinden ilk kurulumu yapın.
  
- Tarayıcının adres çubuğuna aşağıdaki adımları uygulayarak telnet'i etkinleştirelim.

- `http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/xqnetwork/set_wifi_ap?ssid=whatever&encryption=NONE&enctype=NONE&channel=1%3B%2Fusr%2Fsbin%2Ftelnetd`

  - *`<STOK>` yazan yer ilk kurulumu yapınca görülecektir. Sizde farklı olacaktır. Örneğin: `9c2428de4d17e2db7e5a6a337e6f57a3`*

  - Üstteki kodu yazınca bu kodu çıktı vermeli: `{"msg":"Couldn't connect to this network(Probe timeout)","code":1616}`

- `http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/xqsystem/set_name_password?oldPwd=<CURRENTPASS>&newPwd=<NEWPASS>`

  - *`<CURRENTPASS>` ilk kurulumda verilen şifredir. `<NEWPASS>` ise yeni verilecek şifredir.*

  - Üstteki kodu yazınca bu kodu çıktı vermeli: `{"code":0}`

- "TeraTerm" programını açın ve şu şekilde cihaza bağlanın

  ![teraterm](https://github.com/yucellmustafa/openwrt-zyxel-p2812hnu-f1/assets/49123562/1a19a762-c0b9-4720-b243-6da46b747dfa)

- Giriş için alttaki bilgileri girelim
  
  ```
  XiaoQiang login: root
  Password: <NEWPASS>
  ```
  *`<NEWPASS>` yukarıda yeni verdiğin şifredir. Örneğin: `12345678`*

- Firmware dosyasını flashtan cihaza aktaralım: `cp /extdisks/sda1/<file-name> /tmp/<file-name>`
  - *`<file-name>` kısmı yazılım dosyasının adıdır. Örneğin `openwrt-22.03.5-ramips-mt7620-xiaomi_miwifi-mini-squashfs-sysupgrade.bin`*

- Kurulumu yapalım: `mtd -r write /tmp/<file-name> OS1`
  - *`<file-name>` kısmı yazılım dosyasının adıdır. Örneğin `openwrt-22.03.5-ramips-mt7620-xiaomi_miwifi-mini-squashfs-sysupgrade.bin`*

- Mavi ışık sabitlendiğinde kurulum tamamlanmıştır. Eğer sabitlenmez ve mavi ışık yanıp yanıp sönmeye devam ederse cihazı kendimiz yeniden başlatalım.

- [192.168.1.1](http://192.168.1.1/) adresinden arayüze girerek gerekli kurulumu yapın ve kullanmaya başlayınız.

- **Tebrikler OpenWRT kurulumunu tamamladınız.** 👏👏

# 💖 Özel Teşekkürler
- Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.

# 🗃️ Kaynaklar
- [OpenWRT Wiki](https://openwrt.org/toh/xiaomi/miwifi_mini)
-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
