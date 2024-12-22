# Renk Sabitliği ve Manipülasyon Dayanıklılığının Görüntü Sınıflandırma Performansına Etkisi
Bu proje, görüntü işleme tekniklerini ve gürültü augmentasyonu kullanarak hayvan sınıflandırma problemini çözmeye yönelik bir derin öğrenme modelini geliştirmeyi amaçlamaktadır. Proje, Kaggle üzerinden [Animals with Attributes 2](https://www.kaggle.com/datasets/rrebirrth/animals-with-attributes-2) veri setini kullanarak 10 farklı hayvan sınıflarını sınıflandırmak için bir model oluşturmuştur.

## Veri Seti
Proje, Animals with Attributes 2 (AWA2) veri setinden seçilen 10 farklı hayvan sınıfını içermektedir. Veri seti, her bir sınıf için 650'ye kadar görsel içermektedir. Seçilen sınıflar şunlardır:
+ Collie
+ Dolphin
+ Elephant
+ Fox
+ Moose
+ Rabbit
+ Sheep
+ Squirrel
+ Giant Panda
+ Polar Bear
Veri setinde, her görüntü 128x128 piksel boyutuna yeniden boyutlandırılmış ve her bir görüntü normalize edilmiştir.

## Kullanılan Kütüphaneler
Projenin geliştirilmesinde kullanılan bazı önemli kütüphaneler:
+ **OpenCV:** Görüntü işleme için kullanılmıştır. Resimleri okumak, boyutlandırmak ve normalize etmek için kullanılmıştır.
+ **NumPy:** Verilerin işlenmesi ve manipülasyonu için kullanılmıştır.
+ **Matplotlib:** Eğitim sürecinin görselleştirilmesi ve gürültü eklenmiş görüntülerin karşılaştırılması için kullanılmıştır.
+ **TensorFlow:** Derin öğrenme modelinin oluşturulması, eğitilmesi ve değerlendirilmesi için kullanılmıştır.
+ **scikit-learn:** Modeli eğitmeden önce veri setini eğitim ve test olarak bölmek, etiketleri dönüştürmek ve veri ön işleme adımlarını gerçekleştirmek için kullanılmıştır.
  
## Proje Adımları
**1. Veri Ön İşleme:**
+ Seçilen 10 sınıf için her bir sınıftan 65 görüntü seçilmiştir.
+ Görüntüler 128x128 piksel boyutuna yeniden boyutlandırılmıştır.
+ Görüntüler normalize edilerek [0, 1] aralığına getirilmiştir.
  
**2. Gürültü Augmentasyonu:**
+ Eğitim verilerine Gaussian gürültüsü eklenerek, modelin genelleme kapasitesi artırılmaya çalışılmıştır.
+ Gürültü eklenmiş veri, orijinal veriyle birleştirilerek eğitim setinin boyutu artırılmıştır.
  
**3. Model Oluşturma:**
+ Derin öğrenme modelinde Convolutional Neural Network (CNN) yapısı kullanılmıştır.
+ 3 katmanlı konvolüsyonel ağ, MaxPooling ve Dropout katmanları ile tasarlanmıştır.
+ Son katmanda, sınıflandırma için Softmax aktivasyonu kullanılmıştır.

**4. Eğitim ve Değerlendirme:**
+ Model, categorical crossentropy kaybı ve accuracy metriği ile eğitilmiştir.
+ Eğitim süreci boyunca doğruluk ve kayıp grafikleri çizilmiştir.

**6. Manipülasyonlar ve Renk Sabitliği:**
+ Görüntüler üzerinde renk manipülasyonları yapılarak farklı ışık kaynakları altında modelin performansı test edilmiştir.
+ Grey World ve Max RGB yöntemleriyle renk sabitliği uygulanmıştır.

**7. Test Setleri:**
+ Orijinal Test Seti ve Gürültü Eklenmiş Test Seti Sonuçları: Test seti, orijinal görseller ile kullanılmıştır.
+ Manipüle Edilmiş Test Seti: Test setindeki görüntüler, farklı ışık kaynakları ile manipüle edilmiştir.
+ Renk Sabitliği Uygulanan Test Seti: Görüntülere renk sabitliği uygulandı ve modelin başarımı test edilmiştir.

## Başarı Değerlendirmesi
+ **Orijinal Test Seti ve Gürültü Eklenmiş Test Seti Sonuçları:**
  + Test Loss: 1.18
  + Test Accuracy: 62.36%

+ **Manipüle Edilmiş Test Seti Sonuçları:**
  + Test Loss: 3.74
  + Test Accuracy: 20.51%

+ **Renk Sabitliği Uygulanan Test Seti Sonuçları:**
  + Test Loss: 1.27
  + Test Accuracy: 59.68%

## Sonuçlar ve Tartışma
Bu çalışmada, hayvan sınıflandırması için oluşturulan modelin performansı, farklı test senaryolarında değerlendirilmiştir. 
+ Orijinal test seti ve gürültü eklenmiş test seti verileriyle yapılan deneylerde model, %62.36 doğruluk oranı ve 1.178 test kaybı ile iyi bir temel performans sergilemiştir. Bu sonuç, modelin eğitildiği veri kümesindeki özellikleri tanıyabildiğini ve sınıflandırmada belirli bir başarıya ulaştığını göstermektedir. Ancak, modelin bu performansını sürdürebilmesi için daha çeşitli durumlara uyum sağlaması gerekmektedir.
+ Manipülasyon yapılmış test verileriyle gerçekleştirilen deneylerde doğruluk oranı %20.51’e düşmüş ve test kaybı 3.74 olarak ölçülmüştür. Bu düşüş, modelin görsellerdeki manipülasyonlara karşı oldukça hassas olduğunu ve genelleme yeteneğinin sınırlı olduğunu ortaya koymaktadır. Model, özellikle veri manipülasyonları gibi beklenmedik durumlarda önemli ölçüde performans kaybı yaşamaktadır.
+ Renk sabitliği uygulanan test verilerinde doğruluk oranı %59.68 olarak ölçülmüş ve test kaybı 1.27 seviyesinde kalmıştır. Renk sabitleme, modelin performansını bir miktar artırmış olsa da, orijinal veriye kıyasla kayda değer bir iyileştirme sağlamamıştır. Bu sonuç, renk sabitlemenin belirli durumlarda faydalı olabileceğini ancak tek başına modelin genelleme kabiliyetini geliştirmede yeterli olmadığını göstermektedir. Modelin ışık koşulları gibi çevresel faktörlere daha dayanıklı hale getirilmesi için daha karmaşık yöntemlerin kullanılması gerekebilir.

## Çözüm Önerileri

+ **Eğitim Veri Kümesinin Genişletilmesi:** Veri kümesinin çeşitlendirilmesi, modelin genelleme yeteneğini artırabilir. Manipüle edilmiş görüntüler ve farklı aydınlatma koşullarını içeren görseller eklenerek modelin çeşitli durumları öğrenmesi sağlanabilir.

+ **Veri Artırma Tekniklerinin Kullanılması:** Görsellerde gürültü ekleme yöntemi yerine döndürme, ölçekleme, bulanıklaştırma ve renk değişiklikleri gibi farklı veri artırma yöntemleri uygulanarak modelin dayanıklılığı artırılabilir. Bu yöntemler, modelin beklenmedik manipülasyonlara karşı daha başarılı olmasını sağlayabilir.

+ **Model Mimarisi İyileştirmeleri:** Konvolüsyon katmanlarının derinliğinin artırılması veya özel filtrelerin eklenmesi gibi mimari değişikliklerle modelin manipülasyonlara ve renk değişimlerine karşı daha dayanıklı hale gelmesi sağlanabilir. Modelin doğruluk oranını artırmak için daha derin ağ yapıları (daha fazla katman veya daha büyük katmanlar) kullanılabilir. Ancak modeli eğitirken de çok fazla parametre kullanılacağı da göz önünde bulundurulmalıdır.

+ **Transfer Öğrenme Kullanımı:** Daha büyük ve çeşitli bir veri kümesi üzerinde önceden eğitilmiş bir modelin yeniden eğitilmesi, sınırlı veri kümesiyle çalışan modellerde performans artışı sağlayabilir.

<br/>**Kaggle:** [Renk Sabitliği ve Manipülasyon Dayanıklılığının Görüntü Sınıflandırma Performansına Etkisi](https://www.kaggle.com/code/semayln/renk-sabitli-i-ve-manip-lasyon-dayan-kl-l-n-n-g)
