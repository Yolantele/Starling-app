
<p align="center">
    <img height="180" width="180" src="https://www.starlingbank.com/static-files/developer-portal/github/starter-web.png">
</p>

<h1 align="center">
  <a href="http://developer.starlingbank.com/get-started">Starling Developers</a>
  <br>Web Starter Kit
</h1>


This project contains a sample web application that integrates with the Starling Bank API to retrieve a customer's transaction history.
The React Redux application is based on [this starter kit](https://github.com/davezuko/react-redux-starter-kit) and is comprised of a simple REST API written in javascript using node.js with express. The 

Looking for the [Mobile Starter Kit](https://github.com/starlingbank/developer-api-mobile-app-starter) instead?

## Getting Started
Please also take a look at the higher-level [Getting Started Guide](http://developer.starlingbank.com/get-started) on our site, which covers usage of our API as a whole.

### Prerequisites

The only prerequisite is [Node.js](https://nodejs.org). The best way to install Node.js is with [nvm](https://github.com/creationix/nvm).

### Installation

From the root of the project, install dependencies as follows. Use either the `yarn` or `npm` package manager.

```bash
yarn install
```

#### Start the application

```bash
yarn run dev
```

This will serve the client application on `localhost:3000` when using the default configuration.

### Configuration

You must register an application on the [Starling Developers](https://developer.starlingbank.com/get-started) site
 to obtain a `client_id` and `client_secret`. The `client_id` and `client_secret` should then be configured in the `server/config.json` file.
 The redirect URL registered in the developer portal must match the configured URL in this application.

The `config.json` file will look like this
```JSON
{
  "clientId": "<application client id>",
  "clientSecret": "<application client secret>",

  "cookieSecret": "21e361d0-ff2c-4763-a084-1032f2103ce8",

  "productionApi": "https://api.starlingbank.com",
  "personalAccessToken": "<personal access token>",

  "sandboxApi": "https://api-sandbox.starlingbank.com/",
  "initialRefresh": "<Refresh token from Starling Developers site>",

  "oauthApi": "https://oauth.starlingbank.com",
  "oauthRedirectUri": "http://localhost:3000/api/oauth/redirect"
}
```
The missing bits of config are specific to your account - your application, your sandbox customer, your personal access.

You can fill in this config as suits your use-case, be it personal access, sandbox, or oauth/production. 



Simply replace `<application client id>` and `<application client secret>` with the `client_id` and `client_secret` for your application.


Then start the app in production using the following command
```bash
node server/main.js
```

#### Sandbox
For the sandbox environment setup, use the config file, `config.json`, correctly filling in the following fields:
```JSON
{
  "clientId": "<application client id>",
  "clientSecret": "<application client secret>",
  
 "sandboxApi": "https://api-sandbox.starlingbank.com/",
  "initialRefresh": "<Refresh token from Starling Developers site>",
}
```
Where the `<refresh token>` is a sandbox customer's token from the [sandbox environment](https://developer.starlingbank.com/sandbox).

You can then start then select the sandbox from the landing page of your application.

<blockquote>
Note: the current implementation requires the refresh token to be replaced on server restart. This is temporary, as a programatic way to retrieve an application's sandbox customer's is in the works.
</blockquote>

#### Personal Access
This starter kit can also be used to access your own Starling Bank data, right out of the box. This can be achieved using `config_personal.json`.
```JSON
{
  "cookieSecret": "21e361d0-ff2c-4763-a084-1032f2103ce8",
  "partnerApiBase": "https://api.starlingbank.com",
  "initialRefresh": "<personal access token>"
}
```
Where the `<personal access token>` is your personal access token, which can be obtained from your [developer account](https://developer.starlingbank.com/token) after linking it to your customer account.

You can then start the application for use with personal access tokens
```bash
yarn run dev
```

## Mobile Starter Kit Users

Those using the [React Native mobile starter kit](https://github.com/starlingbank/developer-api-mobile-app-starter) need to also clone this repo and follow the installation instructions above, while replacing the contents of the `config.json` file with that given in the mobile starter kit [README.md](https://github.com/starlingbank/developer-api-mobile-app-starter)   
