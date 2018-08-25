--- 
title: Chrome'da Eklentisiz Screenshot
date: 25.08.2018 20:50
---

Geçenlerde yine inspect modundayım, yanlışlıkla kendimi VSCode'da sanıp `CTRL + P` yapmıştım, bir tane kutu geldi sayfanın render ettiği dosyaları gösteren.  

*Type '?' to see aviable commands* demiş, işime yarayabilir bir şeyler çıkar diyerek kurcuklayayım dedim.

| No  | Key |   Açıklama    |
| --- | --- | ------------- |
| 1   |...  | Open file     |
| 2   |:	  | Go to line    |
| 3   |@	  | Go to symbol  |
| 4   |!	  | Run snippet   |
| 5   |>	  | Run command   |

Buradan `Open file` seçeneği kullanılabilir dosyalarda gezinmek için.
`Go to line` kesin kullanırım belirli satıra gitmek için süper olur.  
`Go to symbol` tam olarak çözemedim ama anladığım kadarıyla css ve javascript kodlarında ilgili değişken ve fonksiyonlara gidiyor.  
`Run snippet` bunu daha önce kullanmamıştım ama bu özelliğinde de kullanışlı olduğunu anladım. Hemen açıklayayım;

### Run snippet

DevTools'da `Sources` sekmesine geldikten sonra sol taraftaki sidebarda genellikle `Page` seçili gelir. Aslında orada 5 adet sekme bulunuyor. Sidebarı genişletince veya **>>** ikonuna tıkladığımızda `Snippet` sekmesi karşımıza çıkacak.

Burada `+ New Snippet` diyerek içerisine; nasıl ki console kısmına bazen sürekli yazdığımız kodlar oluyor ya, hah! işte o kodları her zaman yazmayalım diye buraya "snippet" olarak ekleyebiliyoruz ve tek komutla çalıştırabiliyoruz. Çok güzel değil mi yav :)


### Geldik asıl olaya, eklentisiz screenshot nasıl alırız :)

5 numaralı `Run Command` kısayolumuz, diğer bir kısayolu `CTRL + SHIFT + P` olan komut çalıştırma bölümü. Burada türlü tefarek olaylar dönüyor, hepsini anlatmaya gün yetmez. Siz deneyip bulursunuz onları artık, ben yolu gösterdim :)

Şimdi burada `>screenshot` yazıyoruz

| No | Komut                        | Açıklama                                                           |
|----| ---------------------------- | ------------------------------------------------------------------ |
|1   | Capture full size screenshot | Ekranın baştan aşağı tam görüntüsünü alıyor                        |
|2   | Capture node screenshot      | `CTRL + SHIFT + C` ile seçili olan alanın görüntüsünü alıyor       |
|3   | Capture screenshot           | Bulunan pencerenin monitöre göre gözüken kısmın görüntüsünü alıyor |


Harika değil mi yahu! :)