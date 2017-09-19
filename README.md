Курсы валют ЦБ РФ для Django
============================

Простая загрузка курсов валют с сайта ЦБ (http://www.cbr.ru/scripts/XML_daily.asp) в модель Django.


Установка
---------

1) `pip install django-cbr`

2) Пропишите cbr в INSTALLED_APPS

3) `python manage.py migrate`

4) `python manage.py load_cbr`

5) Довавьте в crontab, например:

`0 */2 * * * /var/www/SITE/venv/bin/python /var/www/SITE/manage.py load_cbr`
