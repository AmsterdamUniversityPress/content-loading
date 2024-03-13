# Publication Types

### publication types
- several publication types exist


The site admin can create new:

- Book
- Conference Proceedings
- Journal
- Magazine

and also
- Conference Proceedings Serial
- Periodical


#### RDF Type

publication type | RDF type | remark
----- | ----- | -----
Book | Book, Book Set, Book Set Volume | 
Conference Proceedings | Conference Proceedings | 
Conference Proceedings Serial | Conference Proceedings Serial, Serial | 
Journal | Journal, Serial | 
Magazine | Magazine, Serial | 
Periodical | Periodical, Serial | 

#### filters

filter | remark
----- | -----
Publication date | with from-to by month and year
Publication | shows some (not all) journals
Keyword | 
Content type | the 5 types of individual items, see below
Publisher | 
Article Type | 
Language | 
Access type | 

### Search pages and Content pages
- there are Search pages and Content pages
- Content pages can have filters and A-Z (so are not strictly separate from Search pages)
- Filtering on a content page does not alter the URL. Adding search parameter to a content page's URL (e.g. `https://qa.aup-online.com/content/books?value1=Book&option1=contentType`) does not alter the page

Note that there are other types of pages as well, e.g.

- root pages, like `/banaan`
- admin pages

### Search pages individual items

type | URL | remark
----- | ----- | -----
Conference Papers | `/search?value1=ConferencePaper&option1=contentType` | 
Magazine Issues | `/search?value1=MagazineIssue&option1=contentType` | 
Articles | `//search?value1=Article&option1=contentType` | Note the `//` <!-- This is NOT `/search?value1=article&option1=contentType` -->
Fast Track Articles | `/search?value1=FastTrackArticle&option1=contentType` | 
Chapters | `/search?value1=Chapter&option1=contentType` | 

The overall search for these items is:

- `//search?value1=Article+OR+Chapter+OR+MagazineIssue+OR+ConferencePaper+OR+FastTrackArticle&option1=contentType`

(In spite of the `//` above, it seems the overall search also works with a single `/`.

### Content pages individual items

type | URL | remark
----- | ----- | -----
Conference Papers | `/content/papers/10.5117/978904856222/AHM.2023.004` | 
Magazine Issues | `/content/books/10.5117/DDB2023.2.000` | 
Articles | `/content/journals/10.5117/TRA2022.1.003.COLL` | 
Fast Track Articles | `/content/journals/10.5117/TCW2023.X.002.BIBE` | 
Chapters | `/content/books/10.5117/9786142787672_ch04` | 

### search pages container items

type | URL | remark
----- | ----- | -----
Books | `/search?value1=Book&option1=contentType` |
Journals | `/search?value1=Journal&option1=contentType` | 
Magazines | _no content type_ | 
Series | _no content type_ | 
Proceedings | _no content type_ | 
Collections | _no content type_ | 

The overall search for these items is:

- `/search?value1=Book+OR+Journal&option1=contentType`

### Content pages container items

type | URL | remark
----- | ----- | -----
Books | `/content/books`
Journals | `/content/journals`
Series | `/series` | straight after the root
Proceedings | `/content/proceedings`
Collections | `/content/collections` | with `/content/communicational-studies-nbsp` as individual collection page

There is also `/content/publications` which lumps together all journals and magazines (serials?).

