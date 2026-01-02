[index.js](https://github.com/user-attachments/files/24412916/index.js)
const { Client, GatewayIntentBits, EmbedBuilder } = require("discord.js");

// Create the client
const client = new Client({
  intents: [
    GatewayIntentBits.Guilds,
    GatewayIntentBits.GuildMembers,
    GatewayIntentBits.GuildMessages
  ]
});

// When the bot is ready
client.once("ready", () => {
  console.log(`Logged in as ${client.user.tag}`);
});

// Welcome message
client.on("guildMemberAdd", member => {
  const channel = member.guild.channels.cache.find(ch => ch.name === "welcome");
  if (!channel) return;

  const welcomeEmbed = new EmbedBuilder()
    .setColor("Pink")
    .setThumbnail(member.user.displayAvatarURL())
    .setDescription(`
-♡´-. ݁₊ ⊹ . ݁˖ . ݁
𝐖𝐞𝐥𝐜𝐨𝐦𝐞 ${member} !
𝐖𝐞 𝐡𝐨𝐩𝐞 𝐲𝐨𝐮 𝐞𝐧𝐣𝐨𝐲 𝐲𝐨𝐮𝐫 𝐬𝐭𝐚𝐲.

𝐌𝐚𝐤𝐞 𝐬𝐮𝐫𝐞 𝐭𝐨 𝐫𝐞𝐚𝐝 𝐨𝐮𝐫 𝐫𝐮𝐥𝐞𝐬 𝐚𝐧𝐝 𝐠𝐫𝐚𝐛 𝐬𝐨𝐦𝐞 𝐫𝐨𝐥𝐞𝐬 𝐢𝐧 
<#1443361197444431913> 𝐚𝐧𝐝 <#1443361391988838430>

˗ˏˋ-꒰-♡-꒱-ˎˊ˗
. ݁₊ ⊹ . ݁˖ . ݁-♡´-
    `);

  channel.send({ embeds: [welcomeEmbed] });
});

// Login
client.login(process.env.TOKEN);
[package.json](https://github.com/user-attachments/files/24412918/package.json)
{
  "name": "discord-bot",
  "version": "1.0.0",
  "description": "A simple Discord bot",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "discord.js": "^14.14.1",
    "dotenv": "^16.4.5"
  }
}

