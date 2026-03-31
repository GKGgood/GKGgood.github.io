# JOSHwho Vocabulary

A personal English vocabulary notebook built with Jekyll and hosted on GitHub Pages.

Live site: https://gkggood.github.io/

## About

This project is a lightweight English notebook website for recording:

- words
- phrases
- Chinese meanings
- English definitions
- pronunciation
- example sentences
- personal notes

The site is split into two sections:

- `Words`
- `Phrases`

Each entry has its own detail page, and the list pages are designed for quick browsing.

## Project Structure

```text
.
├─ _words/                 # word entries
├─ _phrases/               # phrase entries
├─ words.md                # words list page
├─ phrases.md              # phrases list page
├─ _layouts/               # custom layouts
├─ assets/css/site.css     # custom styles
├─ _config.yml             # Jekyll configuration
└─ README.md
```

## Features

- Separate pages for words and phrases
- Numbered list view for fast scanning
- Clickable entry titles that open detail pages
- Meanings visible directly in list pages
- Detail pages with:
  - Chinese meaning
  - English definition
  - pronunciation
  - examples
  - notes
- Built-in pronunciation button using browser speech synthesis
- Published with GitHub Pages
- Count the total views and mark the last update time


## Adding A New Word

Create a new Markdown file under `_words/`.

Example:

```text
_words/banana.md
```

Recommended naming rules:

- use lowercase letters
- use hyphens when needed
- avoid spaces
- keep the file name close to the entry itself

Example:

```md
---
title: banana
meaning: 香蕉
definition: A long curved fruit with a yellow skin and soft sweet flesh.
phonetic: /bəˈnæn.ə/
part_of_speech: noun
examples:
  - I ate a banana after lunch.
  - Bananas are rich in potassium.
---

A very common everyday word. Useful for food-related topics and beginner vocabulary.
```

After saving the file, Jekyll will automatically:

- add it to `/words/`
- generate a detail page at `/words/banana/`

## Adding A New Phrase

Create a new Markdown file under `_phrases/`.

Example:

```text
_phrases/on-the-other-hand.md
```

Example:

```md
---
title: on the other hand
meaning: 另一方面
definition: Used to introduce a different point of view or a contrasting idea.
phonetic:
part_of_speech: phrase
examples:
  - This plan is cheap. On the other hand, it may take more time.
  - She is strict, but on the other hand she is very fair.
---

Useful in writing and discussion when you want to compare two sides.
```

After saving the file, Jekyll will automatically:

- add it to `/phrases/`
- generate a detail page at `/phrases/on-the-other-hand/`

Note:

- phrase list pages currently do not show pronunciation
- you can still keep the `phonetic` field for future use if needed

## Entry Format

### Required fields

- `title`
- `meaning`
- `definition`

### Common fields

- `phonetic`
- `part_of_speech`
- `examples`

### Notes body

Any content written below the front matter becomes the note section on the detail page.

## Templates

```md
---
title:
meaning:
definition:
phonetic:
part_of_speech:
examples:
  - 
  - 
---

Write your notes here.
```

## Local Development

Install dependencies:

```bash
bundle install
```

Start the local server:

```bash
bundle exec jekyll serve
```

Then open:

```text
http://127.0.0.1:4000
```

## Update And Publish

This project is managed with GitHub.

Repository:

```text
https://github.com/GKGgood/GKGgood.github.io
```

Typical workflow:

```bash
git add .
git commit -m "Add new vocabulary entries"
git push
```

After pushing, GitHub Pages redeploys the site automatically.

## Use On Another Computer

Clone the repository:

```bash
git clone https://github.com/GKGgood/GKGgood.github.io.git
cd GKGgood.github.io
bundle install
bundle exec jekyll serve
```

Then continue editing entries normally.

## Notes

- If you change `_config.yml`, restart the Jekyll server
- Keep one file per word or phrase
- Use simple lowercase file names
- Save Markdown files as UTF-8 to keep Chinese text and phonetic symbols readable
- Commit often to keep your notebook history clear
