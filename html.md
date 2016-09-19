# Úvod do HTML

## Co je HTML?

HTML je jednoduchý kód který je interpretován tvým webovým prohlížečem - jako je Chrome, Firefox nebo Safari - aby se uživateli zobrazila webová stránka.

HTML je zkratka od "HyperText Markup Language". **HyperText** znamená, že je to typ textu, který podporuje hypertextové odkazy mezi stránkami. **Markup** znamená, že jsme vzali dokument a označili ho kódem, abychom něčemu (v tomto případě prohlížeči) řekli, jak interpretovat stránku. HTML kód se vytváží pomocí **tagů**. Každý začíná znakem `<` a končí znakem `>`. Tyto tagy representují **elementy** značkovacího jazyka (Markup).

## Tvá první stránka!

Abychom si vyzkoušeli jak tvořit HTML stránky, použijeme jednoduchý internetový editor [Thimble](https://thimble.mozilla.org/en-US/projects/new). V levé části píšeme kód a v pravé části vidíme výsledek.


Do souboru `index.html` přidej následující:

```html
    <html>
        <p>Ahoj!</p>
        <p>Funguje to!</p>
    </html>
```

![Obrázek][1]

 [1]: images/step1.png

Fungovalo to! Pěkná práce :)

*   Nejzákladnější tag, `<html>`, je vždy na začátku jakékoli stránky a `</html>` na jejím konci. Jak vidíš, celý obsah stránky je mezi otevíracím tagem `<html>` a zavíracím tagem `</html>`
*   `<p>` je tag pro element paragraf(odstavec), `</p>` každý paragraf ukončuje

## Head & body

Každá HTML stránka je také rozdělena na dva elementy: **head** (hlavu) a **body** (tělo).

*   **head** je element, který obsahuje informace o dokumentu, které se nezobrazují na webu.

*   **body** je element který obsahuje vše ostatní, co se zobrazuje jakou součást webové stránky.

`<head>` používáme abychom prohlížeči sdělili konfiguraci stránky, `<body>` abychom sdělili co na té stránce skutečně je.

Například dovnitř `<head>` můžeš dát element title (titulek), třeba takhle:

```html
    <html>
        <head>
            <title>Ola's blog</title>
        </head>
        <body>
            <p>Ahoj!</p>
            <p>Funguje to!</p>
        </body>
    </html>
```

V našem online editoru bohužel titulek neuvidíme, ale bude se mám hodit později až budeme pracovat na opravdové stránce.

Pravděpodobně jsi si všimla, že každý otevírací tag je doplněn *zavíracím tagem* se znakem `/`, a že elementy jsou *vnořené* (tzn. že nemůžeš zavřít daný tag dokud nejsou zavřeny všechny tagy uvnitř).

Je to jako dávat věci do krabic. Máš jednu velkou krabici, `<html></html>`; uvnitř je `<body></body>`, A ta obsahuje další, menší krabice: `<p></p>`.

Musíš dodržovat pravidlo *zavíracích* tagů a *vnořených* elementů - pokud nebudeš, prohlížeč je nemusí být schopný správně interpretovat a tvá webová stránka se bude zobrazovat nesprávně.

## Přizpůsob si stránku

Teď si můžeš užít trochu zábavy a pokusit se přizpůsobit si svou stránku! Tady je pár užitečných tagů:

*   `<h1>Hlavní nadpis</h1>` - Pro tvůj nejdůležitější nadpis
*   `<h2>Pod-nadpis</h2>` pro nadpis na nižší úrovni
*   `<h3>Pod-pod-nadpis</h3>` ... a tak dále, až k `<h6>`
*   `<em>text</em>` zvýrazňuje tvůj text
*   `<strong>text</strong>` hodně zvýrazňuje tvůj text
*   `<br />` vkládá novou řádku (dovnitř br nemůžeš nic dát)
*   `<a href="https://djangogirls.org">link</a>` vytváří odkaz
*   `<ul><li>První položka seznamu</li><li>second item</li></ul>` vytváří seznam, zrovna jako tento!
*   `<div></div>` definuje sekce stránky

Zde je příklad celé stránky:

```html
    <html>
        <head>
            <title>My blog</title>
        </head>
        <body>
            <div>
                <h1><a href="">My blog</a></h1>
            </div>

            <div>
                <p>published: 14.06.2014, 12:14</p>
                <h2><a href="">Můj první příspěvek</a></h2>
                <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
            </div>

            <div>
                <p>published: 14.06.2014, 12:14</p>
                <h2><a href="">Můj druhý příspěvek</a></h2>
                <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
            </div>
        </body>
    </html>
```  

Tady vytvoříme tři `div` sekce.

*   První `div` element obsahuje titulek našeho blogu - jeho nadpis a odkaz
*   Další dva `div` elementy obsahují naše příspěvky s datem zveřejnění, na `h2` s titulkem příspěvku se dá kliknout a dva `p` (paragrafy) obsahují text, jeden datum a druhý samotný příspěvek.

To nám dá následující efekt:


![Obrázek][2]

 [2]: images/step2.png
