# Location API

Location API is a Flask app, that provides a simple API to store and query user locations via an authenticated RESTful API.

## Installing the backend locally for development

The Backend uses Python 2.7.x and Flask for providing the API to store data to a database.
Please follow the next installation steps in order to get it working nicely in a local environmnet.

1. Clone the repository to your PC
    Clone the repository with `git clone <repo.url>`

2. Install virtual environment for Python
    This helps the Python environment to stay clean and avoid package version collisions

    - if you don't have Python 2.7.x installed, please do install it and add it to PATH
    - install PIP (Python package manager)
    - install virtualenvironment package with pip (pip install virtualenv)
    - create your virtualenvironment somewhere **preferably outside** the project folder not to commit it to git.
        - for example `cd ..` -> `mkdir venv` -> `virtualenv venv`
        - now you can activate it with `source venv/Scripts/activate` in Windows (use ./activate in *NIX)
        - there should be (venv) reading in front of the command line cursor. This means that you are now using a project-specific virtual environment
        - install the required packages specified in a given .txt file by running **`pip install -r requirements.txt`**
    - You are done! Hooray!

3. Create the database on first use
    - `python db_create.py`

4. Run the app
    - run the development server **`python run.py`**

5. If everything works as it should, the development server should give you a local address for the API


## Using the API

1. The API can be queried from the endpoints by using a web browser (for GET requests)
    - try http://localhost:5000/user/1
    - it should return an error in JSON format. This means that the database is still empty.

2. Create a new user via the API with a HTTP POST request.
    - for this I'd recommend using a helper app postman https://chrome.google.com/webstore/detail/postman-rest-client/fdmmgilgnpjigdojojpjoooidkmcomcm?hl=en
    - in Postman create a POST request with a parameter (form-data) Key:name, Value:Jonathan
    - if successful, the API returns success and the ID of the created user
    - now go fetch the user data in JSON format from http://localhost:5000/user/1 - it works!

## Heroku Deployment

Use a command line for this.
A good guide can be found [here](http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xviii-deployment-on-the-heroku-cloud)

- Login to Heroku with `heroku login`
- `git push heroku master` to update the remote in Heroku
- `git run init` to init the database
- `git run upgrade` to upgrade the database
