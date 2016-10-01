# Template extending

## Base template - základní šablona

Vytvořme soubor `base.html` ve složce `blog/templates/blog/`:

```
blog
└───templates
    └───blog
            base.html
            post_list.html
```

Potom ho otevři a ze souboru `post_list.html` zkopíruj vše do souboru `base.html` takto:

{% filename %}blog/templates/blog/base.html{% endfilename %}
```html
{% load staticfiles %}
<html>
    <head>
        <title>Django Girls blog</title>
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css">
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css">
        <link href='//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="{% static 'css/blog.css' %}">
    </head>
    <body>
        <div class="page-header">
            <h1><a href="/">Django Girls Blog</a></h1>
        </div>

        <div class="content container">
            <div class="row">
                <div class="col-md-8">
                {% for post in posts %}
                    <div class="post">
                        <div class="date">
                            {{ post.published_date }}
                        </div>
                        <h1><a href="">{{ post.title }}</a></h1>
                        <p>{{ post.text|linebreaksbr }}</p>
                    </div>
                {% endfor %}
                </div>
            </div>
        </div>
    </body>
</html>
```

Potom v souboru `base.html`, nahraď celý obsah `<body>` (všechno mezi `<body>` a `</body>`) následujícím:

{% filename %}blog/templates/blog/base.html{% endfilename %}
```html
<body>
    <div class="page-header">
        <h1><a href="/">Django Girls Blog</a></h1>
    </div>
    <div class="content container">
        <div class="row">
            <div class="col-md-8">
            {% block content %}
            {% endblock %}
            </div>
        </div>
    </div>
</body>
```

{% raw %}Možná sis všimnul, že jsme všechno od `{% for post in posts %}` do `{% endfor %}` nahradili násleujícím: {% endraw %}

{% filename %}blog/templates/blog/base.html{% endfilename %}
```html
{% block content %}
{% endblock %}
```

Teď ulož soubor `base.html` a znovu otevři `blog/templates/blog/post_list.html`.
{% raw %}Chystáme se odstranit všechno nad `{% for post in posts %}` a pod `{% endfor %}`. Až budeme hotovi, náš soubor bude vypadat:{% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% for post in posts %}
    <div class="post">
        <div class="date">
            {{ post.published_date }}
        </div>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```


{% raw %}Potřebujeme, aby název bloku byl stejný jako jsme definovali v souboru `base.html`. Potřebujeme taky, aby veškerý obsah byl v bloku. To uděláme tím, že vše umístíme mezi `{% block content %}` a `{% endblock content %}`. Takto:{% endraw %}

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% block content %}
    {% for post in posts %}
        <div class="post">
            <div class="date">
                {{ post.published_date }}
            </div>
            <h1><a href="">{{ post.title }}</a></h1>
            <p>{{ post.text|linebreaksbr }}</p>
        </div>
    {% endfor %}
{% endblock %}
```

Zbývá nám poslední věc. Musíme propojit tyto dva soubory. O tom je celé rozšiřování šablon. Uděláme to přidáním `extends` tagy na začátek souboru.

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% extends 'blog/base.html' %}

{% block content %}
    {% for post in posts %}
        <div class="post">
            <div class="date">
                {{ post.published_date }}
            </div>
            <h1><a href="">{{ post.title }}</a></h1>
            <p>{{ post.text|linebreaksbr }}</p>
        </div>
    {% endfor %}
{% endblock %}
```

A máme hotovo! Pojďme zkusit, jestli vše funguje.

> If you get the error `TemplateDoesNotExist`, that means that there is no `blog/base.html` file and you have `runserver` running in the console. Try to stop it (by pressing Ctrl+C – the Control and C keys together) and restart it by running a `python manage.py runserver` command.
