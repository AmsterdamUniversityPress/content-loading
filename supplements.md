# Supplements

AUP journal aricles, book chapters and whole books can have supplementary materials ("supplements" for short).

## Figshare

AUP policy is to place supplements on [Fishare](https://figshare.com/). I don't know how this is done, who does it, and whether the proper citation, with DOI, is mandatory. Nor do I know if this is the _only_ place of supplements.

### example

Take the images [here](https://figshare.com/articles/figure/Temple_of_Concord_View_of_front_facade/24734862?file=43563720). As you can see, Figshare allows users to share quite a bit of information. It also has search functionality and usage metrics. Every (?) Figshare object has a citation and a DOI:

```
G. Massiot & cie (2017). Temple of Concord: View of front facade. University of Notre Dame. Figure. https://doi.org/10.7274/24734862.v1
```

```
https://doi.org/10.7274/24734862.v1
```


## XML

The relevant tag in JATS/BITS is `<supplementary-material>`. Do not confuse this with `<supplement>` which is only used as part of a bibliographic reference (`<element-citation>` and `<mixed-citation>`). 

The tag may be contained in a ` <sec>` in the article `<body>` for journal articles, and in `<book-meta>` and <book-part-meta>` for books. Other places are possible, too, but I recommend regularity.

The tag may contain a link to, and a description of, supplementary material. Given that AUP uses Figshare, this is an example of what such a tag can look like:

```xml
<supplementary-material id="s0" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="https://doi.org/10.7274/24734862.v1">
			<uri>https://doi.org/10.7274/24734862.v1</uri>
			<p>G. Massiot &#038; cie (2017). Temple of Concord: View of front facade. University of Notre Dame. Figure. https://doi.org/10.7274/24734862.v1</p>
		</supplementary-material>

```

Note the use of the `@id` - a local AUP ID - and `<uri>` - always the Figshare DOI. In this example, the `<supplementary-material>` tag is placed in the book metadata, between the permissions and the cover image.

If it were a chapter supplement, it would be placed in the chapter metadata, between the page numbers and the link to the chapter PDF.

## see also

- https://jats.nlm.nih.gov/extensions/bits/tag-library/2.1/element/supplementary-material.html
