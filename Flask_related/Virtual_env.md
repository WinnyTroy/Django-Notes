First step, as you originally tried to do, but this time you specify the "virtualenv" module and the name of the virtualenv. In this case flask:

python -m virtualenv flask

Then you activate your virtualenv like this:

source flask/bin/activate

Then install flask with pip inside the virtualenv

pip install flask

If you want to deactivate your virtualenv, simply type:

deactivate
