# rs-calisma

Uydu görüntülerini Python ve derin öğrenme ile işleme çalışmaları. Antalya Bilim Üniversitesi Uzaktan Algılama ve Coğrafi Bilgi Sistemleri Laboratuvarı kapsamında yürütülüyor.

Hedef: laboratuvarın uydu görüntülerini işleyecek bir model kurmak ve eğitmek. Yol, klasik yöntemlerden (spektral indeksler, Random Forest) derin öğrenmeye (CNN, U-Net) doğru ilerliyor.

## Çalışma programı

| Hafta | Tarih | Konu | Çıktı | Durum |
| --- | --- | --- | --- | --- |
| 0 | 8–11 Eki 2026 | Ortam kurulumu | Kurulu ortam, ilk görüntü okuma | Tamamlandı |
| 1 | 12–18 Eki | Python kütüphaneleri | Antalya RGB ve NDVI haritası | Başladı |
| 2 | 19–25 Eki | Uzaktan algılama temeli, GitHub projeleri | Hazır bina segmentasyonu modelinin çalıştırılması | |
| — | 26 Eki–8 Kas | Vize arası | — | |
| 3 | 9–15 Kas | Makine öğrenmesi | Random Forest ile arazi sınıflandırma haritası | |
| 4 | 16–22 Kas | PyTorch ve CNN | İlk CNN sınıflandırıcı | |
| 5 | 23–29 Kas | U-Net | Bina segmentasyonu, IoU sonucu | |

## Klasör yapısı

```
rs-calisma/
├── hafta1_kutuphaneler/   rasterio, NumPy, matplotlib, geopandas
├── hafta2_rs_github/      uzaktan algılama temeli, repo incelemeleri
├── hafta3_ml/             scikit-learn, Random Forest
├── hafta4_pytorch/        PyTorch temelleri, ilk CNN
├── hafta5_unet/           U-Net ile bina segmentasyonu
├── veri/                  uydu görüntüleri (git'e eklenmez)
└── notlar.md              terimler, sorular, repo notları
```

## Ortam kurulumu

[Miniconda](https://docs.conda.io/en/latest/miniconda.html) kurulduktan sonra Anaconda Prompt'ta:

```
conda create -n rs python=3.11
conda activate rs
conda install -c conda-forge rasterio geopandas matplotlib scikit-learn jupyterlab libgdal
```

`libgdal` paketi gerekli: Sentinel-2 bantları `.jp2` biçiminde ve bu biçimi okuyan GDAL eklentisi onunla geliyor.

Çalışmaya başlarken:

```
conda activate rs
cd Documents\GitHub\rs-calisma
jupyter lab
```

GPU gerektiren eğitimler [Kaggle](https://www.kaggle.com) notebook'larında yapılıyor.

## Veri

- **Sentinel-2 L2A**, [Copernicus Browser](https://browser.dataspace.copernicus.eu) üzerinden ücretsiz indiriliyor. Kullanılan ilk sahne: 19 Eylül 2026, karo T36STG (Antalya'nın kuzeyi).
- Görüntüler büyük olduğu için `veri/` klasörü `.gitignore` ile hariç tutuluyor. Notebook'ları çalıştırmak için sahneyi indirip bu klasöre açmak gerekiyor.

## İlerleme

**8 Ekim 2026:** Ortam kuruldu, Sentinel-2 sahnesi indirildi, B04 (kırmızı) bandı rasterio ile açılıp konum bilgileri okundu: 10980 × 10980 piksel, 10 m çözünürlük, UTM 36N (EPSG:32636). → `hafta1_kutuphaneler/01_rasterio.ipynb`

## Kaynaklar

- [rasterio](https://rasterio.readthedocs.io/) · [NumPy](https://numpy.org/doc/stable/) · [geopandas](https://geopandas.org/) · [scikit-learn](https://scikit-learn.org/stable/)
- [PyTorch eğitimleri](https://pytorch.org/tutorials/) · [TorchGeo](https://torchgeo.readthedocs.io/) · [segmentation_models.pytorch](https://github.com/qubvel-org/segmentation_models.pytorch)
- [satellite-image-deep-learning/techniques](https://github.com/satellite-image-deep-learning/techniques)
