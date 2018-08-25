--- 
title: Konum Çekme
date: 25.08.2018 19:00
---

Geolocation API'nı kullanarak kullanıcının kendi rızası ile kendi yerini bildirmesini sağlar.  

# Nerelerde kullanılır?
Kullanıcıyı bulunduğu hedeften yakın hedeflere yönlendirme, benzer hedeflere yönlendirme, bulunduğu alanı işaretleme gibi gibi bir çok yerde kullanılabilir.  

Örneğin, projenizde fotoğraf yükleme alanı var ve fotoğrafın çekildiği yerin nereye ait olduğunu yazdırmak için Geolocation API kullanarak `lat` ve `lng` koordinat değerlerini çektirebilirsiniz.

<br>
# Nasıl kullanılır?
<br>
Bir buton ekliyorum
```html
<button type="button">Konum al</button>
```
<br>
Hata mesajı için yazdırması bir div ekliyorum
```html
<div id="nudge" style="display:none">Hata: konum alınamadı.</div>
```
<br>
`Lat` ve `Lng` değerlerini yazabilmesi için gereken iki div ekliyorum
```html
<div id="startLat"></div>
<div id="startLon"></div>
```
<br>
Ve son olarak javascript kodlarını sayfama dahil ediyorum
```js
var button = $('button');
button.onclick = function() {
  var startPos;
  var nudge = document.getElementById("nudge");

  var showNudgeBanner = function() {
    nudge.style.display = "block";
  };

  var hideNudgeBanner = function() {
    nudge.style.display = "none";
  };

  var nudgeTimeoutId = setTimeout(showNudgeBanner, 5000);

  var geoSuccess = function(position) {
    hideNudgeBanner();
    // We have the location, don't display banner
    clearTimeout(nudgeTimeoutId);

    // Do magic with location
    startPos = position;
    document.getElementById('startLat').innerHTML = startPos.coords.latitude;
    document.getElementById('startLon').innerHTML = startPos.coords.longitude;
  };
  var geoError = function(error) {
    switch(error.code) {
      case error.TIMEOUT:
        // The user didn't accept the callout
        showNudgeBanner();
        break;
    }
  };

  navigator.geolocation.getCurrentPosition(geoSuccess, geoError);
};
```
<br>
**Burada ne oluyor?**
1. Konumu çekmek için butona tıklandıktan sonra 5 saniye bekletiyor.
2. Sonuç olumlu dönerse, bekletmeyi devre dışı bırakıp değerleri `#startLat` ve `#startLon` divlerine yazdırıyor.
3. Ama eğer zaman aşımından sonra olumsuz dönerse `#nudge` divi içine hata mesajı yazdırıyor.
