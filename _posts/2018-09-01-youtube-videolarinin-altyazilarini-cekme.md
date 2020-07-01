--- 
title: Youtube Videolarından Altyazı Çekmek
date: 01.09.2018 16:00
image: https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Closed_captioning_symbol.svg/1200px-Closed_captioning_symbol.svg.png
---


> Aslında altyazıları ".srt" olarak gayet güzel şekilde çeken generatorler mevcut fakat aşağıdaki kodlarda, pencerenin farklı bir persektifinden bakmak için derlediğim bir yazı oldu.

<br>
Not: Bu yöntem otomatik olarak çevrilen çeviriler için verimli çalışmayabilir.


Method:

```js
function CaptionCollector() {
  var that = this;
  this.captions = '';
  var nowShowing = '';

  this.collect = function(){
    try {
      var currentCaption = document.getElementsByClassName("captions-text")[0].innerText;
    } catch (e) {
      var currentCaption = null;
    }

    if(currentCaption && nowShowing != currentCaption) {
      nowShowing = currentCaption;
      that.captions += ' ' + nowShowing;
    }

    setTimeout(that.collect, 300);
  }
}

var foo = new CaptionCollector();
foo.collect();
```

Altyazı **foo.captions** olarak gelecektir. "foo" yerine istediğinizi kullanabilirsiniz.

<br>
```js
var captionCollector = {
    captions : '',
    nowShowing: '',

    collect : function(){
      try {
        var currentCaption = document.getElementsByClassName("captions-text")[0].innerText;
      } catch (e) {
        var currentCaption = null;
      }
    if(currentCaption && this.nowShowing != currentCaption) {
        this.nowShowing = currentCaption;
        captionCollector.captions += ' ' + captionCollector.nowShowing;
     }
    setTimeout(captionCollector.collect, 300);
  }
}

captionCollector.collect();
```

Bu methodda **captionCollector.captions** olarak getirir

<br>

Ya da global değişkene atayarak da yapabilirsiniz.

```js
(function(){
    ___captions = '';
    var ___nowShowing = '';

    function getCaption() {
        try {
          var currentCaption = document.getElementsByClassName("captions-text")[0].innerText;
        } catch (e) {
          var currentCaption = null;
        }

        if(currentCaption && ___nowShowing != currentCaption) {
          ___nowShowing = currentCaption;
          ___captions += ' ' + ___nowShowing;
        }
        setTimeout(getCaption, 300);
    }

    getCaption();
})();
```

Bu methodda, konsolu global değişkenle yazdırıyorsunuz **___captions**

<br>
Youtube'un videolar için kullandığı "captions-text" classı kullandığı için yalnızca Youtube'da çalışır. Diğer video hizmetleri için classname'i değiştirin.
 
Tüm altyazıları çekmek için tüm videoyu oynatmanız gerekecektir. Ayarlarla videoyu iki kat hızlı oynatabilirsiniz.

Video bittiğinde konsolu temizleyin. Değişkenleri çağırın yazdırın ve hepsini seçip kopyalayın.

İşlem tamam.

<br>

#### Kaynak:
[http://www.standardista.com/capturing-captions-from-youtube-videos](http://www.standardista.com/capturing-captions-from-youtube-videos)