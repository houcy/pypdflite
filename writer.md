---
layout: default
title: Writer
---

# PDFLite

The PDFLite writer object does the initial setup on the document.

1. [Intro](index.html)
1. [Writer](writer.html)
    1. [Constructor](#construct)
    2. [Closing](#close)
    3. [Options](#options)
2. [Document](document.html)
3. [Cursor](cursor.html)
4. [Color](color.html)
5. [Tables](tables.html)
6. [Cell Formats](cellformat.html)


# <a name="construct"></a>Constructor

## writer = PDFLite(filepath, orientation, layout, font\_list, font\_dir)

```
from pypdflite import PDFLite

writer = PDFLite("hello.pdf")

```

**Parameters:** 

* **filepath :**

    * A string file path for the pdf to store the document to,

    * A writable object, i.e. StringIO

    * The literal string "string", to return the buffer as a string

*  **orientation (string):**

    * 'P' for portrait (default)

    * 'L' for landscape

* **layout (string):**

    * 'a3'
    * 'a4'
    * 'a5'
    * 'letter' (default)
    * 'legal'
    * '11x17'

* **font_list (list):**

    * A list of paths to truetype font files you wish to include

* **font_dir (string):**

    * The path to a directory where you want to load fonts from. 

Note: PDFLite searches system files for fonts if "font\_list" and "font\_dir" are not set.

## writer.get_document()

* Returns PDFDocument object.

```
    document = writer.get_document()
```

# <a name="close"></a>Closing

## writer.close()

```
    result = writer.close()
```

* Required at the end to close and generate the pdf.

* Returns None if saved as a document, else returns either a string or the 
writable object given in the constructor.


# <a name="options"></a>Other Options

## writer.set_compression(bool)

* Defaults to True, pdf will be compressed. Set to False if you would like to 
debug the pdf in a text editor.

## writer.set_information(title, subject, author, keywords, creator)

Information is metadata that can be seen in the 'properties' dialog in readers.

* Set with strings, in order or by keyword, use None to skip

set_display_mode(zoom, layout)

**Parameters**

* **zoom (string or int)**
    * "fullpage", "fullwidth", "real", "default".
    * May be an integer 0 < zoom <= 100
    * Describes the level of zoom for the page when it is opened. Defaults to "fullpage".

* **layout(string)**
    * "single", "continuous", "two", "default"
    * Defaults to "continuous".
    * Not related to page orientation

