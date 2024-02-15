# Imprints

This is about managing imprints on AUP Online. On the platform, the term **publishers** is used.

## how to add a new publisher?
This is on QA:

1. log-in as site admin
2. go to `https://qa.aup-online.com/content/publishers`
3. click on the edit menu on the left-hand side (wrench symbol) and select `Create new Publisher`
4. Fill in the desired fields in the pop-up menu and click on `Create` in the bottom right corner.

## how to add a publisher to a publication?


It is _not_ possible to "change" a product's publisher after it has been published on AUP Online. This means you have to assign it a publisher at publication time. The only way around this is to ask Ingenta to do it manually. Do this in emergencies only.

1. create a publisher
2. create publications "under" the publisher, manually onsite or via the XML

currently, only books and journals seem to habve the publisher mentioned, but not Conference Proceedings and Conference Proceedings Serial ??

it's all HTML so you can do `<strong>Hanu</strong> <span style="color: rgb(209, 72, 65);">Publisher 1</span>`

I uploaded an XML file with the test publisher this morning... it loaded correctly but I don't see it on the site... also, the test publiusher is not yet added to the search facet... check again tomorrow....



Why is there no "publisher" option when manually editing a publication's metadata on the platform?

1. XML.... test this...

2. ask Ingenta to do this manually. (Why can't AUP do this  themselves??)
