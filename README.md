# Modmail
## Discord bot used to send anonymous messages to the moderators

### Setup

1. Create a discord bot
  - see https://discordpy.readthedocs.io/en/latest/discord.html for instructions
2. Install bot server software
  - clone the repository `git clone https://gitlab.com/awol-linux/ansible-doc-bot.git`
  - Install requirments `pip install -r requirments.txt`
  - create a .env file and put `DISCORD_TOKEN={your-bot-token}` inside it
  - start the bot `python3 ./bot.py`
``` Please note as of now there is no presistent storage. once that is set up there will probaly need to be a etcd backend. although it may be something else I am not settled yet 
```
3. Alternatively you can use Docker. The bot is not yet in Dockerhub so it still would need to be built.
```
$ git clone https://github.com/NetworkChuckDiscord/Modmail.git && cd ModMail
$ docker build . -t ModMail
$ docker run --env DISCORD_TOKEN={your-bot-token} ModMail
```
## Usage

Once the bot is added to your server, you can interact by sending it a DM. When you do that the bot will create a channel in the catagory named tickets and anonymously forward the messages from that user into that channel. Any responses written in that channel will then be DMed to the user.

There are currently no commands for this bot hopefully there will be soon.

| permision | Command | Description |
|-----------|---------|-------------|
| Admin | $search \<filters\> \<term\>| Type is the search you want to use can be 1) -ltdate -etdate -author and term is the search term |
| Admin | $ds| Direct Search, your parameters are passed directly to the DB (MongoDB) is a big security risk | 
| Admin | $close | Archives the complaint putting a full log in admin log |
| User | $sf | Makes the bot send you a friend reqeust |
| User | $print | spits out all of the tickets sent by the user |

## Configuration

There is currently no config file that is still in the works:

| Setting | default Value | Description |
|---------|---------------|-------------|
| nods | false | Prevents Admins from running direct search due to security risk |
| prefex | $ | sets the default command prefex
| ticket_catagory | Null | catagory where the complaint channels are placed | 
| complaint_log | Null |log where archived messages go |
