--- 
title: Mobilde Hover Simule Etmek
date: 26.08.2018 18:00
---

![](https://media.giphy.com/media/26BRERwHtgJTf7rTG/giphy.gif)

Mobilde aslında hover özelliği olan bir şeye dokunduktan sonra bıraktığımızda basılı kalıyordu. Bir projemde bu özelliğin önüne geçip kullanıcıya mobil uygulama hissiyatı kazandırmak için bu sıkıntıyı çözmem gerekiyordu.

Stackoverflow'da çözümünü buldum. 


**jQuery**
```js
$(document).ready(function () {
    // .hover elementine dokunulduğunda o elemente hover_effect classını uygula
    $('.hover').on('touchstart touchend', function (e) {
        $(this).toggleClass('hover_effect');
    });
});
```

Ama sonra sadece yukarıdaki kodu çalıştırınca elementin üzerinde scroll yapmakta zorlandığımı farkettim ve aşağıdaki kodu da ekledim.  

Yine `document.ready` içine ekledim;

```js
$(document.body).on("touchmove", function (event) {
    event.preventDefault();
    event.stopPropagation();
});
```


**CSS** 
```css
.hover {
    -webkit-user-select: none; /* basılı tutulduğu zaman elemanları seçili hale getirmemesi için */
    -webkit-touch-callout: none; /* iOS cihazlarda basılı tutup bir kaç saniye bekletildiğinde bağlantı hakkında info çıkartmaması için */
}
.element.hover_effect {
    /* hover olduğunda olacak şeyler */
}
```

<br>

### Kaynak
[https://stackoverflow.com/questions/2851663/how-do-i-simulate-a-hover-with-a-touch-in-touch-enabled-browsers](https://stackoverflow.com/questions/2851663/how-do-i-simulate-a-hover-with-a-touch-in-touch-enabled-browsers)


