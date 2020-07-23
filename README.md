# RESTful API Demo for filesystem access

## Instalation via requirements:
```
git clone
cd flask-seznam-api-ext
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

## Usage
REST API allowing access to information about files and folders in file system. The API providese the following functionalities:

- Get a list of files and folders in the specified path, including meta information about the files (creation date, last modification date, size...)
- Get information about a specific single file or folder as in the above.
- Delete the file or empty folder in the specified path.
- Create a new empty file in the specified path.

All responses have the form of JSON:

### Get details of a single file/folder:

** definition **

'GET /file/{path}'

** response **

- 200 OK on success
- 404 if path was not found on filesystem

** example **
 
- if specified {path}: /var the result might look like this

```
{
    "path": "/var",
    "is_file": false,
    "size": 5002412399,
    "time_created": "Sat Mar  7 19:57:20 2020",
    "time_modified": "Sat Mar  7 19:57:20 2020"
}
``` 

### Get details of all files/folders in specified path:

** definition **

'GET /files/{path}'

** response **

- 200 OK on success
- 404 if path was not found on filesystem

** example **
 
- if specified {path}: /var the result might look like this

```
{
    "files": [
        {
            "path": "/var/log",
            "is_file": false,
            "size": 4418927343,
            "time_created": "Tue May 26 20:23:21 2020",
            "time_modified": "Tue May 26 20:23:21 2020"
        },
        {
            "path": "/var/lock",
            "is_file": false,
            "size": 22,
            "time_created": "Mon Jul 13 17:17:28 2020",
            "time_modified": "Mon Jul 13 17:17:28 2020"
        },
        {
            "path": "/var/cache",
            "is_file": false,
            "size": 417982732,
            "time_created": "Thu May 14 19:26:20 2020",
            "time_modified": "Thu May 14 19:26:20 2020"
        },
        {
            "path": "/var/mail",
            "is_file": false,
            "size": 0,
            "time_created": "Tue Apr 21 11:15:56 2020",
            "time_modified": "Tue Apr 21 11:15:56 2020"
        },
    ...
``` 

### Delete empty folder or file on specified path:

** definition **

'DELETE /file/{path}'

** response **

- 200 OK on success
- 400 if directory is not empty
- 404 if directory or file doesnt exists

** example **

- if specified {path}: /var/log/empty_folder the result might look like this

```
    {
    "name": "camera",
    "price": 25.99,
    "store_id": 2
    }
``` 

### Create file/folder specified by path:

** definition **

'DELETE /item/<name>'

** reponse **
- 404 Not Found if it does not exist