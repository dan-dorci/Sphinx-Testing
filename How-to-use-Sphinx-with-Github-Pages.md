# How to use Sphinx with Github Pages


### 1. Adding Sphinx to Local project:
- install Sphinx on local machine (Linux ex: ```apt-get install python3-sphinx```)
- pull/update local repository for the remote Github repository that will have a Sphinx Github Page added to it
- inside the local repository, at the root, create a new folder called ```docs```
- ```cd``` into this ```docs``` folder and run the following command ```sphinx-quickstart --ext-autodoc``` (tag needed to auto document doc strings)
- open the file ```Makefile``` and make the build directory the currect directory ```BUILDDIR      = .```
- open the file ```make.bat``` and make the build directory the currect directory ```set BUILDDIR=.```
- open ```conf.py``` and uncomment the lines ```import os```, ```import sys```, ```sys.path.insert(0, os.path.abspath('.'))``` and change ```sys.path.insert(0, os.path.abspath('.'))``` to ```sys.path.insert(0, os.path.abspath('..'))```
- open ```index.rst``` and add ```modules``` two lines below ```   :caption: Contents:``` with the same indentation
- run the command ```sphinx-apidoc -o . ..```
- run the command ```make html```, the html should now be generated and visible locally
- go into the folder ```/html``` and copy the ```index.html``` file
- paste this file into the ```/docs``` folder and open it
- replace it's contents with a redirect, the following two lines will work ```<!DOCTYPE html>```, ```<meta http-equiv="refresh" content="0; url=./html/index.html" />```
### 2. Adding Sphinx to Github Pages
- after completing the steps above push the new version of code to Github
- from the repository's page on Github, go to settings and select 'Pages' from the side menu
- under 'Source' choose 'main' for branch and '/docs' for the folder
- go into the ```/docs``` folder on Github and make a new empty file called ```.nojekyll```
- navigate back to Github Pages in Settings and click the link provided, wait a few minutes and hard refresh the page (command + R)
- the Sphinx Github Page should now be visible



