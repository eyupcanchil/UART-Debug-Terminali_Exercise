Güzel, README'yi yazıyorum:

STM32 Embedded Roadmap — Faz 2: UART Debug Terminali (FTDI232 + Blue Pill)
Hakkında
Bu proje, gömülü sistemler alanında kendimi geliştirmek amacıyla oluşturduğum STM32 Roadmap'imin Faz 2'sindeki ilk çalışmadır. Amacım teorik bilgiyi gerçek donanım üzerinde uygulayarak pekiştirmek ve profesyonel gömülü yazılım geliştirme alışkanlıkları edinmektir.
Bu Çalışmadaki Amacım
ST-Link olmadan Blue Pill'i FTDI232 üzerinden hem programlamayı hem de gerçek zamanlı UART debug terminalini kullanmayı öğrenmek. Mikrodenetleyicinin içinde ne olduğunu dışarıya konuşturabilmek, gömülü sistemlerde debug'ın temel taşıdır. Bu çalışma o temeli atmak için tasarlanmıştır.
Kullanılan Donanım

STM32F103C8T6 (Blue Pill)
FTDI232 USB-UART dönüştürücü modülü
Passive buzzer (17mm, 80dB)
82Ω direnç
Breadboard ve jumper kablo

Kullanılan Yazılım

STM32CubeIDE 1.18
STM32CubeMX (CubeIDE içinde)
STM32CubeProgrammer 2.17.0
PuTTY (UART terminal)

Nasıl Çalışır
FTDI232, Blue Pill'in UART1 pinlerine (A9 TX, A10 RX) bağlanır. Çip UART bootloader moduna alınarak (BOOT0=1) STM32CubeProgrammer üzerinden flash'lanır. Çalışmaya başlayınca TIM2 PWM çıkışı üzerinden passive buzzer üç farklı frekansta (1000 Hz, 2000 Hz, 500 Hz) ötürülür. Her bip sırasında UART üzerinden bilgisayara mesaj gönderilir, PuTTY terminalinde gerçek zamanlı olarak izlenir.
UART Çıktısı
Sistem baslatildi
[BIP 1] 1000 Hz
[BIP 2] 2000 Hz
[BIP 3] 500 Hz
Öğrendiklerim

FTDI232'nin USB-UART köprüsü olarak çift görev yapması (flash + debug)
STM32 UART bootloader ile ST-Link olmadan programlama
HAL ile UART transmit ve printf yönlendirmesi
TIM2 PWM ile frekans kontrolü
Gömülü sistemlerde debug terminalinin önemi

