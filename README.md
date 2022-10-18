# coredns-gih
CoreDNS üzerine geliştirilmiş güvenli internet hizmeti yazılımı



# Nasıl Kullanılır?

https://dev.to/n1try/how-to-enable-dns-over-tls-on-ubuntu-using-coredns-18mp

Adresinden işletim sisteminizi DNS sunucusuna göre hazırlamalısınız.

Öncelikle coredns binary dosyasını çalıştırılabilir yapmanız gerekli.
```
chmod +x coredns
```
ardından aşağıdaki komut ile 1053 portunda bir dns sunucu oluşturmuş olacaksınız. 
```
./coredns -conf=CoreFile
```
CoreFile dosyasyında ki 1053 portunu 53 (Default DNS Portu) olarak düzenleyebilirsiniz.

Ardından bilgisayarınıza veya yönlendiricinize sunucunuza ait ip adresini girerek filtrelenmiş DNS erişim sağlayabilirsiniz.

# Adresleri nasıl engelleyecek

Sha1 olarak hash haline getirilmiş domain isimlerini gibirgih.host dosyasına her domain tek bir satır olacak şekilde
```
0.0.0.0 5e1f4f7baf524cadb03dbbffde68dc8c1ef253e3
```
girmeniz yeterli olacaktır. Bunu herhangi bir şekilde kendiniz geliştirebileceğiniz gibi aşağıda ki şekilde otomotize de edebilirsiniz.


Önce mysql client kuralım
```
apt install mysql-client

```

Ardından aşağıda ki komut ile mysql den gerekli domainler lokal dosyaya kayıt edilir.

-p den hemen sonra boşluk olmadan mysql şifrenizi girin

```
mysql -h GIH-SUNUCU-IP-ADRESI -u root -p GIH_CLIENT -e "SELECT '0.0.0.0 ', hedef FROM GIH_CLIENT.SITEVEIP where kategori = 'K' group by hedef" > gibirgih.host

Örnek mysql -h 127.0.0.1 -pBenimsifrem GIH_CLIENT ......
```
Kurduğunuz DNS sunucunun özelliklerine göre kategori = 'K' kısmını değiştirebilir veya kombine etmek için  kategori = 'K' or  kategori = 'O' yapabilirsiniz.

- K	Kara Liste
- B	Beyaz Liste
- C	Sohbet
- O	Oyun
- S	Sosyal Medya
- U	Uygun Icerikli Oyun
- W	Cocuk Haric

Bu kodu cronjoba bağlayarak listeyi güncel tutabilirsiniz.


# Daha fazla detaya ihtiyacım var ?

https://coredns.io/manual/toc/

Adresinden coredns hakkında daha fazla bilgiye ulaşabilirsiniz.


# Service olarak çalıştırma

İsterseniz derlenmiş coredns dosyasını işletim sisteminizde servis olarak çalıştırabilirsiniz.

https://github.com/coredns/deployment/tree/master/systemd


# Credits
https://coredns.io/

https://kurumsal.gibir.net.tr

https://gibir.net.tr