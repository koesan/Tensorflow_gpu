# Tensorflow_gpu

# 1.Cuda ve Cudnn sürümleri'nin belirlenmesi.

Öncelikle Tensorlfow sayfasından hangi cuda ve cudnn sürümlerini indireceğini belirlemelisin.

Tensorflow sayfası -->  https://www.tensorflow.org/install/source?hl=tr

![Ekran görüntüsü 2024-02-14 20-35-35](https://github.com/koesan/Tensorflow_gpu/assets/96130124/086f5465-71d7-4a9f-bca3-f8630be0cd5b)

örneğin tensorflow-2.13.0 için cuda 11.8 ve cudnn 8.6 yı kurmalısın.

# 2.Cuda kurulumu

İndireceğin cuda sürümünü belirledikten sonra https://developer.nvidia.com/cuda-toolkit-archive bu sayfadan kurmak istediğim cuda sürümünü kur.

Örneğin ubuntu 20.04 sürümüne cuda 11.8 sürümünü kurmak için.

`
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
`

`
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
`

`
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda-repo-ubuntu2004-11-8-local_11.8.0-520.61.05-1_amd64.deb
`

`
sudo dpkg -i cuda-repo-ubuntu2004-11-8-local_11.8.0-520.61.05-1_amd64.deb
`

`
sudo cp /var/cuda-repo-ubuntu2004-11-8-local/cuda-*-keyring.gpg /usr/share/keyrings/
`

`
sudo apt-get update
`

`
sudo apt-get -y install cuda
`

`
sudo reboot
`

# 3.cuDNN kurulumu

Kurduğun cuda sürümüne uygun cudnn sürümünü https://developer.nvidia.com/rdp/cudnn-archive sitesinden indir.

1. Cuda 11.8 için cudnn 8.6 sürümünü indireceksin.
2. terminalden `cd "dosyanın konumu"` komutunu kullanarak indirdiğin cudnn dosyası'nın olduğu dizine git
3. Bu komutu kullanarak indirilen paketi yerel paket deposuna ekle
`sudo dpkg -i cudnn-local-repo-${OS}-8.x.x.x_1.0-1_amd64.deb` cudnn-local-repo-${OS}-8.x.x.x_1.0-1_amd64.deb bu kısım yerine indirdiğin cudnn dosyasını yaz.
5. CUDA GPG anahtarını içe aktar.
`sudo cp /var/cudnn-local-repo-*/cudnn-local-*-keyring.gpg /usr/share/keyrings/`
6. `sudo apt update`
7. `sudo apt list libcudnn8` libcudnn8'in mevcut sürümlerümünü kontrol etmek için komutu çalıştır. 

    Örnek çıktı= `libcudnn8/bilinmeyen,now 8.6.0.163-1+cuda11.8 amd64`
   
9. `sudo apt install libcudnn8=8.x.x.x-1+cudaX.Y` 8.x.x.x-1+cudaX.Y CUDA ve cudnn sürümüne göre düzelt.

    ör= `sudo apt install libcudnn8=8.6.0.163-1+cuda11.8` 

10. `sudo apt install libcudnn8-dev=8.x.x.x-1+cudaX.Y` 8.x.x.x-1+cudaX.Y bu kısmı düzelt.

    ör= `sudo apt install libcudnn8-dev=8.6.0.163-1+cuda11.8` 

11. `sudo apt install libcudnn8-samples=8.x.x.x-1+cudaX.Y` 8.x.x.x-1+cudaX.Y bu kısmı düzelt.

    ör= `sudo apt install libcudnn8-samples=8.6.0.163-1+cuda11.8` 

# 4.cuDNN kurulumunu doğrula.

1. Terminalde `sudo apt-get install libfreeimage3 libfreeimage-dev` komutu ile gerekli kütüphaneleri yükle.
2. `cp -r /usr/src/cudnn_samples_v8/ $HOME`
3. `cd  $HOME/cudnn_samples_v8/mnistCUDNN`
4. `make clean && make`
5. `./mnistCUDNN`

CuDNN, düzgün bir şekilde yüklenmiş ve çalışıyorsa, aşağıdakine benzer bir mesaj göreceksin:

`Test passed!`

Not. Test Başarılı olmadıysa, eksik bir paketin kurulması gerekebilir. Terminal çıkışında belirtilen paketleri kur ve 4. adımı tekrar uygula.

# 5.Tensorflow kurulumu.

Terminalde `pip3 install tensorflow==2.15.0` komutunu çalıştırıp Tensorflow kurulumunu gerçekleştir.

# 6.Kurulumunu Doğrulama

Terminali açıp

1. `python3` komutunu çalıştır.
2. `import tensorflow as tf` kodu ile tensorflow kütüphanesi'nin importet.
3. `print(tf.test.is_gpu_available())` kodu çalıştır.
4. Çıktı `True` ise kurulum başarılı olmuştur.












