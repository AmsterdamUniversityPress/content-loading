# Magazines

Magazines are periodicals for a more general public. On the platform, the content (PDF) is present in "flipbooks" (Flowpaper functionality). 

Technically, magazines are books on the platform, and this is visible

- in the breadcrumb, e.g. `Home > Books > De Dikke Blauwe Volume 2015 003`
- in the URL, e.g. `/content/books/10.5117/DDB2015.003.000`
- in the navigation, e.g. , you can find the magazines under `/content/books`.

Basically, books and magazines cannot be distinguished on the platform. Moreover, the platform has been tweaked to show journals only. 

However, magazines _are_ a separate content type on the platform and can be filtered using the `MagazineIssue` filter. (Although the magazine issues are called "volumes" and are published twice a year). For example:

- `/search?value1=MagazineIssue&option1=contentType`

The magazine issues ("volumes") can be found under

- `/content/books/[DOI]`, e,g, `/content/books/10.5117/DDB2015.003.000`

The magazine as a whole can be found under

- `/content/periodicals/[ISSN]`, e.g. `/content/periodicals/26664186`


## BITS

Because magazines are books, they are encoded in BITS XML. Currently, the BITS files are metadata only.

### enrich the metadata
It can be helpful to add a little more information to the metadata. `<collection-meta>` and `<book-part>` make little sense, but consider

- ⭐ Add relevant information to the  `<book-meta>`, such as editor, abstract, and especially keywords. Also ISBN.

### example BITS XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//NLM//DTD BITS Book Interchange DTD v2.0 20151225//EN" "BITS-book2.dtd">
<book xmlns:xlink="http://www.w3.org/1999/xlink" book-type="magazine" xml:lang="en">
        <book-meta>
        <book-id book-id-type="doi">10.5117/DDB2022.124.000</book-id>
        <book-title-group>
                <book-title>De Dikke Blauwe Volume 124</book-title>
        </book-title-group>
        <contrib-group>
                <contrib contrib-type="editor">
                   <name>
                       <surname>Renzenbrink</surname>
                      <given-names>Karlijn</given-names>
                      <prefix></prefix>
                   </name>
                 <xref ref-type="aff" rid="bid.m.1"/>
                </contrib>
                </contrib-group>
               <aff id="bid.m.1">
                <institution>Renzenbrink PR &amp; Communicatie</institution>, <addr-line>Amsterdam</addr-line>
               </aff>
        <pub-date publication-format="online">
                <year>2023</year>
                <month>05</month>
        </pub-date>
        <issn publication-format="electronic" content-type="periodical">2666-4186</issn>
        <publisher>
                <publisher-name>Amsterdam University Press</publisher-name>
                <publisher-loc>
                        <addr-line>Nieuwe Prinsengracht 89</addr-line>
                        <postal-code>1018 VR</postal-code>
                        <city>Amsterdam</city>
                        <country>Nederland</country>
                </publisher-loc>
        </publisher>
        <permissions>
                <copyright-statement>Copyright &#x00A9; 2022, Amsterdam University Press</copyright-statement>
                <copyright-year>2022</copyright-year>
                <copyright-holder>Amsterdam University Press</copyright-holder>
        </permissions>
        <self-uri xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="DDB2022_124_000.pdf" content-type="pdf" />
</book-meta>
</book>

```


### XML in the interface

#### search results
- "De Dikke Blauwe Volume 124" --> `<book-title>`
- "May 2023" --> `<pub-date publication-format="online">`
- "MagazineIssue" --> ?
- "Karlijn Renzenbrink" --> `<contrib contrib-type="editor">`

#### search results page = volume page
- De Dikke Blauwe Volume 124 --> `<book-title>`
- Cover image Placeholder --> ?
- Editor: Karlijn Renzenbrink --> `<contrib contrib-type="editor">`
- Format: PDF --> ? 
- Publication Date: May 2023 --> `<pub-date publication-format="online">`
- Publisher: Amsterdam University Press --> `<publisher-name>`
- DOI: https://doi.org/10.5117/DDB2022.124.000 --> `<book-id book-id-type="doi">`
- Knoppen "overview" en "Preview this book". Alleen de eerste is ene knop, en die doet niks. De twee is een kopje boven de preview van de PDF. 
- Copyright © 2022, Amsterdam University Press --> `<permissions>`

