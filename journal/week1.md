# week 1  - Containerize Application 

## Requird Homework/ Tasks

# Clone the frontend and backend repo

Inside Container
make a new folder inside Container

```
WORKDIR /backend-flask
```


# Outside Container -> # Inside Container
# This contain the libraries want to install to run app
COPY requirements.txt 

# Inside Container
# install the python libraries used for the app
```
RUN pip3 install -r requirements.txt
```


# Outside Container -> # Inside Container
# . mean everythins in the current directory
# first period . - /backend-flask (outside container)
# second period . /backend-flash (inside container)
COPY . .

# Set Environment Variable (Env Vars)
# Inside Container and will remain set when the container is running 
ENV FLASK_ENV=development

EXPOSE ${PORT}

# Cmd (Command)
# python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]

```

cd backend-flask
export FRONTEND_URL="*"
export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
cd ..
```

make sure to unlock the port on the port tab

Build 
docker build -t  backend-flask ./backend-flask

run 
issues 
docker build -t  backend-flask ./backend-flask
sol 
FRONTEND_URL="*" BACKEND_URL="*" docker run --rm -p 4567:4567 -it backend-flask


active 
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
