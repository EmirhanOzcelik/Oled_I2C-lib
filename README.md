# Oled kütüphane

---

- [açıklamalar](#açıklamalar)
- [işlevler](#işlevler)
- [kod-blokları](#kod-blokları)

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

## kod blokları

---

### Tek Seferlik

- ekran.kur() (I2C baslat, buffer olustur)

---

### Dongu İcinde

- ekran.sil() (buffer temizle)
- ekran.yaz("metin", x, y) (string yaz)
- ekran.yaz(sayi, x, y) (int yaz)
- ekran.yaz(sayi, x, y, hassasiyet) (float yaz)
- ekran.mod.saat(x, y, ss, dk) (ss:dk formatinda)
- ekran.mod.saat(x, y, ss, dk, sn) (ss:dk:sn formatinda)
- ekran.mod.saat_orta(x, y, ss, dk) (orta boy)
- ekran.mod.saat_buyuk(x, y, ss, dk) (buyuk boy)
- ekran.mod.tarih(x, y, gun, ay, yil)
- ekran.mod.yaz("metin", sayi, x, y) (yazi + sayi beraber)
- ekran.mod.altSatira_ortali_yaz(...)
- ekran.geometri.nokta_ciz(x, y)
- ekran.geometri.nokta_sil(x, y)
- ekran.geometri.yay_ciz(cx, cy, r, baslangic_aci, bitis_aci)
- ekran.geometri.cizgi.ciz.yatay(x, y, uzunluk)
- ekran.geometri.cizgi.ciz.dikey(x, y, uzunluk)
- ekran.geometri.cizgi.ciz.cizgi\_(x0, y0, x1, y1)
- ekran.geometri.cizgi.sil.yatay(x, y, uzunluk)
- ekran.geometri.cizgi.sil.dikey(x, y, uzunluk)
- ekran.geometri.cerceve.ici_dolu.dikdortgen_ciz(x, y, h, w)
- ekran.geometri.cerceve.ici_dolu.cember_ciz(mx, my, r)
- ekran.geometri.cerceve.ici_dolu.ucgen_ciz(x0,y0, x1,y1, x2,y2)
- ekran.geometri.cerceve.ici_dolu.elips_ciz(cx, cy, a, b)
- ekran.geometri.cerceve.ici_bos.dikdortgen_ciz(x, y, h, w, kalinlik)
- ekran.geometri.cerceve.ici_bos.cember_ciz(mx, my, r, kalinlik)
- ekran.geometri.cerceve.ici_bos.elips_ciz(cx, cy, a, b, kalinlik)
- ekran.arkaplan.paragraf_goruntuleyici(metin, azalt, artir)
- ekran.bitmap_ciz(x, y, genislik, yukseklik, veri)
- ekran.guncelle() (buffer ekrana gonder, en son cagir)

---

### Font Secimi

- ekran.font.sec.yazi() (standart yazi fontu)
- ekran.font.sec.minikSayi() (kucuk sayi fontu)
- ekran.font.sec.buyukSayi() (buyuk sayi fontu)

---

### Ekran Kontrol

- ekran.ayarla.ekran_ac()
- ekran.ayarla.ekran_kapa()
- ekran.ayarla.ters_cevir() (ekrani 180 derece cevir)
- ekran.ayarla.renkleri_ters_cevir() (negatif mod)
- ekran.ayarla.renkleri_normale_cevir()

---

### Bitmap Ayarlari

- ekran.ayarla.bitmap.okuma_mod_yatay()
- ekran.ayarla.bitmap.okuma_mod_dikey()
- ekran.ayarla.bitmap.aynalama_x()
- ekran.ayarla.bitmap.aynalama_y()
- ekran.ayarla.bitmap.aynalama_xy()
- ekran.ayarla.bitmap.donme_90()
- ekran.ayarla.bitmap.donme_180()
- ekran.ayarla.bitmap.donme_270()
- ekran.ayarla.bitmap.ayarlari_sifirla()

---
