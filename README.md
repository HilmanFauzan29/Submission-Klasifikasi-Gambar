# Proyek Klasifikasi Gambar: Klasifikasi Jenis Sepatu

## Deskripsi

Proyek ini adalah project klasifikasi gambar yang menggunakan dataset sepatu yang digunakan untuk klasifikasi. Proyek ini menggunakan dataset yang diunduh dari Kaagle. Dataset terdiri dari 12.500 gambar yang memiliki 5 kelas yaitu Boots, Sandals, Slippers, Sneakers, dan Formal Shoes. Dataset dibagi menjadi data train, data validation, dan data test dengan perbandingan 70/15/15.

## Arsitektur Model
Model yang digunakan yaitu menggunakan model sequential dengan pendekatan transfer learning. Model basenya yaitu ResNet101V2 yang sudah dilatih sebelumnya di dataset ImageNet. ResNet ini secara internal sudah memiliki banyak lapisan Conv2D dan pooling. Setelah base model dibekukan (tidak ikut dilatih di awal), kami menambahkan satu lapisan Conv2D dan MaxPooling2D secara eksplisit, lalu diikuti oleh GlobalAveragePooling2D, Dense dengan 128 unit, dan Dropout untuk mencegah overfitting. Terakhir, ditambahkan lapisan output Dense dengan 5 unit dan aktivasi softmax untuk klasifikasi 5 kelas.  Setelah pelatihan awal, model di-fine-tune dengan membuka (unfreeze) 60 lapisan terakhir dari ResNet101V2 dan melatihnya kembali bersama lapisan tambahan menggunakan optimizer Adam dengan learning rate sangat rendah (6e-6). Hal ini dilakukan agar bobot pra-latih bisa menyesuaikan secara halus dengan dataset yang digunakan.

## Hasil Akurasi Model
Hasil pelatihan model klasifikasi gambar ini untuk akurasi training sebesar 93,65% dan akurasi testing sebesar 85,55%.

## Credits
- Dataset: [Shoes Classification Dataset - 13k Images](https://www.kaggle.com/datasets/utkarshsaxenadn/shoes-classification-dataset-13k-images)

## File requirements
File requirements dibuat dengan menggunakan  pip freeze requirements.txt di visual studio code