# Remarqué

Remarque is a tree-based note-taking language for Gedit. Its usefulness lies more in its structure than any syntax highlighting, so a particularly zen user might consider this non-essential (and it is, really).

## Installation and Usage

Remarqué is easy to install (and uninstall) and has no dependencies. Feel free to delete the folder cloned by the installation commands after you're done installing. 

### GTKSourceView Language

```bash
git clone https://github.com/Positron11/remarque.git
sudo mv remarque/Gedit/remarque.lang /usr/share/gtksourceview-4/language-specs/
sudo chmod 0644 /usr/share/gtksourceview-4/language-specs/remarque.lang
```

Select Remarqué in Gedit's language selector to use.

### Gedit Colour Scheme

Because of Remarqué's styling, you'll need to use a color scheme that supports Remarqué. At present, the only such schemes are the [Agenwulf color schemes](https://github.com/Positron11/agenwulf-color-scheme) (as shown in the example image - available in light and dark mode)

### Font

I recommend that you use a font that has support for programming glyphs, for the best possible UI. Not necessary, but it'll look a lot better. I personally prefer the [Fira Code](https://fonts.google.com/specimen/Fira+Code?query=fira+code) font (as shown in the example image).

## Syntax

All of Remarqué (except text formatting) works without any special language and highlighting support - it's a way of writing rather than an actual language. See below for guidelines.

### Headings and Sections

We recommend two lines of space between each section, before and after. Not required, it just looks nice that way. We also recommend no space between heading lines and their content

- **Document heading:** Begin line with ` @ `, space after is optional. Follow with a line of ` = `, preferably of the same length as the heading.

	```
	@FILE HEADING
	=============
	```

- **Section heading:** Begin line with ` & `, space after is optional. Follow with a line of ` - `, preferably of the same length as the heading.

	```
	&Section Heading
	----------------
	```

### Tree Structure

Trees follow a simple, visually intuitive structure comprised of stacked ` |-> ` components. Using the right font greatly enhances the Remarqué tree experience.

- **Basic example:** Trees can extend to as many levels as required. There are no real guidelines for spacing within trees, but we suggest one "leafless branch" when going down a level (eg. level 3 to level 2, as shown below). Remember to maintain the level you're on with a ` | ` when leaving a space.

	```
	|-> Level 1
	| |-> Level 2
	| | |-> Level 3
	| |
	| |-> Another level 2
	|
	|-> And so on...
	```

- **Enumerating trees:** Enumerate trees by adding a number in the empty space between vertical branches as shown below. There's the obvious problem of numbers with more than 1 digit, but there's not much we can do about that right now.

	```
	|-> Enumerated list
	|1|-> Item 1
	|2|-> Item 2
	|3|-> Item 3
	```

### Text Objects

Remarqué offers a few text objects, essentially blocks of text with a somewhat defined purpose.

- **Tags:** Mainly used for indexing list nodes, but can be used for anything else. Put text between square brackets (` [...] `) with no space between the brackets and the contained text.
	
	```
	|-> List node [5.3.7]
	```

- **Banners:** Can be used to add comments and notes to list nodes. Put text after ` <=| `, which should be placed at the end of the line, preferably with a space before.
	
	```
	|-> List node <=|Some notes about this node
	```

- **Placeholders:** Put text between angle brackets (` <...> `) with no space between the brackets and the contained text.
	
	```
	<placeholder text>
	```

### Text Formatting

This part of Remarqué attempts to make use of what limited text formatting capabilities Gedit offers and [**requires a Gedit colour scheme that supports Remarqué**](#gedit-colour-scheme). GTKSourceViewLang's selector protocol unfortunately doesn't allow for nested selectors, so we'll have to make do with one style at a time (for now).

- **Bold text:** Put text between ` ** ` with no space between the apostrophes and the text to be bold.
	
	```
	**Bold Text**
	```

- **Italic text:** Put text between ` * ` with no space between the apostrophes and the text to be italicized.
	
	```
	*Italic Text*
	```

- **Underlined text:** Put text between ` _ ` with no space between the underscores and the text to be bold.
	
	```
	_Underlined Text_
	```

- **Strikethrough text:** Put text between ` ~ ` with no space between the tildes and the text to be struck through.
	
	```
	~Strikethrough Text~
	```

- **Highlighted text:** Put text between ` ! ` with no space between the exclamation marks and the text to be highlighted.
	
	```
	!Highlighted Text!
	```

- **Hyperlinks:** Hyperlinks are automatically formatted

### Productivity

Tree lists can be used as advanced to-do lists or planners for productivity purposes. Remarqué offers two special selectors for this purpose - doing, and done.

- **Doing:** Can also be used to just highlight a particular node at the tree level. Replace the node in question's ` - ` with ` = ` as shown below. 
	
	```
	|-> Regular node
	|=> "Doing" node
	```

- **Done:** Add a ` ✔ ` to the end of the line to signify completion. You'll have to use exactly that symbol, so keep it handy.
	
	```
	|-> Regular node
	|=> "Done" node ✔
	```

## Contributing and Credits

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

All code written by Aarush Kumbhakern. README created with [Apostrophe](https://apps.gnome.org/app/org.gnome.gitlab.somas.Apostrophe/).