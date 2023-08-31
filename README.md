## About

## Disclaimer:
- This is a custom version of the orginial package. All credits to the orginial owners.

interactions.js is a powerful [Node.js](https://nodejs.org) module that allows you to easily interact with [Discord](https://discord.com/developers/docs/intro) interactions.

- Object-oriented
- Performant
- Inbuilt Cache
- Easy to use

## Installation

**Node.js 16.9.0 or newer is required.**

```sh-session
npm i interactions.js
```

## Example Application

```js
const { Application } = require("interactions.js");
require('dotenv').config()

const Client = new Application({
    botToken: process.env.TOKEN, // Your Bot Token
    publicKey: process.env.PUBLICKEY, // The Application Public Key
    applicationId: process.env.APPLICATIONID, // The Application ID
    port: 8221, // Your Port (Default: 1337)
});

/**
 * After calling start(), the api starts on port 8221 in this example and you need to set your application's interaction url to https://your-domain.com/interactions
 * 
 * The /interactions parts is required and you can't change it.
 */
Client.start().then(() => {
    console.log("Client Started");
});

Client.on("debug", debug => console.log(debug));

Client.setAppCommands([
    {
        name: "ping",
        description: "Pong!",
    },
]).catch(console.log);

Client.on("interactionCreate", async (i) => {
    if (i.commandName === "ping") {
        return i.reply({
            content: "Pong!",
            ephemeral: true,
        });
    }
});
```

## Example way to get the guild count
```js
const { UserManager } = require("interactions.js");
const application = await UserManager.fetchMyApplication();

// Note: This is not the actual guild count, but an approximation
const guildCount = application.approximate_guild_count;
```

## Help

If you don't understand something in the documentation, you are experiencing problems, or you just need a gentle
nudge in the right direction, please don't hesitate to join our [discord server](https://discord.gg/ZVERh35).

## Example Handler
- [http-bot-template](https://github.com/mezotv/http-bot-template)

## Bots Using interactions.js
- [Himiko](https://discord.com/api/oauth2/authorize?client_id=1008142696801648711&permissions=2147797056&scope=bot%20applications.commands)
- [Imagine](https://discord.com/api/oauth2/authorize?client_id=1039996075882336336&permissions=313344&scope=applications.commands%20bot)
- [Memer](https://discord.com/api/oauth2/authorize?client_id=927598798019108894&permissions=2147863616&scope=bot%20applications.commands)
- [TindCord](https://discord.com/api/oauth2/authorize?client_id=935185892719603713&permissions=137439332416&scope=bot%20applications.commands)
- [Crypto Helper](https://discord.com/api/oauth2/authorize?client_id=747050613656911892&permissions=0&scope=applications.commands%20bot)
- your bot? [Join our discord server](https://discord.gg/ZVERh35) and let us know!
