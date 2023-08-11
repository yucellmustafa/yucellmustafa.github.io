---
layout: post
title: Mi Router 4C için OpenWRT Kurulum Rehberi
description: Mi Router 4C için OpenWRT Kurulum Rehberi
summary: Mi Router 4C için OpenWRT Kurulum Rehberi
date: 2023-08-11 11:15
comments: true
tags: openwrt
minute: 7
--- 

![thumbnail](https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/98a1cd62-27c3-434a-a992-076d6007c1eb)

Bu yöntem ile Windows üzerinde Mi Router 4C cihaza OpenWRT kurabileceksiniz.  

**OpenWRT kurulumunda oluşabilecek tüm komplikasyonlar sizin sorumluluğunuzdadır.**  

**Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.** 🙏

<p align="left">
  <a href="https://youtu.be/kd4OVsMiQYE"><img src="https://img.shields.io/badge/Youtube-Kurulum Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
</p>
  

# ⚙️ Cihaz Özellikleri

- CPU: 580 Mhz MediaTek MT7628AN
- RAM: 64 MB
- FLASH: 16 MB
- 2.4 GHz Wifi: MT7628AN
- PORT: 3 adet 100 Mbps LAN/WAN

# 💻 Gerekli Program ve Dosyalar
Aşağıdaki programları önceden kuralım.

- Firmware - [sysupgrade](https://firmware-selector.openwrt.org/?version=22.03.5&target=ramips%2Fmt76x8&id=xiaomi_mi-router-4c) olanı indirelim ve ismini `sysupgrade.bin` yapalım.

- TeraTerm - [İndir](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/2-Teraterm-4.106.exe)

- OpenWRTInvasion - [İndir](https://github.com/acecilia/OpenWRTInvasion)

- Python3 - [İndir](https://www.python.org/downloads/)

# 🚀 OpenWRT Kurulumu

- Cihazı LAN portundan bilgisayara bağladıktan sonra [192.168.31.1](http://192.168.31.1/) adresinden ilk kurulumu yapın.

- `OpenWRTInvasion` klasöründe komut satırını başlatıp gerekli python kütüphanelerini aşağıdaki komutla yükleyiniz.

  ```
  pip3 install -r requirements.txt
  ```

- Daha sonra aşağıdaki komutla `Telnet` serverini aktif edelim.

  ```
  python remote_command_execution_vulnerability.py
  ```

- Çıktıya aşağıdaki cevapları verelim.
  ```
  Router IP address: 192.168.31.1
  Enter router admin password: <Wifi Şifresi>

  There two options to provide the files needed for invasion:
    1. Use a local TCP file server runing on random port to provide files in local directory `script_tools`.
    2. Download needed files from remote github repository. (choose this option only if github is accessable inside router device.)

  Which option do you prefer? (default: 1) 1
  ```

- `Telnet` serveri aktif olmuştur.

- "TeraTerm" programını açın ve şu şekilde cihaza bağlanın

  ![teraterm](https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/01b8e2d8-06d5-4f0f-b599-d8e9f2d53b6f)

- Giriş için alttaki bilgileri girelim
  
  ```
  XiaoQiang login: root
  Password: root
  ```

- Python ile http serveri açalım: `python -m http.server`

- Daha sonra kullanıcı ana klasörüne sysupgrade.bin dosyasını atalım.

- Alttaki komutları girerek http serverinden dosyayı cihaza çekelim ve yazılımı cihaza kuralım:

  ```
  cd /tmp
  wget http://<IP adresiniz>:8000/sysupgrade.bin
  mtd -r write sysupgrade.bin OS1
  ```

- Mavi ışık sabitlendiğinde kurulum tamamlanmıştır. Eğer sabitlenmez ve mavi ışık yanıp yanıp sönmeye devam ederse cihazı kendimiz yeniden başlatalım.

- [192.168.1.1](http://192.168.1.1/) adresinden arayüze girerek gerekli kurulumu yapın ve kullanmaya başlayınız.

- **Tebrikler OpenWRT kurulumunu tamamladınız.** 👏👏

# 💖 Özel Teşekkürler
- Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.

# 🗃️ Kaynaklar
- [OpenWRT Wiki](https://openwrt.org/toh/xiaomi/xiaomi_mi_router_4c)

---
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
