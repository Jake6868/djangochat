#DJANGOCHAT
##Video demo: https://www.youtube.com/watch?v=1J99RaM9F1g
##Description: a simple chat for friends to sign up and talk about work and football
- Login field: allow user to login to the account. Check if the login information is correct with the database
- Sign up field: allow new user to sign up a new account. Check if the username already exists or repeated Password does not match, if failed, The screen will render error message.
- Logout field: allow user to log out of the account
- Rooms field: by clicking into the rooms field, user can go to the rooms and chat with everyone else

###djangochat/core:
- This directory includes the templates of login, sign up, frontpage and base html files, and admin.py, apps.py, forms.py, models.py, test.py, urls.py, views.py. 
- The base.html file is the layout of the website, can be reused. The frontpage.html file is a simple landing page. the login.html file allow user to login to the account. The signup.html file allows user to sign up to new account.
- The forms.py defines Signup form class to be used in the sign up page
- The views.py includes functions to render html files and handling requests. 
- The urls.py is responsible for defining URL routing for login, frontpage, signup pages.


###djangochat/room:
- The views.py file include views to display chat rooms, handle user messages, and manage user interactions.
- The admin.py register model Room to the admin site. 
- The consumers.py implements the ChatConsumer class to handle WebSocket events for connecting, disconnecting, and receiving messages.
- The room.html adds JavaScript to establish a WebSocket connection, handle incoming messages, and send new messages.
- The routing.py defines URL patterns for WebSocket connections.
- The models.py file includes models for messages, chat rooms. Each model represent a table with each field represent a column. 
- The apps.py file defines the configuration for the app. It is used to specify configuration options for the room and used to execute startup code when the room is loaded.
- The urls.py file is responsible for defining the URL routing for the room. It maps URL patterns to views.

###djangochat/djangochat:
- The asgi.py file configures the ASGI application to handle HTTP and WebSocket connections using Channels.
- The settings.py to include Channels configuration and ASGI application setup.
- wsgi.py: The script sets up the necessary environment variable to point to your Django settings module.It initializes the WSGI application using Django's get_wsgi_application function. This file is primarily used in the project to a production server. The WSGI server will use the application callable to interact with the application.
- urls.py:  sets up the URL routing for the project. It defines the top-level URL patterns that map to specific applications or views within the project. By using include, I break down the URL configuration into smaller modules corresponding to different applications. This makes the URL configuration more manageable and modular. path('', include('core.urls')) sets the root URL pattern to use the URL configurations from core.urls. path('rooms/', include('room.urls')) sets the pattern for any URL starting with rooms/ to use the URL configurations from room.urls. path('admin/', admin.site.urls) includes the Django admin interface, making it accessible at the /admin/ URL.

###manage.py: The Django command-line administrative utility for the project. Run administrative commands for the project using python manage.py <command> [options].

