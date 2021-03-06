Flask 

***
**Creating environment**

***Install PIP***

pip is a package management system used to install and manage software packages written in Python.

```
# sudo easy_install pip

Searching for pip
Best match: pip 18.1
Processing pip-18.1-py2.7.egg
pip 18.1 is already the active version in easy-install.pth
Installing pip script to /usr/local/bin
Installing pip2.7 script to /usr/local/bin
Installing pip2 script to /usr/local/bin

Using /Library/Python/2.7/site-packages/pip-18.1-py2.7.egg
Processing dependencies for pip
Finished processing dependencies for pip

```

***Installing Virtualenv with Pip***

Virtualenv lets you create an isolated Python environment for your project
To install virtualenv, use pip

```
# pip install virtualenv
```

***Creating virtual env***

```
# virtualenv -p python hello
Already using interpreter /usr/bin/python
New python executable in /Users/andrzejhochbaum/Projects/Python/hello/bin/python
Installing setuptools, pip, wheel...
done.
```

***Activating new environmet***

``` 
source bin/activate
(hello):hello$ 

```

***Deactivating environment***

```
$ deactivate

```


***Installing Flask***

Create source dir and install flask

```

(hello):hello$  mkdir src

(hello) hello $ pip install flask
DEPRECATION: Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won't be maintained after that date. A future version of pip will drop support for Python 2.7.
Collecting flask
  Using cached https://files.pythonhosted.org/packages/7f/e7/08578774ed4536d3242b14dacb4696386634607af824ea997202cd0edb4b/Flask-1.0.2-py2.py3-none-any.whl
Collecting Werkzeug>=0.14 (from flask)
  Using cached https://files.pythonhosted.org/packages/20/c4/12e3e56473e52375aa29c4764e70d1b8f3efa6682bef8d0aae04fe335243/Werkzeug-0.14.1-py2.py3-none-any.whl
Collecting click>=5.1 (from flask)
  Using cached https://files.pythonhosted.org/packages/fa/37/45185cb5abbc30d7257104c434fe0b07e5a195a6847506c074527aa599ec/Click-7.0-py2.py3-none-any.whl
Collecting Jinja2>=2.10 (from flask)
  Using cached https://files.pythonhosted.org/packages/7f/ff/ae64bacdfc95f27a016a7bed8e8686763ba4d277a78ca76f32659220a731/Jinja2-2.10-py2.py3-none-any.whl
Collecting itsdangerous>=0.24 (from flask)
  Using cached https://files.pythonhosted.org/packages/76/ae/44b03b253d6fade317f32c24d100b3b35c2239807046a4c953c7b89fa49e/itsdangerous-1.1.0-py2.py3-none-any.whl
Collecting MarkupSafe>=0.23 (from Jinja2>=2.10->flask)
  Using cached https://files.pythonhosted.org/packages/cd/52/927263d9cf66a12e05c5caef43ee203bd92355e9a321552d2b8c4aee5f1e/MarkupSafe-1.1.0-cp27-cp27m-macosx_10_6_intel.whl
Installing collected packages: Werkzeug, click, MarkupSafe, Jinja2, itsdangerous, flask
Successfully installed Jinja2-2.10 MarkupSafe-1.1.0 Werkzeug-0.14.1 click-7.0 flask-1.0.2 itsdangerous-1.1.0


```


check:

```
 pip list
DEPRECATION: Python 2.7 will reach the end of its life on January 1st, 2020. Please upgrade your Python as Python 2.7 won't be maintained after that date. A future version of pip will drop support for Python 2.7.
Package      Version
------------ -------
Click        7.0    
Flask        1.0.2  
itsdangerous 1.1.0  
Jinja2       2.10   
MarkupSafe   1.1.0  
```

***

***Creating example page***


```
cat hello.py 
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return 'Main Page AH'


@app.route('/hello')
def helloIndex():
    return 'Hello World from Python Flask!'

app.run(host='0.0.0.0', port= 5000)

pip          19.0.2 
setuptools   40.8.0 
Werkzeug     0.14.1 
wheel        0.33.0 


```

,where:

* The script above simply creates the application object as an instance of class Flask imported from the flask package.
* The __name__ variable passed to the Flask class is a Python predefined variable, which is set to the name of the module in which it is used.
* routes module. The routes are the different URLs that the application implements. In Flask, handlers for the application routes are written as Python functions, called view functions.

***routes***

example next script:

```
cat blog.py 
from flask import Flask

app = Flask(__name__)

@app.route('/')
def index():
    return 'Main Page AH'


@app.route('/author')
def author():
    return 'Andrzej Hochbaum'

@app.route('/copyrights')
def copyright():
    return "Copyright 2019"


```

Check:


![Alt](images/flask1.png)



Key facts

* A route is a mapping of an URL, website address,  to a Python function
* Add @app.route('/hello') before a function definition, where hello is your URL path
* The python return string is shown in the web browser

***Dynamic routes***

```
@app.route("/dynamic/<name>")
def getname(name):
    return name

@app.route("/dynamic2/<name>/<age>")
def getusr_age(name,age):
    return "Your name -" + name + " " + age


```
![Alt](images/flask2.png)





