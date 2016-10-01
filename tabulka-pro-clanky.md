# Tabulka pro články

Vytvořit model:

Otevřeme `blog/models.py`, odstraňme z něj všechno a přidejme tam:

{% filename %}blog/models.py{% endfilename %}
```python
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey('auth.User')
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```

Vygenerovat databázové migrace:

```
python manage.py makemigrations blog
```

Spustit migrace:

```
python manage.py migrate
```
