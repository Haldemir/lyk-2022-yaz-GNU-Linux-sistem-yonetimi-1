# LYK-Sistem 1 Gün_2

```bash
$rmdir
remove directory - sadece dizin boş ise dizini kaldırmaya yarar 

ama rm -r ile farkı rmdir sadece klasör boş ise kaldırma işlemi yapar
```

Neden rm kullanırken normalden daha fazla dikkatli olmalıyız ? Linux’da w*ndowsdaki gibi geri dönüşüm kutusu tarzı bir şey yok yani silme işlemi gerçekleştiği anda dosyayı ulaşılamayan kara bir deliğe gönderiyor. Bu yüzden yedeklerimizi almayı ve dosya silme işlemi yaparken neyi sildiğimize dikkat etmeyi unutmayalım.

TO-DO:

&nbsp;&nbsp;symbolick link

&nbsp;&nbsp;block special

&nbsp;&nbsp;dosya türleri

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“-” standart dosyalar

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“l” sembolik link

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“d” directory

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“c” character special

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“b” block file

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“s” socket

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;“p” pipe?

&nbsp;&nbsp;dosya sistemleri

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ext4 → journal/jounal

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fat32

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;exfat

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;xfs

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;zfs

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ntfs

peki hangisini kullanıcaz? bakıcaz ne istiyoruz ve ona göre okuyuş şekillerini inceleyip işimize yarayanı kullanıcaz

## Mutlak yol (Absolute  Path) ve Bağıl yol (Relative Path) nedir ?

Mutlak yol: dosya sisteminin başlangıcından yani “/” den itibaren verilen yol, Bağıl yol ise bulunduğun konumdan itibaren verilen yoldur. Örneğin çalıştığımız konumda bulunan bir dizinin içindeki dosyayı okumak istiyoruz.

```bash
Bağıl yol ( Relative Path )
~$cat configs/vim_config.txt
Mutlak yol ( Absolute Path )
$cat /home/haldemir/configs/vim_config.txt
```

Yav biz arada bir root, root olmamız lazım, root yetkisiyle çalışıyor falan diyoruz, ee peki bu çocuk kim ve ne yapıyor ? Türkçesi kök olan, sistemde her şeyi yapabilme olanağını sağlayan kullanıcıdır. (w\*ndowsdaki admin veya administrator gibi kafanızda canlanabilir ama sadece mantık olarak canlansın çünkü w\*ndowsda her şeye erişimimiz yok). Ve biz faniler olarak yanlış dosyaları bknz.(aklıma gelmedi sistemin çalışmasını gerektiren önemli bir dosya işte) silme gafletinde bulunabiliriz. Neyi neden çalıştırdığımızı, dosyayı kaldırdığımızda ne olacağını bilmiyorsak dikkat edelim ve root yetkisine sahip olmayan bir kullanıcı ile etrafda gezinelim. Tabi aynı şey normal kullanıcı için de geçerli herhangi bir komut çalışmadı diye başına şakkadanak sudo koyup geçmeyelim.

Peki böyle bir kudretli kullanıcıya, son kılıç bükücü jedi’a, ufukların ardındaki gandalfa :kappa: niye ihtiyacımız var ?  Hiyerarşi için başta duracak bir yetkili abimizin olması lazım. Çünkü normal kullanıcıların erişemediği dosyaları okuma veya yazma, sistem configürasyonlarını değiştirme, herhangi bir paketi indirme kaldırma, sistemi veya donanımın yazılımlarını güncelleme gibi gibi önemli işleri yapacak biri gerekiyor.

TO-DO:

nano - nedir, kullanımı

## /etc/passwd’de neler var ?

## /etc/group

## Öğrendiğimiz komutların manual sayfalarını okuyarak ne işe yaradığını öğrendik peki aklımızdaki komutu unuttuk veya x konusunda işimize yarayacak bir komut arıyorsak ne yapabiliriz ? illa google’a mı gidelim.

```bash
$man -k <kelime> veya $apropos <kelime>
bu arkadaşlar ile sistemdeki manuel sayfaları arasında, komutların açıklandığı isim 
kısmında istediğimiz kelimeyi kolayca aratabiliriz
```

TO-DO:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;adduser

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;useradd

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;usermod

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;userdel

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;grouplu bir şeyler

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;groupmod

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;gruopadd

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;groupdel

## İçinde metin bulunan dosyaları okumak için birkaç yol öğrendik peki

Eğer sadece dosyaları okumak ve/veya sayfalar arasında kaymak istiyorsak illa text editörleriyle (vi, nano) birlikte ile açmak zorunda değiliz. İkisiyle de dosyaları okuyabiliriz. Peki aralarındaki tek fark more komutu ile dosyayı okumaya çalıştığımızda, eğer dosya ekranı kaplayacak ölçekden büyükse, alt kısımda ekrandaki dosyanın ne kadarını okuyabildiğimizi gösteren yüzde mi var ? Tabiki hayır. Adından da yola çıkarak düşünülürse, “more” ve “nano  veya vi” dosyayı açarken önce dosyanın tamamını okuyup kullanıcıya gösteriyor ama “less” dosyayı sayfa sayfa okuyor yani tek seferde bütün dosyayı okumak zorunda değil.

```bash
$tail
$head

```
