# CENG 476 - DeepText Multi-Task Classifier Project
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HAasan123/deeplearn-nlp/blob/main/deeplearn-nlp.ipynb)

## 1. Proje Hakkında (Project Overview)
**DeepText Multi-Task Classifier**, doğal dil işleme (NLP) tekniklerini kullanarak üç farklı sınıflandırma görevini tek bir model üzerinde gerçekleştiren gelişmiş bir derin öğrenme projesidir.

Bu proje, **CENG 476 - Introduction to Deep Learning** dersi kapsamında geliştirilmiştir. Projenin temel amacı, farklı metin tabanlı veri setleri (Duygu Analizi, Şiddet İçeren Tweetler ve Nefret Söylemi) üzerinde ortak bir öğrenme yapısı kurarak, modelin genelleştirme yeteneğini artırmak ve tek bir sinir ağı mimarisi ile çoklu görevleri (Multi-Task Learning) başarıyla yönetmektir.

## 2. Proje Geliştiricisi (Develaper)
* **Ad Soyad:** Hasan Çatak
* **Öğrenci No:** 200444073
* **Rol:** Model tasarımı, veri ön işleme, eğitim süreçleri ve optimizasyonun tamamı tarafımdan gerçekleştirilmiştir.

## 3. Model Mimarisi ve Nasıl Çalışır? (Architecture & Methodology)
Bu projede, metin verilerini işlemek için **LSTM (Long Short-Term Memory)** tabanlı hibrit bir mimari kullanılmıştır. Modelin çalışma mantığı şu şekildedir:

### Mimarinin Temel Bileşenleri:
1.  **Veri Ön İşleme:** Metinler temizlenir (stopwords temizliği), `Tokenizer` ile sayısallaştırılır ve `Pad Sequences` ile sabit uzunluğa getirilir.
2.  **Ortak Katmanlar (Shared Layers):**
    * **Embedding Layer:** Kelimeleri vektör uzayına taşır.
    * **Spatial Dropout:** Overfitting'i önlemek için özellik haritalarını rastgele kapatır.
    * **Shared LSTM:** Metindeki bağlamsal ilişkileri öğrenir.
    * **Batch Normalization:** Eğitim sürecini hızlandırır ve kararlılığı artırır.
3.  **Çoklu Çıkış Dalları (Multi-Output Branches):**
    * Model, ortak katmanlardan gelen bilgiyi üç farklı "Dense" katmanına iletir.
    * Her bir çıkış dalı (Emotion, Violence, Hate Speech) kendi sınıf sayısına göre `Softmax` aktivasyonu ile tahmin üretir.

### Kullanılan Teknikler:
* **Multi-Task Learning:** Üç farklı veri seti aynı anda eğitilerek ortak özelliklerin öğrenilmesi sağlandı.
* **Regularization:** L2 Regularization, Spatial Dropout ve Batch Normalization ile modelin ezberlemesi (overfitting) engellendi.
* **Optimization:** `Adam` optimizer kullanıldı ve `ReduceLROnPlateau` ile öğrenme hızı dinamik olarak ayarlandı.
* **Early Stopping:** Modelin gelişiminin durduğu noktada eğitim otomatik olarak sonlandırıldı.

## 4. Kurulum ve Çalıştırma (Installation & Usage)
Bu proje Google Colab veya Kaggle Notebook ile çalıştırılabilir.

### Adım 1: Dosyaları Hazırlama
Projeyi çalıştırmak için aşağıdaki veri setlerinin Kaggle'dan indirilmesi veya ortamda bulunması gerekmektedir:
* `text.csv` (Emotion Dataset)(https://www.kaggle.com/datasets/nelgiriyewithana/emotions)
* `Train.csv` (Gender Based Violence Tweet Classification)(https://www.kaggle.com/datasets/gauravduttakiit/gender-based-violence-tweet-classification)
* `labeled_data.csv` (Hate Speech and Offensive Language)(https://www.kaggle.com/datasets/mrmorj/hate-speech-and-offensive-language-dataset)


### Adım 2: Çalıştırma
Projenin `.ipynb` dosyasını açın ve hücreleri sırasıyla çalıştırın. Model eğitim süreci otomatik olarak başlayacak ve sonuçlar (Classification Report, Confusion Matrix ve Loss Grafikleri) ekrana yazdırılacaktır.

Hızlı çalıştırmak için yukarıdaki **"Open In Colab"** butonunu kullanabilirsiniz.






