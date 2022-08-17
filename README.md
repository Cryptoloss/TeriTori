# TeriTori

_Selam Dostlar bugün sizlerle birlikte otomatic olarak TeriTori Node testnetine katılacağız._
Bilinmesi Gerkenler

Şuan Node testneti ödülsüz, ileride ödüllü olacağını düşünüyorum fakat active sette sadece 100 kişi var boş VPS yoksa katılmayın. 

Puan: 3/10
![image](https://user-images.githubusercontent.com/98783018/183394932-2f80da82-a59f-476f-bd95-5b039eca7c90.png)

**Sistem gerekesinimleri**
```
4 CPU

8B RAM

200 SSD Disk
```

Otomatik FUll Node Kurma Komutu

```
wget -O teritori.sh https://raw.githubusercontent.com/kj89/testnet_manuals/main/teritori/teritori.sh && chmod +x teritori.sh && ./teritori.sh
```

Aşağıdaki kod ile kurulum işlemini başlatıyoruz.Bizden bir isim girmemizi isteyecek girip enterlayarak işleme devam ediyoruz.Kurulum bittiğinde aşağıdaki resimdeki attığım gibi bir görüntü sizi karşılıyor olacak.

![image](https://user-images.githubusercontent.com/98783018/183396726-f0ba2cf1-6488-4d1f-ad77-0746b0c367f6.png)

Aşağıdaki kod ile false olup olmadığınızı kontrol edin . ''false'' komutu çıktığında işleme devam edebilirsiniz.

```
teritorid status 2>&1 | jq .SyncInfo.catching_up
```
**5-6 Saat bekledikten sonra FALSE olmazsa aşşağıdaki kodları sırasıyla girelim.** False çıktısı aldıysanız girmeyin.

```
sudo apt update

sudo apt install lz4 -y 

sudo systemctl stop teritorid
teritorid tendermint unsafe-reset-all --home $HOME/.teritorid --keep-addr-book

cd $HOME/.teritorid

rm -rf data

SNAP_NAME=$(curl -s https://snapshots2-testnet.nodejumper.io/teritori-testnet/ | egrep -o ">teritori-testnet-v2.*\.tar.lz4" | tr -d ">")
curl https://snapshots2-testnet.nodejumper.io/teritori-testnet/${SNAP_NAME} | lz4 -dc - | tar -xf -

sudo systemctl restart teritorid

sudo journalctl -u teritorid -f --no-hostname -o cat
```
Aşağıdaki kod ile cüzdan adresini oluşturunuz ve tüm bilgileri kaydedin..wallet yerine herhangi belirlediğiniz bir cüzdan ismi giriniz.
```
teritorid keys add wallet
```

Şimdi TeriTori [discorda](https://discord.gg/Q6TFfRBr) gidiyoruz verify yapıyoruz ve cüzdanımıza token talep ediyoruz.
![image](https://user-images.githubusercontent.com/98783018/183397893-0981c6d3-099b-4117-bac5-767424662c4b.png)

**Moniker** yerine node kurulum yaparken yazdığınız isimi giriniz.**Wallet** yerine ise cüzdan adınızı giriniz.
```
teritorid tx staking create-validator --chain-id teritori-testnet-v2 --commission-rate 0.1 --commission-max-rate 0.1 --commission-max-change-rate 0.1 --min-self-delegation "900000" --amount 900000utori --pubkey $(teritorid tendermint show-validator) --moniker “Cryptoloss” --from wallet --fees 555utori

```

Aşağıdaki resimdeki gibi bir çıktı alacaksınız bu TX hash çıktısını Tori [explorerde](https://teritori.explorers.guru/) aratınız success dediyse validatörünüz oluşmuş demektir..

![image](https://user-images.githubusercontent.com/98783018/183398481-93c9b178-6cf9-49cb-a816-ea3b300fc05c.png)

Daha sonra yapmamız gereken bir işlem daha kaldı.Validatör ismimize tıklıyoruz ve [validatör](https://discord.gg/Q6TFfRBr) linkimizi kopyalıyoruz bunu Discorda atacağız ve validatör rolü alacağız.

Discordda role-requests kanalına giriyoruz ve validatörümüzün linkini atıyoruz.Ekip gördükden sonra size validatörü rolü verilecektir.

![image](https://user-images.githubusercontent.com/98783018/183398978-8d35aaff-73b7-47f3-b3b1-acd1f12fd06b.png)

Şimdi ekstra ödüller kazanabilmek için quest görevlerine geçiyoruz.[**TIKLA**](https://teritori.crew3.xyz/invite/nd229qsYta5L3YliC1Xlt)

Discord adresimiz ile bağlanıyoruz metamask cüzdanınızı bağlamanıza gerek yok bir kullanıcı adı yazıyoruz ve hazırız.

Aşağıdaki resimde gördüğünüz gibi twitter adreslerini takip ediyoruz quest sekmesinde görevleri görebilirsiniz yaptıkça bir çok bölüm açılacaktır ve puan kazanacaksınız.Ayrıca hergün yeni görevler gelebilmektedir arada bir bakmakda fayda var.

![image](https://user-images.githubusercontent.com/98783018/183399446-4bc9aa9d-97d5-4a18-b62e-06e8a91d4303.png)

Daha sonra sol üstten bir profil oluşturup açılan görevleri yapıyoruz

Destek için:

Telegram:https://t.me/LossNode

Tüm Sosyal Medyalarımız:https://linktr.ee/Cryptoloss



