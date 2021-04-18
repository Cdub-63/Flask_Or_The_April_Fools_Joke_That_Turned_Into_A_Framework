# How to run flask Locally on your windows computer

  - Make sure that you have Python installed, specifically Python3
  - Setup the python Virtual Environament with. I named my "myapp":
> python3 -m venv <env_name>

  - Chnge into the directory of the newly created environment
> cd <env_name> 

  - Activate the environament with:
> Scripts\activate.bat

![image](https://user-images.githubusercontent.com/44756128/115151693-a19b0700-a033-11eb-8c1d-fa7eadcd4717.png)

Install Flask:
> pip install flask

![image](https://user-images.githubusercontent.com/44756128/115151737-d60ec300-a033-11eb-89e5-d2e843a9673c.png)

Install Flask_WTF:
> pip install flask_wtf

![image](https://user-images.githubusercontent.com/44756128/115151772-fcccf980-a033-11eb-98dd-acd31cb98cc6.png)

# Displaying the Flask application:
I deployed the following barebones application that lists objeects in a Todo list and also lets users add submit their own objects to the list:

![image](https://user-images.githubusercontent.com/44756128/115151876-71079d00-a034-11eb-9fb5-6b1d4bbde73e.png)

![image](https://user-images.githubusercontent.com/44756128/115151883-782eab00-a034-11eb-8d59-7c3e3d7f192b.png)

I created a "templates" folder within the "myapp" directory to host the index.html file:

![image](https://user-images.githubusercontent.com/44756128/115151949-c2179100-a034-11eb-83e0-fa6081e0ff34.png)

![image](https://user-images.githubusercontent.com/44756128/115151956-c643ae80-a034-11eb-929d-3ccf9c338e6e.png)

Contents of the index.html file are here:
```html
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
</head>
<body>
	<h1>Todos</h1>
	
	{% for todo in todos %}
		<li>{{ todo }}</li>
	{% endfor %}
	
	<form method="POST">
		{{ template_form.hidden_tag() }}
		<p>
			{{ template_form.todo.label }}
			{{ template_form.todo() }}
		</p>
		<p>{{ template_form.submit() }}</P>
	</form>
</body>
</html>
```

The main code is in my app.py file:
![image](https://user-images.githubusercontent.com/44756128/115151977-e2dfe680-a034-11eb-96f7-6c3413852bbb.png)

Contents of the app.py file is here:
```py
from flask import Flask, render_template, request
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField

app = Flask(__name__)
app.config['SECRET_KEY'] = 'mysecret'

todos =["Learn Flask", "Setup venv", "Build a cool app"] 

class TodoForm(FlaskForm):
	todo = StringField("Todo")
	submit = SubmitField("Add Todo")

@app.route('/', methods=["GET", "POST"])
def index():
	if 'todo' in request.form:
		todos.append(request.form['todo'])
	return render_template('index.html', todos=todos, template_form=TodoForm())
```

# To run the application
You must run flask with:

>flask run

![image](https://user-images.githubusercontent.com/44756128/115152079-4bc75e80-a035-11eb-9207-ba255a367514.png)

Copy and paste the localhost address into a web browser to display the webpage

![image](https://user-images.githubusercontent.com/44756128/115152204-c55f4c80-a035-11eb-86ab-8ad03a7d49a4.png)

# Exit the Application
Exit the application in your CMD by entering:

>cltr+c
