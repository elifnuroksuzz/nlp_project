IMDB Film Yorumları ile Duygu Analizi
Bu proje, IMDB film yorumları veri setini kullanarak metin sınıflandırma ve duygu analizi gerçekleştirir. Projenin amacı, bir film yorumunun "pozitif" mi yoksa "negatif" mi olduğunu makine öğrenmesi modelleriyle tahmin etmektir. Proje, veri temizleme, özellik çıkarma (feature extraction) ve model karşılaştırması gibi temel Doğal Dil İşleme (NLP) adımlarını içermektedir.

🚀 Proje Akışı
Proje, aşağıdaki adımları takip ederek geliştirilmiştir:

Veri Yükleme ve Hazırlık: 50.000 film yorumundan oluşan IMDB veri setinin yüklenmesi ve temel analizinin yapılması.

Metin Temizleme: Yorumlardaki HTML etiketleri, noktalama işaretleri, sayılar ve fazla boşluklar gibi gürültülerin temizlenmesi.

Tokenizasyon ve Lemmatizasyon: Temizlenmiş metinlerin kelimelere (token) ayrılması, etkisiz kelimelerin (stopwords) çıkarılması ve kelimelerin köklerine (lemma) indirgenmesi.

Vektörizasyon: Metin verilerinin makine öğrenmesi modellerinin anlayabileceği sayısal formata dönüştürülmesi. Bu aşamada iki farklı yöntem kullanılmıştır:

Bag of Words (BoW)

TF-IDF (Term Frequency-Inverse Document Frequency)

Model Eğitimi ve Değerlendirme: Veri setinin eğitim ve test olarak ikiye ayrılması ve farklı sınıflandırma algoritmalarının her iki vektörizasyon tekniğiyle eğitilmesi.

Çapraz Doğrulama ve Hiperparametre Optimizasyonu: Modellerin performansını daha güvenilir bir şekilde ölçmek için 10 katlı çapraz doğrulama (cross-validation) ve en iyi model parametrelerini bulmak için GridSearchCV kullanılmıştır.

🔑 Temel Kavramlar
Bu projede kullanılan temel Doğal Dil İşleme (NLP) kavramları:

Tokenizasyon (Tokenleştirme): Bir metnin cümle, kelime veya alt kelime gibi daha küçük birimlere (token) ayrılması işlemidir.

Lemmatizasyon (Kök Bulma): Bir kelimenin eklerini atarak anlamsal kökünü bulma işlemidir. Örneğin, "gözlükçü" kelimesinin kökü "göz"dür. Bu işlem, kelime dağarcığını küçülterek modelin daha verimli çalışmasını sağlar.

Stemming (Gövdeleme): Lemmatizasyona benzer şekilde kelimelerin eklerini atarak gövdesini bulur, ancak bulunan gövdenin her zaman sözlükte anlamlı bir kelime olması gerekmez.

Bag of Words (Kelime Torbası): Bir metni, içindeki kelimelerin sırasını dikkate almadan, sadece hangi kelimeden kaç tane geçtiğini sayarak sayısal bir vektöre dönüştüren yöntemdir.

TF-IDF (Term Frequency-Inverse Document Frequency): Bir kelimenin bir belge içindeki önemini, o kelimenin belge içindeki sıklığı (TF) ve tüm belgelerdeki genel sıklığının tersi (IDF) ile orantılı olarak hesaplayan bir istatistiksel yöntemdir. Nadir ve önemli kelimelere daha yüksek ağırlık verir.

📊 Model Performansı
Projede KNN, Naive Bayes, Karar Ağacı, Lojistik Regresyon ve Random Forest gibi farklı sınıflandırma modelleri test edilmiştir. Yapılan çapraz doğrulama ve hiperparametre optimizasyonu sonucunda en yüksek performansı gösteren modeller ve metrikleri aşağıdaki gibidir:

Model	Vektörizasyon	F1-Skoru (Ağırlıklı)	Doğruluk
Lojistik Regresyon	TF-IDF	0.8812	0.8812
Naive Bayes	TF-IDF	0.8543	0.8544
Random Forest	TF-IDF	0.8427	0.8427
Karar Ağacı	TF-IDF	0.7323	0.7334
Naive Bayes	BoW	0.5100	-
Lojistik Regresyon	BoW	0.5043	-
KNN	TF-IDF	0.5550	0.5627

E-Tablolar'a aktar
🏆 En İyi Model
Yapılan değerlendirmeler sonucunda TF-IDF vektörleştirme tekniği ile eğitilen Lojistik Regresyon modeli, %88.12 F1-Skoru ile en başarılı model olarak belirlenmiştir. Bu sonuç, kelimelerin belge içindeki önemini dikkate alan TF-IDF yönteminin, sadece kelime frekanslarına dayanan Bag of Words yöntemine göre bu veri setinde çok daha üstün olduğunu göstermektedir.
