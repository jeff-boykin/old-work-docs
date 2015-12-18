# Presentations

Hey there! Welcome to General Assembly Presentations. Using this application is easy. Use your right arrow key to move to the next slide.

---

## GitHub Gist

This site is powered on [GitHub Gists](https://gist.github.com). In order to make a new presentation, you'll need to create a new Gist with a few simple rules.

---

## Naming the file

While the name of the file doesn't matter, the type does. Create a new gist and under "Name this file..." choose anything you think makes sense, followed by `.md`.

![how-to-use-gists](https://i.imgur.com/9x1ITwr.png)

---

## Creating Slides

Slides are written in a format called [Markdown](https://help.github.com/articles/github-flavored-markdown/). It's a very simple way to write documents that will eventually be turned into HTML.

A typical markdown presentation may look like the following:

```
# Welcome

---

### Class 1

Introduction to Classes & Objects

![wooo](https://i.imgur.com/LS5z58g.gif)
```

Where `---` denotes a new slide.

---

## Displaying Your Presentation

To display your presentation, click "Update Gist", and then simply take the id of the presentation out of the URL:

For example with:

`https://gist.github.com/bswinnerton/b7c282fae7217918a935`

You would take:

`b7c282fae7217918a935`

And insert it into the URL of this application:

`https://presentations.generalassemb.ly/b7c282fae7217918a935`

---

## And Voilà!

![screenshot](https://i.imgur.com/D94GCb4.gif)

---

## Making Changes

Presentations are cached forever, unless you specifically ask for them to be updated. To update a presentation, update the gist and then add `/reload` to the end of your URL. For example:

`https://presentations.generalassemb.ly/b7c282fae7217918a935#/7`

Would become:

`https://presentations.generalassemb.ly/b7c282fae7217918a935/reload#/7`

(notice `/reload` comes before the `#`)

---

## Configuration

You can optionally create another file (using "Add file"), named `config.yml` which can take the following settings:

```yaml
title: Classes & Objects
homepage: http://lessons.generalassemb.ly
authenticate: true
```

Where:

- `title` changes the value inside the `<title>` tags of the HTML document
- `homepage`, changes the page that the logo returns to
- `authenticate`, will prompt the user to sign in with a GA account first

---

If you have any questions, feel free to reach out to [brooks@ga.co](mailto:brooks@ga.co)

To see how this presentation was made, check out [https://gist.github.com/bswinnerton/b7c282fae7217918a935](https://gist.github.com/bswinnerton/b7c282fae7217918a935).
