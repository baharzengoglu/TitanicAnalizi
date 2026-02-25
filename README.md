# Titanic Survival Analysis

## Proje Amacı
Bu projede Titanic yolcularının hayatta kalmasını etkileyen faktörler veri analizi yöntemleri kullanılarak incelenmiştir. Amaç, veri keşfi (EDA), eksik veri yönetimi ve aykırı değer analizi ile yolcu özelliklerinin survival üzerindeki etkisini anlamaktır.

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
