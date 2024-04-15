# Books

## lower case
The Edify loader expects lower case in the DOIs.

- `<book-part-id book-part-id-type="doi">10.5117/9784955525139_CH01</book-part-id>` = ❌
- `<book-part-id book-part-id-type="doi">10.5117/9784955525139_ch01</book-part-id>` = ✅

Apparently, this requirement will be dropped after the 2024 Q1 release.

## link to the PDF
Make sure to reference the PDFs from the XML using a self-uri element in `<book-part-meta>`.

- `<self-uri xlink:href="10.5117_9784955525139_ch01.pdf" content-type="pdf"/>`

## file names
One file per chapter. File name is identical to the DOI but with underscore instead of slash. Don't forget the file type extension (`.pdf` in this case).

- 10.5117_9784955525139_fm.pdf = front matter
- 10.5117_9784955525139_ch01.pdf = chapter 1
- 10.5117_9784955525139_ch02.pdf = chapter 2, etc.
- 10.5117_9784955525139_bm.pdf = back matter
- 10.5117_9784955525139_cover.jpg = cover image

## cover
Make sure to add a cover image! Add a link to a `.jpg` file between `<permissions` and `<abstract` in the `<book-meta>`:

- `<self-uri xlink:role="http://pub2web.metastore.ingenta.com/ns/coverImage" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="10.5117_9784955525139_cover.jpg"/>`

## pitfall
Make sure all IDs are unique. This includes the ID in the `<xref>` related to the author's affiliation.

`<xref ref-type="aff" rid="cha1_aff1"><sup>1</sup></xref>`

For chapter 2, this should be `cha2_aff1`, etc.!

## practicalities
- 1 PDF file per chapter
- no PDF file for the whole book
- 1 XML file for the whole book. This includes the information per chapter
- don't forget the cover image
- zip the folder(folder name `10.5117_9784955525139` e.g.)

## see also
See the chapter on BITS.

## example
Below is a fake example of an Open Access books consisting of only two chapters. A few questions remains:

1. should the ISBN used in the DOI and file name be the ISBN of the e-book?
2. what shoould the value of `isbn@publication-format=""` be?
3. Does edify support full text XML? (i.e. addition of `<body><p>` etc. after `<chapter-meta>`)


```xml

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE book PUBLIC "-//NLM//DTD BITS Book Interchange DTD v2.0 20151225//EN" "BITS-book2.dtd">
<book xmlns:xlink="http://www.w3.org/1999/xlink" book-type="monograph" xml:lang="en">
	<book-meta>
		<book-id book-id-type="doi">10.5117/9784955525139</book-id>
		<book-title-group>
			<book-title>Test Book 20250415-1 Title</book-title>
			<subtitle>Test Book 20250415-1 Subtitle</subtitle>
		</book-title-group>
		<contrib-group>
			<contrib contrib-type="author">
				<name>
					<surname>Book Author Surname</surname>
					<given-names>Book Author First Name</given-names>
				</name>
			</contrib>
		</contrib-group>
		<pub-date publication-format="print">
			<year>2024</year>
			<month>04</month> 
			<day>15</day>
		</pub-date>
		<pub-date publication-format="online">
			<year>2024</year>
			<month>04</month> 
			<day>15</day>
		</pub-date>
		<isbn publication-format="" content-type="hardcover">9784955525139</isbn> 
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
			<license license-type="open-access" xlink:href="http://creativecommons.org/licenses/by-nc-nd/4.0">
				<license-p>This is an open-access article distributed under the terms of the Creative Commons Attribution License, which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.</license-p>
			</license>
		</permissions>
		<self-uri xlink:role="http://pub2web.metastore.ingenta.com/ns/coverImage" xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="10.5117_9784955525139_cover.jpg"/>
		<abstract xml:lang="en">
			<p>Test Book 20250415-1 Abstract</p>
		</abstract>
	</book-meta> 
	<book-body>
		<book-part book-part-type="chapter">
			<book-part-meta>
				<book-part-id book-part-id-type="doi">10.5117/9784955525139_ch01</book-part-id>
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
					<month>04</month>
					<day>15</day>
				</pub-date>
				<fpage>1</fpage>
				<lpage>100</lpage>
				<self-uri xlink:href="10.5117_9784955525139_ch01.pdf" content-type="pdf"/>
				<abstract xml:lang="en"><p>Chapter 1 Abstract</p></abstract>
				<kwd-group xml:lang="en">
					<kwd>keyword1</kwd>
					<kwd>keyword2</kwd>
					<kwd>keyword3</kwd>
				</kwd-group>
			</book-part-meta>
		</book-part>
		<book-part book-part-type="chapter">
			<book-part-meta>
				<book-part-id book-part-id-type="doi">10.5117/9784955525139_ch02</book-part-id>
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
					<month>04</month>
					<day>15</day>
				</pub-date>
				<fpage>101</fpage>
				<lpage>200</lpage>
				<self-uri xlink:href="10.5117_9784955525139_ch02.pdf" content-type="pdf"/>
				<abstract xml:lang="en"><p>Chapter 2 Abstract</p></abstract>
				<kwd-group xml:lang="en">
					<kwd>keyword1</kwd>
					<kwd>keyword2</kwd>
					<kwd>keyword3</kwd>
				</kwd-group>
			</book-part-meta>
		</book-part>
	</book-body>
</book>

```
