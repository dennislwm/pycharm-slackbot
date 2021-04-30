# pycharm-slackbot

Deploy your first Slack bot to a Platform-as-a-Service ["PaaS"].

<!-- TOC -->

- [pycharm-slackbot](#pycharm-slackbot)
  - [Project](#project)
  - [Azure App Service](#azure-app-service)
    - [Benefits of Azure](#benefits-of-azure)
    - [Installing Azure App Service Extension for Visual Studio Code](#installing-azure-app-service-extension-for-visual-studio-code)
    - [Creating a Development Server on Azure](#creating-a-development-server-on-azure)
    - [Preventing an Azure web app from going to sleep](#preventing-an-azure-web-app-from-going-to-sleep)
  - [Project Structure](#project-structure)
    - [Creating the Virtualenv](#creating-the-virtualenv)
    - [Generating Slack bot tokens](#generating-slack-bot-tokens)
  - [References](#references)

<!-- /TOC -->

## Project

This project is less about building a Slack bot, but is more of how to deploy the bot to various PaaS.

1. [Azure App Service "Web App"](#azure-app-service)

2. Anvil

3. Heroku

4. DigitalOcean App Service

## Azure App Service

### Benefits of Azure

You start using Azure with a free account, you'll get $280 credit to spend in the first 30 days after you sign up. In addition, you get free monthly amounts of two groups of services:

1. Popular services, which are free for 12 months.

2. Other services that are always free.

Fortunately, the Azure App Service comes under second group. You get 10 web, mobile or API apps with 1 GB storage always free.

### Installing Azure App Service Extension for Visual Studio Code

This lab uses Visual Studio Code ["VSCode"] as the editor and we will be installing the [Azure App Service extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice).

Download and install the above extension. Once complete, you'll have an Azure icon in the Activity Bar.

*Note: If your activity bar is hidden, click on View > Appearance > Show Activity Bar.*

Sign in to your Azure Account by clicking **Sign in to Azure**, or if you don't already have an Azure Account, click **Create a Free Azure Account**.

### Creating a Development Server on Azure

Once you are signed in to your Azure account and you have your web app open in VSCode, click the **Deploy** button in the Azure App Service explorer (it's the blue up arrow). Select the folder to deploy.

Choose **Create New Web App** and type a globally unique name for your web app. This name will be your `[SUBDOMAIN]` within the `azurewebsites.net` domain, e.g. `https://[SUBDOMAIN].azurewebsites.net`.

Choose a **Python 3.x** as your Runtime stack, and select the **Free** tier.

If prompted "Would you like to update your workspace configuration to run build commands on the target server?", you should click **Yes**. The ensures that your code will be build on the server after you deploy it.

After the deployment has completed, navigate to the endpoint on your Azure website.

```
https://[SUBDOMAIN].azurewebsites.net/slack/events
```

As we have not generated the Slack bot tokens, you should see the page.

```
These are not the slackbots you're looking for.
```


### Preventing an Azure web app from going to sleep

The Azure web app appears to run in a container that goes to sleep if your web site is inactive for a certain period of time (15 mins?). The container is removed after it's stopped, hence there is no persistent storage for your web app.

Azure web app settings have an **Always on** option with basic and standard tiers that keeps your app alive. However, this feature is disabled on free tier.

This lab uses an online third-party monitor [UptimeRobot](https://uptimerobot.com) to "ping" your web site. It also serves as a monitor for your site, letting you know if it's down.

Even on the free tier, you can create up to 50 monitors to call your web site, at least every 5 minutes, which is sufficiently regular to prevent your site from going to sleep.

---
## Project Structure
     pycharm-slackbot/                <-- Root of your project
       |- .gitignore                  <-- GitHub ignore 
       |- app.py                      <-- Code for Slack bot
       |- README.md                   <-- GitHub README markdown 
       |- requirements.txt            <-- Dependencies for Python app

---
### Creating the Virtualenv


### Generating Slack bot tokens


## References

* [Building your first Python Slackbot - YouTube](https://youtu.be/2X8SrKL7E9A)

* [Azure Free Account FAQ](https://azure.microsoft.com/en-au/free/free-account-faq)

* [How to prevent an Azure website from going to sleep?](https://stackoverflow.com/questions/33789895/how-to-prevent-an-azure-website-from-going-to-sleep)
