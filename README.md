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

### Diğer

* [AdvantageScope 2027 Alpha](AdvantageScope.md)
* [Elastic 2027 Alpha](Elastic.md)

## Alpha 1 Hedefleri

*'Sürüş süresini' Systemcore ile, özellikle Swerve Drive FRC Robotları kullanarak arttırmak.
* Donanım güvenilirliği, kullanım kolaylığı, konektörler ve daha fazlası hakkında geri bildirim sağlamak.
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

USB-C portun, cihaza güç verilmeden önce bağlanırsa, Systemcore flaş modunda girecektir.

### İşletim Sistemi Güncellemelerini Cihaza Yazma (Flashlama)

Alpha sürümü cihazlar 157 kodlu işletim sistemi sürümü yüklü gelir. Eğer yeni başladıysanız bu adımı atlayıp doğrudan programlamaya geçebilirsiniz

[Systemcore Güncelleme -İşletim Sistemini Cihaza Yazma- Eğitim Videosu (60s)](https://player.vimeo.com/video/1095423117)
<details>
<summary>İşletim Sistemi Güncellemelerini Cihaza Yazma (Windows)</summary>

1. Download the latest release from the [systemcore-os-public repository](https://github.com/LimelightVision/systemcore-os-public)
2. Make sure the new [Limelight Hardware Manager 2.0.1](https://downloads.limelightvision.io/software/LimelightHardwareManagerSetup2_0_1.exe) is installed
3. Open Limelight Hardware Manager
3. Navigate to the Flash OS Tab
4. Boot Systemcore into Flash Mode (see 'power' section above). You should see activity in the log window. If you don't see anything, click the 'reinstall drivers' button at .
5. Select an OS .zip or .img to flash. Wait for extraction to complete.
6. Refresh drives and select the one marked as Limelight/Systemcore. 
7. Click the “Flash” Button after it starts flashing.
8. Once complete, remove USB and power from Systemcore


>**Full System Images will take several minutes to flash. Systemcore will soon support fast OTA updates.**

</details>

<details>
<summary>İşletim Sistemi Güncellemelerini Cihaza Yazma (Mac)</summary>

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
<summary>İşletim Sistemi Güncellemelerini Cihaza Yazma (Ubuntu/Debian)</summary>

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

### Exploring On-Robot Telemetry with Elastic and AdvantageScope

[Package Installation Tutorial Video (30s)](https://player.vimeo.com/video/1095497571)

1. Download the Elastic and AdvantageScope IPK packages.
2. Navigate to the web interface.
3. Click the "Add Package" card. 
4. Install one package at a time.
5. Click the new "Elastic" or "AdvantageScope Lite" launch cards.
6. Use Elastic and AdvantageScope as you normally would. A quick way to add live telemetry to your robot is the use of the SmartDashboard API (subject to change soon) ```SmartDashboard.putNumber("key",value);```.
>**Elastic and AdvantageScope Lite packages will soon be pre-baked into the OS**

### Enabling CANivore Support

[Package Installation Tutorial Video (30s)](https://player.vimeo.com/video/1095497571)

1. [Download the CANivore IPK packages.](https://github.com/wpilibsuite/SystemCoreTesting/blob/main/CTR-Phoenix.md#download)
2. Navigate to the web interface.
3. Click the "Add Package" card. 
4. Install the usb-kernel package, and then install the usb package.
5. Powercycle your Systemcore.


### Making Cables

Check the "Mating Connector" Section of the specification sheet and [this github discussion](https://github.com/wpilibsuite/SystemCoreTesting/discussions/11).

### Transitioning from roboRIO
#### I2C

The I2C pinout does not match that of the roboRIO. Cables such as https://www.revrobotics.com/rev-11-1729/?searchid=4554778&search_query=4+wire+i2c will need to be modified - SCL and SDA will need to be swapped. The Systemcore pinout matches the Qwiic / ControlHub pinout.

#### IO

The IO signal pins have a 4.7K pulldown resistor. Limit switches will need to short the SIGNAL pin to the +3.3V pin on Systemcore.
