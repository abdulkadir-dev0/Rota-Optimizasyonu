# Rota-Optimizasyonu

Bu proje, bir metro ağı üzerinden en hızlı ve en az aktarmalı rotaları bulmak için tasarlanmış bir simülasyondur. Kapsadığı hatlar ve istasyonlar arasında yapılan yolculuklarda, kullanıcıların belirttiği başlangıç ve hedef istasyonları arasındaki rotalar, BFS ve A* algoritmaları kullanılarak hesaplanır.

## Kullanılan Teknolojiler ve Kütüphaneler

Bu projede aşağıdaki Python kütüphaneleri kullanılmıştır:

- **collections**: Bu kütüphane, Python'un veri yapıları için faydalı olan çeşitli sınıfları sağlar. `deque` sınıfı, BFS algoritmasında sıralama işlemleri için kullanılırken, `defaultdict` sınıfı hatlar arasındaki istasyonları gruplamak için kullanılmıştır.
- **heapq**: A* algoritmasında öncelikli kuyruk kullanmak için bu kütüphane kullanılmıştır. Bu, her istasyonun toplam süreye göre sıralanarak daha verimli bir yolculuk bulmayı sağlar.
- **typing**: Fonksiyon ve veri yapılarında tür açıklamaları sağlar.

## Algoritmaların Çalışma Mantığı

### BFS Algoritması

BFS (Breadth-First Search) algoritması, genellikle kısa mesafeli rotaları bulmak için kullanılır. Bu projede, en az aktarmalı rotayı bulmak için kullanılmıştır. Algoritma, her bir istasyonun komşularına giderek tüm istasyonları ziyaret eder. Her geçişte, rotayı oluşturan istasyonlar eklenir ve aktarma sayısı en az olan rota tercih edilir. BFS, tüm rotaları keşfetmeye çalışırken, her istasyon sadece bir kez ziyaret edilir.

BFS algoritmasının çalışma mantığı:
- Başlangıç istasyonundan başlayarak komşu istasyonlara geçiş yapılır.
- Her geçişte, önceki rotaya eklenir ve aktarma sayısı artar.
- Tüm istasyonlar ziyaret edilene kadar devam edilir.
- En az aktarmalı yol bulunduğunda işlem sonlandırılır.

### A* Algoritması

A* algoritması, daha verimli bir yol bulma algoritmasıdır ve genellikle en hızlı yolu bulmak için kullanılır. Bu algoritma, her istasyonun tahmini maliyetini (heuristic) dikkate alarak en kısa yolu bulur. Projeye dahil edilen A* algoritmasında, her istasyonun hedefe olan uzaklığı tahmin edilerek, öncelikli kuyrukla (priority queue) işlenir. 

A* algoritmasının çalışma mantığı:
- Her bir geçişte, geçiş süresi ve tahmini hedefe olan mesafe dikkate alınarak istasyonlar sıralanır.
- Öncelikli kuyruk sayesinde, en hızlı yolu bulmaya yönelik istasyonlar önce işlenir.
- Hedef istasyona ulaşıldığında en hızlı yol ve geçiş süresi döndürülür.

### Neden Bu Algoritmalar Kullanıldı?

- **BFS**: En az aktarmalı rotayı bulmak için uygundur çünkü her geçişte aktarma sayısını göz önünde bulundurur ve tüm istasyonlar sırasıyla gezilir.
- **A***: En hızlı rotayı bulmak için daha verimli bir algoritmadır. A* algoritması, her istasyonun hedefe olan uzaklığını hesapladığı için daha hızlı bir yolculuk rotası sunar.

### Örnek Kullanım ve Test Sonuçları

Aşağıdaki örnekler, metro ağındaki çeşitli istasyonlar arasında yapılan rota sorgularını ve sonuçlarını göstermektedir:

### Test 1: AŞTİ'den OSB'ye
rota = metro.en_az_aktarma_bul("M1", "K4")
print("En az aktarmalı rota:", " -> ".join(i.ad for i in rota))

sonuc = metro.en_hizli_rota_bul("M1", "K4")
print(f"En hızlı rota ({sure} dakika):", " -> ".join(i.ad for i in rota))

### Çıktı
En az aktarmalı rota: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
En hızlı rota (18 dakika): AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB

### Projeyi Geliştirme Fikirleri

1.Dinamik Veri Güncelleme: Metro hattındaki istasyonlar, hatlar veya geçiş süreleri değiştiğinde, bu verilerin dinamik olarak güncellenmesi sağlanabilir.
2.Gerçek Zamanlı Trafik Durumu: Geçiş süreleri gerçek zamanlı trafik verisiyle entegre edilerek, daha gerçekçi bir rota planlaması yapılabilir.
3.Mobil Uygulama Entegrasyonu: Bu metro simülasyonu, bir mobil uygulama üzerinden kullanıcı dostu bir arayüzle sunulabilir.
4.Yolculuk Analizi: Kullanıcıların seyahat alışkanlıklarına göre, sık kullanılan rotalar ve optimizasyon önerileri eklenebilir.
5.Daha Gelişmiş Heuristik Fonksiyonları: A* algoritmasında kullanılan heuristik fonksiyonları geliştirerek, daha doğru tahminler yapabiliriz.


