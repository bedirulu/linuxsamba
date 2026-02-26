🚀 VirtualBox Linux Samba Bridge: The "VBOX_E_DND_ERROR" Solution
Bu proje, VirtualBox üzerinde kronikleşen Drag & Drop (Sürükle-Bırak) hatasını aşmak amacıyla geliştirilmiş, Windows ve Linux arasında yüksek performanslı bir ağ paylaşım (Samba) çözümüdür.

📖 Projenin Hikayesi (The Mission)
Sanal makine üzerinde dosya taşırken karşılaşılan VBOX_E_DND_ERROR hatası, basit bir çözüm yerine profesyonel bir ağ altyapısı kurma fırsatına dönüştürülmüştür. Bir MIS öğrencisi olarak, bozuk bir özelliği tamir etmek yerine, daha güvenli ve ölçeklenebilir olan Samba (SMB) protokolü tercih edilmiştir.

🛠️ Teknik Altyapı ve Gereksinimler
Host OS: Windows 10/11

Guest OS: Ubuntu 24.04 (Linux Foundation LFS101 uyumlu)

Networking: Bridged Adapter (Köprü Bağdaştırıcısı)

Protokol: SMB (Samba)

IP Yapılandırması: Yerel ağ üzerinden atanan dinamik/statik IP

🔍 Karşılaşılan Zorluklar ve Çözüm Süreci (Troubleshooting)
Proje sırasında karşılaşılan teknik bariyerler ve uygulanan "Sistem Analisti" yaklaşımları:

1. Yetki ve Erişim Hiyerarşisi
Sorun: Dosya yapılandırmalarında "Permission Denied" hataları alındı.

Çözüm: sudo yetkisi ile chmod 777 ve chown komutları kullanılarak dosya sistemi üzerindeki kısıtlamalar kaldırıldı.

Görsel Kanıt:  (Klasör oluşturma ve yetkilendirme adımları).

2. NetBIOS İsimlendirme Sınırları
Sorun: testparm kontrolünde "netbios name is too long" uyarısı alındı.

Çözüm: NetBIOS standartları gereği (max 15 karakter) sistem ismi revize edilerek ağda görünürlük sağlandı.

3. Veri Bütünlüğü Doğrulaması (Silent File Errors)
Sorun: Dosyaların 0-byte (boş) görünmesi sebebiyle verinin iletilmediği düşünüldü.

Çözüm: strings komutu kullanılarak dosya içeriği ham veri seviyesinde kontrol edildi ve senkronizasyon doğrulandı.

Görsel Kanıt:  (Strings komutu ile terminal üzerinden veri okuma).

4. Güvenlik Duvarı (Firewall) Yönetimi
Sorun: Portlar kapalı olduğu için erişim sağlanamadı.

Çözüm: ufw allow 445/tcp komutu ile Samba trafiği için geçiş izni tanımlandı.

Görsel Kanıt:

🖼️ Projeden Kareler
Kimlik Doğrulama ve Bağlantı
Samba sunucusuna erişim için gereken kullanıcı adı ve şifre yapılandırması başarıyla test edildi.

Final Çıktısı: Windows-Linux Senkronizasyonu
Başarıyla oluşturulan test dosyasının iki işletim sistemi arasındaki canlı iletimi:

🎓 Kazanımlar
Bu proje sayesinde;

Linux Dosya Sistemi hiyerarşisi kavrandı.

Siber Güvenlik kapsamında port yönetimi ve yetki yükseltme (privilege escalation) pratik edildi.

Samba (SMB) protokolü ile ağ tabanlı sunucu yönetimi deneyimi edinildi.

💡 Nasıl Kullanılır?
Sanal makineyi Bridged Adapter modunda başlatın.

ip addr komutu ile sunucu IP adresini öğrenin.

Windows Dosya Gezgini'ne \\<SUNUCU_IP_ADRESI>\OrtakPaylasim yazarak bağlanın.
