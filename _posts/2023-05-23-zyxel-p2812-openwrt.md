---
layout: post
title: ZyXEL P-2812HNU-F1 için OpenWRT Kurulum Rehberi!
description: ZyXEL P-2812HNU-F1 için OpenWRT Kurulum Rehberi! 
summary: ZyXEL P-2812HNU-F1 için OpenWRT Kurulum Rehberi!
date: 2023-05-23 23:00
comments: true
tags: openwrt
minute: 15
--- 

![thumbnail](https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/332f5f41-1433-4839-8464-75fa2b844c34)

Bu yöntem ile Windows üzerinde ZyXEL P-2812HNU-F1 modeminize OpenWRT kurabileceksiniz.  

**OpenWRT kurulumunda oluşabilecek tüm komplikasyonlar sizin sorumluluğunuzdadır.**  

**Rehberimizi kaynak göstererek paylaşmanız önemle rica olunur.** 🙏

<p align="left">
  <a href="https://youtu.be/3NRZ06BoXCM"><img src="https://img.shields.io/badge/Youtube-Kurulum Video Rehberi-blue?logo=youtube&logoColor=white"/></a>
</p>
  

# ⚙️ Cihaz Özellikleri

- CPU: 500 Mhz Lantiq XWAY VRX288 (PSB 80920)
- DSL: Lantiq (PSB 80190)
- RAM: 128 MB (Samsung veya ProMOS V59C1G01168QBJ25)
- FLASH: 128 MB (Samsung K9F1G08U0D-SCB0)
- WI-FI: RaLink RT3062f 300 Mbps b/g/n
- PORT: 4 adet Gigabit LAN, 1 adet Gigabit WAN, 2 adet USB 2.0

# 🧰 Gerekli Malzemeler
- <details>
  <summary>ZyXEL P-2812HNU-F1</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/7fc65d77-1f57-4f8a-9003-6f398af3d8cc"/>
  </details>

- <details>
  <summary>Ethernet Kablosu</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/4a8732fd-f2fe-43d1-b53d-abbb5851714c"/>
  </details>

- <details>
  <summary>PL2303 USB TO TTL Kablo</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/30141ec2-75e7-428a-9db8-eed2b6bca5fc"/>
  </details>

# 💻 Gerekli Programlar
Aşağıdaki programları önceden kuralım.

- PL2303 Driver - [İndir](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/1-PL2303_Driver.exe)

- TeraTerm - [İndir](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/2-Teraterm-4.106.exe)

- Tftpd64 - [İndir](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/3-Tftpd64-4.64.exe)

- WinSCP - [İndir](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/4-WinSCP-5.21.7.exe)

# ✨ Başlarken

- Kuruluma başlamadan önce [OpenWRT.zip](https://github.com/yucellmustafa/yucellmustafa.github.io/releases/download/v1.0/openwrt.rar) dosyamızı indirelim ve masaüstüne çıkartalım.

- <details>
  <summary>Dosyalara ait resim</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/37bb289e-9b1c-4370-b664-db8223f9da96"/>
  </details>

- <details>
  <summary>Windows Ağ ayarlarından Ethernet'imize statik ip atayalım</summary>

  > Denetim Masası\Ağ ve Internet\Ağ Bağlantıları

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/fabd0c78-ce0d-43cf-aecd-32db26b4c642"/>
  </details>

- <details>
  <summary>Modemin içini açalım ve anten kablolarını dikkatlice çıkartıp kartı elimize alalım</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/95f29e74-a4ef-44fd-abe8-8c33c61f09f9"/>
  </details>

- <details>
  <summary>Kartın arka yüzündeki serial dişlerine PL2303 kablomuzu şekildeki gibi bağlayalım</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/e7ceec98-bc9f-4a2e-a2a4-bf45e73a99a6"/>
  
  (Tekli : Siyah) - Yeşil - Beyaz - (Kırmızıyı bağlama)

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/a533fd82-8392-434a-aaa9-7e51ed8b0c95"/>
  </details>

- Son olarak modemi ethernet kablosu ile LAN portundan bilgisayarımıza bağlayalım ve güç kablomuzu modeme takalım. **Ama modem kapalı durumda olsun.**

- <details>
  <summary>Son hali resimdeki gibi olmalıdır</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/83979089-e13b-4b2e-9322-97a7c31b59c8"/>
  </details>


# 🚀 OpenWRT Kurulumu

- <details>
  <summary>İlk olarak "TeraTerm" programını açın Serial portunuzu seçin, "Setup / SerialPort" kısmından "speed'i 115200" ayarlayın</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/53a575c2-8efe-4daf-b658-2d938128d737"/>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/172624c2-6a6d-47e6-8a5f-facf3a83edfe"/>
  </details>

- <details>
  <summary>Şimdi iletken bir madde ile R17 yazan lehimli yeri kısa devre yaptırırken modemi güç tuşuna basarak çalıştıralım</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/9720016c-9f63-4631-a1ae-f7cc175b1ea5"/>
  </details>


- Modemi açtığımızda TeraTerm programında modemin UART moduna girdiğini gösteren alttaki yazıyı göreceğiz

  ```
  ROM VER: 1.0.5
  CFG 02
  UART
  ```
- Şimdi cihaz UART modunda iken TeraTerm programından **"File" "Send File"** kısmından **u-boot.asc** dosyasını seçin.

- U-Boot yüklemesi bittiğinde aşağıdaki komutu girin

  ```
  nand erase.chip
  ```

- <details>
  <summary>Tftp programını açın aşağıdaki gibi ayarlayın uygulama altta beklesin</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/bab17f97-3ee2-4406-ad55-8e62d181328e"/>
  </details>

- TeraTerm programına aşağıdaki komutları sırayla girin:
  ```
  tftpboot openwrt-lantiq-p2812hnufx_nandtpl-u-boot-16M-patch.img

  nand write 0x81000000 0x0 0x38985
  ```

- Modemi kapatın. Modem kapandıktan sonra tekrar açalım ve **TeraTerm** programında görünen **autoboot** işlemini herhangi bir tuşa basarak durdurun.

- Aşağıdaki komutları TeraTerm programına girelim. 

  <details>
  <summary>XX:XX:XX:XX:XX:XX yazan yere modemin arka yüzündeki etikette yazan MAC adresini yazınız</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/542616e2-61ab-418d-a43b-1ca51752da03"/>
  </details>

  ```
  mtdparts add nand0 256k uboot

  mtdparts add nand0 128k uboot-env

  mtdparts add nand0 3m kernel

  mtdparts add nand0 - ubi

  setenv ethaddr XX:XX:XX:XX:XX:XX

  setenv nboot 'nand read 0x80800000 0x60000 0x300000; bootm 0x80800000'

  setenv bootcmd 'run nboot'

  saveenv

  tftpboot openwrt-22.03.0-rc1-lantiq-xrx200-zyxel_p-2812hnu-f1-initramfs-kernel.bin

  bootm $fileaddr

  ```

- Modem yeniden başlayacak. Akan yazılar durduğunda "Enter" tuşuna basalım. OPENWRT diye yazı göreceksiniz.

- Modemin arayüzüne [192.168.1.1](http://192.168.1.1) adresinden giriş yapalım. 

  **username: root ve şifresi yoktur**. Direkt **Login** butonuna tıklayalım.

- Arayüze girdikten sonra üst panelden **System > Backup / Flash Firmware** kısmına girelim.

  En aşağıdaki **Flash image..** butonuna tıklayalım. Açılan pencereden **Browse** butonuna tıklayarak **openwrt-22.03.0-rc1-lantiq-xrx200-zyxel_p-2812hnu-f1-squashfs-sysupgrade.bin** doyasını seçelim.

  **Keep Settings** tikini kaldıralım ve dosyayı kuralım. Kurulum bittiğinde cihaz yeniden başlayacak.

- Modeme OpenWRT kurduk ama wifi driverı olmadığı için şuan modemin wifisi çalışmamaktadır.

  <details>
  <summary>WinSCP programı ile modemin ana dizinine giriş yapalım.</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/df4c4127-6850-45b7-9696-7b322a3a0ca9"/>
  </details>

  <details>
  <summary>/lib/firmware klasörünün içine RT3062.eeprom dosyasını sürükleyerek atalım</summary>

  <img src="https://github.com/yucellmustafa/yucellmustafa.github.io/assets/49123562/f31dec94-0536-4ffc-82ac-2c66fd10b2a4"/> 
  </details>

- **VDSL** bağlantısı WinSCP programınan aynı şekilde **/etc/config/network** dosyasını açın. Aşağıda verdiğim satırdaki **dsl0** yazan satırı bulup **dsl0.35** olarak düzenleyin (diğer kısımlara dokunmayın):

  ```
  config interface 'wan'
    option ifname 'dsl0'
    option proto 'pppoe'
    option username 'XXXXXXXXX@XXXXXXXX.net'
    option password 'XXXXXXXX'
    option ipv6 '1'
  ```

  Düzenledikten sonraki hali:
  ```
  config interface 'wan'
    option ifname 'dsl0.35'
    option proto 'pppoe'
    option username 'XXXXXXXXX@XXXXXXXX.net'
    option password 'XXXXXXXX'
    option ipv6 '1'
  ```

- Modem yeniden başladığında **wifi açılmama sorununu** çözmek için modem arayüzünden **System > Startup** kısmına ve oradan da **Local Startup** kısmına girelim. 

  Çıkan ekrandaki yazıların hepsini aşağıdaki gibi düzenleyelim ve **Save** butonuna basarak kaydedilim:

  ```
  # Put your custom commands here that should be executed once
  # the system init finished. By default this file does nothing.
  echo 1 > /sys/bus/pci/rescan
  exit 0
  ```

- Modem bir kere yeniden başlatalım ve istediğiniz diğer ayarları yapınız. 

- **Tebrikler OpenWRT kurulumunu tamamladınız.** 👏👏

# 💖 Özel Teşekkürler
Yazdığı güzel readme'den örnek aldığım için [@frudotz](https://github.com/frudotz)'a teşekkürler.  

# 🗃️ Kaynaklar
- [OpenWRT Wiki](https://openwrt.org/toh/zyxel/p-2812hnu-f1)
- [Zyxel P-2812HNUL-F1 Modeme Openwrt Kurma Rehberi - Donanım Haber Forum](https://forum.donanimhaber.com/zyxel-p-2812hnul-f1-modeme-openwrt-kurma-rehberi--134393534)

-----------
🎀 Rehberimizi okuduğunuz için teşekkür ederiz!  
