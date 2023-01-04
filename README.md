# Music-Controller-Web-App
Django &amp; React - Full Stack Web App with Python & Javascript from Tech With Tim.<br>

Collaborative Music Playing System. Web app for a group of people to control the music being played in unity.<br>

Host can create a room and give out a code to people who want to join the room. People can join the room, they can vote to skip the song. They can pause/play the song or whatever permissions the host gives them.<br>

Tutorial 1 - Full Stack Web App with Python & JS:<br>
<ul>
  <li>~<code>pip install django djangorestframework </code></li>
  <li>~<code>django-admin startproject music-controller </code></li>
  <li>cd to music_controller directory and ~<code>django-admin startapp api</code></li>
  <li>Add 'api.apps.ApiConfig' and 'rest_framework' to INSTALLED_APPS in settings.py of music_controller project to add add to the project. ApiConfig is from the apps.py in api app</li>
  <li>Create urls.py file in api app to store URLs local to this app. Create urls.py file in music_controller project</li>
  <li>Include api.urls to the url_patterns in urls.py in the music_controller project.</li>
  <li>Add views to the url_patterns in urls.py in the api app</li>
  <li>In music_controller project directory, ~<code>python manage.py makemigrations</code> to update the database and store current changes made to the app</li>
  <li>~<code>python manage.py migrate</code></li>
  <li>~<code>python manage.py runserver</code></li>
</ul>

Tutorial 2 - Django REST Framework:<br>
<ul>
  <li>Create Room model in models.py in api app</li>
  <li>In music_controller project directory, ~<code>python manage.py makemigrations</code> to update the database and store current changes made to the app</li>
  <li>~<code>python manage.py migrate</code></li>
  <li>Create serializers.py in api app. This will take our Python related code and translate it into a JSON response. Add RoomSerializer class to serializers.py</li>
  <li><code>generics.CreateAPIView</code> api view class RoomView. <code>generics</code> allows us to create a class that inherits from an api view.</li>
  <li>~<code>python manage.py runserver</code> and add data</li>
  <li><code>generics.ListAPIView</code> api view class RoomView will list out the data</li>
</ul>

Tutorial 3 - React Integration Using Webpack & Babel:<br>
<ul>
  <li>cd to music_controller project and ~<code>django-admin startapp frontend</code> </li>
  <li>In frontend app, create templates, src and static folders. static holds static files, anything our browser would cache. In static folder create frontend, css and images folders. In src folder create components folder. </li>
  <li>Add 'frontend.apps.FrontendConfig' to INSTALLED_APPS in setting.py of music_controller/music_controller</li>
  <li>cd to music_controller\frontend and perform installations
    <ul>
      <li>~<code>npm init -y</code></li>
      <li>Then install webpack ~<code>npm i webpack webpack-cli --save-dev</code> </li>
      <li>Then install Babel ~<code>npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev</code>, Babel takes our code and transpiles it into code that is friendly with all browsers such as ES6 or ES7 Javascript code </li>
      <li>Then install react ~<code>npm i react react-dom</code> </li>
      <li>Then install material UI ~<code>npm install @material-ui/core</code> </li>
      <li>To use async and await in our Javascript code install ~<code>npm install @babel/plugin-proposal-class-properties</code> </li>
      <li>To reroute our pages install ~<code>npm install react-router-dom</code> </li>
      <li>To use icons from Material UI install ~<code>npm install @material-ui/icons</code></li>
    </ul>
  </li>
  <li>Create babel.config.json file in music_controller/frontend. Set up Babel loader and uses environment presets thats targetting node version 10 and @babel/preset-react because we are using react. Plugins so we can use async and await</li>
  <li>Create webpack.config.js. Webpack will bundle all our Javascript into one file and serve that bundle to the browser</li>
  <li>Update package.json scripts with webpack running in development and watch mode. and build script with webpack in production mode </li>
  <li>We want Django to render a page that react will take control of </li>
  <li>Inside templates, create folder frontend. Inside frontend create index.html </li>
  <li>Inside view.py of music_controller\frontend create index function to render the index template and let react take care of it </li>
  <li>Create a urls.py for music_controller\frontend </li>
  <li>Inside urls.py for music_controller\music_controller add url for frontend </li>
  <li>Create new component App.js inside components folder </li>
  <li>Inside src folder, create index.js and import App from components/App </li>
  <li>Check that server is running in music_controller ~<code>python manage.py runserver</code></li>
  <li>cd to music_controller\frontend and run ~<code>npm run dev</code></li>
  <li>The main.js inside static\frontend now contains the bundled up Javascript</li>
</ul>








