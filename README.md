## A Meta-Llama-3.1 Chatbot Template for FREE monetization ##
Use this template to rapidly build and monetise a [Meta Llama 3.1](https://huggingface.co/meta-llama) chatbot and start earning money

## Requirements for running it locally on laptop ##
* Windows / Mac / Linux with Git installed
* Python 3.8
* Ngrok for Tunneling (For Local Laptop Development Environment)
* Hugging Face API token
  
  * It should look something like this:
![bot_setup](https://github.com/user-attachments/assets/39b3e863-d9ff-44a7-bd20-8646708a571c)
* Click on `Save`. It will redirect you to your dashboard.
* On your dashboard you can see your newly created bot
  * ![figure](https://github.com/machaao/machaao-py/raw/master/images/new_bot.png?raw=true)
* Click on `Settings` tab. It will open your bot configuration page.
  * ![figure](https://github.com/machaao/machaao-py/raw/master/images/bot_config.png?raw=true)
* On the configuration page you'd be able to see a string named `token`. That's your `Machaao API Token`

## Local Setup ##
### Download or clone this repository ###
```
git clone https://github.com/machaao/llama-3.1-8b-instruct-chatbot.git

cd llama-3.1-8b-instruct-chatbot
```

### Install requirements ###
```bash
pip install -r requirements.txt
```

### Create a new .env file in the llama-3.1-8b-sample directory ###
```bash
nano -w .env
```
Put these key-value pairs in your .env file
```
API_TOKEN=<Machaao API Token>
BASE_URL=https://ganglia.machaao.com
NAME=Jess
HUGGINGFACEHUB_API_TOKEN=<YOUR Huggingface API TOKEN> 
MODEL_NAME=meta/meta-llama-3.1-405b-instruct
CREDIT=5
```

Get your HF api token [here](https://huggingface.co)

### Change ```CREDIT``` variable to change the cost of a text message ###
```
CREDIT=5 implies one message would consume 5 credits
```

### Modify logic/prompt.txt to change the system prompt ###
```
You are a helpful assistant named [name]
```


### Modify the core() function in logic/bot_logic.py to personalize responses ###
```
def core(self, req: str, user_id: str):
```
* Refer to [platform documentation](https://messengerx.rtfd.io) for personalization options

### Run the chatbot server from the root directory of the repo ###
```
python app.py
```

### Start ngrok.io tunnel ###
```
ngrok http 5000
```
* You'll get a `Forwarding` URL mentioned on the console as shown below
  * ![figure](https://github.com/machaao/machaao-py/raw/master/images/ngrok_console.png?raw=true)
* Copy the `Forwarding` URL. In this example it would be:
```
https://26ea-150-107-177-46.ngrok-free.app
```

### Update your webhook ###
Update your bot `Webhook URL` on the bot configuration page with the NGROK `Forwarding URL`<br/>
In this example your Webhook URL would be:
```
https://26ea-150-107-177-46.ngrok-free.app/machaao/hook
```
Refer to this screenshot below
![figure](https://github.com/machaao/machaao-py/raw/master/images/update_hook.png?raw=true)

### Test your bot:
Click on `Preview` to chat with your bot

  
### Get Dashbot.io API KEY (Recommended for Production) ###
* You can acquire the API Key via [Dashbot.io](https://dashbot.io) and replace it in the ```.env``` file under the entry
```DASHBOT_KEY```

## Remote Setup (Heroku) ##

We are assuming you have access to a [heroku account](https://heroku.com)
and have installed heroku command line client for your OS.

### Login to Heroku ###
```
heroku login
```

### Create a new app on Heroku and note down your heroku app name
```
heroku create
```

### Commit changes and push the repository to Heroku ###
```
git commit -m ".env updated"
git push heroku master
```

### Open the logs to confirm successful Deployment ###
```
heroku logs --tail
```

### Update your webhook ###
Update your bot Webhook URL at [MessengerX.io Portal](https://portal.messengerx.io) with the heroku app url
```
Webhook Url: <YOUR-HEROKU-APP-URL>/machaao/hook
```

### Test your bot:
Visit: ```https://messengerx.io/<your-character-name>```

## Notes / Additional Resources ##
* Please note that this document isn't meant to be used as a guide for production environment setup.
