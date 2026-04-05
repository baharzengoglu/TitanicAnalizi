# Titanic Survival Analysis

## Proje Amacı
Bu projede Titanic yolcularının hayatta kalmasını etkileyen faktörler veri analizi yöntemleri ile incelenmiştir.

## Amaç
Yolcu özelliklerinin (cinsiyet, sınıf, yaş vb.) hayatta kalma üzerindeki etkisini analiz etmektir.

## Veri Seti
Kaynak: Kaggle Titanic Dataset  
Toplam gözlem: 891  
Toplam değişken: 12  

## Yapılan Analizler

### 1. Veri Keşfi (EDA)
- Veri tipleri incelendi
- Kategorik ve sayısal değişkenler analiz edildi
- Survival oranı incelendi

### 2. Eksik Veri Analizi
- Age değişkeninde 177 eksik değer tespit edildi
- Age değişkeni, Pclass, SibSp ve Parch değişkenlerine göre median kullanılarak dolduruldu
- Embarked değişkeni mode ile dolduruldu
- Cabin değişkeni yüksek eksik oranı nedeniyle çıkarıldı

### 3. Kategorik Değişken Analizi
İncelenen değişkenler:
- Sex
- Pclass
- Embarked
- SibSp
- Parch

Survival oranları grup bazında analiz edildi.

### 4. Sayısal Değişken Analizi
İncelenen değişkenler:
- Age
- Fare

Dağılım ve istatistiksel özet incelendi.

👉 Kadın yolcuların hayatta kalma oranı erkeklere göre belirgin şekilde daha yüksektir

👉 Üst sınıf yolcuların hayatta kalma ihtimali daha yüksektir

👉 Daha genç yolcuların hayatta kalma oranı daha yüksektir

### 5. Aykırı Değer Analizi
IQR yöntemi kullanılarak aykırı değer tespiti yapıldı.

Kullanılan fonksiyon:

```python
def outlier_thresholds(df, col):
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    return lower, upper
