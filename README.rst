=====
app
=====

App is a simple Django m3 app to manage User, Group, Permission and Contenttype framework. 

Detailed documentation is in the "docs" directory.

Quick start
-----------
1. install dependensyse easy_install -U
	--extra-index-url http://pypi.bars-open.ru/simple/
	--trusted-host pypi.bars-open.ru

	django==1.11
	m3-objectpack==2.2.25
2. install app
	easy_install -U django_app-0.1-py3.5.egg

3. Add "app" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'app',
    ]

4. Include 

	from m3 import get_app_urlpatterns


	def workspace(request):
	   u"""
	   Возвращает view для отображения Рабочего Стола
	   на основе шаблона m3
	   """
	   return render(
	       request, 'm3_workspace.html',
	       context={'debug': settings.DEBUG}, )


	urlpatterns = [
	   url(r'^admin/', admin.site.urls),
	   url(r'^$', workspace),
	]

	# =======================================================
	# собираем шаблоны урлов из app_meta подключенных приложений
	#========================================================
	urlpatterns += tuple(get_app_urlpatterns())

3. Visit http://127.0.0.1:8000 to participate in the app.