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

**django.contrib.auth** provides Django with access to the authentication system.  
**django.contrib.contenttypes** is used by the authentication application to track models inside your database.  

NOTE: if you had to add the apps yourself to the INSTALLED APPS, you will have to run the python manage.py migrate command  

###PASSWORD MANAGEMENT  

Django provides a flexible password storage system and uses PBKDF2 by default, with a SHA256 hash, a password stretching mechanism recommended by NIST. This should be sufficient for most users: it’s quite secure, requiring massive amounts of computing time to break.  

Django chooses the alogrithm to use by cosulting the PASSWORD HASHERS setting. This is a list of hashing algorithm classes that this Django installation supports.  

The first entry in the list (that is settings.PASSWORD_HASHERS[0]) will be used to store passwords, all the other entries are valid hashers that can be used to check existing passwords.

The default list usuall looks like this:  
    
    PASSWORD_HASHERS = [  
    'django.contrib.auth.hashers.PBKDF2PasswordHasher',  
    'django.contrib.auth.hashers.PBKDF2SHA1PasswordHasher',  
   'django.contrib.auth.hashers.BCryptSHA256PasswordHasher',  
    'django.contrib.auth.hashers.BCryptPasswordHasher',  
    'django.contrib.auth.hashers.SHA1PasswordHasher',  
    'django.contrib.auth.hashers.MD5PasswordHasher',  
    'django.contrib.auth.hashers.CryptPasswordHasher',  
]  

###Using bcrypt with Django.  

Bcrypt is a popular password storage algorith that's specifically designed for long term password storage.  
To use bcrypt, install the library by running:  
    pip install bcrypt // pip install django[bcrypt]  
    
    Modify PASSWORD_HASHERS to list BCryptSHA256PasswordHasher first as:  
    
    'django.contrib.auth.hashers.BCryptSHA256PasswordHasher',  
'django.contrib.auth.hashers.BCryptPasswordHasher',  


###The User Model  
The core of Django's authentication system is the User object, located at **django.contrib.auth.models.User**. A user object represents each of the people interacting with a django application. Django Docs states that they are used to allow aspects of the authentication system like access restriction, registration of new user profiles and the association of creators with site content.  

The User model comes complete with five primary attributes:  

    the username for the user account;  
    the account’s password;  
    the user’s email address;  
    the user’s first name;  
    the user’s surname.  
    
The model also comes with other attributes such as is_active(which determines whether a particular account is active or not)  


An example model for a User profile:  

class UserProfile(models.Model):  
 # This line is required. Links UserProfile to a User model instance.  
    user = models.OneToOneField(User)  
    
    
    # The additional attributes one wishes to include.  
    website = models.URLField(blank=True)  
    picture = models.ImageField(upload_to='profile_images', blank=True)  
    
     Override the __unicode__() method to return out something meaningful  
    def _unicode_(self):  
        return self.user.username  

After referencing, you have to import within the models.py  

 **from django.contrib.auth.models import User**  
 
 with the user profile model defined, now edit the admin.py to include the new IserProfile model in Django's admin. web interface.  
 In the admin.py file, add the following:  
    
    from django.models import UserProfile  
    
    admin.site.register(UserProfile)  
    
    After this run python manage.py make migrations to create the migration scripts for the new UserProfile model. Then run python manage,py migrate

###Creating a User Registration View and Template  

To provide the user registration functionality I will go through the following steps:
Create a UserForm and UserProfileForm.
Add a view to handle the creation of a new user.
Create a template that displays the UserForm and UserProfileForm.
Map a URL to the view created.
Link the index page to the register page

























































