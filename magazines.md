# Magazines

Magazines are periodicals for a more general public. On the platform, the content is present in "flipbooks" (Flowpaper functionality). 

Technically, magazines are books on the platform, and this is visible

- in the breadcrumb
- in the URL
- in the filters

However, magazines _are_ a separate product type on the platform and can be filtered using the `MagazineIssue` filter.

## BITS

Because magazines are books, they are encoded in BITS XML. Currently, the BITS files are metadata only.

It can be helpful to add a little more information to the metadata.

- ⭐ Add `<collection-meta>` and fill it with appropriate metadata, e.g. the magazine ISSN.
- ⭐ Add relevant information to the  `<book-meta>`, such as editor, abstract, and especially keywords. (Or include book-parts and display chapters). 

#### example BITS XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//NLM//DTD BITS Book Interchange DTD v2.0 20151225//EN" "BITS-book2.dtd">
<book xmlns:xlink="http://www.w3.org/1999/xlink" book-type="magazine" xml:lang="en">
        <collection-meta>
                <collection-id collection-id-type="publisher-id">DDB</collection-id> <!-- is this used? -->
                <volume-in-collection>
                        <volume-number>2022.124</volume-number>
                        <volume-title>De Dikke Blauwe Volume 124</volume-title>
                </volume-in-collection>
                <!-- I believe this should be added
                <issn pub-type="ppub">2666-4186</issn>
               <issn pub-type="epub">1234-5678</issn> 
               or 
               <issn publication-format="electronic" content-type="periodical">2666-4186</issn>
               <issn publication-format="print" content-type="periodical">1234-5678</issn>
               -->
                <publisher>
                        <publisher-name>Walburg Pers</publisher-name>
                </publisher>
        </collection-meta>
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
        <!-- I believe this has no place here -->
        <!-- it HAS to be here now, or it won't load -->
        <issn publication-format="electronic" content-type="periodical">2666-4186</issn>
        <publisher>
                <publisher-name>Amsterdam University Press</publisher-name>
                <!-- do we need this? -->
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
        <!-- I believe this should be added 
        <kwd-group  xml:lang="en">
            <kwd>Philanthropy</kwd>
            <kwd>Pindakaas</kwd>
            <kwd>Borrelnootjes</kwd>
        </kwd-group> -->
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

