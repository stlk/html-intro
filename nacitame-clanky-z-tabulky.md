# Načítáme články z tabulky

V této kapitole se naučíš jak se Django spojuje s databází a jak do ní ukládá data. Pojďme na to!

## Django shell(konzole)

Do konzole napiš tento příkaz:

```
    (myvenv) ~/djangogirls$ python manage.py shell
```

Mělo by to mít takovýto efekt:

```
    (InteractiveConsole)
    >>>
```

### Všechny objekty

Pojďme zkusit zobrazit všechny naše příspěvky. To můžeš udělat následujícím příkazem:

```
    >>> Post.objects.all()
    Traceback (most recent call last):
          File "<console>", line 1, in <module>
    NameError: name 'Post' is not defined
```

Hups! Ukázala se chybová hláška. Říká nám, že tu není žádný Post objekt (příspěvek). To je správně -- zapomněli jsme je importovat!

```
    >>> from blog.models import Post
```

Tohle je jednoduché: importujeme model `Post` z `blog.models`. Pojďme znovu zkusit zobrazit všechny příspěvky:

```
    >>> Post.objects.all()
    [<Post: titulek mého prvního příspěvku>, <Post: titulky dalších příspěvků>]
```

### Vytvoř objekt

Takhle vytvoříš nový Post objekt v databázi:

```
    >>> Post.objects.create(author=me, title='titulek', text='Test')
```

Nejdříve pojďme importovat User model:

```
    >>> from django.contrib.auth.models import User
```

Jaké uživatele máme v naší databázi? Zkus tohle:

```
    >>> User.objects.all()
    [<User: ola>]
```

Tohle je superuser kterého jsme vytvořili dříve! Pojďme si teď vzít instanci tohoto uživatele:

```python
    me = User.objects.get(username='ola')
```

Teď můžeme konečně vytvořit příspěvek:

```
    >>> Post.objects.create(author=me, title='titulek', text='Test')
```

Hurá! Chceš se podívat jestli to fungovalo?

```
    >>> Post.objects.all()
    [<Post: my post title>, <Post: another post title>, <Post: Sample title>]
```

A je to tu, další příspěvek v seznamu!

### Filtrování objektů

Pojďme zkusit filtrovat:

```
    >>> Post.objects.filter(author=me)
    [<Post: titulek>, <Post: Příspěvek číslo 2>, <Post: Můj 3. příspěvek!>, <Post: 4. titulek příspěvku>]
```

Nebo možná chceme vidět všechny příspěvky jež mají slovo 'titulek' v poli `title`?

```
    >>> Post.objects.filter(title__contains='titulek')
    [<Post: titulek>, <Post: 4. titulek příspěvku>]
```

> **Poznámka** Mezi `title` a `contains` jsou dvě podtržítka (`_`). Django ORM používá tuto syntaxi k rozlišení názvů ("title") a operací nebo filterů ("contains"). Pokud použiješ pouze jedno podtržítko, dostaneš chybovou hlášku jako "FieldError: Cannot resolve keyword title_contains".

Také můžeš získat seznam všech publikovaných příspěvků. Uděláme to vyfiltrováním všech příspěvků které mají nastavené `published_date` na nějaký uplynulý datum:

> > > from django.utils import timezone Post.objects.filter(published_date__lte=timezone.now()) []

Bohužel, příspěvek který jsme přidali pomocí Python konzole ještě není publikován. To můžeme změnit! Nejdřív vezmeme instanci příspěvku, který chceme publikovat:

```
    >>> post = Post.objects.get(title="Sample title")
```

A ten publikujeme pomocí naší metody `publish`!

```
    >>> post.publish()
```

Teď se znovu pokus získat seznam publikovaných příspěvků (3 krát zmáčkni šipku nahoru a zmáčkni `enter`):

```
    >>> Post.objects.filter(published_date__lte=timezone.now())
    [<Post: Sample title>]
```

### Řazení objektů

QuerySety ti také umožňují seřadit seznam objektů. Pojďme je zkusit seřadit podle data vytvoření (`created_date`):

```
    >>> Post.objects.order_by('created_date')
    [<Post: titulek>, <Post: Příspěvek číslo 2>, <Post: Můj 3. příspěvek!>, <Post: 4. titulek příspěvku>]
```

Můžeme je také seřadit obráceně přidáním `-` na začátek:

```
    >>> Post.objects.order_by('-created_date')
    [<Post: 4. titulek příspěvku>,  <Post: Můj 3. příspěvek!>, <Post: Příspěvek číslo 2>, <Post: titulek>]
```

### Řetězení QuerySetů

QuerySety můžeš také kombinovat dohromady pomocí **řetězení**:

```
    >>> Post.objects.filter(published_date__lte=timezone.now()).order_by('published_date')
```

Je to mocný nástroj který ti umožňuje psát docela komplexní query.

Cool! Teď jsi připravená na další část! Pro zavření shell konzoli zadej toto:

```
    >>> exit()
    $
```
