# JATS

## Introduction

The guidelines given below pertain to the [Journal Publishing Tag Library NISO JATS version 1.1](https://jats.nlm.nih.gov/publishing/1.1/) (JATS tag set) as the format for loading journal XML content into Ingenta Edify. Supplied XML content must be valid against the NISO JATS version 1.1 tag set.

Due to the size of the JATS tag set, Ingenta Edify does not accommodate all features available in the tag set. This document describes the Ingenta Edify implementation of the JATS tag set. Content that is valid against this specification will also be valid against the JATS tag set, but the reverse is not necessarily true.

## Article formats

Ingenta Edify supports article data in two forms

-   Fully tagged full text XML with or without PDFs - This is our recommended format.
-   Metadata-only XML - This is suitable for articles available only in PDF format without any full text XML.

## General XML guidelines

The XML must be well-formed and conform to the JATS 1.1 DTD. UTF-8 encoding must be used for the content within the XML. The XML tagging must meet the specification outlined below.

## Issue file packaging structure

1.  Content for an issue must be sent in a single zip file to the specified SFTP location.
2.  The name of the zip and files within the zip must consist of alphanumeric characters and must not contain spaces or special characters.
3.  All articles supplied within an issue zip file must belong to the same issue.
4.  Names of all files supplied within a zip file must be unique, even if they are supplied within folders in the zip file.
5.  The names of image files and PDF files supplied within the XML must exactly match the file names of the supplied files within the zip. The file names within the XML must not contain folder names and must be provided with the extensions.  

## XML declaration

Declarations required at the top of each XML file are:

-   XML version
-   Character encoding
-   Document Type Definition

**Example**:

The XML must use UTF-8 as the character encoding to ensure that characters are translated properly upon import into the Ingenta Edify database. Content XML may also contain numeric character references (e.g. `&#345;` or `&#x159;`). Predefined entities for the ampersand, less-than, and greater-than should be used where the intent is to display the actual characters ampersand (`&`), less-than (`<`), or greater-than (`>`) respectively; the predefined entities should not be used where those characters are part of markup or encodings.

## Article wrapper tag

The wrapper tag for the XML must be 

### Article type attribute

The article-type attribute is used for display of the type on the article homepage and as a filter within the site search. By default Ingenta Edify is set up with the article types listed within the [JATS documentation](https://jats.nlm.nih.gov/publishing/tag-library/1.1/attribute/article-type.html). Additional types can be configured if required. The article types are set up with default display names. The display names can be edited by the publisher administrator using the tools within the site. 

**Example**

`<article article-type="research-article">`

The value of article type is case-sensitive and must not contain spaces. Hyphens are permitted in the value of the attribute.

The value of the article-type attribute is used to indicate the article type in the website as per the screenshot below. 

![](https://confluence.ingenta.com/confluence/download/attachments/174994336/image2019-10-13_10-59-0.png?version=1&modificationDate=1617797232537&api=v2)

The following elements are permitted for journal-level metadata. Please note that the journal-level metadata must be consistent within the XMLs for all articles within that journal.

Please note that the elements will be deemed as mandatory if the agreed identifier structure for content URLs requires that element.

**The XPATHs given below are relative to** 

`/article/front/journal-meta/`

Please ensure that XMLs across all articles for an issue provide the same values for all journal level properties e.g. the ISSNs provided should be the same across all XMLs in an issue. If journal-level properties are provided with inconsistent values, the zip file will be rejected as invalid. 

Provide at least the following issue metadata whenever applicable. Metadata is required for both articles with full text and articles that are supplied in PDF only. 

**The XPATHs given below are relative to** 

`/article/front/article-meta/`

### Required issue metadata

### Optional issue metadata

Please ensure that XMLs across all articles for an issue provide the same values for all issue level properties e.g. the pub-date values provided should be the same across all XMLs in an issue. If issue-level properties are provided with inconsistent values, the zip file will be rejected as invalid. 

## Article metadata

Provide at least the following issue metadata whenever applicable. Metadata is required for both articles with full text and articles that are supplied in PDF only. 

**The XPATHs given below are relative to** 

`/article/front/article-meta/`

### Required Article metadata

### Optional Article metadata

Online First Article Metadata

Online first articles have data similar to articles described above but with the following exceptions:

1.  The XML for an online first article must not contain any issue data - e.g. volume and issue metadata.
2.  The XML for an online first article must not contain any page number information.

## Specifying the language of an article

Edify uses the following logic to work out the language of an article. This value of language is used for displaying the language name in the site, filtering by that language in search results etc.

-   Where **`/article/front/article-meta/title-group/article-title`** has an **`@xml:lang`** attribute, the value of the attribute is used as the language of the article
-   Where the **`article`** element has an **`@xml:lang`** attribute, the value of that attribute is used as the language of the article.
-   Where both the above are not provided, the language is defaulted to "en" (English).

In all cases, the value of the **`@xml:lang`** attribute must follow the [guidelines for language codes](https://confluence.ingenta.com/confluence/display/AUP/JATS+XML+Guidelines#JATSXMLGuidelines-language-codes). 

## Publication dates

**The XPATHs given below are relative to** 

`/article/front/article-meta/`

The publication date for an issue must be provided. An empty or missing pub-date must be avoided.

The values of day and month in pub-date default to 1 if they are not provided. It is highly recommended to specify a month.

### Specifying seasonal dates

Please use the pub-date/season element to specify the season for the issue. Please note that the season should be used in addition to the pub-date/year and pub-date/month elements.

The Edify loading system constructs the display date by concatenating the value of pub-date/season, a comma, a space and the value of the pub-date/year element. 

For example

```
<pub-date publication-format="electronic">
    <day>1</day>
    <month>4</month>
    <season>Spring</season>
    <year>2020</year>
</pub-date>
```

In the above case, the display date of the issue will be "Spring, 2020".

## Contributor Information

The contributor name information must be provided within the `<name>` set of elements within the `<contrib>` element. Each contributor must be provided in a contrib  element. Only one `<name>` set of elements must be provided within a `<contrib>` element.

`<contrib>` elements with the `contrib-type` attribute set to anything other than `author` will be ignored. 

The following elements are supported within the `<contrib>` element.

Example contributor markup is as follows

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
    <aff id="aff1"><sup>1</sup>Ingenta, Oxford, OX4` `2HU</aff>
</contrib-group>
```

### Tagging affiliation information

Affiliations can be tagged in one of the following ways

-   Place the <aff> tags within the contrib-group/contrib element for example

`<contrib-group>`
    `<contrib-type="author">`
        `<name><surname>Smith</surname><given-names>John</given-names></name>`
        `<aff>Magdalen College, Oxford</aff>`
    `</contrib>`
    `....`
`</contrib-group>` 

-   Place the aff elements within the contrib-group element and use the xref element within a contrib element to reference the affiliation. For example

`<contrib-group>`
    `<contrib-type="author">`
        `<name><surname>Smith</surname><given-names>John</given-names></name>`
        `<xref ref-type="aff" rid="aff1"/>`
    `</contrib>`
    `<aff id="aff1">Magdalen College, Oxford</aff>`
`</contrib-group>` 

At present, the **`aff-alternatives`** element is not supported in Edify. 

### Tagging ORCIDs

This markup is only supported in JATS 1.0 and above.

An author's ORCID can be tagged using the **`contrib/contrib-id[@contrib-id-type="orcid"]`** element.

To specify that the contributor is authenticated and qualiﬁes for Crossref's auto-update feature, set the **`@authenticated`** attribute to true for the **`contrib-id`** element. 

For example

`<contrib-group>`
    `<contrib>`
        `<contrib-id contrib-id-type="orcid"` `authenticated="true">http://orcid.org/0000-0002-1234-1234</contrib-id>`
        `<name>`
            `<surname>Smith</surname>`
            `<given-names>John</given-names>`
        `</name>`
    `</contrib>`
`</contrib-group>`

## Keywords

You can define keywords for an article within the XML using the **`kwd`** element. Each keyword must be specified in a separate **`kwd`** element. The **`kwd`** elements are enclosed within a **`kwd-group`** element. For example

```
<article>
    <front>
        ...
        <article-meta>
            ...
            <kwd-group>
                <kwd>science</kwd>
                <kwd>physics</kwd>
                ...
            </kwd-group>
```

## Copyright information

Edify extracts copyright information from the XML using the following logic:

1.  It first looks for an element **`/article/front/article-meta/permissions/license[@license-type='licensed-commercial-use']`** and uses the value of that element if it exists.
2.  If 1 is not true **and** if the XML contains an **`/article/front/article-meta/permissions/copyright-statement`** element
    1.  If **`/article/front/article-meta/permissions/license[@license-type='open']`** **or** /**`article/front/article-meta/permissions/license[@license-type='free']`** exists, then the value of the **`copyright-statement`** element is concatenated with the value of the relevant tag.
    2.  If 2a is not true, then the value of **`copyright-statement`** is used.
3.  If 1 and 2 are not true **and** if the XML contains an **`/article/front/article-meta/permissions/copyright-holder element`** **and `/article/front/article-meta/permissions/copyright-year`**, then the value of **`copyright-year`** concatenated with **`copyright-holder`** is used.
4.  If 1, 2 and 3 are not true **and** if the XML contains the **`/article/front/article-meta/permissions/copyright-holder`** element, the value of **`copyright-holder`** is used. 

## Permissions

Please refer to [Acces](acces.md)

## Conflict of Interest information

Please tag conflict of interest information as the value of the element **`/article/front/article-meta/author-notes/fn[@fn-type='COI-statement']`**. Mixed content can be provided as the value of the tag for example links.

## Article publication history

The following article publication history dates are supported

Please note that for a date type, only one date must be provided.

## Figures

Please refer to [XML guidelines for media objects](https://confluence.ingenta.com/confluence/display/AUP/XML+guidelines+for+media+objects)

## Tables

Please refer to [XML guidelines for media objects](https://confluence.ingenta.com/confluence/display/AUP/XML+guidelines+for+media+objects)

## MathML

Please refer to [MathML guidelines](https://confluence.ingenta.com/confluence/display/AUP/MathML+guidelines)

## Related articles e.g. erratum, corrigendum

The related-article tag is used for this purpose. 

The following attributes are required as mandatory.

Please note that the above is based on the assumption that article URLs on the site are constructed with only the DOIs of the articles e.g. /content/journals/10.1234/doi-of-original-article. If this assumption is not valid, then the above specification will need to change.

For example

   `related-article-type="corrected-article"`
   `ext-link-type="doi"`
   `xlink:href="10.1234/doi-of-original-article"/>`

At present, the **`related-object`** element is not supported in Edify.

## Article titles

Article titles must be specified using the **`article-title`** element. In case of sites with multilingual content, an **`@xml:lang`** attribute may be optionally specified for the **`article-title`** element. If the value of **`@xml:lang`** is not specified, Edify defaults the language to be English.

The value of the **`@xml:lang`** attribute must be a two letter language code in all cases. 

### Providing multilingual article titles

The **`article-title`** element along with the corresponding value of **`@xml:lang`** attribute must be used for the original article title. Please use **`trans-title-group/trans-title`** elements with a corresponding **`@xml:lang`** attribute for the **`trans-title-group`** element to provide article titles in other languages. For example

```
<title-group>
    <article-title xml:lang="en">This is an example article title.</article-title>
    <trans-title-group xml:lang="fr"><trans-title>Ceci est un exemple de titre d'article</trans-title></trans-title-group>
</title-group>
```

## Abstract

Please use the **`article/front/article-meta/abstract`** element to specify the original abstract of the article. 

Please note that if **`xref`** tags are included in the **`abstract`** element to link to figures, tables or references in the body of the article, the links will anchor to the corresponding figure, table or reference only within the full text tab and not within the abstract tab.  

Edify does not support the tagging of figures, tables, media objects, supplementary material, references or related content within the abstract tag.

Within an abstract, you may include titled sections using **`sec`** nodes and the **`title`** element in each **`sec`**.

### Providing multilingual abstracts

The abstract element must be used for the original abstract. Please use trans-abstract elements for translated abstracts. The xml:lang attribute must be specified for the abstract and trans-abstract elements in this case. The two letter language code for the language must be used as the value of the xml:lang attribute. 

For example

`<abstract xml:lang="en">This is an example abstract.</abstract>`
`<trans-abstract xml:lang="fr">Ceci est un exemple abstrait.</trans-abstract>`

## Linking the PDF to the article

-   Please use the `**article/front/article-meta/self-uri**` element to link the article to the corresponding PDF.
-   The **`self-uri`** tag must be supplied with an `**xlink:href**` attribute where the value of the attribute exactly matches the name of the PDF file supplied, along with the file name extension.
-   The **`self-uri`** element must be provided with an attribute **`@content-type`** and the value of the attribute must be specified as pdf e.g. **`<self-uri content-type="pdf" xlink:href="ajsr.2020.3.pdf" xmlns:xlink="http://www.w3.org/1999/xlink"/>`**
-   Please note that only one PDF can be supplied per article. 
-   Please do not prepend the file name with a directory path. 
-   If the Edify content loader does not find a PDF file with the name matching the value of the **`@xlink:href`** attribute of the **`self-uri`** element, the zip file will be rejected with an error message, 

## Displaying equations

Equations can be displayed in two ways - as images or through the use of MathML, a W3C standard.

### Equations using MathML

Mathematical equations can be provided using MathML contained in the **`mml:math`** element. This is relevant for content supplied in NLM, JATS and BITS formats.

MathML elements must use “**`mml`**” as the namespace prefix to validate to the NLM/JATS/BITS DTDs.

Edify uses the [MathJax](https://www.mathjax.org/) library to render the MathML content.

## Back matter

The **`ac>`, `app-group`, `bio`, `fn-group`, `ref-list`, `notes`**, and **`sec`** elements can be used in the back matter within the **`/article/back`** element.

## References

-   References or bibliographic citations must be tagged inside a **`ref-list`** element in the back matter.
-   Each reference must be in a separate **`ref`** element. 
-   Each **`ref`** element must be provided with an id attribute which is unique and internally consistent. Best practice is an alphanumeric sequence common to all citations in your document, followed by an incremental number matching the sequential order of citations.
-   References should be tagged at a granular level in order to support optimum display and matching. Without detailed tagging, Edify will be unable to match the reference against resources such as Crossref and would be unable to generate optimum links to citations in Google Scholar.
-   To include a publication's DOI, please use the **`pub-id`** element with an attribute **`@pub-id-type="doi"`** for example <**`pub-id pub-id-type="doi">10.1234/123456789</pub-id>`**.
-   To include a publication's PubMed ID, please use the **`pub-id`** element with an attribute **`@pub-id-type="pmid"`** for example <**`pub-id pub-id-type="pmid">12344</pub-id>`**.
-   Where the publication's DOI or PubMed ID have been specified, they will be used to automatically construct Crossref and PubMed links for the citation.
-   Edify supports the provision of a single **`ref-list`** element within the **`back`** element. Therefore provision of multiple **`ref-list`** elements must be avoided.   
-   The type of citation must be indicated through the **`@publication-type`** attribute for example **`@publication-type="journal"`**. 
    

The following citation elements are supported within the `**back/ref-list/ref**`  element

### element-citation

This element must only contain bibliographic reference elements. It should not include any punctuation or spacing. If this element is used, then punctuation and spacing will be added by Edify.

`<ref` `id="bib13">`
    `<element-citation publication-type="journal">`
        `<person-group person-group-type="author">`
            `<name>`
                `<surname>Smith</surname>`
                `<given-names>John</given-names>`
            `</name>`
            `<name>`
                `<surname>Doe</surname>`
                `<given-names>Jane</given-names>`
            `</name>`
        `</person-group>`
        `<year iso-8601-date="2009">2009</year>`
        `<article-title>Example article title</article-title>`
        `<source>Example Journal Title</source>`
        `<volume>5</volume>`
        `<issue>2</issue>`
        `<fpage>10</fpage>`
        `<lpage>20</lpage>`
        `<pub-id` `pub-id-type="doi">10.1371/journal.pcbi.1000392</pub-id>`
    `</element-citation>`
`</ref>`

### mixed-citation

This element is expected to contain bibliographic reference elements as well as punctuation and spacing. For such self-punctuated references, Edify will display the content of the reference as is and will not attempt to add any punctuation or spacing.

`<ref id="bib12">`
    `<mixed-citation publication-type="journal">`
        `<person-group person-group-type="author">`
            `<string-name>`
                `<surname>Smith</surname>, <given-names>John</given-names>`
            `</string-name>`
        `</person-group>.`
        `<article-title>Example article title</article-title>.`
        `<source>Example Journal Title</source>.`
        `<year>2011</year>`
        `<volume>8</volume>:`
        `<fpage>506</fpage>-`
        `<lpage>515</lpage>.`
    `</mixed-citation>`
`</ref>`

### nlm-citation

JATS 1.1 has deprecated this element. So Edify strongly recommends the use of element-citation or mixed-citation.

-   Footnotes should be included in an **`fn-group`** element, with each footnote in an **`fn`** element.
-   The **`fn`** element must have an **`@id`** attribute if it is linked from elsewhere in the content using an **`xref`** element. 
-   If the **`fn-group`** element does not contain a **`title`** element with the title text for the footnotes section, then Edify will insert a default title "Notes". Please use the **`title`** element if you wish to specify your own section title e.g. **`<fn-group><title>Footnotes</title><fn id=...`**

## Language codes

Wherever language codes are required to be supplied in XML for the value of the **`@xml:lang`** attribute, they must be specified as as the two letter ISO code for the language. The code must be in lower case. For example **`<trans-abstract xml:lang="fr">...`**
