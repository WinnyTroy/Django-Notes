##User Authentication  

I'll be using the auth application provided as part of a standard Django installation in package django.contrib.auth. According to Django's docs, the application consists  of the following aspects:  

    1. Users
    2. Permissions: a series of binary flags (e.g. yes or no) determining what a user may or may not do.  
    3. Groups- a method of applying permissions to more than one user  
    4. A configurable password hashing system - for security of course  
    5. Forms and view tools for logging in users, or restricting content  
    
###Setting Up Authentication  

First off you eed to make sure that the relevant settings are present in your project's settings.py file.  

Within the settings.py file find the INSTALLED APPS tuple and check that **django.contrib.auth** and **django.contrib.contenttypes** are listed.  
    
