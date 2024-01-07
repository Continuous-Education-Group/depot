# Minutes

[home](work/depot/README.md) - [topics](topics.md) - [decks](decks.md)

---

## 2023_01_03_friday

- Topics:
  - Obsidian, deck 000 ([[work/depot/000_intro_deck/source|source]])
  - Golang

### Obsidian Q&A

- Can viewers draw on slides live?
  - Doesn't look like it and we probably don't need it, but we'll look into it
- Can/should we attach detailed notes to a presentation?
  - We can and should write presentation notes that are attached to slides. We can also provide external links

### Golang Q&A

- Golang doesn't have concept of `undefined` or `null` like javascript, what is the type of a declared, uninitialized variable?
  - Short answer is it depends on the type but GoLang doesn't have this idea of uninitialized types
  - Follows principle of zero values so for examples: numbers default to `0`, strings defaults to `""`, and booleans defaults to `false`
  - Pointer and interface types are 2 examples that defaults to `nil`

### TODO items

- [ ] Try to figure out how to display images in GitHub
- [ ] Try to figure out why text is overflowing on some slides
- [ ] Convert Google Slides presentation to Obsidian slide deck
