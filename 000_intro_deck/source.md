---
created: 2023_01_04
updated: 
author: timOTdev
tags:
---
<!-- slide style="font-size: 16pt" -->
# Introduction
## Deck 000

Guide to navigating the org, deck management, and tools

---
<!-- slide style="font-size: 16pt" -->
## Table of Contents

1. About Continuous Education Group (CEG)
2. Topics, Decks, Minutes
3. Our Repository
4. Tools: Obsidian, VS Code, Github Pages
5. Viewing Decks
6. Building Decks
7. Publishing Decks
8. Review

---
<!-- slide style="font-size: 16pt" -->
## 1.0 About Continuous Education Group (CEG)

- We do small informal, presentations to grow our engineering knowledge
- Topics range from features, data patterns, frameworks, or anything tech related
- We try to meet once a week, currently Fridays
- This org is a centralize place to aggregate our collective notes
  
---
<!-- slide style="font-size: 16pt" -->
## 2.0 Topics, Decks, Minutes

- This is the process on how we learn, process, and share
1. Topics - things on agenda we want to cover
2. Decks - slide decks for topics
3. Minutes - meeting agenda to keep us on track

---
<!-- slide style="font-size: 16pt" -->
## 3.0 Our Repository

- Clone our org [depot repository](https://github.com/MH-Continuous-Education/depot)
- _source.md_ is the raw markdown powered by advanced slides file to create decks
	- The _assets_ folder should keep all the files types like images, audios, animations, used in the `source.md`
- _index.html_ is the build output of the source markdown file, deployable to github pages and locally viewable in any browser
	- The build output auto-generated these folders: _css_, _dist_, _plugin_

---
<!-- slide style="font-size: 16pt" -->
## 4.0 Tools: Obsidian, VS Code, Github Pages

- [Obsidian](https://obsidian.md/) is the open-source markdown editor that we create slides with the plugin called [Advanced Slides](https://mszturc.github.io/obsidian-advanced-slides/)
- [VS Code](https://code.visualstudio.com/) is an easy way to deal with version control and see the raw format like when editing properties
- [Github Pages](https://pages.github.com/) stores, hosts, and provides online versions of our presentations
  
---
<!-- slide style="font-size: 16pt" -->
## 5.0 Viewing Decks

- Clone the [repository](https://github.com/MH-Continuous-Education/decks) locally with your terminal or VS code terminal
- Open Obsidian, then Open Folder as Vault
- Open the left hand menu and go to any _source.md_ to view the raw deck
- Click on Show Slide Preview to run the deck in presentation mode (Cmd + Shift + E) or Browser mode (In ... menu)
  
![[work/depot/000_intro_deck/assets/folder_as_vault.png]]

--
<!-- slide style="font-size: 16pt" -->
## 5.1 Plugin Options

- Edit your plugin option for some of these additional viewing options
- Recommend changing setting for Slide Preview Mode to _split workspace_
- Recommend turning on all of the plugins

![[work/depot/000_intro_deck/assets/plugin_options.png|400]]

--
<!-- slide style="font-size: 16pt" -->
## 5.2 Deck overview, Slide Numbers, Controls

- Eagle eye's view of slides and enabled plugin options

![[work/depot/000_intro_deck/assets/deck_overview.png|600]]

--
<!-- slide style="font-size: 16pt" -->
## 5.3 Notes Canvas

- Draw on your slides to emphasize, persists during presentation but doesn't save to file
- Shortcut key: _c_ 

![[work/depot/000_intro_deck/assets/notes_canvas.png|600]]

--
<!-- slide style="font-size: 16pt" -->
## 5.4 Chalkboard

- Open window to draw ideas
- Shortcut key: _b_ 

![[work/depot/000_intro_deck/assets/chalkboard.png|600]]

--
<!-- slide style="font-size: 16pt" -->
## 5.5 Laser Pointer

- Come on, everybody loves lasers
- Shortcut key: _q_ 

![[work/depot/000_intro_deck/assets/laser.png|600]]
  
---
<!-- slide style="font-size: 16pt" -->
## 6.0 Building decks

- [Advanced Slides](https://mszturc.github.io/obsidian-advanced-slides/) is an amazing way to create slides using just markdown syntax
- There are many customizations and we cover a couple of points here, explore their documentation for more ideas
- Feel free to use _template.md_ in the root directory for convenience

--
<!-- slide style="font-size: 16pt" -->
## 6.1 Guidelines

- Recommend adding `<!-- slide style="font-size: 16pt" -->` on each slide to fit all the text
- Create a Table of Contents slide and enumerate the topics being covered
- Copy and paste that to help you make slides quickly
- Slide should have most of the info, Please don't just use 1-word cues as it doesn't help future learners
- Always review your presentation in browser view because that's how github pages will display it, make sure images fit!
- 1st reminder: update the image path to the _assets_ folder after export the html build

--
<!-- slide style="font-size: 16pt" -->
## 6.2 Creating Horizontal Slides

- We call them **branches**
- Use `---` to create new slides which moves horizontally
- Enumerate the branches as whole digits like _1.0_

![[work/depot/000_intro_deck/assets/table_of_contents.png|300]]

--
<!-- slide style="font-size: 16pt" -->
## 6.3 Creating Vertical Slides aka leaves

- Use `--` to create new vertical slides which gets nested under branches
- Enumerate the leaves as decimals like _1.1_

--
<!-- slide style="font-size: 16pt" -->
## 6.4 Using Sequential Transitions

- Use `<!-- element class="fragment" data-fragment-index="1" -->` to do slide transition using index as the order they appear
- Here's an example:
	- This item shows up 1st. <!-- element class="fragment" data-fragment-index="1" -->
	- This item shows up 2nd. <!-- element class="fragment" data-fragment-index="2" -->

--
<!-- slide style="font-size: 16pt" -->
## 6.5 Adding Images

- Add images in _YOUR_DECK_NAME/assets_ folder
- This is for use in the source markdown file and also the html build output
	- 2nd reminder: update the image path to the _assets_ folder after exporting the html
- Use `![[FILE_NAME]]` syntax where the filename is selectable from a dropdown
- Append `|600` after the file name to change the image size easily

---
<!-- slide style="font-size: 16pt" -->
## 7.0 Publishing decks

- After creating the decks, export as html, push the code to Github
	- I have my export directory for the settings as _/export_
- [Github Pages](https://pages.github.com/) is already installed on our repository
	- It will automagically make your html as an online powerpoint with it's own URL
- Known bug: after exporting the html, the source markdown gets wonky and doesn't show images on the deck preview mode
	- It will still show if you run the browser preview or exporting the html

--
<!-- slide style="font-size: 16pt" -->
## 7.1 Exporting as HTML

- Click on Show Slide Preview
- Once in the slides, top right there's a _..._ menu to click
- Then go to export as HTML
- You can set the export directory in the option

![[exporting_html.png|400]]

--
<!-- slide style="font-size: 16pt" -->
## 7.2 Duplicated Assets

- There's an extra assets folder that we don't want: _work_
- **ONLY** copy _css_, _dist_, _index.html_, and _plugin_

![[duplicated_assets.png|500]]

--
<!-- slide style="font-size: 16pt" -->
## 7.3 Publishing to Github Page

- [Github Pages](https://pages.github.com/) is already installed on our repository and automagically make your html as an online powerpoint with it's own URL
- Add your deck to it's own folder
- Enumerate on next number of the latest foder
- Add `https://continuous-education-group.github.io/depot/YOUR_DECK_NAME/index.html` to _decks.md_ if you've structure your folders correctly
- Make a new commit and and push to the repository
- Add your deck to present in _minutes.md_

---
<!-- slide style="font-size: 16pt" -->
## 8.0  Review

- Download the 3 tools: Obsidian, VS Code, Github Pages
- Know how to view, build, and publish decks
- Ready to make your first presentation
  
---
<!-- slide style="font-size: 16pt" -->
## Bonito Finito

- Questions, comments, requests?
