# Your Own Personal AI Chatbot
[![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)   [![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](https://forthebadge.com)
# This repo has been archived
The upstream aitextgen library seems to have been stuck in dependency hell for a long time. I have tried many times to clone this repo myself and get the setup for my bot working again, with different esoteric problems every time, no matter the versions or environment things I tweak. Due to upstream not really seein much attention in the modern era of ChatGPT and much more homogenized, technically-impressive AI, I have decided to archive this repo for the time being. If I ever find a more portable and reproducible way to recapture the funny broken half-coherent AI of old, I promise I will make something new and spread it around. 
## What's This?
Gravital is an AI Discord chatbot based on [aitextgen's](https://github.com/minimaxir/aitextgen) implementation of GPT-2. There is a full, start-to-finish [tutorial](https://github.com/johnnymcmike/Gravital/blob/master/TUTORIAL.md) for setting up and training the bot on your discord server's history, and I have observed it to pick up on my server's inside jokes, say usernames, and generally type a lot like one of us with surprising coherency.

This project is forked from https://github.com/NickBrisebois/DiscordChatAI-GPT2, which used gpt-2-simple, an older implementation of GPT-2 by the same creator. While great, this led to issues, as it was hard to get training working on my own hardware, and generally was lacking some features that I think make a big difference to the believability of the results and the usability of the program.

DiscordChatAI-GPT2 boasts the following features:
- Personalized, intelligent responses that learn from your server's chat history
- Option to have bot randomly respond to some messages without being @'ed first
- Talk to your AI in the command line in "test mode" with no Discord required

And a few more are new to this fork:
- Lightning-fast generation times (in my tests, the GPT-2 124M model averaged 2.58s from mention to response, this was running on an i5-2400, which is a CPU from 2011), more memory-efficiency, and all the other goodies that [aitextgen](https://github.com/minimaxir/aitextgen) brings.
- Context-awareness. Reads the last 9 messages and takes them into account when generating a response.
- Support for GPT-Neo, which can generate longer texts and has other improvements
- Handy dataset-cleaner script for use with [Discord Chat Exporter.](https://github.com/Tyrrrz/DiscordChatExporter)
- Bot says one line of text per message by default, but can also say a random number of lines up to a user-defined `maxlines` limit.
  
## Project Status?
Beta, I guess, but it works. Most of the issues I know about are ones that come from aitextgen's currently beta status, but as those shape up and get fixed so too will everything you need out of Gravital.

## Upcoming Features?
- Re-add Docker support from upstream
- Ability to use emojis
- Support for training the model on your own hardware with one command

Open to suggestions, file an issue if you have an idea.

## Cool! How do I use it?
The [TUTORIAL.md](https://github.com/johnnymcmike/Gravital/blob/master/TUTORIAL.md) file contains all you need.

## Known Issues?
- Training currently doesn't work on Windows at all, and training GPT Neo on Colab in my experience has always resulted in an OOM error.
- Determining the "max length" value for generation currently uses some hacky workarounds, as aitextgen has not yet implemented an option to remove the input text from the output text. This might end up resulting in `IndexError`s, which likely won't crash the bot if that occurs, but will cause some messages to randomly be much shorter (1 or 2 characters) than others.
- Data cleaner script currently does not filter out reaction messages, so occasionally you might see a response that looks like one of those.
- Randomly, for no reason that I can find, bot will repeat verbatim whatever is 9 messages above it. May be a quirk of aitextgen or of my model, but it resolves itself and goes back to normal generation within 1 or 2 messages.
