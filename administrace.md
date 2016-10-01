# Administrace

Umožnit spravovat nový model v administraci:

Otevřeme `blog/admin.py`, odstraňme z něj všechno a přidejme tam:

{% filename %}blog/admin.py{% endfilename %}
```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

http://tutorial.djangogirls.org/en/django_admin/

Pro přihlášení do administrace ale musíme mít účet:

```
python manage.py createsuperuser
```
