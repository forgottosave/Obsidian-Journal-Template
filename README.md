# Personal Journal Template

<img src="https://github.com/user-attachments/assets/79db9aa5-e47f-437d-bf8c-1298b0d97df6" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="300" height="220" />
<img src="https://github.com/user-attachments/assets/992ff3b5-7606-4893-b86f-c236391a0106" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="300" height="220" />

<img src="https://github.com/user-attachments/assets/d72c2c33-f316-4bce-b286-e0bb82179219" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="370" height="220" />
<img src="https://github.com/user-attachments/assets/06a78793-90bb-4286-897c-7efdcfe51625" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="230" height="220" />

This is a template obsidian vault you can use as a daily journal. It supports *daily journals*, *habit tracking* and some cool *graphs*.

## How to use it
Basic usage is very simple: Write different daily notes using the pre-defined template, track your habits and link people you spent the day with. Enjoy some statistics in the *[Tracker](Tracker)* and *Graph-View*.

For details see the following chapters:
1. [Setup](#setup)
2. [Writing a Journal Entry](#writing-a-journal-entry)
3. [Linking People or Notes](#linking-people-or-notes)
4. [Statistics](#statistics)
5. [Connections Graph](#connections-graph)

#### Setup
1. First, install **Obsidian** (on your computer or phone).
2. Download this **template**.
3. **Open** the downloaded folder in Obsidian. It will ask you if you trust this project -> click yes.

The next steps might already be set automatically, but double check it and, if necessary, execute these steps:
4. Enable **community plugins** in `Settings > Community Plugins`.
5. Install the *Dataview* and *Obsidian Charts* Plugin under `Settings > Community Plugins > Browse`. You can optionally also install a theme in `Settings > Apperance` (I recommend *Material Gruvbox* or *Pink Topaz*)

#### Writing a Journal Entry
1. When opening obsidian, you should already be presented with **today's note**.
   If not, or you never close obsidian, just create one by pressing the *Open today's daily note* button.
   <img src="https://github.com/user-attachments/assets/33009e29-80d3-4929-8b06-b3ac67b18a5b" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="300" height="220" />

   On mobile select the 3 vertical bars on the bottom right, then the same button.

3. Fill out the statistics on top. If you want to change the shown statistics, see the chapter [Statistics](#statistics). The defaults are:
    - a **daily rating** (between 0 and 100).
    - how many hours of **sleep** you got
    - how many hours you were **productive**
    - how many hours you engaged in **sports** activities
4. Optionally take some personal notes for the day right below the statistics.
5. Link people when mentioning them (see chapter [Linking People or Notes](#linking-people-or-notes)). This creates a nice graph linking all people to all days you spent with them, or thinking about them (see chapter [Connections Graph](#connection-graph))

#### Linking People or Notes
To link files in Obsidian, you can use double-square-brackets like so: `[[file]]`. You can use this to mention people in a journal entry.

If a person doesn't exist yet in the `People in my life/` directory, create a note for them. Then you can link them like this:
Today my [[Dad]] went to get some milk at the gas station.

**Advanced:** You can add a display-text in the brackets behind a vertical bar like so: `[[file|text]]` (results in a link like this: [[README|text]]).

I personally use this the following way:
I name notes about people with their full name (e.g. Max Muster), but while writing I type `[[Max Muster|Max]]`, resulting in the following:
Today I talked with [[Max Muster|Max]].

#### Statistics
In the [[Tracker]] you can find some nice graphs that display some information that you are tracking in your journal entries.

If you are using the default categories, fine. If you want to add some of your own categories, or change the displayed information, then it gets a little more complicated :)
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
- [[README - Ideas|Ideas]]: Any random or planned ideas coming to my mind
- [[README - Journal|Journals]]: Journal Entries, just open your daily notes here, using the template.
- [[README - People|People in my life]]: The people I met in my life
- All images, external content and templates are stored in [[README - src|_src_]], templates in Templates

## Obsidian
[Obsidian](https://obsidian.md/) is the markdown editor that I use to be able to easily visualize, link and structure my Markdown files in this repository. Some views can't render without this program and its plugins (see .obsidian for list of used plugins).
