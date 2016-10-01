# Zkrášlujeme náš blog

## Instalace Bootstrapu

Chceš-li nainstalovat Bootstrap, je třeba přidat do `< head >`

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
```


## Statické soubory

Udělej složku s názvem `static` ve složce `blog`:

```
djangogirls
├── blog
│   ├── migrations
│   └── static
└── mysite
```

## Tvůj první CSS soubor!

Vytvoř složku `css` v naší složce `static` a v ní vytvoř nový soubor `blog.css`.

```
djangogirls
└─── blog
     └─── static
          └─── css
               └─── blog.css
```

A vlož do něj následující kód:

{% filename %}blog/static/css/blog.css{% endfilename %}
```css
.page-header {
    background-color: #ff9400;
    margin-top: 0;
    padding: 20px 20px 20px 40px;
}

.page-header h1, .page-header h1 a, .page-header h1 a:visited, .page-header h1 a:active {
    color: #ffffff;
    font-size: 36pt;
    text-decoration: none;
}

.content {
    margin-left: 40px;
}

h1, h2, h3, h4 {
    font-family: 'Lobster', cursive;
}

.date {
    color: #828282;
}

.save {
    float: right;
}

.post-form textarea, .post-form input {
    width: 100%;
}

.top-menu, .top-menu:hover, .top-menu:visited {
    color: #ffffff;
    float: right;
    font-size: 26pt;
    margin-right: 20px;
}

.post {
    margin-bottom: 70px;
}

.post h1 a, .post h1 a:visited {
    color: #000000;
}
```

Teď ještě musím aplikovat css třídy na naše HTML tagy. Nahraď následující kód

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% for post in posts %}
    <div class="post">
        <p>published: {{ post.published_date }}</p>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```

v souboru `blog/templates/blog/post_list.html` tímto:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
<div class="content container">
    <div class="row">
        <div class="col-md-8">
            {% for post in posts %}
                <div class="post">
                    <div class="date">
                        <p>published: {{ post.published_date }}</p>
                    </div>
                    <h1><a href="">{{ post.title }}</a></h1>
                    <p>{{ post.text|linebreaksbr }}</p>
                </div>
            {% endfor %}
        </div>
    </div>
</div>
```

Musíme také naší šabloně říct, že jsme přidali nějaký CSS soubor. Otevři `blog/templates/blog/post_list.html` a na začátek přidej:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% load staticfiles %}
```
