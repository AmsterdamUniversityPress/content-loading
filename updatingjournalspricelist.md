# updating journals price list

The journals price list is a PDF that needs to be updated annually. Here is how.

Note: this only works for the live site. (Because there is no appropriate folder on the FTP for QA and we cannot create one).

## 1. edit web page

1. Go to the [web page in question](https://qa.aup-online.com/how-to-subscribe) and log in as site admin.
2. Click on the edit symbol below the text on the page. (This symbol is easily overlooked so look closely).
3. Edit the text. Do this in HTML so you know what you are doing.
4. Change the URL, for example from `https://www.aup-online.com/upload/GeneralDocs/2023AUPJournalsPriceListTEST.pdf` to `https://www.aup-online.com/upload/GeneralDocs/2024AUPJournalsPriceListTEST.pdf`. Make sure the URL corresponds to the file name!
5. Save and publish.

## 2. upload document

1. Go to the live site sFTP and login as AUP (not as typesetter)
2. Upload the document into the `GeneralDocs` folder in the `upload` folder. Presto!

