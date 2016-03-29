


##How To Install and Configure Django with Postgres, Nginx, and Gunicorn  

Before anything else, make sure all packages installed are upto date. Root to your directory and run:  
        
        sudo apt-get update  
        
        sudo apt-get upgrade  
        
        
###Install and create a viretual Environment  
Installing vthe viretual env is quite simple. Just run the following command:  
        sudo apt-get install python-virtualenv  
        
 Now create the virtual env with a name of your choice, I suggest one related to the current project.  
        
        sudo virtualenv /<root folder>/<virtualenv name>  
        
A directory will be created with the environment name.  


###Install Django  
Activate the virtual environment so as to install packages needed for the project  
        source ./<env name>/bin/activate  
        
We can now install Django with the virtual env active. To do this, we'll use **pip** a Python package manager much like Easy install. Here's the commnad you'll run:  

        pip install Django  
        
Getting errors o using pip?  
This should Do;  
        sudo apt-get install python-pip  
        
        
 
        
###Install PostgreSQL  
     
        
        
