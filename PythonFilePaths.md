###Using UniPath  

# At the top of settings.py  
from unipath import Path  
BASE_DIR = Path(__file__).ancestor(3)  
MEDIA_ROOT = BASE_DIR.child("media")  
STATIC_ROOT = BASE_DIR.child("static")  
STATICFILES_DIRS = (  
BASE_DIR.child("staticfiles"),  
.
)  
TEMPLATES = [  
{  
'BACKEND': 'django.template.backends.django.DjangoTemplates',  
DIRS = (BASE_DIR.child("templates"),)  
},  

**NOTE**: If you really want to set your BASE_DIR with the Python standard library's os.path library, though, this is  
one  way to do it in a way that will account for paths:  

from os.path import join, abspath, dirname  

here = lambda *dirs: join(abspath(dirname(__file__)), *dirs)  
BASE_DIR = here("..", "..")  
root = lambda *dirs: join(abspath(BASE_DIR), *dirs)  

#Confirguring MEDIA_ROOT  

MEDIA_ROOT = root("media")  

#Confirguring STATIC_ROOT  

STATIC_ROOT = root("collected_static")  

#Additional locations of static files  

STATICFILES_DIRS = (  
	root("assets"),  
	)  

#Configuring TEMPLATE_DIRS  

TEMPLATES = [  
	{  
		'BACKEND': 'django.template.backeds.django.DjangoTemplates',  
		DIRS = (root("templates"),)  
	},  
	]  
