TO-DO: dosya uzantılarının hiç bir önemi yok agam linuxda

### SSH nedir ?


Açılımı Secure Shell’dir. Bilgisayarlar arasındaki bağlantıyı şifreleyerek iletişimi sağlayan programdır. Yani uzaktan sistemlere bağlanmamıza yardımcı oluyor.

Ee peki Secure Shell falan dedik. Peki nedir bu Shell ? Türkçe olarak kabuk anlamına geliyor ve kernel ( çekirdek ) ile donanıma erişmemizi sağlıyor.

Kurduğumuz sanal makinelere sadece ana makinemizden ssh ile bağlantı yapabilmek için Virtualbox’ın Host Network Managerından host-only internet adaptörü oluşturduk. Sonra sanal makinelerimizin ağ ayarlarından bu oluşturduğumuz adaptörü Host-only adaptör seçeneğinden bağladık.

Uzaktan bağlantı kurabilmemiz için makinelere ıp adresi almaya çalıştık.

**Rocky** kendi kendine DHCP aracılığıyla kendine ip atayabiliyor ama kıl olan **Debian** bu işlemi kendi kendine yapamıyor. Bu yüzden makine ağ ayarlarından default olarak gelen NAT seçeneği seçili olan adaptörü devre dışı bırakıyoruz, daha sonra makineden DHCP'den ip alıyoruz.

```bash
$ip a
görüldüğü üzere sadece localhost var
$dhclient
ip dağıtılma işlemi gerçekleştirildi kontrol edelim
$ip a
görüldüğü üzere artık bu makinemizin de internete çıkabilmesi için bir ip adresi var.
```

ip adresi alım işlemi gerçekleştikten sonra makinemizi internete çıkabilir hale geri getirebiliriz. ( Devre dışı bıraktığımız adaptörü aktifleştirerek. )

### SSh ile uzak sunucuya bağlanmak

Uzak sunucuya bağlanmak için bize bağlanılacak makinenin adresi ( IP ), hangi kullanıcıya bağlanılacaksa kullanıcının adı ve parolası gerekiyor.

Popüler ssh hizmeti sağlayan uygulamalar;

- Git Bash
- Putty
- bla bla

Popüler ve Özgür yazılım olsun bizim olsun :d

### Git Bash ile ssh bağlantısı yapmak

```bash
$ssh -l <kullanıcı_adı> <makine_adresi> or $ssh <kullanıcı_adı>@<makine_adresi>
```

# Temel Linux Komutları

TO-DO: fotolarla daha çekici hale getirilebilir

Linux da her şey bir dosyadır.

Başında nokta varsa gizli dosya olmuş olur tabi ne kadar gizli ? normalde gözükmesini istediğimizi dosyaların başına nokta atarak gizleyebiliriz.

```bash
$whoami
sistemde hangi kullanıcıda oturum açıldığını söyler
```

```bash
$pwd
Print Working Directory - açılımından anlaşıldığı üzere bulunduğumuz dizini gösterir
```

```bash
$man
Manual - eğer çalıştırılan komutun sistemde manuel sayfası bulunuyorsa onu gösterir.
Daha da açıklamak gerekirse insanlar dosyalarının veya uygulamalarının ne işe yaradığını,
hangi parametreleri aldığını veya parametrelerin ne işe yaradığını içeren bir döküman 
açılır.
```

### Ahmetcan hocanın da sık sık söylediği gibi takıldığın bi yerde “Bana bakma man’a bak” 😀

Manuellerdeki parametrelerin açıklandığı kısımların yanında tek tre işareti ile (-) harf yazıyor ama bazılarının yanında iki tane tre işareti ile (—) uzun ismi yazıyor. Neden ?

Çalıştığımız şirketlerde daha önceden kullanılan bir komutu kullanacağımızı varsayalım ve çalışan sallıyorum şöyle karmaşık bir komut çalıştırmış.

```bash
$compgen -abcdefgjksuv | grep "?est*"
```

Böyle bir komut gördüğümüz zaman pek anlışılabilir durmuyor bu yüzden başkalarının da ne yapmak istediğimizi daha rahat anlayabilmesi için uzun isimlerini kullanmak isteyebiliriz. Örneğin;

```bash
	$ls /home/haldemir/Desktop --all --block-size --color=auto | grep "?est*"
```

görüldüğü üzere okunup daha rahat anlaşılabilir bir komut oldu.

```bash
$ls
list - dizindeki dosyaları listelemeye yarıyor.
$ls -l
long - dosyaları biraz daha detaylı bir şekilde liste halinde alt alta gösteriyor.
$ls -a
all - gizli dosyalar da dahil gösteriyor yani dizinde kim var kim yok gösteriyor

```

Ayrıca tek çizgiden sonra parametreler birleştirilebiliyor. Arka arkaya gereksiz şeyler yazmaktan kaçınabiliriz. Örneğin;

```bash
$ls -a -l 
yazmak yerine
$ls -al
hem bütün dosyaları göster ve hem de daha detaylı bir şekilde göster
```

### Gizli dosyaları da listeledik anam bir de ne görelim . ve .. olmak üzere iki dosya daha gözüküyor ?

. bulunduğumuz dizini temsil ediyor ve .. bir üstteki dizini temsil ediyor.

TO-DO: sütunların ne işe yaradığı yazılacak.

```bash
$cd
change directory - dizinler arasında gezinmek için işimize yarıyor.
> kullanımı
$cd Downloads
Downloads klasörüne gir
$cd ..
bir dizin üste çıkar

>bazı pratik bilgiler;
$cd -
en son bulunan dizine gider
$cd ~
kullanıcının home dizinine gider
```

```bash
$history
shellde kullanılan komutların geçmişini gösterir.

geçmişimizi tarayıp aradığımızı bulduk peki bu komutu nasıl çalıştırabiliriz illa kopyala
yapıştır mı yapmamız gerekiyor ?
$!<istedigimiz_komutun_bulundugu_satirin_numarasi> 
```

```bash
$help
çekirdeğin içerisinden gelen komutların kısaca kullanım yapısını gösterir.
```

```bash
$info
sistemin içerisinden gelen komutların ne işe yaradığını gösteriyor.
```

```bash
$cat
????????????
```

Elimizde mahmut.pdf.jpg adında bir dosya var peki bu dosyanın neci veya kimlerden olduğunu, acaba açılabilir bir fotoğraf mı ya da arkada bir şeyler çalıştırabilecek bir uygulama mı olduğunu bakarak anlayamıyoruz. Elimizde de güvenli bir ortamda dosyayı çalıştırıp ne işe yaradığını öğrenemeyeceğimizi varsayarsak ne yapabiliriz ?

```bash
$file <dosya_adi>
dosyanın tipini metadatasını inceleyerek söylüyor. Acaba bize söylediği %100 doğru mu ?
```