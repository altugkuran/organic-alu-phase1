# Organik Tabanlı ALU'ya Giden Yol — Faz 1
## Tasarlanmış Biyolojik Mantık Hücreleri, Yönlü Elektriksel Bağlantılar ve Fan-out
**Toward an Organic-Based ALU — Phase 1: Engineered Logic Cells, Directional Electrical Interconnects, and Fan-Out**

**Sürüm:** 0.1 — 18 Kasım 2026  
**Durum:** Tasarım hipotezi; deneysel olarak doğrulanmış bir ALU değildir.

## Özet
Bu rapor, nöronlardan esinlenen, genetik olarak tasarlanmış canlı hücrelerden oluşan, **dış boyutu 20 mm'den küçük** bir aritmetik-mantık birimine (ALU) giden ilk araştırma fazını tanımlar. Uzun aksonlar, kimyasal sinapslar ve öğrenmeye dayalı sinir ağları yerine, kısa ve seçici elektriksel hücre bağlantıları; pA düzeyinde akım kodlaması; iki bağımsız çıkış; eşik tabanlı mantık ve standartlaştırılmış hücre üretimi önerilir. Amaç ilk aşamada tam ALU değil, tek kapı, iki hücre bağlantısı ve **fan-out = 2** işlevini gösteren prototip için ölçülebilir araştırma hipotezleri oluşturmaktır. Bu boyut hedefi ileride biyolojik RISC işlemci ve organik yapay zekâ mimarisiyle bütünleşme için bir tasarım kısıtıdır; henüz kanıtlanmış yerleşim hesabı değildir.

## 1. Araştırma sorusu ve kapsam
Bir canlı hücre, kararlı eşiklere sahip NOT/AND/OR/NAND/NOR mantık işlevlerinden birini yerine getirecek biçimde tasarlanabilir mi? Bu hücre aynı mantık sonucunu, giriş yükleri değişse bile, **iki ayrı elektriksel çıkıştan** iletebilir mi? Seçici elektriksel hücre bağlantılarıyla, hücreler arası istenmeyen ters etkileşim azaltılabilir mi? Üretilebilir hücre hattından tekrarlanabilir mantık elemanları elde edilebilir mi?

Faz 1 dışı: tam 8-bit ALU'nun üretildiği iddiası, bellek, komut çözücü, saat ağı, RISC yürütme birimi, öğrenme algoritmaları, otonom fotovoltaik besleme. Bunlar sonraki fazların sistem gereksinimleridir.

## 2. Ana mimari — N-CURRENT / N-GATE / N-LINK
- Nöron kökenli veya nöron benzeri tasarlanmış, metabolik olarak canlı mantık hücresi.
- Bilgi taşıyıcısı pA ölçeğinde iyon akımıdır; membran potansiyeli ve elektrokimyasal gradyanlar fiziksel olarak yine gereklidir.
- Düşük empedanslı giriş akım algılama **hedef**, yüksek dinamik empedanslı aktif çıkış **hedef**; doğal nöronda otomatik gerçekleşmez.
- Kısa, geometrik olarak yönlendirilmiş membran temasları ve seçici heterotipik gap junction proteinleri **bağlantı adayıdır**. Seçicilik, doğrultma veya sinyal kazancı garantisi değildir.
- Hücre başına en az iki çıkış. Her çıkış için ayrı yerel sürücü ve membran uzantısı; çıkışlar arası elektriksel çapraz etkileşim ölçülür.
- Başlangıç akım kazancı hedefi tek çıkış için 1 olabilir; **iki eşit büyüklükte çıkışın toplamı girişten büyükse toplam akım kazancı 2'dir** ve metabolik enerji tüketir. Bu nedenle 'kazançsız fan-out' diye sunulamaz.

## 3. İki çıkış için iki alternatif
**A — Ortak mantık çekirdeği + iki ayrılmış sürücü:** Aynı mantık durumu iki farklı membran bölgesinde yerel iyon kanallarını kontrol eder. İki ayrı çıkışın yükten kaynaklanan akım/gerilim değişimlerinin birbirine etkisi azaltılmaya çalışılır. Ortak sitoplazma ve membran nedeniyle tam izolasyon varsayılamaz.

**B — Ortak girişler + hücre içinde iki ayrı mantık bölgesi:** A mimarisi kabul edilebilir fan-out ve izolasyon vermezse, her biri aynı giriş durumlarını algılayan ve ayrı çıkış üreten iki yerel mantık alt-birimi denenir. Bu seçenek **iki ayrı hücre değil, aynı hücre içinde iki işlevsel mantık bölgesi** öngörür. Ortak girişlerin birbirini yüklemesi, bölgesel protein hedefleme, hücre içi kablolama ve enerji bütçesi ayrı risklerdir. B de henüz biyolojik olarak kanıtlanmış bir düzenek değildir.

**C — Karşılaştırma kontrolü:** Tek sürücünün iki bağlantıya pasif dallanması; iki yükteki akım bölünmesi ölçülerek A ve B'nin yararı nicel olarak değerlendirilir.

## 4. Basit elektriksel model
Her hücre için: C_m dV/dt = I_in - g_L(V-E_L) - I_ion(V,t). İki bağlantı için ilk yaklaşım: I_j = g_j(V_out - V_load,j); gerçek gap junction iletkenliği gerilime, protein türüne ve yönüne bağlı olabilir. İdeal akım kaynağı varsayımı biyolojik olarak ayrıca doğrulanmalıdır.

Çapraz yük duyarlılığı: K_12 = |(Delta I_2 / I_2) / (Delta Z_1 / Z_1)|. Referans değerlendirme olarak, önceden belirlenmiş yük aralığında ikinci çıkışın %5'ten az değişmesi **önerilen mühendislik ölçütüdür, literatür bulgusu değildir**. İleri/geri bağlantı asimetrisi, bit hata oranı, durum eşiği ayrımı, tepki gecikmesi, enerji tüketimi ve hücreler arası varyans ayrıca raporlanır.

Yük ve kapasitans: Q = I*t. Örneğin 10 pA x 1 ms = 10^-14 C ≈ 6.24x10^4 tek değerlikli iyon. İdeal 10 pF kapasitansta bu yalnızca 1 mV eder; kaçak akım ve kanal kinetiği hesaba katıldığında daha da karmaşıktır. Dolayısıyla düşük akım, tek başına yüksek hız veya güvenilir anahtarlama sağlamaz.

## 5. Mantık işlevleri
Soyut eşik modeli Y = H(w_A A + w_B B + b), H(x)=1 (x>0) aksi halde 0. NOT: (-1,0,+0.5); AND: (+1,+1,-1.5); OR: (+1,+1,-0.5); NAND: (-1,-1,+1.5); NOR: (-1,-1,+0.5). Bu katsayılar biyolojik iyon kanalı tasarımına doğrudan dönüşmez. XOR tek doğrusal eşik birimiyle gerçekleştirilemez; çoklu bölge veya birden fazla hücre gerekir. İlk gösterim için NOT ve iki çıkış yeterli; sonraki kapılar ek aşamalardır.

## 6. Hücre üretimi ve besleme
Olgun nöronları güvenilir biçimde bölünmeye zorlamak yerine, genetik olarak düzenlenmiş çoğalabilir kök/öncü hücre hattından farklılaştırılmış mantık hücreleri üretme yaklaşımı önerilir. Genetik eşitlik elektriksel parametrelerin eşitliğini garanti etmez; tek hücre karakterizasyonu, seçme ve kalibrasyon gerekir.

Fotovoltaik kaynak -> pil/kondansatör -> kontrollü elektrokimyasal arayüz uzun vadeli enerji yaklaşımıdır. Elektriksel depolama, hücre membranındaki iyon gradyanlarını doğrudan sürdürmez; iyon pompaları ve metabolizma için enerji dönüşüm yolu gereklidir. Faz 1'de standart hücre kültürü metabolizması ve harici ölçüm/uyarım daha gerçekçidir.

## 7. İlk faz deneysel doğrulama mantığı (kavramsal)
1. Tek hücrenin kararlı NOT benzeri yanıtı ve eşik gürültü marjı.
2. Seçici iki hücre teması; doğru eşleşme / yanlış eşleşme karşılaştırması.
3. İleri ve ters elektriksel iletim; seçiciliğin doğrultmayla karıştırılmaması.
4. Bir çıkıştan iki yükün pasif sürülmesi; yük değişimine duyarlılık.
5. A mimarisinde iki çıkış ve çapraz etkileşim ölçümü.
6. A başarısızsa B mimarisinde ortak giriş, iki yerel mantık bölgesi ve çıkış bağımsızlığı.
7. Tekrarlanabilirlik, yaşama süresi, kanal varyansı, enerji ve hız ölçümü.

**Karar kapısı:** Güvenilir mantık seviyeleri, yönlü/istenmeyen geri beslemeyi sınırlayan bağlantı ve iki yükte tekrarlanabilir durum gösterilmeden ALU ölçekleme iddiasına geçilmez. Başarısızlık tek mimariyi eler; biyolojik mantığın tüm olasılıklarını değil.

## 8. 20 mm altı hedefin yorumu
Mekanik dış sınır <20 mm; biyolojik işlem elemanları, hücre yaşam destek hacmi, elektrotlar, mikroakışkan kanallar ve bağlantı topolojisi ayrı ayrı bütçelenmelidir. İlk fazda hedef boyut için kanıtlanmış kapı yoğunluğu veya zamanlama bulunmamaktadır. Tasarım, ileride RISC işlemci, kayıtlar, kontrol, bellek ve organik yapay zekâ sistemleriyle ortak bir hücre platformuna evrilebilecek biçimde belgelenir.

## 9. Temel riskler ve yanlışlanabilirlik
- Doğal gap junction iki hücreyi elektriksel olarak birleştirerek izolasyonu bozabilir.
- Heterotipik seçici eşleşme zorunlu olarak tek yönlü iletim vermez.
- İki sürücü aynı membran/sitoplazma üzerinden güçlü bağlaşabilir.
- Düşük empedanslı giriş algılamayı kolaylaştırmak yerine yerel voltaj değişimini söndürebilir.
- pA akımlarda kanal stokastisitesi, membran kaçakları ve küçük sinyal marjı önemlidir.
- Aynı hücrede iki mantık bölgesi protein yerleşimi ve ortak giriş yüklemesi nedeniyle başarısız olabilir.
- Hücre ölçeği ve bağlantı yoğunluğu <20 mm ALU hedefiyle uyuşmayabilir.

## 10. Öncelikli laboratuvarlar (iletişim kurulmadı)
1. **Kafui Dzirasa Lab, Duke University (ABD):** 2026 seçici mühendislik ürünü elektriksel sinaps çalışması; moleküler eşleşme ve bağlantı tasarımı. https://www.neuro.duke.edu/research/faculty-labs/dzirasa-lab
2. **Nenad Bursac Lab, Duke University (ABD):** uyarılmayan hücrelerin genetik olarak elektriksel iletken dokulara dönüştürülmesi; iyon kanalı mühendisliği ve hücre örüntüleme. https://bursaclab.pratt.duke.edu/research/electrophysiology-excitable-cells-and-tissues
3. **Adam E. Cohen Lab, Harvard University (ABD):** tasarlanmış uyarılabilir hücreler, voltaj ölçümü, biyofiziksel modelleme. https://cohenweb.rc.fas.harvard.edu/Research/research.html
4. **Michael Levin Lab, Tufts University (ABD):** sentetik biyoloji, iyon akımlarıyla hücre kontrolü, hücreler arası biyolojik hesaplama. https://as.tufts.edu/biology/levin-lab/research/direction-lab
5. **Edmond Walsh / Richard Wade-Martins işbirliği, University of Oxford (Birleşik Krallık):** mikroakışkan odacıklarla insan nöron devreleri; fiziksel yerleşim ve yönlendirme. https://eng.ox.ac.uk/news/creating-brain-circuits-with-human-neurons-and-fluid-walls

Bu liste bilimsel konu eşleşmesine göre oluşturulmuştur; laboratuvarların projeyi kabul edeceği veya işbirliği yapacağı teyit edilmemiştir.

## 11. Kaynaklar
[1] Ransey E. et al. (2026). *Long-term editing of brain circuits using an engineered electrical synapse*. Nature. DOI: 10.1038/s41586-026-10501-y. https://pmc.ncbi.nlm.nih.gov/articles/PMC13372691/

[2] Kirkton R.D. & Bursac N. (2011). *Engineering biosynthetic excitable tissues from unexcitable cells for electrophysiological and cell therapy studies*. Nature Communications 2, 300. https://www.nature.com/articles/ncomms1302

[3] Nebuloni F. et al. (2024). *A fluid-walled microfluidic platform for human neuron microcircuits and directed axotomy*. Lab on a Chip 24, 3252–3264. DOI: 10.1039/D4LC00107A. https://pubs.rsc.org/en/content/articlehtml/2024/lc/d4lc00107a

[4] Rabinowitch I., Colón-Ramos D.A., Krieg M. (2024). *Understanding neural circuit function through synaptic engineering*. Nature Reviews Neuroscience 25, 131–139. https://www.nature.com/articles/s41583-023-00777-8

[5] Ori H. et al. (2023). *Observation of topological action potentials in engineered tissues*. Nature Physics 19, 290–296. https://www.nature.com/articles/s41567-022-01853-z

[6] University of Oxford (2025). *Creating brain circuits with human neurons and fluid walls*. https://eng.ox.ac.uk/news/creating-brain-circuits-with-human-neurons-and-fluid-walls

[7] Cohen Lab, Harvard University. *Voltage imaging throughout life* (lab research overview). https://cohenweb.rc.fas.harvard.edu/Research/research.html

[8] Levin Lab, Tufts University. *Direction of Lab*. https://as.tufts.edu/biology/levin-lab/research/direction-lab

## 12. Açık araştırma soruları
- İki ayrı membran uzantısının izolasyonunu sayısal olarak hangi geometri sağlar?
- İki sürücüdeki iyon akımı, aynı mantık durumuna hangi biyolojik transdüksiyonla bağlanır?
- A ve B mimarileri arasında hız, enerji, varyans, üretim karmaşıklığı farkı nedir?
- Seçici connexin çiftinin iletim asimetrisi ve geri besleme etkisi nedir?
- 2 cm altı RISC-uyumlu bir ALU için minimum mantık kapısı, bağlantı ve destek alanı nedir?

**Sonuç:** Faz 1 tamamlanmış bir biyolojik cihaz değil, literatürle desteklenen ve açık başarısızlık koşulları tanımlanmış bir tasarım hipotezidir.