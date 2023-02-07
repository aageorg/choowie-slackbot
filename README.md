# Choowie Slackbot
Choowie moves slack threads from one channel to another on trigger reaction. 
## Dependencies
You need to include boltdb/bolt (https://github.com/boltdb/bolt/) package to your golang environment.
## Getting started
First of all, create your own Slack application on https://api.slack.com/apps/. When done, and you got a credentials you can build and run an application. 
1. Install go and download choowie:
```
$ git clone github.com/aageorg/choowie-slackbot
```
2. Build the application 
```
$ go build -o choowie *.go
```
3. Run choowie with flag --help. 
```
$ ./choowie --help
Usage of ./choowie:
  -port string
        Https port where to listen incoming callbacks from Slack (default "8444")
  -slack-app-id string
        App id from slack app settings
  -slack-client-id string
        Client ID for making oauth.v2.access request
  -slack-client-secret string
        Secret for making your oauth.v2.access request
  -slack-sign-secret string
        Slack signs the requests we send you using this secret
  -tls-cert-path string
        Full path to TLS certificate file.
  -tls-privkey-path string
        Full path to TLS private key file
```
All parameters excludind -port are mandatory. Most of them you can get on application credentials page of your Slack account. You also must obtain a valid SSL certificate for your server domain name and provide both files (fullchain.pem and privkey.pem) to choowie.

4. Now we need to enable event subscription for our Slack application. From your app page go to "Add features and functionality" -> "Event subscription". Switch this feature on and provide to Slack url where does choowie listen (e.g. https://choowie.yourdomain:8444). Slack will immediatelly check availability of your server (choowie should be launched) and save settings on success.
5. Add choowie to your team in Slack. Using owner or admin account with high permission level sign in to Slack. Open in web browser https://choowie.yourdomain:8444/setup and allow appcication to get access to requested scopes. Now your choowie slackbot is ready to work
## Slack commands
+ `/automove <#channelfrom> #channelto` - to enable threads automove. 
+ `/showautomoves` - to see all enabled automoves 
+ `/noautomove <#channelfrom> #channelto` - to disable an automove

