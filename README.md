# todo_graphql_api
The application describes a simple GraphQL API build with Python, Flask and Ariadne 
(A library for using GraphQL applications)

##Setting up
1) Clone the application
####
    git clone https://github.com/njugunanduati/todo_graphql_api.git
####
2) Change directory to get into the application
####
    cd todo_graphql_api
####
3) Create a virtual environment using python3
####
    python3 -m venv venv
####
4) Activate the environment
####
    source venv/bin/activate
####
5) Install the environment variables in the requirements.txt file
####
    pip install -r requirements.txt
####
6) Make a .env from the .env.example file and update the variables required. 
   The application is using a postgres database so make sure to create a <b>todo</b> 
   database first. 
####
    cp .env.example .env
Update the environment variables
####
    FLASK_APP=
    FLASK_ENV=
    SECRET_KEY=
    
    # DB Credentials
    DB_ENGINE=
    DB_USER=
    DB_PASSWORD=
    DB_NAME=
    DB_HOST=
    DB_PORT=
####
7) Create the table using migrations
####
    flask db init
    flask db upgrade
    flask db migrate
####
8) Run the application
####
    flask run
####
9) By default, the application will run on port 5000. On your browser open
    http://127.0.0.1/5000/graphql
####
10) Now to test the api's. Note that for graphql, <b>queries</b> are used 
    for reading data and <b>mutations</b> are used for inserting and 
    modifying records in a database.
    
## Query Examples
#### Fetching all todos
    query fetchAllTodos {
      todos {
        success
        errors
        todos {
          description
          completed
          id
        }
      }
    }
####
#### Fetching a single todos
    query fetchTodo {
      todo(todoId: "1") {
        success
        errors
        todo { id completed description dueDate }
      }
    }
####
##Mutation Examples
#### Creating a todo
    mutation newTodo {
      createTodo(description:"Wash the car", dueDate:"27-04-2021") {
        success
        errors
        todo {
          id
          completed
          description
        }
      }
    }