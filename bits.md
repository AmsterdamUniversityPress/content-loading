# BITS

## Introduction
- Books on AUP Online (Ingenta Edify Platform) must be in BITS.
- The core publication unit is the chapter, not the book as a whole.
- Currently, content is in PDFs, with the BITS only containing metadata


<!--
The guidelines given below pertain to the Books Interchange Tag Suite (BITS) version 2.0 as the format for loading book and chapter XML content into Ingenta Edify. Supplied XML content must be valid against the NISO BITS version 2.0 tag set. The guidelines supplement the BITS documentation.

Due to the size of the BITS tag set, Edify does not accommodate all features available in the tag set. This document describes the Edify implementation of the BITS tag set. Content that is valid against this specification will also be valid against the BITS tag set, but the reverse is not necessarily true.

This specification is a living document. Please contact Ingenta with any questions regarding the elements described below or to help handle the situations not covered in the document.

Note: Please note that for clarity in this document, elements have been specified with angle brackets e.g. `<book-part>` and attributes have been prefixed by "@" e.g. @publication-format

## Content formats
Edify supports book XML in two forms

- Fully tagged full text XML with or without PDFs - This is our recommended format.
- Metadata-only XML - This is suitable for content available only in PDF format without any full text XML.

Book metadata for both forms must be complete as described here.

Guidelines regarding body tagging do not apply to metadata-only XMLs.

## General XML guidelines
The XML must be well-formed and conform to the BITS 2.0 DTD. UTF-8 encoding must be used for the content within the XML. The XML tagging must meet the specification outlined below.

## XML declaration
Declarations required at the top of each XML file are:

XML version
Character encoding
Document Type Definition

Example:

`<?xml version="1.0" encoding="UTF-8" standalone="no"?>`
`<!DOCTYPE book PUBLIC "-//NLM//DTD BITS Book Interchange DTD v2.0 20151225//EN" "BITS-book2.dtd">`

The XML must use UTF-8 as the character encoding to ensure that characters are translated properly upon import into the Edify database. Content XML may also contain numeric character references (e.g. &#345; or &#x159;). Predefined entities for the ampersand, less-than, and greater-than should be used where the intent is to display the actual characters ampersand (`&`), less-than (`<`), or greater-than (`>`) respectively; the predefined entities should not be used where those characters are part of markup or encodings.
-->

## Content identifiers
Every book, chapter and media object (e.g. figure, table, multimedia) in the XML must have a unique immutable identifier which is suitable for constructing a URL.

Book and chapter identifiers will be agreed between Ingenta and the publisher during the content analysis and loader set-up phase.

The Edify loader is pre-configured to use the following elements to create the identifiers.

Type of content | XPath
----- | ----
Book | `/book/book-meta/book-id[@book-id-type="doi"]`
Chapter / Section | `book-part[@book-part-type="chapter"]/@id`
Figure	| `fig/@id`
Table | `table-wrap/@id`
Other Media | `media/@id`

Please note that the above defaults can be configured to pick up identifiers from other elements in the XML as long as the identifier values satisfy the above constraints.

### ISBNs
The `<isbn>` element is used to designate the ISBN of the book. Please use the @publication-format attribute to indicate whether the ISBN is for the print or electronic version of the book. `<isbn>` elements without the @publication-format attribute will be ignored.

The following markup will designate the print ISBN

`<isbn publication-format="print">...</isbn>`

The following markup will designate the electronic ISBN

`<isbn publication-format="electronic">...</isbn>`

## Cover image
`<self-uri xlink:role="http://pub2web.metastore.ingenta.com/ns/coverImage" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="10.5117_9788447874422_cover.jpg"/>`

## Book level metadata
This metadata is contained within the `<book-meta>` element. This element is always required by the Edify loading system. If the book zip file contains separate XMLs per chapter, you must ensure that the book metadata is provided consistently in every XML.

The table below describes the required elements within the `<book-meta>` element

Element | Required attributes | Notes
----- | ----- | -----
`<book-title>` |  | This must be provided as a child of the `<book-title-group>` element.
`<pub-date>`/`<year>` |  | The year of publication. This must be a 4 digit year only for example `<pub-date><year>2018</year></pub-date>`. The month and day of publication can also be provided using the `<pub-date>`/`<month>` and `<pub-date>`/`<day>` elements. If the month and day are not provided they will both default to 01. If the month and day are provided they must be a 2 digit number e.g. `<month>`02`</month>` and `<day>`08`</day>`
`<book-id>` | `@book-id-type="doi"` | Used to provide the DOI of the book. The Edify loader is configured by default to use the DOI to generate the unique identifier for a book. If the use of a different element for the unique identifier has been agreed between the publisher and Ingenta then the provision of this element can be optional.

The following optional elements are supported within the `<book-meta>` element.

Element | Required attributes | Notes
----- | ----- | -----
`<subtitle>` | | The subtitle of the book. This must be provided as a child of the `<book-title-group>` element.
`<abstract>` | | The description of the book. While this is not a mandatory element Ingenta recommends that an abstract is provided to improve discoverability of the content.
`<kwd-group>` | | The keywords for a book. Please use a `<kwd>` element for each keyword.
`<contrib-group>` | | Please refer to the Contributors section
`<isbn>` | @publication-format | Please refer to the ISBNs section
`<self-uri>` | | Please refer to the Full text section
`<edition>` | | Used to provide the edition of the book
`<permissions>` | | Please refer to the Permissions section.
`<book-page-count>` | | Must be provided within the `<counts>` element. Used to provide the number of pages of the book.

## Book table of contents
The table of contents within the book on the website is dynamically generated using the `<book-part>` elements within the book. Where the sections and chapters are provided within a single book XML, the order in which the `<book-part>` elements are provided will be used to determine the ordering within the TOC.

## Book body
This content is provided under the `<book-body>` element. The book body includes parts(sections) and chapters. Chapters may or may not belong to sections. Book sections and chapters are tagged using the `<book-part>` element within `<book-body>`. The @book-part-type>` attribute is used to indicate whether the book part is a Section or a Chapter. The value of the @book-part-type attribute must be "part" for a Section and "chapter" for a Chapter.

Unless alternative identifiers have been agreed between the publisher and Ingenta, the `<book-part>` element must have an @id attribute which must be unique and is used to construct the URL for the section and chapter.

## Section level metadata
Section metadata must be provided through the `<book-part>` set of elements where the @book-part-type attribute is specified with a value of "part".

The `<book-part>` element must have an @id attribute which is used as default by the Ingenta Edify loader to construct the section identifier.

Section level metadata is provided within the `<book-part-meta>` child of the `<book-part>` element. The table below describes the mandatory children of the `<book-part-meta>` element for sections

Element | Required attributes | Notes
----- | ----- | -----
`<title>` | | This must be provided as a child of the `<title-group>` element which in turn must be a child of the `<book-part-meta>` element. The @xml:lang attribute can be used to indicate the language

## Chapter level metadata
Chapter metadata is provided through the `<book-part>` set of elements where the @book-part-type attribute is specified with a value of "chapter".

The `<book-part>` element must have an @id attribute which is used as default by the Edify loader to construct the chapter identifier.

Chapter level metadata is provided within the `<book-part-meta>` child of the `<book-part>` element. The table below describes the mandatory children of the `<book-part-meta>` element.

Element | Required attributes | Notes
----- | ----- | -----
`<title>` | This must be provided as a child of the `<title-group>` element which in turn must be a child of the `<book-part-meta>` element. The @xml:lang attribute can be used to indicate the language.

The following optional elements are supported within the book-part-meta element.

Element | Required attributes | Notes
----- | ----- | -----
`<abstract>` | | Used to provide the abstract of the chapter. Use the @xml:lang attribute to denote the language
`<fpage>` | | Starting page of the chapter
`<lpage>` | | Ending page of the chapter
`<elocation-id>` | | Replaces starting and end page for electronic-only publications
`<permissions>`/`<copyright-statement>` | | Copyright statement for the chapter
`<contrib-group>` | | Please refer to the Contributors section
`<kwd-group>` | | Keywords for the chapter. Please use a `<kwd>` element for each keyword.
`<self-uri>` | | Please refer to the Full text section

<!--
## References
References need to be tagged at as granular a level as possible to enable Edify to query systems such as Crossref for matches for the references and display links for those references on the website.

Edify accepts both `<element-citation>` and `<mixed-citation>` elements for tagging reference data. Edify requires the @publication-type attribute to be specified with a value of journal for both `<element-citation>` and `<mixed-citation>` elements so that they can be matched against third parties. For book references please supply the @publication-type attribute with a value of book.

Please refer to the BITS documentation for best practices about the granularity of tagging references.

If the publisher's workflow is able to determine the DOI and/or the PubMed ID of the reference, these can be included in the reference metadata through the following markup:

For Crossref DOIs

`<pub-id pub-id-type="doi">`10.1234/example.doi.5678`</pub-id>`

For PubMed IDs

`<pub-id pub-id-type="pmid">`12345`</pub-id>`
-->

## Permissions
Are only possible at book level ?????????????????????

## Contributors
Contributors can be provided at book level as well as individual chapter level.

### Book contributors
The Edify loader supports the provision of authors and editors at book level. They are provided through `<contrib-group>` set of elements under `<book-meta>`.

Metadata for each author or editor is provided through a `<contrib>` element. The @contrib-type attribute for the `<contrib>` element indicates whether the metadata is for an author or editor.

The following markup designates an author at book level.

```
<book-meta>
....
<contrib-group>
    <contrib contrib-type="author">
        ....
    </contrib>
```

The following markup designates an editor at book level.

```
<book-meta>
....
<contrib-group>
    `<contrib contrib-type="editor">
        ....
    </contrib>
```

### Chapter contributors
The Edify loader supports the provision of authors at chapter level. They are provided through `<contrib-group>` set of elements under `<book-part-meta>`.

Metadata for each author is provided through a `<contrib>` element.

The following markup designates an author at book-part level.

```
<book-part-meta>
....
<contrib-group>
    <contrib contrib-type="author">
        ....
    </contrib>
```

### Contributor metadata
The contributor name information must be provided within the `<name>` set of elements within the `<contrib>` element. Only one `<name>` set of elements must be provided within a `<contrib>` element.

The following elements are supported within the `<contrib>` element.

Element | Required attributes | Notes
----- | ----- | -----
`<name>`/`<given-names>` | | 
`<name>`/`<surname>` | | 
`<name>`/`<prefix>` | | 
`<name>`/`<suffix>` | | 
`<email>` | | 
`<xref>` | @ref-type="aff" AND @rid | This element is used to point to an affiliation. The @xref-type attribute indicates that the xref is for an affiliation. The @rid attribute is used to provide the list of IDs of the affiliation `<aff>` elements referred to, As per the BITS specification this is the recommended way of tagging affiliations for contributors. The target `<aff>` element must be in the same XML file as the `<contrib>` and `<xref>`.
`<contrib-id>` | @contrib-id-type="orcid" or @authenticated="true" OR @authenticated="false" | This indicates the ORCID for the contributor. The URL of the ORCID must be provided as the body of the `<contrib-id>` element.
`<aff>` | | This element can be used to tag the affiliation for the contributor. However as per the BITS specification the use of the `<xref>` element as mentioned above is recommended.

Example contributor markup is as follows:

```
<contrib-group>
    <contrib contrib-type="author">
        <name>
            <surname>John</surname>
            <given-names>Smith</given-names>
            <prefix>Dr</prefix>
            <suffix>Jr</suffix>
        </name>
        <xref ref-type="aff" rid="aff1"><sup>1</supp></xref>
    </contrib>
    <aff id="aff1"><sup>1</sup>Ingenta, Oxford, OX4 2HU</aff>
</contrib-group>
```

## Full text
Ingenta recommends the use of the `<self-uri>` element for designating full text files. This can be provided within the `<book-meta>` element for book full text and within the `<book-part-meta>` element for chapter full text. The element must have the @xlink:href attribute which must contain the file name of the full text file with the file extension. Any folder paths must not be included in the value of the @xlink:href attribute. The full text content type is indicated through the @content-type attribute. The loader currently accepts pdf and epub as possible values of the @content-type attribute.

For example

`<self-uri content-type="pdf" xlink:href="abc.pdf" />`
 
`<self-uri content-type="epub" xlink:href="abc.epub" />`

## Tables, figures, and graphics
Please refer to [media](media.md)

<!-- 
Hi Crius Group, I apologise for the extreme delay in response to this ticket.
There seems to be an implicit assumption in our book loader that DOIs will be lower case, we'll remove that the next release but in the meantime if you update the _FM and _BM DOIs to be lower case then the file will proceed through the loader.
There's a further problem in the XML, the PDFs aren't actually referenced from it, you need to add in a self-uri element, e.g.
                        <book-part-meta>
                                <book-part-id book-part-id-type="doi">10.5117/9789463721943_fm</book-part-id>
                                <title-group>
                                        <title>Front matter</title>
                                </title-group>
                                <pub-date publication-format="print">
                                        <year>2023</year>
                                        <month>10</month>
                                        <day>17</day>
                                </pub-date>
                                <fpage>1</fpage>
                                <lpage>14</lpage>
                                <self-uri xlink:href="10.5117_9789463721943_FM.pdf" content-type="pdf"/>
                        </book-part-meta>
If you make those changes then the book will load with each chapter being created with their own PDF.
Regarding the cover image, wed don't support PDF cover images, you need to use an image file, include it in the zip file and reference it in the XML through self-uri like this:
<self-uri xlink:role=http://pub2web.metastore.ingenta.com/ns/coverImage xmlns:xlink=http://www.w3.org/1999/xlink xlink:href="9789463721943-cover.png"/>
The xlink:role attribute indicates that it is a cover image and the xlink:href attribute defines the name of the image file.
-->
