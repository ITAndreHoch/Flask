
Key facts

An URL route can have more than one variables

```
@app.route("/user/<a>/<b>")

```
To pass multiple variables to a template, pass a dictionary

```
context = { 'a': a, 'b': b } 
render_template('index.html', **context)

```
Inside the template use {‌{a}}, {‌{b}} or iterate over the dictionary

***


***Example:***

cat multi.py 

```

from flask import Flask, render_template

app = Flask(__name__)


@app.route('/')
def exampleIndex():
    return render_template('index.html')

@app.route('/hello/name')
def helloIndex(name):
    return render_template('hello.html', name=name)

@app.route('/abc/<a>/<b>/<c>')
def abcIndex(a,b,c):
    context = { 'a':a, 'b':b, 'c':c }
    return render_template('abc.html', context=context)


app.run(host='0.0.0.0', port= 5000)

```


cat ./templates/index.html 

```

<!doctype html>
<html>
   <body>
   
      <h1>Hello </h1>
      
   </body>
</html>

```


cat ./templates/abc.html   

```

<!doctype html>
<html>
   <body>
   
      <h1>Hello </h1>
      <table>
      {% for key, value in context.items() %}
          <tr>
              <th> {{ key }} </th>
              <td> {{ value }} </td>
          </tr>
       {% endfor %}
       </table>
      
   </body>
</html>

```

<img src="images/flask4.png " alt="drawing" width="300"/>

***

And now - we can change some values - example:

cat multi.py 

```
from flask import Flask, render_template

app = Flask(__name__)


@app.route('/')
def exampleIndex():
    return render_template('index.html')

@app.route('/hello/name')
def helloIndex(name):
    return render_template('hello.html', name=name)

@app.route('/abc/<a>/<b>/<c>')
def abcIndex(a,b,c):
    context = { 'jeden':a, 'dwa':b, 'trzy':c }
    return render_template('abc.html', context=context)


app.run(host='0.0.0.0', port= 5000)


```

<img src="images/flask5.png " alt="drawing" width="300"/>


