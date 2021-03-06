# MyMoneyStats
A small web app to keep track of your expenditure. It currently features a single anonymous user (password only login) and only uses sqlite (for now) and flask as 
well as vanilla JavaScript and SASS/SCSS.

## Install
Requires [python3](https://www.python.org/downloads/), [yarn](https://yarnpkg.com/lang/en/docs/install/), [gulp](https://gulpjs.com/) and [sqlite](https://www.sqlite.org/download.html).
See the links on how to install those on your OS.

Clone the repository
```
git clone https://github.com/Phosphenius/MyMoneyStats.git
cd MyMoneyStats
```
Create and activate virtualenv
```
python3 -m venv env
. ./env/bin/activate
```
Create and activate virtualenv on Windows
```
py -3 -m venv env
.\env\Scripts\activate.ps1
```
Install python requirements
```
pip install -r requirements.txt
```
Install NPM deps
```
cd gulp
yarn install
```
## Set up
The following steps can be omitted by running the setup script
```
sh setup.sh
```
If you prefer to do these steps by hand, follow the instructions below  
  
Create a `settings.cfg` file with the following structure
```
SECRET_KEY=yoursecretkey
PASSWD=yourplaintextpassword
```
The secret key can be generated with python (__This key must be kept secret and should never be added to any repository!__):
```python
import os
os.urandom(24)
```
Create database file
```
mkdir data
cd data
sqlite3 mms.sqlite < ../db-schema.sql
```
## Run gulp task(s)
Compile SCSS and uglify JavaScript
```
cd gulp
gulp sass
gulp uglify
```
Start the watch gulp task if you work on CSS/JavaScript
```
cd gulp
gulp watch
```
## Run
Start the app with
```
flask run
```
Open [http://127.0.0.1:4562](http://127.0.0.1:4562) in your browser.
