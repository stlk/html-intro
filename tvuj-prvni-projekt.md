# Tvůj první Django projekt!

Vytvořit "projekt":

```
django-admin startproject mysite .
```

Spustit server:

```
python manage.py runserver $IP:$PORT
```

Vytvořit "aplikaci":

```
python manage.py startapp blog
```

Do sekce `INSTALLED_APPS` v souboru `mysite/settings.py` přidat `'blog',`.

Výsledek:

{% filename %}mysite/settings.py{% endfilename %}
```python
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog',
]
```
