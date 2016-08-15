Now MYSQL is truth be told, one of the best open source database servers that can handle just about any load you want to throw at it, and it has lots of powerful tools that can be used to manage it.
The other popular open source database is PostgreSQL, which is cross-platform and is used by numerous applications. Although PostgreSQL is often seen as being as powerful as MySQL, 
it doesn't have nearly the number of available tools to make setup and management as easy as its competition. 

## Step 1: Install PostgreSQL

Here are the installation steps on Ubuntu (this installation will also work on any Debian-based distribution):

1.Open a terminal window.
2.Issue the command sudo apt-get install postgresql.
3.Type the sudo password necessary to give you admin rights and hit Enter.
4.Allow apt to pick up any necessary dependencies.


Once the installation is complete, it's time to set this baby up.


## Step 2: Change the default user password


Caution: If you don't follow this step, you will not be able to add databases and administer PostgreSQL, and the database will not be secure.

Here's how to change the password for the default user. The user in question is postgres, and the password is changed like so:

1.Open a terminal window.
2.Issue the command sudo passwd postgres.
3.Type (and confirm) that password to be used for this user.

N.B
The postgres user will be the only user on your system that can open the PostgreSQL prompt without defining a database,
ie when you type sudo su-postress, you should be in the postgress prompt(like venv) without having to define a database
all other users will hav to gain access to the postgress prompt while defining the db name like so : 'psql DB_NAME'
 which means postgres is the only user who can administer PostgreSQL.
 
##  Step 4: Create your first database
This is where it gets exciting. Let's create a new database called testdb. To do this, follow these steps:

1.Open a terminal window.
2.Change to the postgres user. ie sudo su - postgres
3.Log in to the postgres prompt. ie psql
4.Issue the command ie CREATE DATABASE testdb;

Now, to check if the db was created successfully,  issue the command (from the postgres command prompt):

\l

The output should look like this:
testdb    | postgres | UTF8     | en_US.UTF-8 | en_US.UTF-8 |


