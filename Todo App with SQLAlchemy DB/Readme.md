I am building a TODO list app web pages that allows you to add Todo items. With the addition of SQLAlchemy, the new items will no longer be stored only within memory and will persist after a reload.

Please reference my "How to Run Flask (Windows)" document on the initial set up. Make sure that you have a templates folder with an index.html file and can run pip to install the needed libraries.

# Install SQLAlchemy
Install SQLAlchemy with:
```sh
pip install flask_sqlalchemy
```

![image](https://user-images.githubusercontent.com/44756128/115944861-0a441280-a47e-11eb-8474-d7839c3dda6c.png)

When you run "flask run", you should see a myDB.db file created in your python env folder:

![image](https://user-images.githubusercontent.com/44756128/115944997-f4831d00-a47e-11eb-8aba-032e83b8c958.png)

You can create todos directly in the Python interperter with the following:
```py
from app import db, Todo
second_todo = Todo(todo_text="Setup venv")
db.session.add(second_todo)
db.session.add(Todo(todo_text="Build a cool app"))
db.session.commit()
Todo.query.all()
```

OUTPUT
```
[<Todo 1>, <Todo 2>, <Todo 3>]
```

![image](https://user-images.githubusercontent.com/44756128/115945175-10d38980-a480-11eb-9aea-615521282a52.png)

We know that items are saved to the database when after restarting our server, the Todo items are still there:

![image](https://user-images.githubusercontent.com/44756128/115945361-11205480-a481-11eb-8ea5-1e6b9254bffc.png)

```sh
Cltr + c
```

![image](https://user-images.githubusercontent.com/44756128/115945386-31e8aa00-a481-11eb-8eeb-32a6abcbf843.png)

![image](https://user-images.githubusercontent.com/44756128/115945397-3dd46c00-a481-11eb-9bee-c6299eacea08.png)
