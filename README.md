# Kablosuz Ekran Yansıtma: Scrcpy Kurulum ve Kullanım Kılavuzu

Bu kılavuz, Android telefonunuzu kablosuz olarak bilgisayarınıza yansıtmak için scrcpy aracını kurmayı ve kullanmayı adım adım açıklamaktadır. Kılavuz, herhangi bir USB bağlantısı olmadan, yalnızca yerel ağ üzerinden yansıtma yapmayı içerir.
Gereksinimler

    Bilgisayarınızda yüklü ADB (Android Debug Bridge) ve scrcpy
    Telefon ve bilgisayarın aynı Wi-Fi ağına bağlı olması
    USB hata ayıklama seçeneğinin aktif olduğu bir Android telefon

## Kurulum Adımları
### 1. ADB ve Scrcpy Kurulumu

Linux

	sudo apt update
	sudo apt install adb scrcpy

Windows

    ADB ve scrcpy’yi kurmak için scrcpy GitHub sayfasından Windows kurulum dosyalarını indirin.
    İndirilen dosyaları çıkarın ve adb ve scrcpy çalıştırılabilir dosyalarının sisteme tanımlı olduğundan emin olun.

macOS

	brew install android-platform-tools scrcpy

### 2. Telefonunuzda USB Hata Ayıklama Özelliğini Etkinleştirme

    Telefonunuzda Geliştirici Seçenekleri’ni açın:
        Ayarlar > Telefon Hakkında > Yapı Numarası'na 7 kez arka arkaya dokunun.
        Geliştirici Seçenekleri artık Ayarlar menüsünde görünmelidir.
    USB hata ayıklamayı etkinleştirin:
        Ayarlar > Geliştirici Seçenekleri > USB hata ayıklama’yı etkinleştirin.

### 3. Telefona USB ile Bağlanma ve Kablosuz Hata Ayıklamayı Etkinleştirme

    Telefonunuzu USB ile bilgisayara bağlayın.

    Terminal veya Komut İstemi açın ve cihazın bağlı olup olmadığını kontrol edin:

adb devices

Çıktıda cihazınızı görüyorsanız, bağlantı başarılıdır.

Cihazı kablosuz hata ayıklama için hazırlamak amacıyla şu komutu çalıştırın:

    adb tcpip 5555

    USB bağlantısını kesin.

### 4. Kablosuz Bağlantı Sağlama

    Telefonunuzun IP adresini öğrenin:
        Ayarlar > Wi-Fi > Bağlı olduğunuz ağın ayarları > IP Adresi.
        Örnek IP adresi: 192.168.1.11

    Terminal veya Komut İstemi’ne geri dönerek, kablosuz bağlantıyı kurmak için şu komutu kullanın:

    adb connect 192.168.1.11:5555

    Not: IP adresinizi kendi cihazınızın adresiyle değiştirin.

    Cihazın başarılı bir şekilde bağlanıp bağlanmadığını doğrulamak için adb devices komutunu tekrar çalıştırın. Çıktıda cihazınızın IP adresi ile birlikte görünüyor olmalıdır.

### 5. Scrcpy’yi Başlatma

Artık scrcpy’yi başlatıp ekranınızı yansıtabilirsiniz:

scrcpy

Ekran kablosuz olarak bilgisayarınıza yansıtılacaktır. Bu adımlar başarıyla tamamlandığında, Android cihazınızı kablosuz bir bağlantı üzerinden kontrol edebilir ve görüntüleyebilirsiniz.
Ek Komutlar ve Problemler
Bağlantıyı Sonlandırma

Kablosuz bağlantıyı kesmek için:

adb disconnect

Yeniden USB Bağlantısı Gerektiğinde

Eğer kablosuz hata ayıklamayı yeniden etkinleştirmeniz gerekiyorsa, yukarıdaki adımları USB bağlantısı ile tekrarlayın.
Sık Karşılaşılan Sorunlar

    Bağlantı Sağlanamıyor: Telefon ve bilgisayarın aynı Wi-Fi ağına bağlı olduğundan emin olun.
    adb Komutu Bulunamadı: adb komutunun sistem PATH'ine eklendiğinden emin olun veya komutu tam yolu ile çalıştırın.
    Ses Aktarımı: scrcpy görüntü aktarımı yapar, ses aktarımı yapmaz. Ses aktarmak için sndcpy gibi ek araçlar kullanılabilir.

Bu kılavuz, scrcpy ile Android cihazınızı kablosuz olarak bilgisayarınıza yansıtma sürecinde size rehberlik etmelidir.
