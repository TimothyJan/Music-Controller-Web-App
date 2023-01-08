# Music-Controller-Web-App
Django &amp; React - Full Stack Web App with Python & Javascript from Tech With Tim.<br>

Collaborative Music Playing System. Web app for a group of people to control the music being played in unity.<br>

Host can create a room and give out a code to people who want to join the room. People can join the room, they can vote to skip the song. They can pause/play the song or whatever permissions the host gives them as long as they have Spotify Premium.<br>

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
  <li>Modify CreateRoomPage so that we can pass props to the CreateRoomPage as well as have default props for a new room. Do so by removing hard-coded default values and providing a <code>defaultProps</code></li>
  <li>Create <code>renderCreateButtons()</code> and <code>renderUpdateButtons()</code>. One method that renders the buttons to create a new room and one method that renders the button to update the room. </li>
  <li>Update <code>render()</code> in CreateRoomPage.js with ternary operator to determine title: "Update Room" or "Create a Room"</li>
  <li>Create <code>handleUpdateButtonPressed()</code> in CreateRoomPage.js to handle the UpdateRoom on the backend. Add <code>errorMsg</code> and <code>successMsg</code> to the this.state. Bind <code>this.handleUpdateButtonPressed</code>. Update <code>onClick</code> with <code>this.handleUpdateButtonPressed</code> for the <code>renderUpdateButtons()</code></li>
  <li>Import Collapse from MaterialUI. Collapse will allow us to show something or collapse it on the screen. Add Collapse to <code>render()</code> function. <code>in</code> is a Boolean value, tells us whether or not to show Collapse or not</li>
  <li>Update default value in Guest Control of Playback State in CreateRoomPage.js with <code>this.props.guestCanPause.toString()</code></li>
  <li>After updating Room in settings, we want the Room page to auto update as well. Update Room.js for the updating CreateRoomPage using <code>updateCallback</code> and calling the <code>this.getRoomDetails</code>. Update <code>handleUpdateButtonPressed()</code> with <code>this.props.updateCallback();</code> to update Room.js when going back to that Room page. Bind <code>this.getRoomDetails</code> in Room.js</li>
  <li>~<code>npm install @material-ui/lab</code>. <code>import Alert from "@material-ui/lab/Alert";</code> in Create RoomPage.js. Update error or success messages with Alerts. <code>severity</code>: "success" makes it green and error makes it "red". <code>onClose()</code> to clear the successMsg or errorMsg
</li>
</ul>

Tutorial 13 - Spotify API Tutorial (Authentication & Tokens)
<ul>
  <li>We authenticate our application with Spotify. Then the user authenticates our application - your application has access to my information it can control the music so on and so forth. Then using that authentication(tokens), we can send requests to the Spotify API and will in turn control the user's music
    <ul>
      <li>Application requests authorization to access data -> Spotify displays scope of what Application wants to access and prompts user to login -> User logs in and authorizes access</li>
      <li>Application requests access and refresh tokens -> Spotify returns access and refresh tokens, access tokens used to access info and refresh token used to ask for another token because access tokens expire after a period of time</li>
      <li>Application uses access tokens in requests to Web API -> Spotify WEB API returns requested data</li>
      <li>Application - User access token in requests to Web API -> Spotify returns new access token</li>
    </ul>
  </li>
  <li>Go to <a href="https://developer.spotify.com/dashboard/">Spotify Developer</a>, log in, and create an app</li>
  <li>Create new app in music_controller/music_controller using ~<code>python manage.py startapp spotify</code>. Add <code>'spotify.apps.SpotifyConfig'</code> to INSTALLED_APPS of settings.py in music_controller project</li>
  <li>Create urls.py and credentials.py in spotify app. Add credentials from Spotify to the credentials.py</li>
  <li>To authenticate or request access from Spotify - in views.py of spotify app, create apiview <code>class AuthURL(APIView)</code> to generate a url we can use to authenticate our Spotify application. Update urls.py of spotify app for AuthURL. Update urls.py for music-controller project for spotify app</li>
  <li>Need to set up a redirect URI in credentials.py and in Spotify developer online. After sending request to Authurl, we need a callback or some url that the information requested(returned code and state) gets returned to. After getting Authorization access, we then need to send another request and get the access and refresh token. </li>
  <li>To create new model that can store tokens, create new model <code>class SpotifyToken</code> in models.py of Spotify app. ~<code>python manage.py makemigrations</code> and ~<code>python manage.py migrate</code></li>
  <li>Create util.py in spotify app to save our tokens by saving into a brand new model or updating a model. Create <code>get_user_tokens</code> in util.py to get user tokens. Create <code>update_or_create_user_tokens</code> in util.py to update/create user tokens </li>
  <li>In views.py of the spotify app, create function <code>spotify_callback</code>. Associate session key/id with their access/refresh tokens and store in our database. Use <code>update_or_create_user_tokens</code> to store tokens in database and then use redirect back to our original application. Update urls.py of spotify app with redirect to frontend for <code>spotify_callback</code>. To allow this, need to add <code>app_name = 'frontend'</code> in urls.py of frontend app because Django needs to know this urls.py file belongs to the frontend app. Need to give the '' path a formal name so that when we call the redirect we know which path we should actually go to</li>
  <li>Need to check if current user is authenticated. Just need to check if the current session id representing the user is in the database and if the token is expired or not. Create <code>is_spotify_authenticated()</code> and <code>refresh_spotify_token()</code> in utils.py of spotify app</li>
  <li>Need to set up a view that can tell us whether or not we are authenticated. The util is returning python code but we need it to return json so our front end can understand. Create new apiview <code>class IsAuthenticated()</code> in views.py of spotify app to call util function and return json response. Set up IsAuthenticated in the urls.py of spotify app</li>
  <li>As soon as we get into a room, if we are the host we need to immediately authenticate our Spotify, in order to control the music. If not the host, they need to authenticate with Spotify -> Show Spotify login prompt, give authorization, take tokens and store them in the database</li>
  <li>Add <code>spotifyAuthenticated</code> to this.state in Room.js. Create new method <code>authenticateSpotify</code> to send request to backend to check if current user is authenticated, but only if the situation is a host. Need to wait until <code>getRoomDetails()</code> has run before calling <code>authenticateSpotify</code> method and therefore need to modify <code>getRoomDetails()</code> with if statement checking if <code>this.state.isHost</code> then <code>this.authenticateSpotify()</code>. Bind <code>this.authenticateSpotify</code>. This will redirect us to spotify authorization page, then after user authorizes us, it will redirect us spotify callback. The spotify callback will save the token and redirect us to the front end and then the front end will redirect us back to the room page</li>
</ul>

Tutorial 14 - Using the Spotify API
<ul>
  <li>Want to get the information of the currently playing song like the duration, if it's playing or not. Need to send a request to the Spotify API to get the current information about the host of the room's playback information</li>
  <li>In util.py create function <code>execute_spotify_api_request()</code> to send requests to Spotify.</li>
  <li>To get information about the current song create a new api view <code>class CurrentSong(APIView)</code> in views.py of spotify app. Add path for CurrentSong view in urls.py of spotify app. Test by making a new room, playing Spotify and using http://127.0.0.1:8000/spotify/current-song</li>
  <li>Update this.state with <code>song</code> as a dictionary with all the song information in Room.js. When song ever changes, <code>this.state.song</code> will be updated accordingly</li>
  <li>Create new method <code>getCurrentSong()</code> in Room.js to fetch current song data from spotify app. Call <code>getCurrentSong()</code> after authenticating spotify and getting room details with <code>this.getRoomDetails();</code> in the constructor</li>
  <li>Need to be constantly checking for updates, like if song is playing or paused. Spotify does not have support for public web sockets, and therefore we need to use polling method. The polling method is basically continually updating every single second. We set up an interval so that every second we update this.state in Room.js. We do this by creating method <code>componentDidMount()</code> to set <code>this.interval</code> and <code>componentWillUnmount()</code> to clear <code>this.interval</code> in Room.js. Also need to bind <code>this.getCurrentSong</code>. Make sure song is playing when checking http://127.0.0.1:8000/room/AOCYOS</li>
  <li>Create new component MusicPlayer.js to provide a nice music player component in Room.js. In Room.js import MusicPlayer and use <code><MusicPlayer {...this.state.song} /></code> to pass song information into MusicPlayer </li>
</ul>

Tutorial 15 - Pausing & Playing Music with Spotify API
<ul>
  <li>Create methods <code>play_song(session_id)</code> and <code>pause_song(session_id)</code> in utils.py of spotify app. Update urls.py with paths for PauseSong and PlaySong</li>
  <li>Create apiviews <code>def PauseSong()</code> and <code>def PlaySong()</code> in views.py of spotify app</li>
  <li>Modify MusicPlayer.js to use api views <code>PauseSong</code> and <code>PlaySong</code></li>
  <li>Create methods <code>pauseSong</code> and <code>playSong</code> in MusicPlayer.js to fetch url paths. Modify icon buttons to use <code>pauseSong</code> and <code>playSong</code></li>
</ul>

Tutorial 16 - Skipping Songs and Handling Votes
<ul>
  <li>Create function <code>skip_song(session_id)</code> in util.py of spotify app. Create a path for <code>skip_song</code> in urls.py of spotify app</li>
  <li>Create new apiview <code>SkipSong</code> in views.py of spotify app</li>
  <li>Create new method skipSong in MusicPlayer.js</li>
  <li>To handle votes we will need to store who has voted, check how many votes there are for a room, check if the vote was for which song and current/previous song and when the vote was cast </li>
  <li>Update Room model in models.py of api app with current_song field</li>
  <li>Create new model Vote in models.py of spotify app. ForeignKey, we need to pass an instance of another object(in this case Room object) to this Vote model. This will store a reference to the Room object in our Vote. That way whenever we look at a vote we can determine which Room Object that was in, as well as access information about that Room object directly. If Room gets deleted, <code>models.CASCADE</code> will cascade down and delete anything that was referencing this room</li>
  <li>~<code>python manage.py makemigrations</code> and ~<code>python manage.py migrate</li>
  <li>Add method <code>update_room_song()</code> to view <code>CurrentSong(APIView)</code> in views.py in spotify app. <code>from .models import Vote</code>. Add <code>self.update_room_song(room, song_id)</code> before returning Response in view <code>CurrentSong(APIView)</code></li>
  <li>Update apiview <code>SkipSong</code> in views.py of spotify app with voting for skipsong. Update <code>CurrentSong</code> method, <code>song['votes']</code> with <code>votes = len(Vote.objects.filter(room=room, song_id=song_id))</code> and <code>song['votes_required']</code> with <code>'votes_required': room.votes_to_skip</code></li>
  <li>Update MusicPlayer.js with <code>{this.props.votes} / {this.props.votes_required}</code> votes needed</li>
</ul>

Tutorial 17 - Functional Components (useState, useEffect)
<ul>
  <li></li>
</ul>

