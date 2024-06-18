# Ritual-Network-Testnet

# ritual-network


## Sistem Gereksinimleri

# PEK Bişey Harcamıyor Şu Anlık.
| Bileşenler | Minimum Gereksinimler | 
| ------------ | ------------ |
| Ubuntu 20.04.2 |
| CPU |	2 |
| RAM	| 4 GB |
| Storage	| 100 GB SSD |

# Sunucumuzu Güncelliyoruz.

```
apt-get update
```

```
apt-get -y update && apt-get -y upgrade
```

```
apt-get install libav-tools
```

```
sudo apt-get install make
```

# Dockeri Kuruyoruz.

```
sudo apt install gnome-terminal
```

```
sudo apt-get update
```

```
sudo apt-get install ca-certificates curl
```

```
sudo install -m 0755 -d /etc/apt/keyrings
```

```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

```
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

# Ritual Reposunu Klonluyoruz.

```
git clone --recurse-submodules https://github.com/ritual-net/infernet-container-starter
```

Repo İçerisine Giriyoruz.

```
cd infernet-container-starter
```

Screen Açıyoruz.

```
screen -S ritual
```

# hello-world'u Oluşturuyoruz.

```
make build-container project=hello-world
```

RUN Ediyoruz.

```
make deploy-container project=hello-world
```

Loglar Akmaya Başlayınca Screenden Çıkın. CTRL+A+D


# Config dosyamızın Bazı Yerlerini Değiştiriyoruz.

1-) RPC, Şunu Yazın: https://base-rpc.publicnode.com/

2-) Coordinator address bunu yazın: 0x8d871ef2826ac9001fb2e33fdd6379b6aabf449c

3-) PRİVATE KEYİMİZİ Değiştiriyoruz.

4-) Daha Sonra CTRL+X+Y+ENTER Diyerek Kaydediyoruz.

Config Dosyamıza Girelim.

```
cd
```

```
cd infernet-container-starter/deploy
```

```
nano config.json
```

# Restart Atıyoruz.

```
docker restart anvil-node
```

```
docker restart hello-world
```

```
docker restart deploy-node-1
```

```
docker restart deploy-fluentbit-1
```

```
docker restart deploy-redis-1
```

# En Son Node Kaydetme Var Ama Hata Alıyorum Sürekli Bilen Varsa Çözümünü PR Atabilir.

Şu Komutla Containerlara Bakın.

```
docker ps
```

Resimdedki Gibi Gözükecek.

![Ekran görüntüsü 2024-03-30 013039](https://github.com/tuncgs52/ritual-network/assets/80161670/12b576c2-0f2e-49f9-b3c2-4b8889978616)

Kayıt İçin Şu Komut Var. Bütün Containerları Kayıt Edip, Aktif Etmek Gerekiyor.

KAYIT KOMUTU

```
docker exec container-name make register-node
```
Aldığım Hata ise Şu Resimde Mevcut.

![Ekran görüntüsü 2024-03-30 013508](https://github.com/tuncgs52/ritual-network/assets/80161670/a6036d90-5e9f-426f-8ee6-62cd268ebf61)
