# Django-Basic

SETTING UP DJANGO:

1.  mkdir (project)

2. install virtualenv   (virtualenv 'venv')

3. turn on virtualenv  (. venv/Scripts/activate)

4. while in virtualenv, install django  (pip install django)

5. create a project (django-admin.py startproject 'project name')
						NOTE: if not working try without .py
						
6. open text editor and attach the folder to it

7. in your (project) folder runserver: python manage.py runserver

8. then in same folder: python manage.py migrate (creates admin screen)

9. then in same folder: python manage.py createsuperuser

10.  set up user name and password



START APP:

11. then in same folder: python manage.py startapp (newapp)

12. in your new app folder create a 'urls.py' file

13. in main folder(project) add the newly created app (newapp) under 'INSTALLED APPS'

14. in (newapp) urls.py add the bear bones:

		from django.urls import path

		urlpatterns = [
			
		]

15. create a VIEW or VIEWS:  the views.py is created automatically in your (newapp)
							 to create a view is similar to creating a new page in 
							 flask, with a function. so for basic home page you would
							 do:
					
					
			def home(request):   <--pass a request thru function because the browser is requesting that a page be shown
			    return render(request, "home.html", {})
								
								
			FOR EACH PAGE ON YOUR SITE YOU CREATE ONE OF THESE!
			about me
			about them
			next page 
			etc.
			
16. create TEMPLATES to match each VIEW:  

			inside the (newapp) folder, create a 'templates' folder for html files

17. layout the desired html files that you created in VIEWS

18. go to (newapp) urls.py, import all from views and add the paths for each view:

			exemple:
			
				from django.urls import path
				from . import views

				urlpatterns = [
					path('', views.home, name='home'),
					path('about/', views.about, name='about'),

				]
				
19. NOW go to (project) urls.py, and INCLUDE the (newapp) urls:

			exemple:
			
				from django.contrib import admin
				from django.urls import path, include

				urlpatterns = [
					path('admin/', admin.site.urls),
					path('', include('newapp.urls')),
				]
				
				
20. NOW to add future pages just resort to (newapp) urls.py and add it in path:

			exemple:
			
				from django.urls import path
				from . import views

				urlpatterns = [
					path('', views.home, name='home'),
					path('about/', views.about, name='about'),
					path('newpage/', views.newpage, name='newpage'),
				]
				
				
21. THEN go to views.py in (newapp) and add view:

			#HOME
			def home(request):
				return render(request, "home.html", {})
				
			#ABOUT
			def about(request):
				return render(request, "about.html", {})
			
			#NEWPAGE
			def newpage(request):
				return render(request, "newpage.html", {})

				
22. THEN go to templates and create the 'newpage.html'

AND SO FORTH:					
			



DJANGO IS MVC ARCHITECTURE

M - Models: Database
V - Views: Webpages
C - Controller: Routers (URLS )
