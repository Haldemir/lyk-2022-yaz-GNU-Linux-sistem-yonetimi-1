
Sistemde bir komut çalıştırıyoruz örneğin pwd yazdığımızda bize bulunduğumuz dizini söylüyor, peki dosyayı nereden çalıştırması gerektiğini veya bulunduğumuz konumu nereden biliyor bunlar ?

Herhangi bir dosyayı çalıştırdığımız zaman, dosyanın çalışabilmesi için belli başlı bilgileri işletim sistemi abimizden istemesi lazımki işini yapabilsin. Bu yüzden, Çevresel Değişkenler (environmental variables) diye bir meret var ve sistemdeki uygulamalara veya dosyalara çalışırken kolaylık sağlıyor. Eğer bir çok uygulamala aynı şeylere ihtiyaç duyuyorsa niye hepsi ayrı ayrı uğraşıp belli başlı değişkenleri bulmak için OS’a sorsun veya uğraşsın. O yüzden çevresel değişkenler diye bir şey oluşturulmuş ve her kullanıcıya da özel olarak ayarlanmış.

```bash
$env
çalıştıran kullanıcı için kayıtlı çevresel değişkenleri gösterir
```

Peki $LANG değişkenini değiştirdikten sonra açılan uygulamalar türkçe dil desteğiyle birlikte çalışıyorsa veya $PATH değişkenini sıfırladıktan sonra çalıştırdığımız komutlar çalışmıyorsa, $USER değişkenini değiştirdiğimiz zaman neden yeni dosya oluşturulduktan sonra dosyanın sahibi değişmiyor ?
Çünkü dosyayı oluşturan kişiyi global değişkende okunup yazılmıyor. Onun yerine anladığım kadarıyla USER ID'ye ve birkaç değişkene göre işlem yapılıyor.
 

## SUDO

Buraya not düşmek istiyorum, sudonun açılımını ve aslında ne amaçla kullanıldığını öğrendiğiniz zaman hayel kırıklığına uğrayabilirsiniz. Çünkü internette veya topluluklarda çoğu insan SUDO’yu

Super User Do olarak bilir. Ama manual sayfasına da baktığımızda asıl amacının Switch User Do olduğunu göreceksiniz. Kandırıldık leennn. 

```bash
$sudo -u mahmut ls /home/mahmut
mahmut kullanıcısına özel olan ev dizinini mahmutun parolasını girdikten sonra listeyebiliyoruz
ve böylece mahmut kullanıcısına girip listeledikten sonra çıkmamıza gerek kalmıyor.
```

Tabi aslında genel kullanımı olarak sadece sudo yazıp istediğimiz komutu çalıştırdığımız için sudo kullanıcı girilmezse kendisi otomatik olarak rootu baz alarak işlemi gerçekleştiriyor.

## Dosya İzinleri ve Yetkiler

TO-DO: yazılacakke

r = 4 → 2^2

w = 2 → 2^1

x = 1 → 2^0

- = 0

```bash
$chmod
```

Peki neden dizinlerin read ve execute yetkisi var da dosyaların sadece read yetkisi var ?

TO-DO:

```bash
$realpath

$basename

$dirname
```

## Operatörler

```bash
|
sol kısmındaki çıktıyı sağ tarafdaki girdiye yollar
Usage:
	history | grep "rmdir"
```

```bash
>
sol kısmındaki inputu yani standart girdiyi sağ tarafdaki dosyaya overwrite eder.
Usage:
	echo "Buralara kadar gelmiş zahmet etmişsin efenim" > welcome.txt
>>
sol kısmındaki inputu yani standart girdiyi sağ tarafdaki dosyaya ekler.
Usage:
	history > gecmis.back
```

```bash
<
<<
```

TO-DO:
tee

&&

||

true

false