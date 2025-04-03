# Personal Journal Template
This is a template you can use as a journal. It supports *daily journals*, *dream journals* & *habit tracking* and even has a cook book integrated!

The [[Tracker]] can be used as a "start page" to your journal, where you can keep an overview over your most important goals and habits. Seeing them every time you open the vault can really help you keep focus on your important goals.

Read more about using it below, and enjoy!

## How to use it
Basic usage is very simple: Write different notes in the directory `Journal/` for each day, track your habits and link people you spent the day with. Enjoy some statistics in the *[[Tracker]]* and *Graph-View*.

For details see the following chapters:
1. [[README#Setup|Setup]]
2. [[README#Writing a Journal Entry|Writing a Journal Entry]]
3. [[README#Linking People or Notes|Linking People or Notes]]
4. [[README#Statistics|Statistics]]
5. [[README#Connection Graph|Connections Graph]]

#### Setup
1. First, install Obsidian (on your computer or phone).
2. Download this template.
3. Open the downloaded folder in Obsidian.
4. Enable community plugins in `Settings > Community Plugins`.
5. If this didn't happen automatically, install the *Dataview* and *Obsidian Charts* Plugin in the settings. You can optionally also install a theme in `Settings > Apperance` (I recommend *Material Gruvbox* or *Pink Topaz*)
6. Done :)

#### Writing a Journal Entry
1. Create a new Journal Note. I usually copy & paste the last day :)
2. Fill out the statistics on top. If you want to change the shown statistics, see the chapter [[README#Statistics|Statistics]]. The daily rating should be between 0 and 100.
   I personally set a "normal day" as 60, fluctuating between 50 and 70. Anything below or above is a special occasion for me to be very happy/excited or very sad/depressed.
3. Optionally take some personal notes for the day below.
4. Link people when mentioning them (see chapter [[README#Linking People or Notes|Linking People or Notes]]). This creates a nice graph linking all people to all days you spent with them, or thinking about them (see chapter [[README#Connection Graph|Connections Graph]])

#### Linking People or Notes
To link files in Obsidian, you can use double-square-brackets like so: `[[file]]`. You can use this to mention people in a journal entry.

If a person doesn't exist yet in the `People in my life/` directory, create a note for them. Then you can link them like this:
Today my [[Dad]] went to get some milk at the gas station.

**Advanced:** You can add a display-text in the brackets behind a vertical bar like so: `[[file|text]]` (results in a link like this: [[README|text]]).
I personally use this the following way: I name notes about people with their full name (e.g. Max Muster), but while writing I type `[[Max Muster|Max]]`, resulting in the following:
Today I talked with [[Max Muster|Max]].

#### Statistics
In the [[Tracker]] you can find some nice graphs that display some information that you are tracking in your journal entries. If you are using the default categories, fine. If you want to add some of your own categories, then it gets a little more complicated :)
If you know me personally, I can of course set it up for you. If not, then here is the guide:

TODO

#### Connections Graph
If you want to see a visual representation of the connections between your friends and your days, then just click on "graph" in Obsidian.
If you consistently link people and days you get a nice self-structuring graph where
1. you can see how much time you spend with someone, as more and more days hover around them
2. all your friend groups tend to stick together as you spend time with them on the same days
3. etc.

## Structure
There are different sections in this journal project. Here  and this should be a quick guide, what can be found where:
- [[Tracker]]: The "Front Page" of my personal repository
- [[README - Dreams|Dreams]]: My dream diaries
- [[README - Notes|Ideas]]: Any random or planned ideas coming to my mind
- [[README - Journal|Journals]]: Journal Entries, just open your daily notes here, using the template.
- [[README - Lists|Lists]]: Any kind of list, like *best-of*s, or recipes
- [[README - People|People in my life]]: The people I met in my life
- All images and external content is stored in [[README - src|src]], templates in Templates

## Obsidian
[Obsidian](https://obsidian.md/) is the markdown editor that I use to be able to easily visualize, link and structure my Markdown files in this repository. Some views can't render without this program and its plugins (see .obsidian for list of used plugins).