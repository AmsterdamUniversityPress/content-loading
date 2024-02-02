# Content identifiers


| Item | Specification | XML tag or attribute | AUP sign-off |
| --- | --- | --- | --- | --- |
| 1 | Journal URLs | Suggested: `/content/journals/<issn>for example /content/journals/09215077` This can be the print ISSN if provided in the XML or the electronic ISSN if not. The other option is to use the publisher-id specified in the XML for example "in" or "tvgesch" for example /content/journals/in. This relies on the typesetter providing the ID consistently in the XML. | issn with pub-type set to "ppub" or issn with pub-type set to "epub" or journal-id with journal-id-type set to "publisher-id" | Agreed with Irene van Rossum  in the meeting on 07 Apr 2021 to use ISSNs (print first and if not, then electronic) for journal identifiers. |
| 2 | Issue URLs | Suggested: `<Journal URL>/volume/issue` For example `/content/journals/09215077/34/1` can also be a year and not an issue e.g. `/content/journals/09215077/2021` Priya Parvatikar to check if this can be done for one journal and not all journals | Specification for the journal URL as specified in 1 concatenated with "/" and `/article/front/article-meta/volume`and `"/"` and `/article/front/article-meta/issue` | Agreed with Irene van Rossum in the meeting on 07 Apr 2021 to use the suggested issue identifie
- Irene van Rossum could you point us to an existing example where you have a year and not an actual issue number or is it something that might come along in the future?
- Priya Parvatikar This would be for future use for the journal of Computational Communication Research. |
| 3 | Article URL | Suggested `/content/journals/<article-doi>` for example /content/journals/10.5117/go2021.1.001.bren
 | /article/front/article-meta/article-id with pub-id-type set to "doi". | Agreed with Irene van Rossum  in the meeting on 07 Apr 2021 to use the suggested article identifier. |
