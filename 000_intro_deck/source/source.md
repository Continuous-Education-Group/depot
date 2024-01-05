---
created: 2023_01_04
updated: 
author: timOTdev
tags: 
theme: blood
---
## Introduction Deck

Version: 2023/1/4

---

### Table of Contents

1. About Continuous Education Group (CEG)
2. The 3 Steps: Topics > Decks > Minutes
3. Our Repository
4. Tools: Obsidian, VS Code, Github Pages
5. Viewing Decks
6. Building Decks
7. Publishing Decks
8. Review

---

### 1.0 About Continuous Education Group (CEG)

- We do small informal, presentations to grow our engineering knowledge
- Topics range from company features, data patterns, frameworks, or anything tech related
- We try to meet once a week, currently Fridays
- This org is a centralize place to aggregate our collective notes
  
---

### 2.0 The 3 Steps: Topics > Decks > Minutes

- Use the repository as a central hub and look at examples to help
1. Topics - things on agenda we want to cover
2. Decks - slide decks for topics
3. Minutes - meeting agenda to keep us on track

---

### 3.0 Our Repository

- [Depot repository on our org](https://github.com/MH-Continuous-Education/depot)
- Each deck has `source` and `html` folders
- `source` folder has a `source.md` which is the raw slide in markdown format that's viewable in obsidian and all related assets
- `html` folder has export of the html/pdf version is generated using the Advanced Slides plugin in Obsidian
  
![[folder_structure.png|600]]

---

### 4.0 Tools: Obsidian, VS Code, Github Pages

- [Obsidian](https://obsidian.md/) is the open-source markdown editor that we create slides with the plugin called [Advanced Slides](https://mszturc.github.io/obsidian-advanced-slides/)
- [VS Code](https://code.visualstudio.com/) is an easy way to deal with version control and see the raw format like when editing properties
- [Github Pages](https://pages.github.com/) stores, hosts, and provides online versions of our presentations (Neato!)

---

### 5.0 Viewing Decks

- Clone the [repository](https://github.com/MH-Continuous-Education/decks) locally with your terminal or VS code terminal
- Open Obsidian, then Open Folder as Vault
- Open the left hand menu and go to `source.md` to view the raw deck
- Click on Show Slide Preview to run the deck in presentation mode
  
![[folder_as_vault.png|600]]

--

### 5.1 Viewing Options

- Edit your plugin option for some of these additional viewing options

![[plugin_options.png|600]]

--
### 5.2 Deck overview, Slide Numbers, Controls

- Eagle eye's view of slides

![[deck_overview.png|600]]

--

### 5.3 Notes Canvas

- Draw on your slides to emphasize, persists during presentation but doesn't save to file, use `c` to toggle

![[notes_canvas.png|600]]

--
### 5.4 Chalkboard

- Open window to draw ideas, use `b` to toggle

![[chalkboard.png|600]]

--
### 5.5 Laser Pointer

- Everybody loves lasers, use `q` to toggle

![[laser.png|600]]
  
---

### 6.0 Building decks

- [Advanced Slides](https://mszturc.github.io/obsidian-advanced-slides/) is an amazing way to create slides using just markdown syntax
- There are many customizations and we cover a couple of points here, explore their documentation for more ideas
- Feel free to use `template.md` in the root directory for convenience

--

### 6.1 Guidelines

- Don't use heading 1  (`#`) on slides because it makes the text too large
	- Use `##` for the deck title page
	- Use `###` for individual slide titles
- Create a Table of Contents slide and enumerate the topics being covered
- Copy and paste that to help you make slides quickly
- Keep slide to max of 5 or 6 bullets for sizing and conciseness
- Slide should have most of the info, don't have 1 word cue words as it doesn't help future learners

--

### 6.2 Creating Horizontal Slides aka branches

- Use `---` to create new slides which moves horizontally
- Enumerate the branches as whole digits like `1.0`

![[table_of_contents.png|300]]

--

### 6.3 Creating Vertical Slides aka leaves

- Use `--` to create new vertical slides which gets nested under branches
- Enumerate the leaves as decimals like `1.1`

--

### 6.4 Using Sequential Transitions

- Use `<!-- element class="fragment" data-fragment-index="1" -->` to do slide transition using index as the order they appear
- Here's an example:
- This item shows up 1st. <!-- element class="fragment" data-fragment-index="1" -->
- This item shows up 2nd. <!-- element class="fragment" data-fragment-index="2" -->

--

### 6.5 Adding Images

- Add images in `source/assets` folder
- Use `![[controls.png|800]]` where the filename is selectable from a dropdown and 800 is the size in pixels

---

### 7.0 Publishing decks

- After creating the decks, export as html, push the code to Github
- [Github Pages](https://pages.github.com/) is already installed on our repository 
- It will automagically make your html as an online powerpoint with it's own URL

--

### 7.1 Exporting as HTML

- Click on Show Slide Preview
- Once in the slides, top right there's a `...` to click
- Then go to export as HTML
- You can set the export directory in the option

![[exporting_html.png|400]]

--

### 7.2 Publishing to Github Page

- [Github Pages](https://pages.github.com/) is already installed on our repository and automagically make your html as an online powerpoint with it's own URL
- Add your deck to it's own folder
- Enumerate on the next triple digit number
- Add `https://continuous-education-group.github.io/decks/YOUR_FOLDER_NAME/index.html` to `decks.md` if you've structure your folders correctly
- Make a new commit and and push to the repository

---

### 8.0  Review

- Download the 3 tools: Obsidian, VS Code, Github Pages
- Know how to view, build, and publish decks
- Ready to make your first presentation
  
---

### Bonito Finito

- Questions, comments, requests?