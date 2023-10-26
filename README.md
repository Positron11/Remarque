<img src="example.png">

# Remarqué

Remarque is a tree-based note-taking language for GTKSourceView editors. Its usefulness lies more in its structure than any syntax highlighting, so a particularly zen user might consider this non-essential (and it is, really). Supported by GTKSourceView-compliant editors such as Gedit and Gnome Text Editor.

## Installation and Usage

Remarqué is easy to install (and uninstall) and has no dependencies.

### GTKSourceView Language

```bash
git clone https://github.com/Positron11/remarque.git
sudo mv remarque/GTKSourceView-5/remarque.lang /usr/share/gtksourceview-5/language-specs/
sudo chmod 0644 /usr/share/gtksourceview-5/language-specs/remarque.lang
rm -rf ./remarque
```

Select Remarqué in your editor's language selector. Save files with the `.rmq` extension.

### GTKSourceView Colour Scheme

Because of Remarqué's styling, you'll need to use a color scheme that supports Remarqué. At present, the only such schemes are the [Agenwulf color scheme](https://github.com/Positron11/agenwulf) (as shown in the example image - available in light and dark mode)

### Font

Basically any font that had a good-looking `->` ligature. Not necessary, but it'll look a lot better. The font in the example image is [Maple Mono](https://github.com/subframe7536/maple-font).

## Syntax

All of Remarqué (except text formatting) works without any special language and highlighting support - it's a way of writing rather than an actual language. See below for guidelines.

### Doctitle and Sections

We recommend at least one line of space between each section, before and after. Not required, it just looks nice that way. We also recommend no space between heading lines and their content. All headings must be on their own line.

- **Document title:** Begin line with `TITLE:` and a space after.

	```
	TITLE: Document Title
	```

- **Section heading:** Begin line with a section number, with depth delimited with `.` (ie. `1.5.2...`), and a space after is optional.

	```
	1 Section Heading
	⋮
	2.3.1 Sub-Subsection Heading
	```

### Text Formatting

This part of Remarqué attempts to make use of what limited text formatting capabilities basic text editors offer and [**requires a GTKSourceView colour scheme that supports Remarqué**](#gtksourceview-colour-scheme). GTKSourceViewLang's selector protocol unfortunately doesn't allow for nested selectors, so we'll have to make do with one style at a time (for now). Style markers (`*`, `~`, `_`, etc.) will seem to disappear when they've been applied, but they're still there, they're just very small.

- **Bold text:** Put text between ` # ` with no space between the hashtag and the text to be made bold.
	
	```
	#Bold Text#
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

### Text Objects

Remarqué offers a few text objects, essentially blocks of text with a somewhat defined purpose.

- **Tags:** Put text between square brackets with no space between the brackets and the contained text. An example usage:
	
	```
	[20/10/2023] #Some Notes#
	-> Cillum pariatur occaecat magna 
	-> Minim non aliquip quis eu consectetur
	-> Nisi et elit eu dolor tempor qui
	```

- **Placeholders:** Put text between angle brackets with no space between the brackets and the contained text.
	
	```
	Dear <placeholder name>,

	I hope this email finds you in the lowest of spirits... 
	```

- **Inline code block:** Put code between `` ` `` with no space between the backticks and the code to be formatted.
	
	```
	`char* function(void);`  
	```

### Tree Structure

Trees follow a simple, visually intuitive structure comprised of stacked `->` components. Using the right font greatly enhances the Remarqué tree experience.

- **Basic example:** Trees can extend to as many levels as required. Maintain the level you're on with a `|` proceeded by a space.

	```
	-> Level 1
	| -> Level 2
	| | -> Level 3
	| |
	| -> Another level 2
	|
	-> And so on...
	```

- **Enumerating trees:** Enumerate trees by adding numbers, lowercase letters, spaces, or `.` in square braces immediately preceding the arrow of the desired node/leaf

	```
	-> Enumerated list
	| [1]-> Item 1
	| [2]-> Item 2
	| | [ i]-> Item 3
	| | [ii]-> Item 4
	```

### Productivity

Tree lists can be used as advanced to-do lists or planners for productivity purposes. Remarqué offers two special selectors for this purpose - doing, and done.

- **Doing:** Can also be used to just highlight a particular node at the tree level. Replace the node in question's ` - ` with ` = ` as shown below. 
	
	```
	|-> Regular node
	|=> "Doing" node
	```

- **Completion Status:** Add ` :d ` to the end of the line to signify successful completion and ` :f ` to indicate failure.
	
	```
	|-> Success :d
	|-> Failure :f
	```

## Contributing and Credits

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

All code written by Aarush Kumbhakern. README created with [Apostrophe](https://apps.gnome.org/app/org.gnome.gitlab.somas.Apostrophe/).

## License

[MIT](https://choosealicense.com/licenses/mit/)
