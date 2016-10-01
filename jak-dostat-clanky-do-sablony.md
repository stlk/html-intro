# Jak dostat články do šablony


Musíme přidat nový import:

{% filename %}blog/views.py{% endfilename %}
```python
from django.shortcuts import render
from django.utils import timezone
from .models import Post
```

Načteme data z tabulky jako v minulé kapitole:

{% filename %}blog/views.py{% endfilename %}
```python
from django.shortcuts import render
from django.utils import timezone
from .models import Post

def post_list(request):
    posts = Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
    print(posts)
    return render(request, 'blog/post_list.html', {})
```

Předáme data do šablony:

{% filename %}blog/views.py{% endfilename %}
```python
from django.shortcuts import render
from django.utils import timezone
from .models import Post

def post_list(request):
    posts = Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
    return render(request, 'blog/post_list.html', {'posts': posts})
```
