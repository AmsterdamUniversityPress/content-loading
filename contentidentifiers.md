# Content identifiers


Item | Specification | XML tag or attribute | Example
----- | ----- | ----- | -----
journal URL | based on P ISSN or (secundarily) E ISSN) | `<issn pub-type="ppub">0929-8592</issn>` or `<issn pub-type="epub">2667-1689</issn>` | `https://www.aup-online.com/content/journals/09298592`
journal publisher ID | abbreviated title | `<journal-id>`  | `<journal-id journal-id-type="publisher-id">QUE</journal-id>`
issue URL | Journal URL/volume/issue | n/a | `https://www.aup-online.com/content/journals/09298592/29/1`
article URL | based on article DOI  | n/a | `https://www.aup-online.com/content/journals/10.5117/QUE2022.1.001.KLEI`
article DOI | DOI | `<article-id>` | `<article-id pub-id-type="doi">10.5117/QUE2022.1.001.KLEI</article-id>`
article publisher ID | this is the  article ID  | `<article-id>` | `<article-id pub-id-type="publisher-id">QUE2022.1.001.KLEI</article-id>`

Note that currently no identfiers are used for authors (like ORCID) or insitutitions (that authors may be affiliated with) (like ROR).


<!-- 
| | Item | Specification | XML tag or attribute | AUP sign-off |
| --- | --- | --- | --- | --- |
| 1 | Journal URLs | Suggested: `/content/journals/<issn>for example /content/journals/09215077` This can be the print ISSN if provided in the XML or the electronic ISSN if not. The other option is to use the publisher-id specified in the XML for example "in" or "tvgesch" for example /content/journals/in. This relies on the typesetter providing the ID consistently in the XML. | issn with pub-type set to "ppub" or issn with pub-type set to "epub" or journal-id with journal-id-type set to "publisher-id" | Agreed with Irene van Rossum  in the meeting on 07 Apr 2021 to use ISSNs (print first and if not, then electronic) for journal identifiers. |
| 2 | Issue URLs | Suggested: `<Journal URL>/volume/issue` For example `/content/journals/09215077/34/1` can also be a year and not an issue e.g. `/content/journals/09215077/2021` Priya Parvatikar to check if this can be done for one journal and not all journals | Specification for the journal URL as specified in 1 concatenated with "/" and `/article/front/article-meta/volume`and `"/"` and `/article/front/article-meta/issue` | Agreed with Irene van Rossum in the meeting on 07 Apr 2021 to use the suggested issue identifie
- Irene van Rossum could you point us to an existing example where you have a year and not an actual issue number or is it something that might come along in the future?
- Priya Parvatikar This would be for future use for the journal of Computational Communication Research. |
| 3 | Article URL | Suggested `/content/journals/<article-doi>` for example /content/journals/10.5117/go2021.1.001.bren
 | /article/front/article-meta/article-id with pub-id-type set to "doi". | Agreed with Irene van Rossum  in the meeting on 07 Apr 2021 to use the suggested article identifier. |
-->
