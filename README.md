# Music-Controller-Web-App
Django &amp; React - Full Stack Web App with Python & Javascript from Tech With Tim.<br>

Collaborative Music Playing System. Web app for a group of people to control the music being played in unity.<br>

Host can create a room and give out a code to people who want to join the room. People can join the room, they can vote to skip the song. They can pause/play the song or whatever permissions the host gives them.<br>

Tutorial 1 - Full Stack Web App with Python & JS:
~<code>pip install django djangorestframework </code><br>
~<code>django-admin startproject music-controller </code> <br>
cd to music_controller directory and ~<code>django-admin startapp api</code> <br>
Add 'api.apps.ApiConfig' and 'rest_framework' to INSTALLED_APPS in settings.py of music_controller project to add add to the project. ApiConfig is from the apps.py in api app. <br>
Create urls.py file in api app to store URLs local to this app. Create urls.py file in music_controller project.<br>
Include api.urls to the url_patterns in urls.py in the music_controller project.<br>
Add views to the url_patterns in urls.py in the api app.<br>
In music_controller project directory, ~<code>python manage.py makemigrations</code> to update the database and store current changes made to the app. <br>
~<code>python manage.py migrate</code><br>
~<code>python manage.py runserver</code><br>

Tutorial 2 - Django REST Framework:
