# Citations and References

First, a terminological distinction:

- **citations** are works credited in the text
- **references** are listed at the end of text to provide the information necessary to identify and retrieve each work cited in the text

This is the terminology used by all major style guides (APA, Chicago, MLA, etc.) although certainly not universal.

## styles

AUP uses the APA style. This means the Author Date System.

## authors

- authors should be encouraged to use reference managers (see below)

### reference managers


## copy editing and typesetting

- typesetters should take the reference list submitted by the author as input.
- Word and Zotero plugin
- separate bibtex file

Last resort is the manual conversion of a references into a **datafied** reference. Under no circumstance should the creation of a stylified reference be allowed. We need _data_ as well as derivative formats.

### JATS, BITS


#### citations
JATS has no dedicated citaton element. NLM recommends using `<xref>` with a `@ref-type` and a target ID that matches that of the `<ref>` (see below). 

NLM's example....

```xml
<body>
  <p>... Although there is considerable descriptive literature on day hospital
   care,<xref ref-type="bibr" rid="B1">1</xref> ...</p>
  ...
 </body>
  
 <back>
  ...
  <ref-list>
   <ref id="B1">
    <label>1</label>
    <element-citation publication-type="book">
     ...
   </ref>
   ...
  </ref-list>
  ...
 </back>
</article>
```

If this is insufficient, consider tagging the author, year, specific part of the source explicitly, like in this example of a parenthetical citation:

```
(Shakespeare, 1623/1995, 1.3.36-37)
```

can be tagged like this

```xml
<xref ref-type="bibr" rid="B1">(<name>Shakespeare</name>, <year>1623/1995</year>, <page-range>1.3.36-37</page-range>)</xref>
```

#### references

`<back>`, `<ref-list>`, `<ref>`.

##### strict

- https://jats.nlm.nih.gov/archiving/tag-library/1.3/element/element-citation.html | element citation

##### not so strict

- https://jats.nlm.nih.gov/archiving/tag-library/1.3/element/mixed-citation.html | mixed citation


### a neutral format

## technical standards

### CSL


### citegen and citeproc


## the website

### what it looks like
a tab on the publication page...


### documentation
The following documentation is from the Ingenta Confluence.

- https://confluence.ingenta.com/confluence/display/AUP/JATS+XML+Guidelines#JATSXMLGuidelines-References | Ingenta Confluence

#### References

References or bibliographic citations must be tagged inside a ref-list element in the back matter.

Each reference must be in a separate ref element. 

Each ref element must be provided with an id attribute which is unique and internally consistent. Best practice is an alphanumeric sequence common to all citations in your document, followed by an incremental number matching the sequential order of citations.

References should be tagged at a granular level in order to support optimum display and matching. Without detailed tagging, Edify will be unable to match the reference against resources such as Crossref and would be unable to generate optimum links to citations in Google Scholar.

To include a publication's DOI, please use the `pub-id element` with an attribute `@pub-id-type="doi"`, for example `<pub-id pub-id-type="doi">10.1234/123456789</pub-id>`.

To include a publication's PubMed ID, please use the pub-id element with an attribute `@pub-id-type="pmid"`, for example `<pub-id pub-id-type="pmid">12344</pub-id>`.

Where the publication's DOI or PubMed ID have been specified, they will be used to automatically construct Crossref and PubMed links for the citation.
Edify supports the provision of a single `ref-list` element within the `back` element. Therefore provision of multiple `ref-list` elements must be avoided.   
The type of citation must be indicated through the `@publication-type` attribute, for example `@publication-type="journal"`. 

The following citation elements are supported within the `back/ref-list/ref` element

`element-citation`

This element must only contain bibliographic reference elements. It should not include any punctuation or spacing. If this element is used, then punctuation and spacing will be added by Edify.

```xml
<ref id="bib13">
    <element-citation publication-type="journal">
        <person-group person-group-type="author">
            <name>
                <surname>Smith</surname>
                <given-names>John</given-names>
            </name>
            <name>
                <surname>Doe</surname>
                <given-names>Jane</given-names>
            </name>
        </person-group>
        <year iso-8601-date="2009">2009</year>
        <article-title>Example article title</article-title>
        <source>Example Journal Title</source>
        <volume>5</volume>
        <issue>2</issue>
        <fpage>10</fpage>
        <lpage>20</lpage>
        <pub-id pub-id-type="doi">10.1371/journal.pcbi.1000392</pub-id>
    </element-citation>
</ref>
```

`mixed-citation`

This element is expected to contain bibliographic reference elements as well as punctuation and spacing. For such self-punctuated references, Edify will display the content of the reference as is and will not attempt to add any punctuation or spacing.

```xml
<ref id="bib12">
    <mixed-citation publication-type="journal">
        <person-group person-group-type="author">
            <string-name>
                <surname>Smith</surname>, <given-names>John</given-names>
            </string-name>
        </person-group>.
        <article-title>Example article title</article-title>.
        <source>Example Journal Title</source>.
        <year>2011</year>
        <volume>8</volume>:
        <fpage>506</fpage>-
        <lpage>515</lpage>.
    </mixed-citation>
</ref>
```

`nlm-citation`

JATS 1.1 has deprecated this element. So Edify strongly recommends the use of element-citation or mixed-citation.


## some other things

### CrossRef

### DOI
