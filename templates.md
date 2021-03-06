
**TEMPLATES**

It is possible to return the output of a function bound to a certain URL in the form of HTML. For instance, in the following script, hello() function will render ‘Hello World’ with ```<h1>``` tag attached to it.

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
   return '<html><body><h1>'Hello World'</h1></body></html>'

if __name__ == '__main__':
   app.run(debug = True)
   
```
   
However, generating HTML content from Python code is cumbersome, especially when variable data and Python language elements like conditionals or loops need to be put. This would require frequent escaping from HTML.

This is where one can take advantage of Jinja2 template engine, on which Flask is based. Instead of returning hardcode HTML from the function, a HTML file can be rendered by the render_template() function.

```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
   return render_template(‘hello.html’)

if __name__ == '__main__':
   app.run(debug = True)
   
```
Flask will try to find the HTML file in the templates folder, in the same folder in which this script is present.

Application folder
- Hello.py
- templates (folder):
      - hello.html
      
```
ls -laR ./*
-rw-r--r--  1 andrzejhochbaum  staff  180 Feb 18 15:12 ./hello2.py

./templates:
total 8
drwxr-xr-x  3 andrzejhochbaum  staff   96 Feb 18 15:12 .
drwxr-xr-x  4 andrzejhochbaum  staff  128 Feb 18 15:12 ..
-rw-r--r--  1 andrzejhochbaum  staff   91 Feb 18 15:12 hello.html

```




**The term ‘web templating system’ refers to designing an HTML script in which the variable data can be inserted dynamically.** A web template system comprises of a template engine, some kind of data source and a template processor.

Flask uses **jinga2** template engine. A web template contains HTML syntax interspersed placeholders for variables and expressions (in these case Python expressions) which are replaced values when the template is rendered.

The following code is saved as hello.html in the templates folder.
***template: ./templates/hello.html***
```
<!doctype html>
<html>
   <body>
   
      <h1>Hello World!</h1>
      
   </body>
</html>

```
Next, run the following script from Python shell.

***Main file: hello.py:***

```
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def exampleIndex():
    return render_template('hello.html')


app.run(host='0.0.0.0', port= 5000)

```


***


***Key facts***

* Templates are stored in the /templates/ directory
* A template is an HTML file (Flask uses the Jinja template engine)
* Templates can contain Python variables using this syntax {‌{x}}
* Python functions can return templates

```
# your function
return render_template('example.html')
Don't forget the line

# top of python file
import from flask import Flask, render_template, request
```

***

**Dynamic variables**

Example:

cat hello2.py 

```
from flask import Flask, render_template

app = Flask(__name__)


@app.route('/hello/<user>')
def hello_name(user):
    return render_template('hello.html', name = user)


app.run(host='0.0.0.0', port= 5000)

```

cat ./templates/hello.html 


```

<!doctype html>
<html>
   <body>
   
      <h1>Hello  - {{name}} !</h1>
      
   </body>
</html>

```

<img src="images/flask3.png " alt="drawing" width="300"/>


***

Key facts

Templates can contain Python variables, to access {‌{x}}

Pass the variables in render_template

```
# function return
return render_template('hello.html', name=name, x=x)
```



