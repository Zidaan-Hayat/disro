# [dis](https://discord.com)[ro](https://roblox.com)

Discord -> Roblox moderation system.

This system **at the moment** is only able to execute moderation actions from discord to a roblox game.


Much bigger implementations are planned including:
- Updating the codebase with more commands for utility usage (Like checking server data, server fps, server uptime, etc.)
- Cleaning up of the entire codebase cause it is very messy 💀
- Sorting the roblox-client side code allowing scripters to easily implement additional systems

---

## Installation


### Step 1.

```sh
# Clone this project
git clone https://github.com/Zidaan-Hayat/disro.git

# Go into the directory
cd disro

# Install the required dependencies (from the package.json)
npm install
```

### Step 2.

Edit the `config.json` file.
```json
{
	"botToken": "The bot token given from your application",
	"botPrefix": "The prefix all your bot commands will use",
	"ownerIds": [
		"A list of all the bot owner discord IDs (As strings [wrapped in quotes] not integers!)"
    ],
    "serverApiKey": "The API key for your server to communicate with the roblox client, can be any random generated string",
	"moderationRoleId": "The role ID that is required to run game moderation commands, if it's an empty string only game owners will be able to use commands"
}
```

### Step 3.

Copy all files in the `roblox` folder, into a location in your `ServerScriptService`

The only thing you need to make sure is that the files share the same Parent (Folder, etc.)

---

## Commands

`<>` Indicates a required argument

`[]` Indicates an optional argument

### `findplayer <username>`

Find the server a player is currently in (if they're in any)

### `gameservers [server ID]`

With server ID: Get a list of all the players in the server
Without server ID: Get a list of all the current game servers

### `gamekick <username> <reason>`

Kick a player from the server they're currently in

### `gameban <username> <reason>`

Ban a player from the game entirely and if they're in a server, kick them

### `gameunban <username>`

Unban a player from the entire game

---

## FAQs

### Why did you implement [rbxwebhook.js](https://www.npmjs.com/package/rbxwebhook.js) in your code instead of installing the dependency?

The dependency manages client connections by assigning a random UUID, for this system to be a little easier to use, I assign each connection the ID of the server it's connected to. I'm yet to make a pull request for this to the dependency.

### How are bans currently handled?

A datastore named "bans" is created and entries are written directly into that datastore with the entry keys being the target user ID and the value being the ban reason

The module to handle all this is in `roblox/banStore`

### How do I implement my own ban handling/storage system?

Go to `roblox/modFunctions` and you can adjust/re-do the "handle" prefixed functions as you wish, given the arguments they receive

---

## Dependencies

This project is nothing without the blood, sweat and tears of other dependencies. The listed projects severely assisted the creation of this system and are depended on within the code someway or another.

Their code repositories are listed below:

- [Axios](https://www.npmjs.com/package/axios)
- [Discord.js-commando](https://www.npmjs.com/package/discord.js-commando)
- [Express](npmjs.com/package/express)
- [rbxwebhook.js](https://www.npmjs.com/package/rbxwebhook.js) (Custom implementation was made but the essence of the discord -> robox communication is directly from this project)

## Suggestions

I do not have a discord server for this since it's a very weeny project, so if you have any suggestions please slap me a friend request on Discord (Zz#7940) and you can talk to me directly from there :D