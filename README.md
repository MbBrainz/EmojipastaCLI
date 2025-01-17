# Emoji Pasta CLI
[![PyPI version](https://badge.fury.io/py/emojipasta-cli.svg)](https://badge.fury.io/py/emojipasta-cli)

## Description
A cli tool that turns your text into emojipasta. 
example: `its getting hot in here` -> `it's getting hot 🔥😍 in 🔽👏 here 💪👏`

after installation, you can use the cli tool by typing `emojipasta` in your terminal. 

<!-- you can add this alias to your `.bashrc` or `.zshrc` file to make your git commits more spicy: -->



### Installation
`pip install emojipastabot`

### Usage
```
emojipasta "it's getting hot in here"
>>> it's getting hot 🔥😍 in 🔽👏 here 💪👏
```

or add the `-c` flag to use it as a git commit message hook:
```
emojipasta -c "new commit feature"
[[CURRENT_BRANCH] [COMMIT_HASH]] new 🗞👆 commit feature
```
*The original Readme should still make sense mostly, except for some directory changes:*
## Description
[u/AnEmojipastaBot](https://www.reddit.com/user/anemojipastabot) (now suspended from reddit) turns the parent
of your comment into emojipasta. It can be summoned by mentioning it.

Example:

```
redditor 1: hello world
  redditor 2: u/AnEmojipastaBot
    AnEmojipastaBot: hello world 🌍
```

It was built by scraping thousands of comments from r/emojipasta
and using them to form mappings from word->emoji. The bot itself,
and the scraping tool, are based on the PRAW framework, and the
'emoji' Python package was used to identify emojis in the r/emojipasta
comments.

There are no hard-coded credentials or user details in the code, so
everyone is free to run their own version of the bot.

## Installation
Clone the repository, run setup.py to install dependencies, add it to your Python path somehow.

## How to use...

#### The bot

```
python ./src/emojipasta/bot.py <client_id> <client_secret> <user_agent> <username> <password>
```

If you don't have credentials or a reddit user, then follow the setup
instructions in the [PRAW docs](http://praw.readthedocs.io/en/latest/getting_started/quick_start.html).

#### The scraper
The scraper saves comments to a hard-coded location, you may want
to modify it.
```
python ./src/emojipasta/scraping/reddit_scraping.py <client_id> <client_secret> <user_agent> <username> <password>
```

#### The emojipasta generator
```python
from emojipasta.generator import EmojipastaGenerator
generator = EmojipastaGenerator.of_default_mappings()
generator.generate_emojipasta("it's getting hot in here")
```
Output:
```
it's getting hot 🔥😍 in 🔽👏 here 💪👏
```

If you want to create an EmojipastaGenerator with custom emoji
mappings (a dict that maps from a lowercase word to a list
of emojis):
```python
from emojipasta.generator import EmojipastaGenerator
EmojipastaGenerator.of_custom_mappings({"hello": ["👋", "👈"]})
``` 
