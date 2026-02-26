# 🚀 VirtualBox Linux Samba Bridge: The "VBOX_E_DND_ERROR" Solution

Bu proje, VirtualBox üzerinde kronikleşen **Drag & Drop (Sürükle-Bırak)** hatasını aşmak amacıyla geliştirilmiş, Windows ve Linux arasında yüksek performanslı bir ağ paylaşım (Samba) çözümüdür.

## 📖 Projenin Hikayesi (The Mission)
Sanal makine üzerinde dosya taşırken karşılaşılan `VBOX_E_DND_ERROR` hatası, basit bir çözüm yerine profesyonel bir ağ altyapısı kurma fırsatına dönüştürülmüştür. Bir MIS öğrencisi olarak, bozuk bir özelliği tamir etmek yerine, daha güvenli ve ölçeklenebilir olan **Samba (SMB)** protokolü tercih edilmiştir.

---

## 🔍 Karşılaşılan Zorluklar ve Çözüm Süreci (Troubleshooting)

### 1. Yetki ve Erişim Hiyerarşisi
**Sorun:** Dosya yapılandırmalarında "Permission Denied" hataları alındı.
**Çözüm:** `sudo` yetkisi ile `chmod 777` ve `chown` komutları kullanılarak dosya sistemi üzerindeki kısıtlamalar kaldırıldı.

<img width="480" alt="Samba Setup Steps" src="https://github.com/user-attachments/assets/321a9060-8f5b-4e71-896d-98d641fd0859" />

### 2. Güvenlik Duvarı (Firewall) Yönetimi
**Sorun:** Portlar kapalı olduğu için erişim sağlanamadı.
**Çözüm:** `ufw allow 445/tcp` komutu ile Samba trafiği için geçiş izni tanımlandı.

<img width="480" alt="Firewall Config" src="https://github.com/user-attachments/assets/e0a4af75-97a5-4e62-aeab-f5cc63dcd459" />

### 3. Veri Bütünlüğü ve Senkronizasyon
**Sorun:** Dosyaların boş görünmesi senkronizasyon şüphelerine yol açtı.
**Çözüm:** `strings` komutu ile terminal üzerinden veri doğrulaması yapıldı.

<img width="734" alt="Data Verification" src="https://github.com/user-attachments/assets/d3846de8-0660-4f7b-9d95-333de8df45a0" />

---

## 🖼️ Projeden Kareler

### Kimlik Doğrulama ve Ağ Erişimi
Windows tarafında Samba sunucusuna giriş ekranı ve başarılı kimlik doğrulaması.

<img width="414" alt="Auth Popup" src="https://github.com/user-attachments/assets/2cf88e72-1513-4663-8f20-ae1b971287df" />

### Final Çıktısı: Windows-Linux El Sıkışması (Handshake)
Oluşturulan `PROJE_TAMAMLANDI.txt` dosyasının iki sistem arasındaki canlı iletimi:

<img width="931" alt="Final Success" src="https://github.com/user-attachments/assets/fe484f84-3999-46cf-ba66-1b647daaaa45" />

---

## 🎓 Kazanımlar
- **Linux Dosya Sistemi** ve mutlak yol mantığı kavrandı.
- **Siber Güvenlik** kapsamında port yönetimi pratik edildi.
- **Samba (SMB)** protokolü ile ağ tabanlı sunucu yönetimi deneyimi edinildi.

## 💡 Nasıl Kullanılır?
1. Sanal makineyi **Bridged Adapter** modunda başlatın.
2. `ip addr` komutu ile sunucu IP adresini öğrenin.
3. Windows'tan `\\<SUNUCU_IP_ADRESI>\OrtakPaylasim` yazarak bağlanın.
