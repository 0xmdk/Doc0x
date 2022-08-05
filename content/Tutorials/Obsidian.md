Obsidian.md is a [markdown](https://www.markdownguide.org/getting-started/) text editor. It is different from other markdown editors because it has jumped on the _linked thought_ band wagon. “Linked Thought” refers to a group of note taking applications that allow you to seamlessly link thoughts and notes together. It is like having your very own wikipedia. The applications go much further than note taking. Applications like [Obsidian.md](https://obsidian.md/) and [Roam Research](https://roamresearch.com/) are spearheading a [knowledge management](https://en.wikipedia.org/wiki/Knowledge_management#:~:text=Knowledge%20management%20(KM)%20is%20the,the%20best%20use%20of%20knowledge.&text=KM%20is%20an%20enabler%20of%20organizational%20learning.) revolution. People have used it to write academic papers and novels. People also use it to support their own work: everyone from software developers to lawyers are seeing the value in the idea of _linked thought_.

If you are unfamiliar with markdown it can be tricky to get started with obsidian. This article is meant to be a quick reference guide on the basics of Obsidian and the Markdown specific to obsidian. It is aimed at beginners and people who are unfamiliar with markdown.

Most Obsidian Tutorials start with how to link pages together, this doesn’t make any sense. While this is one of the big selling points of Obsidian it can be a confusing topic for someone that is just starting out. My approach will be to explain obsidian as a text editing tool, and then we’ll add “linked thought” at a later stage as the icing on the cake. You can use the contents menu to jump to a section you want to read more about.

Here is a walkthrough of [my Obsidian.md personal knowledge management system](https://rossgriffin.com/tru/).

## Basic Text formatting

Like Microsoft Word or Apple pages Obsidian allows you to perform some basic text editing like making text: Bold, Italic, Strike Through and highlighted.

This is some bold text:

```markup
**This is some bold text**
```

Copy

_This is italicized text:_

```markup
*This is italicized text*
```

Copy

~~This text has a strikethrough:~~

```markup
~~This text has a strike through~~
```

Copy

This is highlighted

```javascript
==This is highlighted==
```

Copy

Block quotes are a good way of indicating that you’re quoting someone, or to call attention to specific text:

![](https://i0.wp.com/rossgriffin.com/wp-content/uploads/2021/08/Block-Quote.jpg?w=800&ssl=1)

```markup
> Block Quote
```

Copy

[YouTube Explanation](https://www.youtube.com/watch?v=59lB4CgF7uY)

## Headings and Horizontal Rules

In Obsidian you can add headings:

![](https://i0.wp.com/rossgriffin.com/wp-content/uploads/2021/08/Headings-Example.jpg?w=800&ssl=1)

```markup
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

Copy

Another helpful text editing tool is the horizontal rule:

---

Use 3 dashes for a horizontal rule: 

```markup
---
```

Copy

One more note on headings and horizontal rules: you can put 3 dashes underneath text to make it a heading like this:

```markup
some text
---
```

Copy

The code above will display as a Heading 1 in Obsidian.md

[YouTube Explanation](https://youtu.be/VdyE72fZU_8)

## How to add an Underline In Obsidian

Obsidian.md doesn’t come with an underline feature built in. However you can install the [Obsidian Underline](https://github.com/Benature/obsidian-underline) plugin from the community plugins dialogue of your Obsidian.md application. This plugin adds the **Ctrl + U** shortcut and inserts the HTML markup (not markdown) for an underline. The result is an underline. Unfortunately it looks messy in raw markdown, but it’s currently the fastest and best way that I know of to add an underline to an Obsidian.md markdown document.

```markup
<u>This is some underlined text</u>
```

Copy

## Lists and Checklists

In Obsidian you can create ordered lists, unordered lists and check lists:

### Ordered list

1.  This
2.  is an
3.  Ordered list

The Markdown:

```markup
1. This
2. is an
3. Ordered list
```

Copy

### Unordered List

-   This
-   is an
-   unordered list

**The Markdown:**

```markup
- This
- is an
- unordered list
```

Copy

### Checklist

-   ![☑️](https://s.w.org/images/core/emoji/14.0.0/svg/2611.svg)This
-   ![☑️](https://s.w.org/images/core/emoji/14.0.0/svg/2611.svg)is a
-   ![☑️](https://s.w.org/images/core/emoji/14.0.0/svg/2611.svg)checklist

**The Markdown:**

```markup
- [ ] This
- [ ] is a
- [ ] checklist
```

Copy

[YouTube Explanation](https://youtu.be/qRcVGfsgOC8)

### Obsidian Cheat Sheet

Download

## Code Blocks

Code blocks are useful for two reasons: one, the code is not compiled in your editor. Two, the code will in most cases have proper syntax highlighting.

![](https://i0.wp.com/rossgriffin.com/wp-content/uploads/2021/08/HTML-example.jpg?w=800&ssl=1)

To insert a code block use the “` followed by the programming language you want to use. For example:

The Markdown:

````markup
```html
some code here
```
````

Copy

[YouTube Explanation](https://youtu.be/VSpjJWv6-ho)

## Tables

Tables are a bit tricky to work with in markdown so I’d recommend downloading the plugin “Advanced Tables” which makes editing tables a more pleasant experience.

Obsidian allows you to insert tables into text:

Heading

Description

Header

Title

Paragraph

Text

The Markdown:

```markup
| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
```

Copy

[YouTube Explanation](https://youtu.be/m81Q0tqM4ps)

## Footnotes

Footnotes are great if you want to add something to your notes without breaking the flow of your writing. 

Tip: I’d highly recommend the plugin: “Footnote Shortcut” if you are going to be using footnotes on a regular basis.

The mark up would look like this:

```javascript
Text with foot note[^1]

lorem ipsum

[^1]: Footnote
```

Copy

You can also insert footnotes directly into text like so: 

```javascript
This is some text. Some More text
This text has a foot note ^[Foot Note Text]
```

Copy

[YouTube Explanation](https://youtu.be/FIimThW6SXQ)

## Linking

### Linking and back Linking

The most basic way to link in obsidian is the wiki style link. This is an in-text link to another page in your obsidian vault. You can achieve this by using square brackets like so: [[Page Link]]

You can also link to specific blocks by adding a “^” symbol after your page name like so: [[Page Link^block to link to]]. When you do this, Obsidian will bring up a context menu to assist you in choosing the correct block in your document. You can link to other pages in your obsidian vault or you can use this to link to blocks in the current document. This is helpful for creating page contents for large documents.

You can also link to specific heading by doing this **[[Page Link#The Heading]].**

Explaining back links in text is a bit difficult so I have made a video below to demonstrate how this works.

[YouTube Explanation](https://youtu.be/j2fH1lglbts)

## Adding Aliases

Aliases are a way to link to your files with different names. For example, you want to link to a page called “Productivity Home” this page contains all your important research on productivity. If you wanted to use this text in a natural sentence it would be tricky. In come Aliases: using an aliase you can refer to this page like so “[[Productivity Home|Productivity]] is a topic that too many people have an opinion about, but few have truly mastered.” The bolded text is what will display in your document. You can find a more clear explanation of this in the video below:

[YouTube Explanation](https://youtu.be/_niqHMPDITU)

## Linking to External Locations

You can link to websites and files on your computer by using external links. They’re different from internal links. External links look like this: [Text]([https://placetolinkto.com](https://placetolinkto.com/))

## Embedding content

Embedding content is another thing that makes _linked thought_ software so powerful. In Software like Obsidian.md and Roam Research you can link to other pages or blocks. This is powerful because you can show an entire page within a page, or just a paragraph or two.

This is great because when the content is updated on the original page it is also updated everywhere it’s embedded. People have found many creative uses for this feature.

To embed a single page use this syntax: ![[Page Name]] Notice how it’s the same as linking to page except you just put the exclamation mark in front?

You can embed just a paragraph by using the same syntax but, you’ll need to include the “^” symbol after the page name like so: ![[Page Name^block to link to]]

### Embedding images and other file types.

You can embed media in your Obsidian documents. You’ll need to make sure that the media exists in the vault folder first. Many people like to create an attachemnts folder and keep all their media there. Once you’ve put your media in the obsidian folder you can link to it like this: ![[picture.jpg]]

Here is a list of file types you can embed in obsidian:

1.  Markdown files: `md`;
2.  Image files: `png`, `jpg`, `jpeg`, `gif`, `bmp`, `svg`;
3.  Audio files: `mp3`, `webm`, `wav`, `m4a`, `ogg`, `3gp`, `flac`;
4.  Video files: `mp4`, `webm`, `ogv`;
5.  PDF files: `pdf`.

[Video] – Coming Soon

## Queries and Search

Queries allow you to find several notes in your vault that match a specific criteria. This is helpful if you want to create a hub for specific notes. For example, you could tag all notes derived from videos, and then query your vault so only the notes from a specific creator are shown:

````markup
```query
#video + Tiago Forte
```
````

Copy

In my vault this will show me all notes on videos by the creator Tiago Forte

[Video] – Coming Soon

## Adding Meta Data

You can add additional data to your notes such as tags and aliases. Metadata uses a markup called YAML which stands for “Yet another markup language”.

YAML metadata is useful if you want to add tags to your notes or globally refer to notes by an alias. YAML is hidden in notes so you can add a lot of data to the YAML markup without making your notes messy.

YAML in obsidian typically looks like this:

```markup
---
alias: [how to use obsidian,obsidian guide]
tags: <span id=easy-footnote-1-1295 class=easy-footnote-margin-adjust></span><span class=easy-footnote><a href=#easy-footnote-bottom-1-1295 title><sup>1</sup></a></span>
---
```

Copy

The dashes will go a different colour (By default, the dashes are green) if you have placed the YAML in your notes correctly.

By default obsidian supports the following YAML in this order:

1.  alias
2.  tags
3.  cssclass

You are able to add more YAML metadata but it’s not natively supported by obsidian. However, this can still be useful if you’re using plugins like _Dataview_