# Pisi Linux Dark

**Türkçe** · [English](README.en.md)

KDE Plasma 6 için hazırlanmış koyu renkli masaüstü teması. Pisi Linux'un kurumsal kimliğini Plasma masaüstüne taşıyan tema; koyu gri tonları üzerine turkuaz vurgu rengi kullanır ve duvar kağıdı, renk şeması, açılış (splash) ekranı, kilit ekranı ve oturum kapatma ekranlarını tek bir pakette birleştirir.

![Pisi Linux Dark önizleme](usr/share/plasma/look-and-feel/pisilinux-dark/contents/previews/preview.png)

## İçerik

Depo, dosyaları doğrudan yerleşim yollarıyla (`usr/share/...`) içerir; böylece hem elle kopyalanabilir hem de paketleyiciler tarafından olduğu gibi kullanılabilir.

| Bileşen | Yol |
|---|---|
| Plasma masaüstü teması | `usr/share/plasma/desktoptheme/pisilinux-dark/` |
| Görünüm ve his (Look-and-Feel) paketi | `usr/share/plasma/look-and-feel/pisilinux-dark/` |
| Renk şeması (`PisilinuxDark.colors`) | `usr/share/color-schemes/` |
| Duvar kağıdı (2.4.4, 1280x1024 – 3840x2160) | `usr/share/wallpapers/pisilinux-2.4.4-wallpaper/` |

### Masaüstü teması

`widgets/` altında Plasma bileşenlerinin (panel arka planı, düğmeler, kaydırma çubukları, görev çubuğu, araç ipuçları, liste öğeleri, sekme çubuğu, medya denetleyicisi vb.) SVGZ grafikleri bulunur. `dialogs/` altında ise iletişim kutularının arka planı yer alır.

### Görünüm ve his paketi

Tek seferde tutarlı bir görünüm kuran varsayılanlar (`contents/defaults`):

- **Renk şeması:** `PisilinuxDark`
- **Pencere dekorasyonu:** Breeze
- **Araç takımı (widget) stili:** Breeze
- **Simge teması:** Kora
- **İmleç teması:** Mevlana
- **Duvar kağıdı:** Pisi Linux 2.4.4

### Ekranlar

- **Açılış ekranı (splash):** `contents/splash/` — Pisi Linux arka planı ve animasyonlu `Pisi.gif` logosu.
- **Kilit ekranı:** `contents/lockscreen/` — `LockScreen.qml`, `LockScreenUi.qml`, `MainBlock.qml`, `ChangeSession.qml` ve `LockOsd.qml`. Arka plan olarak paket içindeki `lockscreen/background.png` kullanılır.
- **Oturum kapatma ekranı:** `contents/logout/` — Plasma 6 API'sine uyarlanmış, Breeze tabanlı `Logout.qml`, `LogoutButton.qml` ve geri sayım için `timer.js`. Varsayılan olarak 30 saniyelik geri sayım sonunda seçili eylem uygulanır.
- **Önizlemeler:** `contents/previews/` — Sistem Ayarları'nda gösterilen `preview.png`, `lockscreen.png` ve `splash.png`.
- **Diğer:** `osd/`, `runcommand/`, `userswitcher/`, `windowswitcher/` ve `desktopswitcher/` Breeze düzenleri üzerine Pisi Linux görselleriyle hazırlanmıştır.

### Renk paleti

| Rol | Renk |
|---|---|
| Vurgu / seçim | `#1F9CCB` (turkuaz) |
| Pencere arka planı | `#34383E` |
| Görünüm arka planı | `#2C3036` |
| Düğme arka planı | `#4A4E55` |
| Normal metin | `#E8EAED` |
| Bağlantı | `#6DB2D6` |
| Negatif / pozitif / nötr | `#E06E6E` / `#7EC88C` / `#E0B25C` |

## Depo yapısı

```
usr/share/
├── color-schemes/PisilinuxDark.colors
├── plasma/
│   ├── desktoptheme/pisilinux-dark/     # Plasma masaüstü teması (SVGZ)
│   └── look-and-feel/pisilinux-dark/    # Global tema, splash, kilit ve çıkış ekranları
└── wallpapers/pisilinux-2.4.4-wallpaper/
```

## Gereksinimler

- KDE Plasma 6 (tema `X-Plasma-API 5.0`, Look-and-Feel `X-Plasma-APIVersion 2` kullanır)
- `plasma-workspace` — kilit ve çıkış ekranlarının kullandığı `org.kde.plasma.private.sessions` modülü için
- Breeze görünüm ve his bileşenleri (`org.kde.breeze.components`) ve Breeze pencere dekorasyonu
- Tam görünüm için isteğe bağlı: `kora` simge teması, `Mevlana` imleç teması

## Kurulum

### Sistem geneli

```sh
sudo cp -r usr /
```

Ardından Plasma'yı yeniden başlatın veya oturumu kapatıp açın:

```sh
kquitapp6 plasmashell && kstart plasmashell
```

### Yalnızca kullanıcı için

```sh
mkdir -p ~/.local/share
cp -r usr/share/plasma ~/.local/share/
cp -r usr/share/color-schemes ~/.local/share/
cp -r usr/share/wallpapers ~/.local/share/
```

### Etkinleştirme

**Sistem Ayarları → Görünüm** bölümünden:

1. **Genel Görünüm (Global Theme):** `pisilinux-dark` seçip uygulayın. Renk şeması, duvar kağıdı, splash ve kilit ekranı birlikte gelir.
2. **Renkler:** `PisilinuxDark`
3. **Masaüstü Teması:** `Pisi Linux Dark`
4. **Açılış Ekranı:** `pisilinux-dark`
5. **Duvar Kağıdı:** `pisilinux 2.4.4`

Tek tek uygulamak yerine yalnızca renk şemasını denemek için:

```sh
plasma-apply-colorscheme PisilinuxDark
```

veya tüm global temayı uygulamak için:

```sh
lookandfeeltool -a pisilinux-dark
```

## Kaldırma

```sh
sudo rm -rf /usr/share/plasma/desktoptheme/pisilinux-dark \
            /usr/share/plasma/look-and-feel/pisilinux-dark \
            /usr/share/color-schemes/PisilinuxDark.colors \
            /usr/share/wallpapers/pisilinux-2.4.4-wallpaper
```

Kullanıcıya özel kurulum yaptıysanız aynı yolları `~/.local/share` altında silin.

## Sürüm notları

- Kilit ekranındaki geçersiz `components/artwork/background.png` referansı kaldırıldı; arka plan artık paket içindeki `lockscreen/background.png` dosyasından yükleniyor.
- Plasma 5 tabanlı oturum kapatma ekranı, Plasma 6 uyumlu Breeze bileşenleriyle yeniden yazıldı (`Logout.qml`, `LogoutButton.qml`, `timer.js`).
- Önizleme görselleri (`preview.png`, `lockscreen.png`) güncellendi.

## Paketleme notları

Depo, `usr/` kök yapısını koruduğu için `/` dizinine açılarak kurulabilir. Pisi Linux için `pspec.xml`/`actions.py` tabanlı paketleme yapılacaksa `usr/` ağacı olduğu gibi `$install_dir` içine kopyalanmalı, `metadata.json` dosyalarındaki sürüm alanları paket sürümüyle eşitlenmelidir.

## Katkıda bulunanlar

- **Erkan İŞİK** — tema bakımı, renk şeması ve Plasma 6 uyarlaması (`erkanisik@pisilinux.org`)
- **Smokey** — Look-and-Feel paketinin temel aldığı çalışma
- **Murat Özgün** — Pisi Linux 2.4.4 duvar kağıdı

## Lisans

Depo kökündeki `LICENSE` dosyası **GNU GPL v3** metnini içerir. Masaüstü teması ve Look-and-Feel paketi GPLv3, duvar kağıdı LGPLv3 olarak işaretlenmiştir. Yeniden dağıtımda ilgili bileşenin `metadata.json` dosyasındaki lisansı esas alın.

Oturum kapatma ekranı QML dosyaları KDE Breeze projesinden türetilmiştir ve `GPL-2.0-or-later` lisansı altındadır; dosya başlarındaki SPDX başlıkları korunmuştur.
