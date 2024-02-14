# Tensorflow_gpu

* Cuda ve Cudnn sürümleri'nin belirlenmesi.

Öncelikle Tensorlfow sayfasından hangi cuda ve cudnn sürümlerini indireceğini belirlemelisin.

Tensorflow sayfası -->  https://www.tensorflow.org/install/source?hl=tr

![Ekran görüntüsü 2024-02-14 20-35-35](https://github.com/koesan/Tensorflow_gpu/assets/96130124/086f5465-71d7-4a9f-bca3-f8630be0cd5b)

örneğin tensorflow-2.13.0 için cuda 11.8 ve cudnn 8.6 yı kurmalısın.

* Cuda kurulumu

İndireceğin cuda sürümünü belirledikten sonra https://developer.nvidia.com/cuda-toolkit-archive bu sayfadan kurmak istediğim cuda sürümünü seçip kurmalısın.

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

