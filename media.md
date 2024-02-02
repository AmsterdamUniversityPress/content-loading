# Media

### Graphics

Figures are tagged using the `<fig>` element. They should be placed after the paragraph where they have been first cited and not within the paragraph. If more than one figure is cited within a paragraph they should be placed in the order in which they are cited.

Figures tagged within `<fig>` elements are included in the list of figures within the "Figures and tables" section on the content homepage and also within the full size figure viewer.

The `<fig>` element must be provided with an `@id` attribute which is used to construct a unique identifier for the figure. XMLs where fig elements have been provided without the id attribute will be rejected. 

The figure title is constructed as follows:

-   If the `<label>` element is provided under the `<fig>` element then it is used to construct the figure title.
-   If the `<label>` is not provided the contents of the `<title>` element under the `<caption>` element is used
-   If the `<label>` and `<caption>/<title>` are both not provided the value of the `@xlink:href` attribute of the `<fig>` element is used.
-   If none of the above are present the figure is given a title "Untitled".

The table below lists the mandatory elements under `<fig>`

element | required attributes | notes
----- | ----- | ----
`<graphic>` | `@xlink:href`	| The value of the attribute must be the filename of the graphic file with the file extension. Folder names must not be included in the name. The file name must be unique within the issue or book.

The table below lists optional element under `<fig>`

element | required attributes | notes
----- | ----- | ----
`<label>` | | As mentioned above this is used to construct the title for the figure
`<caption>` | | Used to provide the caption for the  figure
`<copyright>/<copyright-statement>` | | Used to provide copyright text for the figure. If this is not provided, the copyright for the content item (book, article. chapter) is used in the site.
  
Please note that tables supplied within fig tags are not supported within Ingenta Edify.

### Inline graphics

Inline graphics appear within text and are tagged using the inline-graphic element. An `<inline-graphic>` must have an attribute `@xlink:href`, whose value must be the exact file name of the image with the extension and without any folder names. The file name of the image must be unique within the issue or book. 

Tables are tagged using the `<table-wrap>` element.  They should be placed after the paragraph where they have been first cited and not within the paragraph. If more than one table is cited within a paragraph they should be placed in the order in which they are cited.

The `<table-wrap>` element must be provided with an `id` attribute which is used to construct a unique identifier for the table. XMLs where fig elements have been provided without the id attribute will be rejected. 

The `<table-wrap>` element may contain a `<label>` and `<caption>.`

Tables can tagged in two ways

1.  XHTML within the XML – in which case the `<table>` element must be used. Edify supports the XHTML table model within JATS. 
2.  An image for the table – In this case, the `<graphic>` element must be used instead of the `<table>` element. The use of the graphic element for tables is similar to that for figures - A <graphic> element must have an `@xlink:href` attribute whose value must be the exact file name of the image with the extension and without any folder names. The file name must be unique within the issue or book. Each table image must be supplied as a separate file.
