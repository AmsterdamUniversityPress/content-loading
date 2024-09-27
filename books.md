# Books


## platform

The landing page of a successfully uploaded book is:

- `/content/books/[DOI]` e.g., `/content/books/10.5117/9781386367109`

The book will be listed among the other books for browsing, here:

- `/content/books`

Searching by content type `book` ought to return all books:

- `/search?value1=Book&option1=contentType`

Note that this page has other search filters than `/content/books` ....

## landing page

The book landing page has a number of default tabs

- Overview
- Chapters
- References
- Cited By
- Supplements

Overview (URL `\#overview`) and Chapters (URL `\#chapters`) are always filled out. It is not possible to upload a book without chapter information (i.e., without book parts in the XML). The list of chapters acts as a table of contents. 

If a book has no abstract a preview is shown; this is the first page of the PDF. (This is irrespective of access or license).

If there is an abstract, that will be shown, together with keywords and license information (if applicable; if the book is "Subscribed-to" content nothing is shown).

## uploading books onto the FTP

### lower case

The Edify loader expects lower case in the DOIs.

- `<book-part-id book-part-id-type="doi">10.5117/9784955525139_CH01</book-part-id>` = ❌
- `<book-part-id book-part-id-type="doi">10.5117/9784955525139_ch01</book-part-id>` = ✅

(This requirement was dropped after the 2024 Q2 release. Remember, the reference in the XML has to match _exactly_ the file name. In any case, **we continue to use lower case**).

### link to the PDF

Make sure to reference the PDFs from the XML using a self-uri element in `<book-part-meta>`.

- `<self-uri xlink:href="10.5117_9784955525139.pdf" content-type="pdf"/>`

### file names
One file per book. File name is identical to the DOI, but with an underscore instead of a slash. Don't forget the file type extension (e.g., `.pdf`).

- 10.5117_9784955525139.xml = metadata
- 10.5117_9784955525139.pdf = PDF of the book
- 10.5117_9784955525139_cover.jpg = cover image

Currently, AUP doesn't offer book parts, but if it did, the names would be

- 10.5117_9784955525139_fm.pdf = front matter
- 10.5117_9784955525139_ch01.pdf = chapter 1
- 10.5117_9784955525139_ch02.pdf = chapter 2, etc.
- 10.5117_9784955525139_bm.pdf = back matter

### cover
Make sure to add a cover image. Add a link to a `.jpg` file between `<permissions` and `<abstract` in the `<book-meta>`:

- `<self-uri xlink:role="http://pub2web.metastore.ingenta.com/ns/coverImage" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="10.5117_9784955525139_cover.jpg"/>`

### pitfall
Make sure all IDs are unique. This includes the ID in the `<xref>` related to the author's affiliation.

`<xref ref-type="aff" rid="cha1_aff1"><sup>1</sup></xref>`

For chapter 2, this should be `cha2_aff1`, etc.!

### practicalities

- one PDF file with the _content_ for the whole book
- one XML file with the _metadata_ for the whole book. This includes the information per chapter
- don't forget the cover image
- zip the folder. The folder name is, e.g., `10.5117_9784955525139`, and the zip name is `10.5117_9784955525139.zip`
- the "leading" ISBN, as used in the DOI and file names, should be the print ISBN
- add abstracts and keywords where possible

<!-- 
## platform specifics

### book page
A book page on Edify has

- URL, e.g. `https://qa.aup-online.com/content/books/10.5117/9783358449707`
- title
- subtitle
- cover image
- By Book Author First Name Book Author Surname
- Format:
- Publication Date: April 2024
- Publisher: Amsterdam University Press
- Ebook ISBN: 9789048552399
- DOI: https://doi.org/10.5117/9783358449707
- five tabs: Overview, Chapters, References, Cited by, Supplements
- Overview tab has abstract and license / copy right statement

References (and then also Cited by) - are we going to do them? 

How do Supplements work? Figshare

- content editing tool

#### abstract
The abstract section of the book displays the _blurb_. The blurb is stored in Zeno. There are no book abstracts. There are only chapter abstracts

### chapter page
....
-->

## see also

- See the chapter on [BITS](https://amsterdamuniversitypress.github.io/content-loading/bits)

## example
Below is a example of the BITS XML of an Open Access books (not a real one 😊) consisting of only two chapters.

```xml

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//NLM//DTD BITS Book Interchange DTD v2.0 20151225//EN" "BITS-book2.dtd">
<book xmlns:xlink="http://www.w3.org/1999/xlink" book-type="monograph" xml:lang="en">
	<book-meta>
		<book-id book-id-type="doi">10.5117/9786718211792</book-id>
		<book-title-group>
			<book-title>Test Book 20240620-2 OA met PDF heel boek; GEEN hfd pagina's</book-title>
			<subtitle>Test Book 20240620-2 Subtitle Vlaai</subtitle>
		</book-title-group>
		<contrib-group>
			<contrib contrib-type="author">
				<name>
					<surname>This Book Author Surname</surname>
					<given-names>This Book Author First Name</given-names>
				</name>
			</contrib>
		</contrib-group>
		<pub-date publication-format="print">
			<year>2024</year>
			<month>06</month> 
			<day>20</day>
		</pub-date>
		<pub-date publication-format="online">
			<year>2024</year>
			<month>06</month> 
			<day>20</day>
		</pub-date>
		<isbn publication-format="print" content-type="hardcover">9786718211792</isbn>
		<isbn publication-format="electronic" content-type="pdf">9789048552399</isbn>
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
			<copyright-statement>&#x000a9; Amsterdam University Press B.V., Amsterdam 2024</copyright-statement>
			<copyright-year>2024</copyright-year>
			<copyright-holder>Amsterdam University Press B.V.</copyright-holder>
			<license license-type="open-access">
			<license-p>This is an open access article distributed under the terms of the CC BY-NC 4.0 license. <ext-link ext-link-type="uri" xlink:href="http://creativecommons.org/licenses/by/4.0/">http://creativecommons.org/licenses/by/4.0</ext-link></license-p>
			</license>
			</permissions>
		<!-- heel boek -->
		<self-uri xlink:href="10.5117_9786718211792.pdf" content-type="pdf"/>
		<self-uri xlink:role="http://pub2web.metastore.ingenta.com/ns/coverImage" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="10.5117_9786718211792_cover.jpg"/>
		<abstract xml:lang="en">
			<p>Test Book 20240620-2 Abstract Abstract Abstract Abstract</p>
		</abstract>
		<kwd-group xml:lang="en">
			<kwd>Test Book 20240620-2 keyword1</kwd>
			<kwd>Test Book 20240620-2 keyword2</kwd>
			<kwd>Test Book 20240620-2 keyword3</kwd>
		</kwd-group>
	</book-meta> 
	<book-body>
		<book-part book-part-type="chapter">
			<book-part-meta>
				<book-part-id book-part-id-type="doi">10.5117/9781386367109_ch01</book-part-id>
				<title-group>
					<title>Chapter Title 1</title>
					<subtitle>Chapter Subtitle 1</subtitle>
				</title-group>
				<contrib-group>
					<contrib contrib-type="author">
						<name>
							<surname>Chapter 1 Author Surname</surname>
							<given-names>Chapter 1 Author First Name</given-names>
						</name>
						<bio content-type="about-the-author"><p>The author wrote this book.</p></bio>
						<xref ref-type="aff" rid="cha1_aff1"><sup>1</sup></xref>
					</contrib>
				</contrib-group>
				<aff id="cha1_aff1">
					<label>1</label>
					<institution>Some University</institution>
				</aff>
				<pub-date publication-format="print">
					<year>2024</year>
					<month>06</month>
					<day>19</day>
				</pub-date>
				<fpage>1</fpage>
				<lpage>100</lpage>
				<abstract xml:lang="en"><p>Chapter 1 Abstract</p></abstract>
				<kwd-group xml:lang="en">
					<kwd>chapter 1 keyword1</kwd>
					<kwd>chapter 1 keyword2</kwd>
					<kwd>chapter 1 keyword3</kwd>
				</kwd-group>
			</book-part-meta>
		</book-part>
		<book-part book-part-type="chapter">
			<book-part-meta>
				<book-part-id book-part-id-type="doi">10.5117/9781386367109_ch02</book-part-id>
				<title-group>
					<title>Chapter 2 Title</title>
					<subtitle>Chapter 2 Subtitle</subtitle>
				</title-group>
				<contrib-group>
					<contrib contrib-type="author">
						<name>
							<surname>Chapter 2 Author Surname</surname>
							<given-names>Chapter 2 Author First Name</given-names>
						</name>
						<bio content-type="about-the-author"><p>The author wrote this book.</p></bio>
						<xref ref-type="aff" rid="cha2_aff1"><sup>1</sup></xref>
					</contrib>
				</contrib-group>
				<aff id="cha2_aff1">
					<label>1</label>
					<institution>Some University</institution>
				</aff>
				<pub-date publication-format="print">
					<year>2024</year>
					<month>06</month>
					<day>20</day>
				</pub-date>
				<fpage>101</fpage>
				<lpage>200</lpage>
				<abstract xml:lang="en"><p>Chapter 2 Abstract</p></abstract>
				<kwd-group xml:lang="en">
					<kwd>chapter 2 keyword1</kwd>
					<kwd>chapter 2 keyword2</kwd>
					<kwd>chapter 2 keyword3</kwd>
				</kwd-group>
			</book-part-meta>
		</book-part>
	</book-body>
</book>

```
