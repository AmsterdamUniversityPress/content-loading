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

## practicalities
- 1 PDF file per chapter
- no PDF file for the whole book
- 1 XML file for the whole book. This includes the information per chapter
- don't forget the cover image
- zip the folder(folder name `10.5117_9784955525139` e.g.)

## see also
See the chapter on BITS.

