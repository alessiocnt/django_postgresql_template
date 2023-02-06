# django_backend
Dockerized django backend example with postgresql.

## Project setup

1. Create the Django project by running the docker compose run command as follows. <br>
``` cmd
sudo docker compose run web django-admin startproject composeexample .
```
2. Connect db <br> 
    - Edit ```composeexample/settings.py``` file.
    - Replace ```DATABASES = ... ```
  ``` Python
  # settings.py
  import os
  [...]
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.postgresql',
          'NAME': os.environ.get('POSTGRES_NAME'),
          'USER': os.environ.get('POSTGRES_USER'),
          'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
          'HOST': 'db',
          'PORT': 5432,
      }
  }
  ```
3. Run docker compose up 
``` cmd
docker compose up
```

At this point, your Django app should be running at port ```8000``` on your Docker host. 
On Docker Desktop for Mac and Docker Desktop for Windows, go to ```http://localhost:8000``` on a web browser to see the Django welcome page.
<br>
In Windows 10 set ```ALLOWED_HOSTS``` in ```settings.py```. For demo porpouse: ```ALLOWED_HOSTS = ['*']```
