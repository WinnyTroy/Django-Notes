###Restful programming is about?  
1. Resources being identified by a persistent identifier: URLs are the obiquitous choice of identifier these days  
2. Resources being manipulated using a common set of verbs: HTTP methods are the commonly seen case. THe methods: Create, Retrieve, Update, Delete become: POST, GET, PUT and DELETE.  
3. The actual representation retrieved for a resource is dependent on the request and not thw identifier: use HTTP Accept headers to control whether you want XML, HTTP or Java object representing the resource.  
4. Representing relationships between resources in the representation of the resource: the links between objects are embedded directly in the representation.  
5. resource representations describe how the representation can be used and under what circumstances it should be discarded/refetched in a consistent manner: usage if HTTP Cache-Control headers.  
This last one is most likely the most important in terms of consequences and overall effectiveness of REST. Overall, most of th RESTful discussions seem to center on HTTP and its usage from a browser and what not.  

####A Simple REST API 
The API below simply fetches data from a web app to be delivered to another application, could be mobile or web. Note this is a simple demo, it also doesn't involve an oauth  system.

#####Requirements:(probaby the newest versions)  
			Django==1.9  
			psycopg2==2.6.1  
			pycparser==2.14  
			wsgiref==0.1.2  
			djangorestframework  

First off start your project, """django-admin.py startproject Marine """ 
Here's how your structire should look:  
			projectFolder/  
  					Myenv/
      					Marine/  
						admin.py    
						manage.py  
						db.sqlite3 
						Marine/ 

		
Register a new application - """python manage.py startapp fish"""
Now it should be something like this:  

			projectFolder/  
  					Myenv/
      						Marine/
      							Marine/
      								__init__.py  
      								settings.py  
      								urls.py  
      								wsgi.py
      							fish/
								__init__.py  
								admin.py  
								apps.py
								migrations/  
								models.py  
								views.py   
								urls.py (you can add your custom urls here)      
							admin.py    
							manage.py  
							db.sqlite3
				

#####In my settings.py:  
		INSTALLED_APPS = [  
    			'django.contrib.admin',  
    			'django.contrib.auth',  
    			'django.contrib.contenttypes',
    			'django.contrib.sessions',  
    			'django.contrib.messages',  
    			'django.contrib.staticfiles',  
    			'fishes',  (my app name :-) )  
    			'rest_framework'  (important for the api)
		]  

I like using postgres, it's a very efficient db especially when querrying.

		DATABASES = {  
    			'default': {  
        		'ENGINE': 'django.db.backends.postgresql',  
        		'NAME': 'username',  
        		'USER': 'user',
        		'PASSWORD': 'password',  
        		'HOST': 'localhost', (Empty for localhost through domain sockets or '127.0.0.1' for localhost through TCP.)
        		'PORT': '',   
    			}  
			}  

Our API, 'Marine' will be  getting fish data :-)  
First off we'll need a fish model, this will also register our fish in the database as a table. Here's the model, in Models.py;  
		
			class Fish(models.Model):  
				name = models.CharField(max_length=255)   name of the fish  
				created = models.DateTimeField('auto_now_add=True')  date it was "delivered" to the port  
				active = models.BooleanField()  

Try and run the server with """python manage.py runserver""". Django will notify you about some migrations to make? well, that's creating the actual tables in the database ;-)  

In order to access the admin interface, you also require an account, run the following command:  
		""" python manage.py create superuser """  
follow the steps described.

Root to the folder 'admin.py', here we'll register our application in the admin interface.  
First add an import: from fish.models import Fish  

then add : admin.site.register(Fish). 

run the server and access the admin, the address should be 127.0.0.1:8000/admin 

Are you using Version Control? This is probably a good time to commit.


In the next part, we're going to add a Serializer, add some fish and check out our API  



	
