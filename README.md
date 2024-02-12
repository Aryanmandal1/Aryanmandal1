/*------------------------------------------------------------------------------------------------------------------------------------------------------
Copyright (C) 2023 Loki - Xer.
Licensed under the  GPL-3.0 License;
you may not use this file except in compliance with the License.
Jarvis - Loki-Xer 
------------------------------------------------------------------------------------------------------------------------------------------------------*/

const { System, getBuffer, toAudio, } = require("../lib/");

const logo = 'https://i.imgur.com/42JWHXp.jpeg';
var audios = ["https://i.imgur.com/yYO6W4q.mp4", "https://i.imgur.com/BrMw2T1.mp4","https://i.imgur.com/wZ3DNfp.mp4","https://i.imgur.com/ijWcyO5.mp4","https://i.imgur.com/c7VZSbx.mp4","https://i.imgur.com/6eMLKnZ.mp4","https://i.imgur.com/gGEJgdi.mp4"];

System({ pattern: "mention", on: "all", allowBot: true, fromMe: 'public', desc: "mention audio", }, async (message, match) => {

const audio = audios[Math.floor(Math.random() * audios.length)]
		const Audio = await getBuffer(audio)
		const image2 = await getBuffer(logo)
		try {
		var res = await toAudio(Audio, 'mp4')
		} catch (b) {
		return await message.client.sendMessage(message.client.user.id, {
		text: `Error on parsing audio \n ${b}\n\n${audio}\n\ndelete this url from audio list`
			})
		}

if(!message.mention.isOwner) return;
try {
return await message.client.sendMessage(message.jid, {
         audio: res,
	 mimetype: 'audio/mpeg',
	 ptt: true,
	 waveform: [00,99,00,99,00,99,00],
         contextInfo: {
            externalAdReply: {
               title: "ᎧᎮ ᭄ ★Aʀʏᴀɴ ★࿐ ⚡",
               body: "🎀you are my happiness ankana🌸🍃",
	       renderLargerThumbnail: false, // use true for larger thumbnail
               thumbnail: image2,
               mediaType: 1,
               mediaUrl: 'hhtps://www.instagram.com/i_aam_adi07',
               sourceUrl: "https://wa.me/+917318812338?text=_𝐇𝐞𝐥𝐥𝐨+Aryan+𝐬𝐢𝐫+✌🏻_",
               showAdAttribution: true,
                   }
         }, 
      }, { quoted:message });
} catch (e) {
return await message.send(e);
}
});


// mention audio for Jarvis-md
// credit : @Loki-Xer
// Thanks to @inrl-official 
