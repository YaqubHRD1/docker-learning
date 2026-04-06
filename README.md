The redisproject folder contains the code used to build a multi-container application that consists of a Flask web app and a Redis database.

The Flask web app has two routes. One route displays a welcome message. The other route increments and displays a visit count that's stored in Redis.

Docker compose is used to manage the multi-container application. 

Bonus features include:

Configured Redis to use a volume to persists it's count between different sessions.
Modified the Flask app to read Redis connection details from environment variables.
Scaled the Flask web app to run multiple instances and load balance with Nginx. 
