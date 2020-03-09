Adding additional Django page to your GeoNode Project
=====================================================

Since GeoNode is based on Django, your GeoNode project can be augmented and enhanced by adding additional Django page.


Adding your own Django page
--------------------------

It could be necessary to add additionnal page to your Django Geonode project but if you don't know Django, it could be difficult ! 


# Create basic About Us Page

   Since we have already created our GeoNode project from a template project, we will start by creating our 
   page :

   Before creating webpage, it could be usefull remembering our geonode project's structure :

       <my-geonode-project>/
               __init__.py
               apps.py
               celeryapp.py
               locale
               local_settings.py
               local_settings.py.sample
               settings.py
               static/
                   css/
                       site_base.css
                   img/
                       bing_*.png
                   js/
                   less/
                       site_base.less
                   gulpfile.js
                   package.js
                   README
               templates/
                   geonode_base.html
                   site_base.html
                   site_index.html               
               version.py
               views.py
               wsgi.py

   
   So We will edit a new page in templates directory : 
   
         $ cd <my-geonode-project>
         $ touch templates/aboutus.html
         $ echo '<h1>About Us page</h1>' >> templates/aboutus.html


   Now we have our page, it will not be visible by geonode until we add declare it in our Django Geonode Project.
   Let's Edit urls.py and replace this code :
   
            urlpatterns += [
            ## include your urls here
            ]

   
   by this one : 
   

            urlpatterns += [
            ## include your urls here
            url(r'^aboutus/$', TemplateView.as_view(template_name='aboutus.html'), name='aboutus'),
            ]
            
   Open your brower and go to your http://<your_geonode>/aboutus
   You will se a blank page with 'About Us page' written in blank page meaning : It works !!!!
   
   Extends Geonode template to your new page. 
   Edit your aboutus.html and add some Django blocks like : 
   
            {% extends 'geonode_base.html' %}
            {% block content %}
            <h1>About Us page</h1>
            {% endblock %}
            
            
            
   
   Now you will have your page with Geonode theme .... Update your page with what you would like to display ! 
    
    
    
    
    
   Additionnal note : how to find code to add in urls.py =>
   Just go to geonode folder where urls.py is present, then look for code in this file or do this bash command (An about page is already present in standard Geonode installation) : 
   
   
   
            $ cat geonode/urls.py | grep about
                url(r'^about/$',
                    TemplateView.as_view(template_name='about.html'),
                    name='about'),


   
