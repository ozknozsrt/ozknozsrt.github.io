--- 
title: Mobilde İkon Kullanımı ve Tarayıcı Sekmesi Rengi
date: 25.08.2018 18:00
---

![](https://media.giphy.com/media/3oGRFLswfKzceq5kLm/giphy.gif)  

Günümüz tarayıcılarında kullanıcılarla etkileşimi arttıran, ikon ve adres çubuğu rengi gibi belirli alanları özelleştirmeyi sağlayan basit ince ayarlar mevcut.

Web sayfamız görüntülendiğinde, tarayıcımız web sayfasının ikonunu favicon olarak çekebiliyor. Web sayfamızı mobilde incelediğimizde, aslında ikonumuzu diğer özelleştirilmiş alanlarda da göstermemiz mümkün.

**Tam olarak neresi oluyor bu özelleştirilmiş alan?**  

Tarayıcı sekmesi, arkaplanda çalışan uygulamaların görüldüğü bölüm, yeni sekme sayfası açarken çıkan alan gibi bir yerleri özelleştirebiliyoruz.  

Yalnızca modern tarayıcılarda çalışan bu özellik için `<head>` etiketi içine bir kaç tag eklemek yeterli.

```html
<!-- Yüksek çözünürlüklü ikon -->
<link rel="icon" sizes="192x192" href="icon.png">

<!-- Safari tarayıcısı için aynı ikonu tekrar çağır -->
<link rel="apple-touch-icon" href="ios-icon.png">

<!-- IE tarayıcıları için -->
<meta name="msapplication-square310x310logo" content="icon_largetile.png">
```

İkonların boyutları 48px, 96px, 144px ve 192px olması gerekiyor.
<br><br>

# Safari
Safari'nin kullandığı `<link>` etiketinin `rel` özniteliği: `apple-touch-icon` olması gerekir.

Her boyut için farklı bir etiket kullanarak farklı tema ve görünüme sahip olan telefonların ikonu otomatik olarak yeniden boyutlandırarak çözünürlüğünü bozmak yerine aşağıdaki etiketleri kullanarak farklı görünümler için farklı boyutlarda ikonları tanıtabilirsiniz.   

```html
<link rel="apple-touch-icon" href="touch-icon-iphone.png">
<link rel="apple-touch-icon" sizes="76x76" href="touch-icon-ipad.png">
<link rel="apple-touch-icon" sizes="120x120" href="touch-icon-iphone-retina.png">
<link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad-retina.png">
```
<br>
# Internet Explorer ve Windows Phone

Her ne kadar Türkiye pazarında fazla bir popülasyona sahip olmasa da hedef kitleniz windows phone kullanıyorsa aşağıdaki meta etiketlerini tanımlayabilirsiniz. 

```html
<meta name="msapplication-square70x70logo" content="icon_smalltile.png">
<meta name="msapplication-square150x150logo" content="icon_mediumtile.png">
<meta name="msapplication-wide310x150logo" content="icon_widetile.png">
```

<br>

# Renkli tarayıcı sekmeleri

Farklı `meta` etiketi kullanarak, tarayıcıyı özelleştirebiliyoruz. Sadece modern tarayıcılarda çalışacaktır.

```html
<!-- Chrome, Firefox OS ve Opera -->
<meta name="theme-color" content="#4285f4">
```