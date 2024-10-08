# Supplements

AUP journal articles, book chapters and whole books can have supplementary materials ("supplements" for short).

## Figshare

AUP policy is to place supplements on [Figshare](https://figshare.com/). I don't know how this is done, who does it, and whether the proper citation, with DOI, is mandatory. Nor do I know if this is the _only_ place of supplements.

### example

Take the images [here](https://figshare.com/articles/figure/Temple_of_Concord_View_of_front_facade/24734862?file=43563720). As you can see, Figshare allows users to share quite a bit of information. It also has search functionality and usage metrics. Every (?) Figshare object has a citation and a DOI:

```
G. Massiot & cie (2017). Temple of Concord: View of front facade. University of Notre Dame. Figure. https://doi.org/10.7274/24734862.v1
```

```
https://doi.org/10.7274/24734862.v1
```

## How to upload supplements onto AUP Online?

There are two ways: through the XML and manually.

### XML
It has to go through the XML. But how? The description here [here](https://confluence.ingenta.com/confluence/pages/viewpage.action?spaceKey=AUP&title=JATS+XML+Guidelines#JATSXMLGuidelines-Supplementarymaterial) is less than useless as it tells us nothing about metadata or how files should be loaded. The only thing we know is that we must use the `<supplementary-material>` element within `article/front/article-meta`.

### Manual
Supplementary material can also be uploaded through the content editing tools in the site. General documentation for the tool is provided [here](https://confluence.ingenta.com/confluence/display/AUP/Content+Editing+Tool).

If you access an article when logged in as admin you can click on `Edit Article` in the left side tools menu and one of the fields in the pop up allows you to create supplementary material. Supplementary material can be added for books in a similar way.

### Figshare
Edify supports integration with Figshare. This can be enabled in the site through a change request. 

[Here](https://www.microbiologyresearch.org/content/journal/acmi/10.1099/acmi.0.000511.v3#supplementary_data) is an example of the Figshare integration in another Edify site.

## XML again

The relevant tag in JATS/BITS is `<supplementary-material>`. Do not confuse this with `<supplement>` which is only used as part of a bibliographic reference (`<element-citation>` and `<mixed-citation>`). 

The tag may be contained in a `<sec>` in the article `<body>` for journal articles, and in `<book-meta>` and `<book-part-meta>` for books. Other places are possible, too, but I recommend regularity.

The tag may contain a link to, and a description of, supplementary material. Given that AUP uses Figshare, this is an example of what such a tag can look like:

```xml
<supplementary-material id="S0" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:title="local_file" xlink:href="Italy-Girgenti-temple-Concord.jpg" mimetype="image/jpeg">
  <caption><p>G. Massiot &#038; cie (2017). Temple of Concord: View of front facade. University of Notre Dame. Figure. https://doi.org/10.7274/24734862.v1</p></caption>
</supplementary-material>
```

<!--
This is what I had first. That did NOT work

<supplementary-material id="s0" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="https://doi.org/10.7274/24734862.v1">
  <uri>https://doi.org/10.7274/24734862.v1</uri>
  <p>G. Massiot &#038; cie (2017). Temple of Concord: View of front facade. University of Notre Dame. Figure. https://doi.org/10.7274/24734862.v1</p>
</supplementary-material>

Note the use of the `@id` - a local AUP ID - and `<uri>` - always the Figshare DOI. In this example, the `<supplementary-material>` tag is placed in the book metadata, between the permissions and the cover image.

If it were a chapter supplement, it would be placed in the chapter metadata, between the page numbers and the link to the chapter PDF.
-->


**Important**

1. **the `<supplementary-material>` tag has to go BETWEEN `<publisher>` AND `<permissions>` or the upload will fail.**
2. **only LOCAL files are permitted**. This basically means that everything is uploaded twice: onto Edify and onto Fighare. It looks like the name of the file is irrelevant, but you haver to get the MIME type right. **The file is included in the zip that is uploaded onto the FTP.**
3. **Only the `<caption>` element and its children `<title>` and `<p>` are processed by the application (and reduced to `<span>` so no mark-up).**.


## supplements tab on Edify
If the XML is tagged correctly, the supplements metadata will be displayed on the supplements tab in Edify. (Silly example [here](https://qa.aup-online.com/content/books/10.5117/9787062629530#supplementary_data)). Also, an icon (and some text) will be displayed for the supplement itself. Click on the icon and the supplement will open in a new tab. (Silly example [here](https://qa.aup-online.com/docserver/fulltext/10.5117/9787062629530/Italy-Girgenti-temple-Concord.jpg?expires=1725462546&id=id&accname=21&checksum=FFD8A426AB56B7B1F1FAE95935E76C3C&union=true)).

Note that access to the supplements tab is determined by the user's access to the content. For example, not anyone can see the supplements for a subscribed-to article, only the paying user.

## see also

- https://jats.nlm.nih.gov/extensions/bits/tag-library/2.1/element/supplementary-material.html
- https://confluence.ingenta.com/confluence/pages/viewpage.action?spaceKey=AUP&title=JATS+XML+Guidelines#JATSXMLGuidelines-Supplementarymaterial
- https://confluence.ingenta.com/confluence/display/AUP/Content+Editing+Tool
