# MikroTik Ether1 Durum Takibi ve Telegram Uyarı Sistemi

Bu script, MikroTik RouterOS üzerinde ether1 arayüzünün çalışma durumunu düzenli olarak kontrol eder.
Eğer ether1 arayüzü DOWN olursa, sistem yöneticisini Telegram üzerinden anında uyarır ve aynı zamanda MikroTik log’larına warning kaydı düşer.

# Ne Yapar? 

ether1 arayüzünün aktif (running) durumunu kontrol eder

Arayüz çalışmıyorsa (DOWN) uyarı üretir

Telegram botu aracılığıyla belirlenen kullanıcıya mesaj gönderir

MikroTik log sistemine warning kaydı ekler

# Çalışma Mantığı

ether1 arayüzünün running durumu okunur

Durum false ise:
Log’a uyarı yazılır

Telegram API kullanılarak mesaj gönderilir

# Nasıl Kurulur

# 1.Script Oluşturma  
RouterOS arayüzüne giriş yapın (Winbox veya WebFig)

System → Scripts menüsüne girin

Add New (+) butonuna tıklayın

Script bilgilerini aşağıdaki gibi doldurun:

Name: Ether1Kontrol

Source: Script kodunu yapıştırın

Policy:

 read

 test

(Sorun yaşarsanız write ve policy ekleyebilirsiniz)

Script’i kaydedin

# 2.Otomatik Çalıştırma (Scheduler)

System > Scheduler bölümüne gidin

Yeni bir zamanlayıcı (+) ekleyin:

Name: Ether1Kontrol

Interval: 00:05:00 (istediğiniz sıklığa göre ayarlayın)

On Event:
/system script run scriptin erher1Kontrol
