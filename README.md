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
girmeniz yeterli olacaktır.