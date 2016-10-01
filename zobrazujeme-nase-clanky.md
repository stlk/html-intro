# Jak dostat načtená data do šablony

Pojďme zkusit vypsat proměnnou:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{{ posts }}
```

Měl by vypadat takto:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
[<Post: My second post>, <Post: My first post>]
```

Teď zkusme použít cyklus:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
{% for post in posts %}
    {{ post }}
{% endfor %}
```

Výsledné HTML pro výpis článků:

{% filename %}blog/templates/blog/post_list.html{% endfilename %}
```html
<div>
    <h1><a href="/">Django Girls Blog</a></h1>
</div>

{% for post in posts %}
    <div>
        <p>published: {{ post.published_date }}</p>
        <h1><a href="">{{ post.title }}</a></h1>
        <p>{{ post.text|linebreaksbr }}</p>
    </div>
{% endfor %}
```
