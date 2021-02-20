# Fedibot Guide
> Get your api token right from the commandline without other software

## Prerequisites
* A commandline
* curl
* A text editor
* This repo saved locally (`git clone https://github.com/taizweb/fedibot-guide.git` or just [download the zip](https://github.com/taizweb/fedibot-guide/archive/master.zip))

## Create Your Account
Go on whichever instance you plan to host the bot and make it an account. This will likely require an email.

## Getting your client ID/Secret
* Go to the directory with this README inside it and edit `api1`
* Change the line with "client\_name" to whatever you intend to name your bot.
* Change `INSTANCE.HERE` to whatever instance you put the account on. Keep the rest of the line the same
* Save the file
* Now, from your commandline, run `./api1`
* You will get some text back from the instance as a response. Copy the parts after `client_id` and `client_secret` to a file. You should probably label these

## Getting the access token
* Edit `api2`
* Change `client_id` and `client_secret` with the info you got from the last step
* Change `INSTANCE.HERE` to whatever instance you put the account on. Keep the rest of the line the same
* Save the file
* Now, from your commandline, run `./api2`
* Once again you'll get some text back. This time you'll just want the `access_token`. Copy this somewhere

## Confirming
* Edit `api3`
* On the second line, after the word "Bearer", paste your access token from the last step. There should be a space between Bearer and your token
* Change `INSTANCE.HERE` to whatever instance you put the account on. Keep the rest of the line the same
* Save the file
* Now, from your commandline, run `./api3`
* If all goes well, a file named test will be created and contain info about your bot

## Getting Auth Code
* Open a browser and visit `https://INSTANCE.NAME/oauth/authorize?client_id=CLIENT_ID&scope=read+write+follow+push&redirect_uri=urn:ietf:wg:oauth:2.0:oob&response_type=code`
* **BEFORE you actually visit, edit	`INSTANCE.NAME` to your instance's domain, and change the `CLIENT_ID` to whatever your client id was from a previous step**
* On the page, type in your username/password for the account
* If all went well, you should be at a page saying "Successfully authorized" and be given a token code. Save this.
NOTE: On some displays, the token code won't be entirely visible in the box. To ensure you copied the entire thing, double click the code to highlight it, then copy it

## Getting the Token
* Edit `api4`
* Replace `client_id`, `client_secret` and `code` (the authcode from last step) with your information
* Change `INSTANCE.HERE` to whatever instance you put the account on. Keep the rest of the line the same
* Save the file
* Now, from your commandline, run `./api4`
* Finally, copy the `access_token` you get as a response and save it

## Making a test post
This step is entirely optional, but if you want to be sure the token is working:
* Edit `post`
* On the second line, after "Bearer" (mind the space), past your token from the last step in
* Replace INSTANCE.NAME with your instance
* Save the file
* Now, from your commandline, run `./post`
* You should get some data back, but it's safe to ignore that. Instead, go to your bot account in your browser and see if the message was posted

## Where to go from here
Now that you have the token, you can do anything the api allows. I recommend checking out [the Mastodon docs](https://docs.joinmastodon.org/) for things to use on the api. Additionally there's multiple api wrappers that you can now make full use of, such as [https://github.com/halcy/Mastodon.py](Mastodon.py).

