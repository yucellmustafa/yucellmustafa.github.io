---
layout: post
title: ADB ile Android Sistem Uygulamalarını Silme
description: Android telefonlarda yüklü gelen ve silinemeyen gereksiz uygulamaların bilgisayar aracılığıyla silinmesi
summary: Android telefonlarda yüklü gelen ve silinemeyen gereksiz uygulamaların bilgisayar aracılığıyla silinmesi
tags: android
date: 2022-07-30 19:30
comments: true
minute: 7
---

Bildiğimiz üzere çoğu telefonda gereksiz birçok silinemeyen uygulama (Google apps :) mevcut. Rootlu telefonlarda bilgisayarsız bir şekilde uygulama ile siliniyor. Ama rootsuz telefonlarda bu daha farklı şekillerde yapılıyor. 

Bilgisayar ile gereksiz uygulamaları sileceğiz. Bunun için **Android Debugging Bridge (ADB)** driverı kullanacağız. 

**Not:** ADB driver'ı bilgisayarsız (local) olarak kullanmanın yolu da var ama denemedim. Google Play'den [LADB - Local ADB Shell](https://play.google.com/store/apps/details?id=com.draco.ladb) programını kullanarak deneyebilirsiniz. (Geliştirici seçeneklerden wifi debug açmanız gerekiyor)

Şimdi bilgisayar için ADB driver kurulumunu Linux, MacOS ve Windows için anlatacağım. 

## ADB Driver Kurulumu
### Linux 
Repoları güncelleyelim ve ADB driver kuralım:

Ubuntu
```
sudo apt update && sudo apt upgrade && sudo apt install android-tools-adb
```

Fedora
```
sudo dnf update && sudo dnf upgrade && sudo dnf install android-tools
```

Arch
```
sudo pacman -Syu android-tools
```

### MacOS
Homebrew kuralım:
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

ADB Driver kuralım:
```
brew install android-platform-tools
```

### Windows
ADB minimal portable olarak [indirmek için tıkla](https://androidfilehost.com/?fid=962187416754459552)

İndirdigimiz dosyayı herhangi bir dizine çıkartalım.

Daha sonra **adb.exe** olan klasörde herhangi bir yere "shift + mouse sağ tık" yapalım. Açılan pencereden 'Komut Pencersini Burada Aç' benzeri buton çıkacak ve ona tıklayalım. 

## USB Debug Modunu Aktif Etme
İnternette aratarak telefonunuzun geliştirici seçeneklerini aktif ediniz ve Geliştirici Seçeneklerden **USB Hata Ayıklama** modunu aktif edelim. 

Telefonu bilgisayara bağladıktan sonra telefon üzerinden Bilgisayara Erişim İznini verelim.

Eğer "Yanlızca Şarj" seçeneğinde bilgisayar telefonu görmüyorsa modları değiştirmeyi deneyin.

## ADB Shell Kullanım
Telefonu ADB Shell üzerinden kontrol edelim.
```
adb devices
```

Komutu girdikten sonra ID adresi ile birlikte bir cihaz görünmesi gerekiyor. 

Daha sonra shell'i başlatalım.
```
adb shell
```

Telefonda kurulu olan paketleri listeleyelim.
```
pm list packages
```

Paket araması yapmak.
```
pm list packages | grep google
```

Google kelimesi geçen paketleri gösterir. 

**Not: Paket isimlerini daha kolay görmek için [Package Name Viewer 2.0](https://play.google.com/store/apps/details?id=com.csdroid.pkg) uygulamasını kullanabilirsiniz**


İstediğimiz uygulamayı silelim.
```
pm uninstall -k --user 0 package-name
```

Örneğin Google uygulamasını silelim:
```
pm uninstall -k --user 0 com.google.android.googlequicksearchbox
```

Success yazısını görmüşseniz kaldırma başarılıdır :)


Sildiğiniz uygulamaları kolayce yeniden yüklemek.
```
pm install-existing package-name
```

Örneğin Google uygulamasını yeniden yükleyelim:
```
pm install-existing com.google.android.googlequicksearchbox
```

Sonuna kadar okuduğunuz için teşekkürler :)
