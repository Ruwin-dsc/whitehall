# Voici un petit guide pour l'utilisation des module
## blackjack

> Ce repo est un fork de ["3061LRTAGSPKJMORMRT"](https://github.com/3061LRTAGSPKJMORMRT) pour le blackjack. La différence est que celui là est disponible en discord.js v14 et j'ai ajouté un troisième fieldd

Exemple d'utilisation:
```js
const Discord = require("discord.js");
const blackjack = require('whitehall')

exports.help = {
  name: "blackjack",
  category: "jeux", 
  aliases: ["bj"],
  description: "Lance un blackjack",
  usage: "blackjack <amount>"
};

exports.run = async (bot, message, args, color) => {



    let embed = {
            title: "BlackJack 🎲",
            fields: [
                { name: `Votre main`, value: "", inline: true },
                { name: `‎`, value: "‎", inline: true },
                { name: `Main de ${bot.user.username}`, value: "", inline: true }
            ],
            footer: { text: `${message.author.username}, si vous abandonnez la partie, seulement 50% de vos coins vous seront remboursés !`}
        }
  
        const game = await blackjack(message, {resultEmbed: false, normalEmbed: false, normalEmbedContent: embed});


        switch (game.result)
        {
            case 'WIN': {
                message.reply('Vous avez gagné !')
            }

            case 'LOSE': {
                message.reply('vous avez perdu !')
            }
        };
}
```