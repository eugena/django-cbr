Курсы валют ЦБ РФ для Django
============================

Простая загрузка курсов валют с сайта ЦБ (http://www.cbr.ru/scripts/XML_daily.asp) в модель Django.


Установка
---------

1) `pip install django-cbr`

2) Пропишите django-cbr в INSTALLED_APPS

3) `python manage.py migrate`

4) `python manage.py load_cbr`

5) Довавьте в crontab, например:

`0 */2 * * * /var/www/SITE/venv/bin/python /var/www/SITE/manage.py load_cbr`


Использование
-------------

cbr_informer.py

```
from django import template
from cbr.models import CBRCurrencyRate

register = template.Library()


@register.inclusion_tag('cbr/informer.html', takes_context=True)
def currency_informer(context):
    usd = CBRCurrencyRate.objects.filter(currency__char_code='USD').last()
    eur = CBRCurrencyRate.objects.filter(currency__char_code='EUR').last()

    return {
        'request': context['request'],
        'usd': usd,
        'eur': eur,
    }
```

