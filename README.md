# reinterpretive-label

## RULE #1:

be civil.

We want to make public spaces more --- not less -- pleasant.

## Also,

understand relevant legal restrictions in your area and do not violate them.

## Prerequisites

You'll need to have a [Unix shell](https://en.wikipedia.org/wiki/Unix_shell) you can run things in.

You'll also need to have software called [Singularity](https://singularity.lbl.gov/) that facilitates packaged Linux workflows.

## Usage

Grab a copy of the repo using [git](https://git-scm.com/).
```
git clone https://github.com/mmore500/reinterpretive-label
cd reinterpretive-label
```

Make a copy of the template reinterpretive label Latex file in order to customize it.

```
cp tex/template.tex instance.tex
```

Now, you can open `instance.tex` with your favorite text editor and change the text.
You don't really need to know much Latex in order to make edits.
That said, if you're unfamiliar you can find some helpful hints in the "Latex Pointers" section below.

When you're satisfied with your reinterpretive label (`instance.tex`), here's how to generate a PDF.

```
singularity run shub://mmore500/reinterpretive-label
```

This will download the packaged linux workflow for you and do the actual work of compiling `instance.tex` to `instance.pdf`.

If you want to fiddle with your reinterpretive label some more (i.e., make futher edits to `instance.tex`) and then recompile `instance.pdf`, waiting for the singularity workflow image to download again can be annoying.
You can get around this by using the cached `.simg` file generated when you run from SingularityHub (`shub`) the first time.

```
singularity run mmore500-reinterpretive-label-master-latest.simg
```

Finally, to clean up, use
```
make clean
```


## Printing Stickers

You can print stickers wherever you want.

[MakeStickers](https://www.makestickers.com/), though, seems convenient to me because it allows for
* PDF upload
* custom aspect ratios of [rectanglular stickers](https://www.makestickers.com/products/custom-stickers/rectangle-stickers) (the height to width of the generated PDF label depends on the amount of content), and
* small batch-size when printing.

## Be Social!

Share what you're up to with the hashtag [#reinterpretivelabel](https://twitter.com/hashtag/reinterpretivelabel) and\or tweet at me [@MorenoMatthewA](https://twitter.com/MorenoMatthewA).

Bonus points for including the twitter handle of your local modern art museum in your stickers.

## Inquiries

If you're having any issues figuring out how to generate a sticker --- or even just don't have the computational means to do it yourself --- get in touch.
I might be willing to fund a few sticker print jobs, too, if you're unable.

```
matthew.andres.moreno@gmail.com
```

## Latex Pointers

To edit a `.tex` file, use a [plain text editor](https://en.wikipedia.org/wiki/Text_editor), not a rich text editor like Microsoft Word.

The actual text goes in between `\begin{document}` and `\end{document}`.
Don't make any edits outside these markers!

Quotation marks:
```
`` '' YES
" NO
```

Em dashes:
```
--- YES
- NO
```

Text size:
wrap the text you want to resize inside curly braces and tell what effect you want with `\sizename`.
``
{\huge BIG TEXT}
{\huge small text}
```

Available size descriptors include: `\Huge`, `\huge`, `\LARGE`, `\Large`, `\large`, `\small`, `\footnotesize`, `\scriptsize`, and `\tiny`.

Text styling:
I defined two text modifiers for you: `\myboldfont` and `\myitalicfont`.
Just like with text size, wrap the text you want to modify inside curly braces and tell what modifier you want.
``
{\myboldfont BOLD TEXT}
{\myitalicfont italic text}
```

Whitespace:
to create a paragraph break, simply have an empty line between two lines of text.
```
I'm in the top paragraph!
I'm in the top paragraph, too.

I'm in the bottom paragraph.
```

Use `\smallskip`, `\medskip`, and `\largeskip` to space out your paragraphs.

```
I'm in the top paragraph!
I'm in the top paragraph, too.

\largeskip

I'm in the bottom paragraph and further away now.
```

Special characters:
the following characters might confuse the Latex compiler and cause an error:
```
 # $ % & ~ _ ^ { }
```
You can get around this by placing a `\` in front.
For example, type `\#` instead of just `#` and `\$` instead of just `$`.