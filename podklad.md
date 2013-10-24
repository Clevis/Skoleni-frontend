# Frontend školení

## Menü

0. 15 minutek základů kódování na 220°
// kostra, knihovny (bower)
 * příprava surovin  
// sémantika, udržitelnost, přístupnost
 * éčka v HTML  
// preprocesory
 * CSS glutamát 
// responsive
 * želé 
// komponenty a kompozice
0. Práce s nožem 
// Dokumentace
0. Psaní jídelního lístku
// Build & optimalizace
0. Aranžování jídla
// Frontbase
0. Kuchařka
// Produktivní tipy & debug
0. Pohlreich v kuchyni

## 30 minutek základů kódování na 220°

### Příprava surovin
* Fork kostry projektu
```
build/
docs/
img/
js/
libs/
sass/
  comps/
  parts/
  screen.sass
index.html
```
* Bower `bower install`
* CDN + local fallback pro rozšířené knihovny
```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>
<script>window.jQuery || document.write('<script src="libs/jquery/jquery.min.js"><\/script>')</script>
```

### éčka v HTML
* HTML = DATA, jejich popis a struktura
* Každý element či vlastnost elementu má svůj definovaný význam
 * hX - nadpis (či podnadpis) pro danou část dokumentu
 * ol - tříděný seznam položek
 * article - nezávislý obsah typu článek, příspěvek fóra, blogpost, komentář, ...
> Authors must not use elements, attributes, or attribute values for purposes other than their appropriate intended semantic purpose, as doing so prevents software from correctly processing the page. @WHATWG
* K rozšíření významu elementu používáme třídy
* Pojmenování tříd:
> authors are encouraged to use values that describe the nature of the content, rather than values that describe the desired presentation of the content. @WHATWG
* Udržitelnost
Šílenci v Yahoo
```html
<div class="Bfc M-10">
  <div class="Fl-start Mend-10 W-25">column 1</div>
  <div class="Bfc">column 2</div>
</div>
```
Ti ostatní
```html
<div class="content-wrap">
  <aside class="sidebar">column 1</aside>
  <section class="content">column 2</section>
</div>
```
### Přístupnost
 * WAI - [Web Accessibility Initiative](http://www.w3.org/WAI/)
 * WAI-ARIA - [Accessible Rich Internet Applications](http://www.w3.org/TR/wai-aria/)
 * Joshue O Connor - [Pro HTML5 Accessibility](www.amazon.com/Pro-HTML5-Accessibility-Joshue-Connor-ebook/dp/B007N4WSQU)
* Skvělá dokumentace [HTML: The Living Standard](http://developers.whatwg.org/)

### Sémantický web IS NOT DEAD 
-> schema.org: Google výsledky (people, events, reviews, products, recipes and breadcrumb navigatios)
![recipe](https://www.google.com/help/hc/images/webmasters_173379_en.png)
![events](https://www.google.com/help/hc/images/webmasters/webmasters_164506_richsnippets_multipleevent_en.gif)
-> OpenGraph: Facebook
![Příklad použití OpenGraph](https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-prn1/851586_188416314641828_1439591137_n.png)
```html
<div>
 <h1>Avatar</h1>
 <span>Director: James Cameron (born August 16, 1954)</span>
 <span>Science fiction</span>
 <a href="../movies/avatar-theatrical-trailer.html">Trailer</a>
</div>
```
```html
<div itemscope itemtype ="http://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <div itemprop="director" itemscope itemtype="http://schema.org/Person">
  Director: <span itemprop="name">James Cameron</span> (born <span itemprop="birthDate">August 16, 1954)</span>
  </div>
  <span itemprop="genre">Science fiction</span>
  <a href="../movies/avatar-theatrical-trailer.html" itemprop="trailer">Trailer</a>
</div>
```
[Getting started with schema.org](http://schema.org/docs/gs.html)
[Google Structured Data Testing Tool](http://www.google.com/webmasters/tools/richsnippets)
[Open Graph Overview](https://developers.facebook.com/docs/opengraph/overview/)

### CSS glutamát
* [LESS](http://lesscss.org), [SASS](http://sass-lang.com), [Stylus](http://learnboost.github.io/stylus/)
* Výhody
 * Parametrizace
 * Znovupoužitelnost
 * Udržitelnost
* Nevýhody
 * nutnost kompilace
 * zneužívání zanořování - max. 3 úrovně!
 * bloat

```sass
// Generation of classes for image sprites based on $count @Mobilove
$i: $count
@while $i > 0
	._i#{$i}
		background-position: (-$i*100 + 100%) 0
	$i: $i - 1
```

```css
.performers ._i7 {background-position:-600% 0}
.performers ._i6 {background-position:-500% 0}
.performers ._i5 {background-position:-400% 0}
.performers ._i4 {background-position:-300% 0}
.performers ._i3 {background-position:-200% 0}
.performers ._i2 {background-position:-100% 0}
.performers ._i1 {background-position:0% 0}
```

### Webpage je želé
http://msimek.cz/ccd3a95740.png
http://i.imgur.com/YuIrD.jpg
http://www.youtube.com/watch?v=4n5AfHYST6E
* Nezměrný počet různých zařízení s přístupem na web
* Budoucnost nepředvídatelná
* Způsob boje: responsive


## Práce s nožem
LEGO! http://msimek.cz/6379db4c97.png
http://mrlagency.co.uk/wp-content/uploads/2012/11/Lego.jpg

* Stavební bloky - komponenty
* Kombinace bloků - kompozice

[Frontbase ideology...](https://github.com/Clevis/Clevispace/wiki/Frontbase)


## Psaní jídelního lístku
* Dokumentování CSS zlepšuje čitelnost a udržitelnost kódu
* [StyleDocco](http://jacobrask.github.io/styledocco/)
```css
/* Provides extra visual weight and identifies the primary action in a set of buttons.

    <button class="btn primary">Primary</button>
*/
.btn.primary {
    background: steelblue;
    color: snow;
    border: 2px outset steelblue;
}
```
* [KSS](http://warpspire.com/kss/)
```css
// A button suitable for giving stars to someone.
//
// :hover             - Subtle hover highlight.
// .stars-given       - A highlight indicating you've already given a star.
// .stars-given:hover - Subtle hover highlight on top of stars-given styling.
// .disabled          - Dims the button to indicate it cannot be used.
//
// Styleguide 2.1.3.
a.button.star{
```

## Aranžování jídla
Kompilace, minifikace a spojení souborů, sledování změn, servírování souborů, ...

![](http://gruntjs.com/img/grunt-logo.png)

[GRUNT](http://gruntjs.com) - The JavaScript Task Runner
Instalace: `npm install -g grunt-cli`
Konfigurace: `/Gruntfile.js`
Příklad tasků:
* `grunt` - produkční build
* `grunt dev` - vývojový režim

## Kuchařka
![rocket](https://github.global.ssl.fastly.net/images/icons/emoji/rocket.png)
Frontbase - a starter fuel for web projects 
https://github.com/Clevis/Frontbase


## Pohlreich v kuchyni
Produktivní tipy & debug - názorná ukázka… 

## Flame wars time...
