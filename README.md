# sqlserver-django
Docker on sqlserver2016 + Ubuntu16.04 Django

## Requirement(Confirmed)

 - MacOSX 10.12.5
 - Docker for Mac Version 17.06.0-ce-mac19 (18663)

## Install

1. Install Docker for Mac  
https://docs.docker.com/docker-for-mac/install/#download-docker-for-mac

1. Running Docker for Mac  
Customize Docker Preferences  
    1. [Preferences] - [Advanced] - [Memory]  
    1. Change Memory Size 4GB or over. (Require SQLServer Container)
1. get this repository.  
    ```sh
    $ git clone https://github.com/JunichiYukawa/sqlserver-django.git
    $ cd sqlserver-django
    $ sh start.sh
    ```
1. Rewrite settings.py
    1. Open myapp/settings.py
    1. Replace DATABASES by dbsettings
    1. Add DATABASE_CONNECTION_POOLING by dbsettings
    
    eg.)
    ```
    DATABASES = {
        'default': {
            'ENGINE': 'sql_server.pyodbc',
            'NAME': 'BBT',
            'HOST': 'sqlserver',
            'PORT': 1433,
            'USER': 'SA',
            'PASSWORD': 'P@55w0rd',
            'OPTIONS': {
                'driver': 'ODBC Driver 13 for SQL Server',
            },
        }
    }
    DATABASE_CONNECTION_POOLING = False
    ```
    
1. docker setup  
    ```sh
    $ docker-compose build
    ```
1. docker start  
    ```sh
    $ docker-compose up
    ```
    
## Usage

1. Open `localhost:8000` in browser

## Author
Junichi Yukawa
