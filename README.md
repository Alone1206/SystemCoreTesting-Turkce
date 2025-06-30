# SystemCore Test
## BU DOKÜMAN ORİJİNİAL DOSYADAN TÜRKÇEYE ÇEVRİLMİŞTİR. GÜNCEL OLMAYABİLİR. LÜTFEN EN GÜNCEL BİLGİ İÇİN ANA REPO'YA BAKINIZ.
Bu belgedeki çeviri revizyonlarını ---  adresinde görebilirsiniz.

Systemcore ve Motioncore cihazlarının Alfa ve Beta testleri için oluşturulumuş bir repodur.


2027 WPILib değişiklikleri, yeni özellikler vb. için tüm güncel belgeleri WPILib Docs sitesinin '2027' sürümünde bulabilirsiniz: https://docs.wpilib.org/en/2027/.


>**Burada yayınlanan dosya ve kodlar, 2027 sezonu için Alpha sürümüdür, Control Hub ve roboRIO ile uyumlu değildir**

![SystemcoreTopHousing](https://ik.imagekit.io/llimi/controlsystem/tophousingcrop)

[Systemcore Özellikler PDF - İngilizce](https://downloads.limelightvision.io/documents/systemcore_specifications_june15_2025_alpha.pdf)

>**Alfa sürümü cihazların soketlerini belirten etiketleri yoktur**
![SystemcoreUnboxing](https://ik.imagekit.io/llimi/controlsystem/scunboxing.png)

## Beta Yazılımlar

### Araçlar

[2027 WPILib Yükleyici]( https://packages.wpilib.workers.dev/installer/v2027.0.0-alpha-1/)

[Limelight Hardware Manager 2.0.1 - Limelight Donanım Yöneticisi 2.0.1](https://downloads.limelightvision.io/software/LimelightHardwareManagerSetup2_0_1.exe)

[İşletim Sistemi Sürümleri, Paket Örnekleri, Çapraz Derleme Örnekleri](https://github.com/LimelightVision/systemcore-os-public)

### Üretici Kütüphaneleri

* [CTR Electronics Phoenix 6](CTR-Phoenix.md)
* [REV Robotics](REV.md)
* [AdvantageKit](AdvantageKit.md)
* [ChoreoLib](ChoreoLib.md)

### Diğer

* [AdvantageScope 2027 Alpha](AdvantageScope.md)
* [Elastic 2027 Alpha](Elastic.md)

## Alpha 1 Hedefleri

*'Robotların -özellikle swerve sürüş sisttemli olanların- olabildiğince çok ve süre boyunca sürülmesini sağlamak.
* Donanım güveilirliği, kullanım kolaylığı, konektörler ve daha fazlası hakkında geri bildirim sağlamak.
* Mümkün olduğunca çok sayıda kafa karışıklığı ve hayal kırıklığı yaratabilecek noktayı ortadan kaldırmak.

## Systemcore Hızlı Başlangıç

|  |  |
|---------|-------|
| Dahili Wi-Fi Erişim Noktası SSID | SYSTEMCORE |
| Dahili Wi-Fi Erişim Noktası Parolası | PASSWORD |
| Systemcore Wi-Fi Erişim Noktası IP | 172.30.0.1 |
| Systemcore USB IP (Windows) | 172.28.0.1 |
| Systemcore USB IP (Linux, Mac) | 172.29.0.1 |
| Varsayılan Kullanıcıadı | systemcore |
| Varsayılan Şifre | systemcore |
| USB Arabirimleri için Varsayılan Bağlama Konumları (Atanan Konumlar) | /U, /V ...|
| CAN Bus Arayüz Adları | can_s0, can_s1, can_s2, can_s3, can_s4 |

### Güç Açma

Systemcore'unuzu robotunuzun güç dağıtım cihazına (PDP, PDH) bağlayın. 18AWG kablo ile beyaz renk Weidmuller ferrül kullanmanızı öneririz.

Her iki güç girişini (Köprü (4 pinli motioncore soketi) + Weidmuller) aynı anda kullanmayın.

### Güncelleme Modu - Flash Modu

USB-C portundan pc'ye kablo, Systemcore'a güç verilmeden önce bağlanırsa, Systemcore flaş modunda girecektir.

### İşletim Sistemi Güncellemelerini Cihaza Yazma (Flashlama)

Alpha sürümü Systemcorelar 157 kodlu işletim sistemi sürümü yüklü gelir. Eğer yeni başladıysanız bu adımı atlayıp doğrudan programlamaya geçebilirsiniz

[Systemcore Güncelleme -İşletim Sistemini Systemcore'a Yazma- Eğitim Videosu (60s)](https://player.vimeo.com/video/1095423117)
<details>
<summary>İşletim Sistemi Güncellemelerini Systemcore'a Yazma (Windows)</summary>

1. En son sürümü indirin [systemcore-os-public repository](https://github.com/LimelightVision/systemcore-os-public)
2. Bilgisayarınızda yeni [Limelight Hardware Manager 2.0.1 - Limelight Donanım Yöneticisi 2.0.1](https://downloads.limelightvision.io/software/LimelightHardwareManagerSetup2_0_1.exe)'nin yüklü olduğundan emin olun.
3. Limelight Donanım Yöneticisini (Limelight Hardware Manager) açın.
3. Flash OS Sekmesini açın.
4. Systemcore'u flash moduna sokun (yukarıdaki 'Güncelleme Modu' bölümüne bakın). Log penceresinde yeni satırlar oluşması lazım. Olmadıysa, 'reinstall drivers' (sürücüleri yeniden yükle) düğmesine tıklayın.
5. Flaşlamak için bir işletim sistemi .zip veya .img dosyası seçin. Dosya çıkarma işleminin tamamlanmasını bekleyin.
6. Sürücüleri yenileye basın  ve Limelight/Systemcore yazanı seçin. 
7. Yanıp sönmeye başladıktan sonra “Flash” butonuna tıklayın.
8. Tamamlandığında, Systemcore'dan USB-C'yi çıkarın ve gücünü kesin.

>**Tam işletim ssitemi dosyalarının flaşlanması (cihaza yazılması) birkaç dakika sürecektir. Systemcore yakında hızlı OTA güncellemelerini destekleyecektir.**

</details>

<details>
<summary>İşletim Sistemi Güncellemelerini Systemcore'a Yazma (Mac)</summary>

1. Download [Balena Etcher](https://etcher.balena.io/).
2. Spin-up RPIBoot:
    ```
    brew install libusb
    brew install pkg-config
    git clone --recurse-submodules --shallow-submodules --depth=1 https://github.com/raspberrypi/usbboot
    cd usbboot
    make
    cd mass-storage-gadget64
    sudo ../rpiboot -d .
    ```
3. Boot Systemcore into Flash Mode.
4. Flash with Etcher.

</details>

<details>
<summary>İşletim Sistemi Güncellemelerini Systemcore'a Yazma (Ubuntu/Debian)</summary>

1. Download [Balena Etcher](https://etcher.balena.io/).
2. Spin-up RPIBoot:
    ```
    apt update
    apt install libusb-1.0-0-dev pkg-config build-essential
    git clone --recurse-submodules --shallow-submodules --depth=1 https://github.com/raspberrypi/usbboot
    cd usbboot
    make
    cd mass-storage-gadget64
    sudo ../rpiboot -d .
    ```
3. Boot Systemcore into Flash Mode.
4. Flash with Etcher.

</details>

> **Yeni Donanım Yöneticisi yakında platformlar arası çalışabilecek.**

> **Tarayıcı tabanlı bir işletim sistemi güncelleme özelliği geliştirme aşamasındadır.**

### Web Arayüzüne Erişim ve Takım Numaranızı Ayarlama

1. Systemcore'u normal şekilde başlatın.
2. USB, Ethernet veya Wi-Fi üzerinden bağlanın
3. Bir web tarayıcınızda http://robot.local adresine gidin.
4. Yapılandırma sekmesinde takım numaranızı ayarlayın ve kırmızı "Change Team Number" (Türkçesi Takım Numarasını Değiştir) butonuna tıklayın.

![](https://ik.imagekit.io/llimi/controlsystem/teamnumber.png)

6. NI DriverStation'a da aynı takım numarasını girin
7. Bu noktad artık NI DriverStation'ın Systemcore ile iletişim kurması gerekir.

![](https://ik.imagekit.io/llimi/controlsystem/dsconnectivity.png)

### Wi-Fi Yapılandırması

157 kodlu işletim sistemi sürümü varsayılan bir Wi-Fi kanalı seçer. Bu, parazit (interferans) nedeniyle bazı ortamlarda sorunlara neden olabilir. Daha iyi bir bağlantı için kanal yapılandırmasını 'otomatik' olarak değiştirin ve frekansı 5Ghz olarak ayarlayın.

### İlk Robot Kodunuzu Systemcore'a Yükleme

1. Systemcore çalıştırın ve bağlantı kurun.
2. WPILIB 2027'nin kurulu olduğundan emin olun.
3. '2027_alpha1 WPILib VS Code'u açın
4. MNormalde yaptığınız gibi yeni bir WPILib projesi oluşturun ve proje oluşturma adımında takım  numarasını girdiğinizden emin olun.
5. Projeyi normalde yaptığınız gibi robota yükleyin (Shift + F5).
6. NI DriverStation robot kodunun yüklldiğini göstermelidir (Robot Code seçeneği yeşile dönmelidir).

![](https://ik.imagekit.io/llimi/controlsystem/dscode.png)

7. Artık robotu etkinleştirmeye (enable) hazırsınız.
8. Bu yeni projeyle ilk testinizi yaptıktan sonra, VS Code'a geri dönebilir ve mevcut robot kodlarınızı açabilirsiniz. Bu, Importer'ı devreye sokup eski projenizi 2027'ye transfer etmenizi sağlayacak ekranı getirmelidir. (Eski projeyi 2027'sürmüne taşımak ister misiniz şeklinde uyarı çıkıyor.)

###  Robot Telemetrisini Elastic ve AdvantageScope ile İnceleme

[Package Installation Tutorial Video (30s)](https://player.vimeo.com/video/1095497571)

1. Elastic ve AdvantageScope IPK paketlerini indirin.
2. Web arayüzünü açın.
3. "Paket Ekle" (Add Package) seçeniğine tıklayın.
4. Paketleri teker teker kurun.
5. Yeni belirecek "Elastic" veya "AdvantageScope Lite" başlatma seçennklerine tıklayın.
6. Elastic ve AdvantageScope'u normalde kullandığınız gibi kullanın. Robotunuza canlı telemetri eklemenin hızlı bir yolu, SmartDashboard API'ını kullanmaktır (bu yöntem yakında değişebilir): ```SmartDashboard.putNumber("key",value);```.
>**Elastic ve AdvantageScope Lite paketleri yakında işletim sistemine gömülü olarak gelecektir.**

### CANivore Desteğini Etkinleştirme

[Paket Kurulumu Videosu (30sn)](https://player.vimeo.com/video/1095497571)

1. [CANivore IPK paketlerini indirin..](https://github.com/wpilibsuite/SystemCoreTesting/blob/main/CTR-Phoenix.md#download)
2. Web arayüzünü açın.
3. "Paket Ekle" (Add Package) seçeneğine tıklayın.
4. Önce usb-kernel paketini, ardından usb paketini kurun.
5. Sytemcore cihazınızın gücünü kesip yeniden vererek yeniden başlatın (powercycle).


### SystemCore Uyumlu Kablolar

Cihazın teknik özellik dosyasındaki ("specification sheet") "Eşleşen Konnektör" (Mating Connector) bölümünü veya [bu forumu](https://github.com/wpilibsuite/SystemCoreTesting/discussions/11) inceleyebilirisiniz.

### RoboRio'dan Systemcore'a Geçereken...

#### I2C

I2C pin dizilimi roboRIO'nunkiyle aynı değildir. https://www.revrobotics.com/rev-11-1729/?searchid=4554778&search_query=4+wire+i2c gibi kabloların modifiye edilmesi gerekecektir - SCL ve SDA pinlerinin yerleri değiştirilmelidir. Systemcore pin dizilimi, Qwiic / ControlHub pin dizilimi ile uyumludur.

#### IO

IO sinyal pinlerinde 4.7K'lık bir pulldown (aşağı çeken) direnç bulunur. Limit anahtarlarının ("limit switch"), Systemcore üzerindeki SIGNAL pinini +3.3V pinine kısa devre yapması gerekli.
