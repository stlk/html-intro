# Zobrazujeme články

Jak reagovat na příchozí požadavky:


{% filename %}mysite/urls.py{% endfilename %}
```python
from django.conf.urls import include, url
from django.contrib import admin

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'', include('blog.urls')),
]
```

{% filename %}blog/urls.py{% endfilename %}
```python
from django.conf.urls import url
from . import views

urlpatterns = [
    url(r'^$', views.post_list, name='post_list'),
]
```

View, funkce, která odpoví na požadavek a zobrazí HTML:

{% filename %}blog/views.py{% endfilename %}
```python
def post_list(request):
    return render(request, 'blog/post_list.html', {})
```

### HTML

Adresářová struktura:

```
blog
└───templates
    └───blog
```

První šablona:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
<html>
    <head>
        <title>Ola's blog</title>
    </head>
    <body>
        <p>Hi there!</p>
        <p>It works!</p>
    </body>
</html>
```

Pusť server a podívej se na výsledek.


Základní HTML struktura:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
<html>
    <head>
        <title>Django Girls blog</title>
    </head>
    <body>
        <div>
            <h1><a href="">Django Girls Blog</a></h1>
        </div>

        <div>
            <p>published: 14.06.2014, 12:14</p>
            <h2><a href="">My first post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
        </div>

        <div>
            <p>published: 14.06.2014, 12:14</p>
            <h2><a href="">My second post</a></h2>
            <p>Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut f.</p>
        </div>
    </body>
</html>
```
