# Oled kütüphane

---

- [açıklamalar](#açıklamalar)
- [işlevler](#işlevler)
- [Kullanım](#kullanım)
- [kod-blokları](#kod-blokları)
  - [setup](#setup)
  - [temel](#temel-öğeler)
  - [mod sınıfı](#mod-sınıfı)
  - [geometri sınıfı](#geometri-sınıfı)
  - [arkaplan sınıfı](#arkaplan-sınıfı)
  - [font sınıfı](#font-sınıfı)
  - [ayarlar sınıfı](#ayarlar-sınıfı)
  - [bitmap sınıfı](#bitmap-sınıfı)

---

## açıklamalar

---

- bu kütüphane şimdilik sadece 128x64 oled ekranlar içindir.
- uno nano ve nodemcu(esp8266) ile denenmiştir
- bellek tüketimi ve işlemler optimizedir
- çok dar projelerde bellek tasarrufu için sadece sil yaz güncelle fonksiyonları kullanılması önerilir

---

## işlevler

---

- türkçe karakterleri destekler
- bitmap vs çizimi için standart prosedür
- ekran için ayarlamalar
- hazır ekran stilleri, hazır uygulamalar
- modlu yazım şekilleri ile hızlı gruplama

---

## Kullanım

---

- zip indirip veya projeyi remote ile çekip dosyayı proje klasörüne ekleyin. ardından `OLED_LIB.h` dosyasını import edip nesnenizi tek bir dosyadan oluşturun.

```cpp
#include "OLED_LIB.h"
oled ekran; //ekran adında nesne
void setup(){
    ekran.kur(); // buffer başlatıldı bu işlem tekrarlı yapılmamalı bellek kaplar
}
void loop(){
    ekran.sil();                    //tamamen siler
    ekran.yaz(millis(),ORTA,ORTA);  // x ve y ekseninde ortalanmış şekilde millis değerini yaz
    ekran.guncelle();               // ekranı günceller
}
```

- h dosyalarında extern ile belirtmeli ve dış dosyalardan h dosyasındaki aracı ile bağlantı kurmanız gerekir

```h
#pragma once
extern oled ekran; //cpp deki tanıma referans verdik her yerde bellek oluşturmak projeyi çökertir
```

---

## kod blokları

---

### setup

```cpp

 ekran.kur() // (I2C baslat, buffer olustur)

```

### temel öğeler

```
ekran.sil()                         // (buffer temizle)
ekran.yaz("metin", x, y)            //(string yaz)
ekran.yaz(sayi, x, y)               // (int yaz)
ekran.yaz(sayi, x, y, hassasiyet)   // (float yaz)
ekran.guncelle()                    // (buffer ekrana gonder, en son cagir)
ekran.bitmap_ciz(x, y, genislik, yukseklik, veri)
```

### mod sınıfı

```
ekran.mod.saat(x, y, ss, dk)        //(ss:dk formatinda)
ekran.mod.saat(x, y, ss, dk, sn)    //(ss:dk:sn formatinda)
ekran.mod.saat_orta(x, y, ss, dk)   //(orta boy)
ekran.mod.saat_buyuk(x, y, ss, dk)  //(buyuk boy)
ekran.mod.tarih(x, y, gun, ay, yil)
ekran.mod.yaz("metin", sayi, x, y)  //(yazi + sayi beraber)
ekran.mod.altSatira_ortali_yaz(...)
```

### geometri sınıfı

```
ekran.geometri.nokta_ciz(x, y)
ekran.geometri.nokta_sil(x, y)
ekran.geometri.yay_ciz(cx, cy, r, baslangic_aci, bitis_aci)
ekran.geometri.cizgi.ciz.yatay(x, y, uzunluk)
ekran.geometri.cizgi.ciz.dikey(x, y, uzunluk)
ekran.geometri.cizgi.ciz.cizgi\_(x0, y0, x1, y1)
ekran.geometri.cizgi.sil.yatay(x, y, uzunluk)
ekran.geometri.cizgi.sil.dikey(x, y, uzunluk)
ekran.geometri.cerceve.ici_dolu.dikdortgen_ciz(x, y, h, w)
ekran.geometri.cerceve.ici_dolu.cember_ciz(mx, my, r)
ekran.geometri.cerceve.ici_dolu.ucgen_ciz(x0,y0, x1,y1, x2,y2)
ekran.geometri.cerceve.ici_dolu.elips_ciz(cx, cy, a, b)
ekran.geometri.cerceve.ici_bos.dikdortgen_ciz(x, y, h, w, kalinlik)
ekran.geometri.cerceve.ici_bos.cember_ciz(mx, my, r, kalinlik)
ekran.geometri.cerceve.ici_bos.elips_ciz(cx, cy, a, b, kalinlik)
```

### arkaplan sınıfı

```cpp
ekran.arkaplan.paragraf_goruntuleyici(metin, azaltici, artirici) // uzun metin için kaydırmalı ekran oluşturur azaltici ve artirici değerleri için buton vs koyabilirsiniz
```

### Font sınıfı

```cpp
ekran.font.sec.yazi()       //(standart yazi fontu)
ekran.font.sec.minikSayi()  //(kucuk sayi fontu)
ekran.font.sec.buyukSayi()  //(buyuk sayi fontu)
```

### ayarlar sınıfı

```cpp
ekran.ayarla.ekran_ac()
ekran.ayarla.ekran_kapa()
ekran.ayarla.ters_cevir()           //(ekrani 180 derece cevir)
ekran.ayarla.renkleri_ters_cevir()  //(negatif mod)
ekran.ayarla.renkleri_normale_cevir()
```

### Bitmap sınıfı

```cpp
ekran.ayarla.bitmap.okuma_mod_yatay()
ekran.ayarla.bitmap.okuma_mod_dikey()
ekran.ayarla.bitmap.aynalama_x()
ekran.ayarla.bitmap.aynalama_y()
ekran.ayarla.bitmap.aynalama_xy()
ekran.ayarla.bitmap.donme_90()
ekran.ayarla.bitmap.donme_180()
ekran.ayarla.bitmap.donme_270()
ekran.ayarla.bitmap.ayarlari_sifirla()
```

---
