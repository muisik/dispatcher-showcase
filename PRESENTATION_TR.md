# Dispatcher — Paylaşım metni

Bir süredir geliştirdiğim Dispatcher'ın mühendislik PoC'sini toparladım.

Bu örnekte DeepSeek Flash'a sınırları açık bir kod görevi verdim. Gerçek API ajanı
ayrı bir Git worktree'de kaynak dosyasını düzeltti. Bağımsız doğrulayıcı yamayı
temiz bir checkout'a uyguladı ve beş kabul testini yeniden çalıştırdı: tamamı geçti.

İki kontrol de var: hatalı hesap testlerden kalıyor; korunan testleri değiştirerek
geçmeye çalışan aday kapsam ihlalinden reddediliyor. Bu iki aday deterministik;
modelin davranışı olarak sunulmuyor.

Showcase reposunda 24 saniyelik GIF, ekran görüntüleri, gerçek örnek patch'i,
test çıktısı ve temizlenmiş doğrulama kaydı bulunuyor. Konsol görüntüleri kayıt
tekrarı olarak etiketli; canlı VM veya üretim SaaS iddiası yok.

Daha önce gerçek Linux ortamında Codex/Antigravity oturumlarını ve Codex ile
görev–dosya–sonuç hattını da denemiştik. Bu repo, o mühendislik çalışmasının
gösterilebilir kanıtlarını topluyor. Uygulama kaynak kodunu dağıtmıyorum.

Repo: [GitHub yayını sonrasında showcase bağlantısını ekle]

## GIF sırası

1. Görev ve gerçek API kanıt özeti.
2. Mevcut konsolda kayıtlı sonuçlar.
3. API ajanının ürettiği gerçek diff.
4. Bağımsız beş kabul testinin sonucu.
5. Korunan test dosyasına değişiklik yapan kontrolün reddi.
6. Gereksinimler ve kapsam.

GIF canlı video kaydı değildir. Tam çözünürlüklü JPEG'ler ayrı olarak bulunur.
Küçük sentetik örneğin kod parçaları kanıttır; Dispatcher uygulamasının kaynağı,
derlenmiş arayüzü, çalıştırma scriptleri veya özel Git geçmişi pakette yoktur.
