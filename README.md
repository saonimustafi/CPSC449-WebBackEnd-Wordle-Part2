# CPSC449-WebBackEnd-Wordle-Part2

Introduction
In this project, we developed a RESTful microservice for tracking user wins and losses.

·	Posting a win or loss for a particular game, along with a timestamp and number of guesses – The user should be able to make a post request providing the win/loss of a particular game, the game id, and the number. The timestamp, by default, will be the current timestamp. This request will insert a record in the games table.

·	Retrieving the statistics for a user – The user will be able to retrieve information like the current streak, maximum streak, guesses, win percentage, games played, games won, average guesses.

·	Retrieving the top 10 users by the number of wins – This makes a get request to retrieve the usernames of the top 10 users who have the maximum number of wins.

·	Retrieving the top 10 users by longest streak – This makes a get request to retrieve the usernames of the top 10 users by their maximum streak.
Before sharding, the database used to accomplish these tasks is ‘stats.db', and the tables created are – users and games. We also have two views - wins and streaks which are used to find the top 10 users by the number of wins and longest streaks.

For sharding, we created four SQLite databases –three databases holding shards of the games table, and one database containing the users tables. We changed the primary key of the users tale from user_id to uuid so that we do not get duplicate user ids for users in the database shards of the games table.
If possible write about traefik and testing

Steps to Initiate the Databases and Run the Processes – 
1. Run stats.py to create stats DB
2. Run the DB initialization file 'db_init.py' to shard the database by typing the command - python3 db_init.py
3. Run the services using the commands - python3 microserviceproj3.py
4. Run foreman using following command - foreman start --formation "api1=1, api2=1, api3=1,api4=3"
