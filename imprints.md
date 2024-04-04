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

<!-- It's all HTML so you can do `<strong>Hanu</strong> <span style="color: rgb(209, 72, 65);">Publisher 1</span>` -->

I uploaded an XML file with the test publisher this morning... it loaded correctly but I don't see it on the site... Also, the test publusher is not yet added to the search facet... check again tomorrow....

Why is there no "publisher" option when manually editing a publication's metadata on the platform? Because you can't change the publisher after publication?

## see also

- the relevant change request is [CR009](https://confluence.ingenta.com/confluence/display/AUP/AUP+CR009+-+Add+imprints+functionality)
- the CR was delivered in the [2023 Q2 release](https://confluence.ingenta.com/confluence/display/AUP/AUP+Q2+2023+Release+Notes)

> `https://qa.aup-online.com/content/publishers` shows a list of publishers within the site.
> New publishers can be created from this page.
> While creating a new journal, please go to the homepage of the corresponding publisher and create the journal from there so that the journal gets associated with that publisher. 
> https://qa.aup-online.com/content/content/test_pub1 is an example of a publisher and the journal Scheepshistorie  has been associated with it. The publisher name is displayed on the journal homepage and article homepage for example
> The journals listing page shows a publisher facet 

