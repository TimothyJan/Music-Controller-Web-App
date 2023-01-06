# Music-Controller-Web-App
Django &amp; React - Full Stack Web App with Python & Javascript from Tech With Tim.<br>

Collaborative Music Playing System. Web app for a group of people to control the music being played in unity.<br>

Host can create a room and give out a code to people who want to join the room. People can join the room, they can vote to skip the song. They can pause/play the song or whatever permissions the host gives them.<br>

Tutorial 1 - Full Stack Web App with Python & JS:
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

Tutorial 2 - Django REST Framework:
<ul>
  <li>Create Room model in models.py in api app</li>
  <li>In music_controller project directory, ~<code>python manage.py makemigrations</code> to update the database and store current changes made to the app</li>
  <li>~<code>python manage.py migrate</code></li>
  <li>Create serializers.py in api app. This will take our Python related code and translate it into a JSON response. Add RoomSerializer class to serializers.py</li>
  <li><code>generics.CreateAPIView</code> api view class RoomView. <code>generics</code> allows us to create a class that inherits from an api view.</li>
  <li>~<code>python manage.py runserver</code> and add data</li>
  <li><code>generics.ListAPIView</code> api view class RoomView will list out the data</li>
</ul>

Tutorial 3 - React Integration Using Webpack & Babel:
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

Tutorial 4 - React Router and Building Components:
<ul>
  <li>Create an index.css in static\css folder</li>
  <li>cd to music_controller\frontend and run ~<code>npm run dev</code>. cd to music_controller\frontend and run ~<code>python manage.py runserver</code></li>
  <li>Create new components HomePage.js RoomJoinPage.js CreateRoomPage.js</li>
  <li>As of late 2021, react dom v6 switch is replaced by "Routes". To use TechwithTim code, do ~<code>npm uninstall react-router-dom</code> and then <code>npm install react-router-dom@5.2.0</code></li>
  <li>Update urls.py of music_controller/frontend with urls for react components</li>
</ul>

Tutorial 5 - Handling POST Requests (Django REST):
<ul>
  <li>in views.py of api app import following
    <ul>
      <li><code>from rest_framework.views import APIview</code> for generic apiview</li>
      <li><code>from rest_framework.response import Response</code> to send custom responses from our view</li>
      <li><code>from rest_framework import status</code> to give us access to HTTP status codes, which we will need to use when use send our custom responses</li>
    </ul>
  </li>
  <li>Create a new serializer class CreateRoomSerializer in serializers.py of api app. We will send a POST request to the endpoint. This serializer will make sure the payload of the POST request corresponds with the correct fields that we need to create a new room. </li>
  <li>Create new view class CreateRoomView in views.py of api app. use session_key.</li>
  <li>Whenever we connect to a website we establish a session. A session is s temporary connection between 2 computers/devices. ex) don't have to sign into FB later because using the same session, everything authenticated already. Sessions have unique identities, in this case stored in system RAM. </li>
  <li>Add CreateRoomView to urls in urls.py of api app.</li>
  <li>Issue with editing the Room with POST. Result in Bad Request: /api/create-room and  "POST /api/create-room HTTP/1.1" 400 12241</li>
  <li>Solved with ~<code>manage.py migrate --run-syncdb</code></li>
</ul>

Tutorial 6 - Material UI Components:
<ul>
  <li>Update CreateRoomPage.js with MaterialUI and connect with backend.</li>
</ul>

Tutorial 7 - Calling APi Endpoints From React
<ul>
  <li>Create Room.js, responsible for handling the room page</li>
  <li>Update HomePage.js with route for room page using roomCode</li>
  <li><code>this.props.match.params</code>, match is the prop that stores all the information about how we get to this component from this react router</li>
  <li>Update urls.py in music_controller\frontend with url for room. Should be able to access http://127.0.0.1:8000/room/ROOMCODE</li>
  <li>Create a view for the Room. Add view class GetRoom to view.py in the api app 
Update urls.py in api app with GetRoom view</li>
  <li><code>request.GET.get(self.lookup_url_kwarg)</code> will get the code from the parameers in the url that matches the name 'lookup_url_kwarg', in this case 'code'</li>
  <li>Check to see if works with http://127.0.0.1:8000/api/get-room?code=ROOMCODE</li>
  <li>Update Room.js with getRoomDetails() to fetch response from api</li>
  <li>Update fetch in CreateRoomPage.js for the createRoom</li>
</ul>

Tutorial 8 - Creating the Room Join Page
<ul>
  <li>Add center class to index.css. Modify the render div in App.js with className="center" </li>
  <li>Update RoomJoinPage.js for handling textfieldchange and roombutton pressed.</li>
  <li>Create apiview class JoinRoom to check room exists</li>
  <li>Add urls to urls.py in api app</li>
  <li>Update RoomJoinPage.js to handle the api/join-room request</li>
</ul>

Tutorial 9 - ComponentDidMount and Django Sessions
<ul>
  <li>Update HomePage with <code>renderHomePage()</code>. More practice with Grid, Typography and ButtonGroup. <code>disableElevation</code> to remove shadows. <code>variant="contained"</code> to align horizontally</li>
  <li>Update HomePage path with <code>renderHomePage()</code> function</li>
  <li>Check if user is already in a room and if they are, we can redirect them to that room</li>
  <li>Using React lifecycle component methods. Every component in React has a lifecycle which you can monitor and manipulate during 3 phasess: Mounting, Updating and Unmounting</li>
  <li>Create new apiview <code>class UserInRoom</code> in views.py of api app. Update urls.py with url for UserInRoom</li>
  <li>Update HomePage with <code>async componentDidMount</code>. On first render, it will show us the homepage, once <code>componentDidMount</code> has finished running it will check if we have a room and redirect if so</li>
  <li>Update HomePage router in HomePage.js to join session or go to homepage with no room</li>
</ul>

Tutorial 10 - Django Sessions and Leaving Rooms
<ul>
  <li>Update Room.js with MaterialUI</li>
  <li>Create <code>leaveButtonPressed()</code> in Room.js to connect with backend and access endpoint. Bind <code>this.leaveButtonPressed</code> in the constructor </li>
  <li>Create new apiview LeaveRoom in views.py of the api app. If host of the room leaves, then removes room and everyone leaves. Query on all the room objects to see if user was the host using <code>Room.objects.filter(host=host_id)</code></li>
  <li>Update urls.py with <code>LeaveRoom</code> view</li>
  <li>Create a <code>clearRoomCode</code> function in HomePage.js to set the state of the roomCode to null.</li>
  <li>Update '/room/:roomCode' route in HomePage.js with render. <code>props</code> are given by the route. Return a room with the <code>...props</code> and leaveRoomCallback. '...' is the spread operator, will take all the properties passed in as an object and spread them out as prop1 is prop1 value and prop2 is prop2 value etc. Callback is a way that child component actually modify the parent component. This passes a method to the Room component so the Room component can call that method and modify the Room component</li>
  <li>Update <code>leaveButtonPressed()</code> in Room.js to call LeaveRoom endpoint with fetch</li>
  <li>Update <code>getRoomDetails</code> in Room.js to account for if we do not get response.ok. If we don't get response.ok, use method <code>this.props.leaveRoomCallBack()</code>, which was passed to us from the HomePage, clear the state on the HomePage. Then use <code>this.props.history.push("/")</code> to redirect back to the home page because the room doesn't exist.</li>
</ul>

Tutorial 11 - Updating Django Models
<ul>
  <li>Create a new Serializer <code>UpdateRoomSerializer</code> to handle the new Room settings update. Cannot pass a unique code to the serializer and therefore need to use <code>code = serializers.CharField(validators=[])</code> and pass that <code>code</code> to the UpdateRoomSerializer</li>
  <li>Create a new view <code>class UpdateRoom</code> in views.py of the api app. Will be using patch to update instead of get or post. Import the <code>UpdateRoomSerializer</code> and use that as the serializer_class. Check if room exists and if user is host before sending response</li>
  <li>Update urls.py in api app for the <code>UpdateRoom</code> view</li>
  <li>Update this.state in Room.js with <code>showSettings</code> to determine whetehr to show settings or not. Update Room.js with <code>updateShowSettings(value)</code> function. Bind <code>this.updateShowSettings</code></li>
  <li>Create renderSettingsButton() in Room.js make a method that will only show settings if the user is the host. Add ternary operator above leave room to show Settings button if user is the host</li>
  <li>Create <code>renderSettings()</code> to access room settings. Import <code>CreateRoomPage</code> for room settings updates</li>
  <li>Bind renderSettingsButton and renderSettings to this</li>
  <li>Add if statement to render show settings or not</li>
</ul>

Tutorial 12 - React Dafult Props and Callbacks
<ul>
  <li></li>
</ul>
