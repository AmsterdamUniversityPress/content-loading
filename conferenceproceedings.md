# Conference Proceedings

## Introduction

The guidelines given below pertain to the [Journal Publishing Tag Library NISO JATS version 1.1](https://jats.nlm.nih.gov/publishing/1.1/) (JATS tag set) as the format for loading journal XML content into Ingenta Edify. Supplied XML content must be valid against the NISO JATS version 1.1 tag set.

Due to the size of the JATS tag set, Ingenta Edify does not accommodate all features available in the tag set. This document describes the Ingenta Edify implementation of the JATS tag set. Content that is valid against this specification will also be valid against the JATS tag set, but the reverse is not necessarily true.

## Conference proceeding formats

Ingenta Edify supports conference data in two forms

-   Fully tagged full text XML with or without PDFs -
-   Metadata-only XML with PDFs

## General XML guidelines

The XML must be well-formed and conform to the JATS 1.1 DTD. UTF-8 encoding must be used for the content within the XML. The XML tagging must meet the specification outlined below.

## Conference proceeding file packaging structure

1.  Content for a proceeding must be sent in a single zip file to the specified SFTP location.
2.  The name of the zip and files within the zip must consist of alphanumeric characters and must not contain spaces or special characters.
3.  All papers supplied within a zip file must belong to the same proceeding.
4.  Names of all files supplied within a zip file must be unique, even if they are supplied within folders in the zip file.
5.  The names of image files and PDF files supplied within the XML must exactly match the file names of the supplied files within the zip. The file names within the XML must not contain folder names and must be provided with the extensions.  

## XML declaration

Declarations required at the top of each XML file are:

-   XML version
-   Character encoding
-   Document Type Definition

**Example**:

The XML must use UTF-8 as the character encoding to ensure that characters are translated properly upon import into the Ingenta Edify database. Content XML may also contain numeric character references (e.g. `&#345;` or `&#x159;`). Predefined entities for the ampersand, less-than, and greater-than should be used where the intent is to display the actual characters ampersand (&), less-than (<), or greater-than (>) respectively; the predefined entities should not be used where those characters are part of markup or encodings.

## Content identifiers

Every serial, proceeding, paper and media object (e.g. figure, table, multimedia) in the XML must have a unique immutable identifier which is suitable for constructing a URL.

Proceeding and paper identifiers will be agreed between Ingenta and the publisher during the content analysis and loader set-up phase.

The Edify loader is pre-configured to use the following elements to create the identifiers.

Please note that the above defaults can be configured to pick up identifiers from other elements in the XML as long as the identifier values satisfy the above constraints.

## **Conference paper wrapper tag**

The wrapper tag for the XML must be 

### Article type attribute

The article-type attribute is used for display of the type on the article homepage and as a filter within the site search. By default Ingenta Edify is set up with the article types listed within the [JATS documentation](https://jats.nlm.nih.gov/publishing/tag-library/1.1/attribute/article-type.html). Additional types can be configured if required. The article types are set up with default display names. The display names can be edited by the publisher administrator using the tools within the site. 

**Example**

`<article article-type="research-article">`

The value of article type is case-sensitive and must not contain spaces. Hyphens are permitted in the value of the attribute.

The value of the article-type attribute is used to indicate the article type in the website as per the screenshot below. 

![](https://confluence.ingenta.com/confluence/download/attachments/187369857/image2019-10-13_10-59-0.png?version=1&modificationDate=1637764765564&api=v2)

The following elements are permitted for serial-level metadata. Please note that the serial-level metadata must be consistent within the XMLs for all papers within that proceeding

Please note that the elements will be deemed as mandatory if the agreed identifier structure for content URLs requires that element.

**The XPATHs given below are relative to** 

`
/article/front/journal-meta/
`

Please ensure that XMLs across all papers for a proceeding provide the same values for all serial level properties e.g. the ISSNs provided should be the same across all XMLs in a proceeding.

Provide at least the following proceeding metadata whenever applicable.  

**The XPATHs given below are relative to** 

`
/article/front/article-meta/
`

### Required proceeding metadata

### Optional proceeding metadata

Please ensure that XMLs across all papers for a proceeding provide the same values for all proceeding-level properties e.g. the pub-date values provided should be the same across all XMLs in a proceeding.

Provide at least the following paper metadata whenever applicable.  

**The XPATHs given below are relative to** 

`
/article/front/article-meta/
`

### Required Paper metadata

### Optional Paper metadata

## Specifying the language of a paper

Edify uses the following logic to work out the language of a paper. This value of language is used for displaying the language name in the site, filtering by that language in search results etc.

-   Where **`/article/front/article-meta/title-group/article-title`** has an **`@xml:lang`** attribute, the value of the attribute is used as the language
-   Where the **`article`** element has an **`@xml:lang`** attribute, the value of that attribute is used as the language.
-   Where both the above are not provided, the language is defaulted to "en" (English).

In all cases, the value of the **`@xml:lang`** attribute must follow the [guidelines for language codes](https://confluence.ingenta.com/confluence/display/AUP/Conference+Proceedings+XML+Guidelines#ConferenceProceedingsXMLGuidelines-language-codes). 

## **Publication dates**

**The XPATHs given below are relative to** 

/article/front/article-meta/

The publication date for a proceeding must be provided. An empty or missing pub-date must be avoided.

The values of day and month in pub-date default to 1 if they are not provided. It is highly recommended to specify a month.

## **Contributor Information**

The contributor name information must be provided within the `<name>` set of elements within the `<contrib>` element. Each contributor must be provided in a contrib  element. Only one `<name>` set of elements must be provided within a `<contrib>` element.

`<contrib>` elements with the `contrib-type` attribute set to anything other than `author` will be ignored. 

The following elements are supported within the `<contrib>` element.

Example contributor markup is as follows

```xml
<contrib-group>
    <contrib contrib-type="author">
        <name>
            <surname>John</surname>
            <given-names>Smith</given-names>
            <prefix>Dr</prefix>
            <suffix>Jr</suffix>
        </name>
        <xref ref-type="aff"` `rid="aff1"><sup>1</supp></xref>
    </contrib>
    <aff` `id="aff1"><sup>1</sup>Ingenta, Oxford, OX4` `2HU</aff>
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
        `<contrib-id` `contrib-id-type="orcid"` `authenticated="true"> http://orcid.org/0000-0002-1234-1234</contrib-id>`
        `<name>`
            `<surname>Smith</surname>`
            `<given-names>John</given-names>`
        `</name>`
    `</contrib>`
`</contrib-group>`

## Keywords

You can define keywords for a paper within the XML using the **`kwd`** element. Each keyword must be specified in a separate **`kwd`** element. The **`kwd`** elements are enclosed within a **`kwd-group`** element. For example

`<article>`
    `<front>`
        `...`
        `<article-meta>`
            `...`
            `<kwd-group>`
                `<kwd>science</kwd>`
                `<kwd>physics</kwd>`
                `...`
            `</kwd-group>`

## Copyright information

Edify extracts copyright information from the XML using the following logic:

1.  It first looks for an element **`/article/front/article-meta/permissions/license[@license-type='licensed-commercial-use']`** and uses the value of that element if it exists.
2.  If 1 is not true **and** if the XML contains an **`/article/front/article-meta/permissions/copyright-statement`** element
    1.  If **`/article/front/article-meta/permissions/license[@license-type='open']`** **or** /**`article/front/article-meta/permissions/license[@license-type='free']`** exists, then the value of the **`copyright-statement`** element is concatenated with the value of the relevant tag.
    2.  If 2a is not true, then the value of **`copyright-statement`** is used.
3.  If 1 and 2 are not true **and** if the XML contains an **`/article/front/article-meta/permissions/copyright-holder element`** **and `/article/front/article-meta/permissions/copyright-year`**, then the value of **`copyright-year`** concatenated with **`copyright-holder`** is used.
4.  If 1, 2 and 3 are not true **and** if the XML contains the **`/article/front/article-meta/permissions/copyright-holder`** element, the value of **`copyright-holder`** is used. 

## Permissions

Please refer to [Content Licensing XML Guidelines](https://confluence.ingenta.com/confluence/display/AUP/Content+Licensing+XML+Guidelines)

## Paper publication history

The following paper publication history dates are supported

Please note that for a date type, only one date must be provided.

## Tables, Figures

Please refer to [Media]()

## Paper titles

Paer titles must be specified using the **`article-title`** element.

## Abstract

Please use the **`article/front/article-meta/abstract`** element to specify the original abstract of the paper. 

Please note that if **`xref`** tags are included in the **`abstract`** element to link to figures, tables or references in the body of the paper, the links will anchor to the corresponding figure, table or reference only within the full text tab and not within the abstract tab.  

At present, Edify does not support the tagging of figures, tables, media objects, supplementary material, references or related content within the abstract tag.

Within an abstract, you may include titled sections using **`sec`** nodes and the **`title`** element in each **`sec`**.

## Linking the PDF to the paper

-   Please use the `**article/front/article-meta/self-uri**` element to link the paper to the corresponding PDF.
-   The **`self-uri`** tag must be supplied with an `**xlink:href**` attribute where the value of the attribute exactly matches the name of the PDF file supplied, along with the file name extension.
-   The **`self-uri`** element must be provided with an attribute **`@content-type`** and the value of the attribute must be specified as pdf e.g. **`<self-uri content-type="pdf" xlink:href="ajsr.2020.3.pdf" xmlns:xlink="http://www.w3.org/1999/xlink"/>`**
-   Please note that only one PDF can be supplied per paper. 
-   Please do not prepend the file name with a directory path. 

## Displaying equations

Equations can be displayed in two ways - as images or through the use of MathML, a W3C standard.

### Equations using MathML

Mathematical equations can be provided using MathML contained in the **`mml:math`** element. This is relevant for content supplied in NLM, JATS and BITS formats.

MathML elements must use “**`mml`**” as the namespace prefix to validate to the NLM/JATS/BITS DTDs.

Edify uses the [MathJax](https://www.mathjax.org/) library to render the MathML content.

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

`<ref` `id="bib12">`
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

## Language codes

Wherever language codes are required to be supplied in XML for the value of the **`@xml:lang`** attribute, they must be specified as as the two letter ISO code for the language. The code must be in lower case. For example **`<trans-abstract xml:lang="fr">...`**


## Content loading for Conference Proceedings and papers

Content for a proceeding must be sent in a single zip file to the specified SFTP location. The name of the zip and files within the zip must consist of alphanumeric characters and must not contain spaces or special characters. All papers supplied within a zip file must belong to the same proceeding. Names of all files supplied within a zip file must be unique, even if they are supplied within folders in the zip file. The names of image files and PDF files supplied within the XML must exactly match the file names of the supplied files within the zip. The file names within the XML must not contain folder names and must be provided with the extensions. 

While setting up SFTP access through Filezilla, please make sure to set the port number as 22 (the standard SFTP port).

Environment	SFTP Host	Username	Password	Input directory
QA	aup-sftp.ingenta.com	aupqa-sftp	7HC0.vAstSg?	autoprocessing/aup/conference-papers-live/input
LIVE	aup-sftp.ingenta.com	aup-sftp	mdho,+%m13TB	autoprocessing/aup/conference-papers-live/input


## Creation of a new Conference Proceeding Series

Conference Proceeding Series i.e. the containers for Conference Proceedings are created and managed manually in the site.

For managing these series, please log in as super-administrators or as administrators with content creation privileges.

## Creation of a new series

A new series must be created before you start supplying proceedings under that series.

Please access the homepage of the publisher e.g. https://qa.aup-online.com/content/aup in the QA environment. When you hover over the left side "wrench" icon, it will expand to show you content management links in a tools menu. Please click on the "Create new Conference Proceedings Serial" link highlighted in the screenshot below.

This will open a popup window with a form for creating a new series - screenshot below. Key notes regarding filling up the form are provided below the screenshot.

In the ID field, please enter proceedings/<e-ISSN of the series> e.g. proceedings/03007995

The value of the e-ISSN must exactly match the value provided in <issn pub-type="electronic"> element in the proceedings XMLs

An example of the value that must be provided in the field is in the screenshot below.

Another key value is the RDF Type of the Proceeding Series. This is a dropdown field. For this field, please select the Conference Proceedings Serial value. Example screenshot below.

After filling in the above and all the mandatory values, please click on the "Create" button to create the series.

## Editing an existing series

For changing metadata for an existing series, please navigate to the homepage of the series and hover over the "wrench" icon on the left. It will expand to show you links to manage the series. Click on the "Edit Conference Proceedings Serial" link highlighted in the screenshot below. This will open a popup form with metadata for that series.



