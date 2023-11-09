![1_dUI9555WREvUtpNXlMM5-g](https://github.com/imelike/KaggleDatasets_into_GoogleColab/assets/128046415/b87134e2-1568-4854-a524-a1ba9cdc63c2)

#### Aşağıdaki kodları sırasıyla Colab Notebook üzerinde çalıştıralım

```
import pandas as pd 
import os

from google.colab import drive
drive.mount('/content/gdrive')

!ls
```
_out: gdrive sample_data_

# 
Kaggle hesabımızdaki kendi API tokenımızı(kaggle.json dosyası) alalım ve GDrive klasörüne koyalım (ör. MyDrive/Colab Notebooks/input)
![kaggle-account-settings-click-create-new-token](https://github.com/imelike/KaggleDatasets_into_GoogleColab/assets/128046415/1a0ff3dd-847c-4062-899c-75ed744659a1)


```
os.environ['KAGGLE_CONFIG_DIR'] = "/content/gdrive/MyDrive/Colab Notebooks/input"

#changing the working directory
%cd "/content/gdrive/MyDrive/Colab Notebooks/input"

#Check the present working directory using pwd command
!pwd
```
_out: /content/gdrive/MyDrive/Colab Notebooks/input_

#
Daha sonra indirmek istediğimiz veri setine gidelim ve aşağıdaki gibi API komutunu kopyalayalım, Colab'a dönüp kopyaladığımız komutu yapıştıralım **(yapıştırmadan önce başına ! koyalım)**
![Screenshot 2023-11-09 160404](https://github.com/imelike/KaggleDatasets_into_GoogleColab/assets/128046415/9227b709-5970-4504-88a5-bbdce178b469)
```
!kaggle datasets download -d savasy/multiclass-classification-data-for-turkish-tc32

!ls
```
_out: kaggle.json  multiclass-classification-data-for-turkish-tc32.zip_

```
# Veri seti zip klasöründen çıkarılır
!unzip \*.zip  && rm *.zip

!ls
```
_out: kaggle.json ticaret_yorum.csv_

```
# Veri setini dataFrame'e dönüştürelim

data = pd.read_csv('ticaret-yorum.csv')
pd.set_option('max_colwidth', 100)
data.head(5)
```
![image](https://github.com/imelike/KaggleDatasets_into_GoogleColab/assets/128046415/3d54e922-6592-4878-ace3-ccf418a8fa9d)


### References

[Kaggle Dataset is here.](https://www.kaggle.com/savasy/multiclass-classification-data-for-turkish-tc32?select=ticaret-yorum.csv)

[A blog post explaning how to download Kaggle Datasets is here.](https://medium.com/analytics-vidhya/how-to-fetch-kaggle-datasets-into-google-colab-ea682569851a)
