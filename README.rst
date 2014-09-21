==========================
django-declarative-urlconf
==========================

Configure Django urlconf using class definitions.

Installation
~~~~~~~~~~~~

Install via pip::

 pip install git+https://github.com/bpeschier/django-declarative-urlconf.git


Basic usage
~~~~~~~~~~~

.. code-block:: python

    # urls.py
    import declarative_urlconf as urlconf
    from .views import ListView, CreateView, DetailView, UpdateView, DeleteView


    class ViewSet(urlconf.URLs):

        index = urlconf.URL(r'^$', ListView)
        create = urlconf.URL(r'^add/$', CreateView)
        detail = urlconf.URL(r'^(?P<pk>.+)/preview/$', DetailView)
        update = urlconf.URL(r'^(?P<pk>.+)/edit/$', UpdateView)
        delete = urlconf.URL(r'^(?P<pk>.+)/delete/$', DeleteView)

    urlpatterns = ViewSet().as_urls()


Referenced views can be class-based or functions.
