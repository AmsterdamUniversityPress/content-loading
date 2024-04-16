# License

## Access types
Access types determine the conditions under which users can access and use the content. Subscribed means users need to be logged-in. OA and Free means users need not be logged-in. 

### AUP business models
AUP business models have three types of access

1. Subscribed (customer pays)
2. Open Access (author/institution pays)
3. Free (AUP pays)

### AUP Online
The platform supports four types of access

1. S = Titles Subscribed To
2. OA = Open Access Content = content will be shown to users as Open Access on the platform.
3. T = Free Trial Content = content will be shown to users as indefinitely Free on the platform.
4. F = Free Content

I have no idea how 3 is done.

## XML
The access type is included in the XML - both JATS and BITS - through `<license>` and its `@license-type` attribute in  the `<permissions>` element.

### Subscribed to
Omit `<license>` from `<permissions>`.

Example from `10.5117.ANTW2023.1.007.LEEZ`:

```xml
<permissions>
<copyright-statement>&#x00a9; Michiel Leezenberg</copyright-statement>
<copyright-year>2023</copyright-year>
<copyright-holder>Michiel Leezenberg</copyright-holder>
</permissions>
```

### Free content
Use "free" or "FREE" as the value of the @license-type attribute.

Example from `10.5117.ANTW2023.1.001.DORR`:

```xml
<permissions>
<copyright-statement>&#x00a9; Steven Dorrestijn &#x0026; Herman Westerink</copyright-statement>
<copyright-year>2023</copyright-year>
<copyright-holder>Steven Dorrestijn &#x0026; Herman Westerink</copyright-holder>
<license license-type="free"><license-p></license-p></license>
</permissions>
```

### Open Access 
Use "open-access" or "OPEN-ACCESS" as the value of the @license-type attribute. Also, add a link to the appropriate _Creative Commons_ license using the @xlink:href attribute.

Example from `10.5117.QUE2022.1.001.KLEI`:

```xml
<permissions>
<copyright-statement>&#x00a9; Ru Klein</copyright-statement>
<copyright-year>2022</copyright-year>
<copyright-holder>Ru Klein</copyright-holder>
<license license-type="open-access">
<license-p>This is an open access article distributed under the terms of the CC BY-NC 4.0 license. <ext-link ext-link-type="uri" xlink:href="http://creativecommons.org/licenses/by/4.0/">http://creativecommons.org/licenses/by/4.0</ext-link></license-p>
</license>
</permissions>
```

This is displayed as follows on the platform:
```
© Ru Klein. This is an open access article distributed under the terms of the CC BY-NC 4.0 license. http://creativecommons.org/licenses/by/4.0
```

<!-- in reality, this works differently. the article journal actually reads `<license license-type="open">` but when I tried that with a book it failed -->


## free trial access
How to setp up a free trial on Edify?

### Introduction

This document outlines the process of setting up free trials in Ingenta Edify through the site administration tools. Free Trials can be set up at multiple levels e.g., for individual issues or articles, or at journal level for all issues under the journal etc. The steps below refer to setting up a free trial for an article, but they can be used at other levels too.

### Setting up a free trial

- Go to site.
- Navigate to an Article page e.g. https://qa.aup-online.com/content/journals/10.5117/TvAR2023.11.001.KORT
- Login as the site administrator.
- Hover over the 'wrench' icon button on left-hand side of the page.
- Click on "Manage prices for this article". This will open a popup window which will show existing free, Open Access, purchase and free trial licenses set up for that content item.
- Click on "Create new pricing & access rule". This will open a form with a drop down of pricing models as shown in the screenshot below.
- Select Pricing Model > Free Trial. A form will be displayed.
- Enter the Trial validity i.e. From and To Date. 
- Select the checkbox for 'Eligible user.'
  - Select the radio button "All users" for a free trial available to everyone.
  - Select the radio button "Selected users" to search for and select the users who should have access to the free trial. 
- Fill in the Trial Name field. This is the display name for the trial.
- Navigate to field "Trial duration."
  - Select the first radio button for add duration for days.
  - Select the second radio button to set the trial duration to be the same as the validity range defined in step 9.
  - Select the third radio button to set the trial duration to be perpetual. 
- Navigate to Applicability field. You can use this field to specify the types of users who can sign up for trials.
  - Select the first checkbox to allow only institutions to sign up for the trial.   
  - Select the second checkbox to allow only registered personal users to sign up for the trial.   
  - Select the third checkbox to enable all users including guest users to sign up for the trial. Please note that this checkbox will be clickable only after selecting one of above checkboxes.
- Select 'Requires approval' checkbox to set the free trial to be moderated i.e., to become active only after you approve it. Leaving the box unchecked means that users can start the trial as soon as they sign up for it without needing it to be approved.
- Select 'Notification' checkbox to receive notifications of trials.
- Enter Notification Email address to get an email notification when a free trial is started on a content. The Price Status box defaults to 'active' which means the trial becomes active as soon as it is saved. If you want to set up the trial in advance but do not want to make it active yet, then you can uncheck the box. To make the trial active later, you can edit the trial, check the box and save the changes.
- Click on Save button.
- Click on Close button.

The option to sign up for a free trial will be visible on the homepage of the relevant content item(s). As an example, a link to sign up trial set up for an issue will be displayed on the homepage of the issue. Please see the screenshot below for an example of the trial sign-up link on an article page.

### the other elements in `<permissions>`
These elements are NOT nested and NOT (?) mandatory.

1. `<copyright-statement>`
2. `<copyright-year>`
3. `<copyright-holder>`

The copyright statement is displayed below the abstract (or one-page PDF if there is no abstract) on the article or chapter page. Copyright year and copyright holder are NOT displayed. Make sure to include that information in the copyright statement.

## delayed open access
Is this a fourth kind of license? It certainly introduces a new tag:

```xml

<permissions>
<copyright-statement>&#x00a9; Maria Vlaar</copyright-statement>
<copyright-year>2023</copyright-year>
<copyright-holder>Maria Vlaar</copyright-holder>
    <license><ali:license_ref content-type="open-access" start_date="2023-07-05" xmlns:ali="http://www.niso.org/schemas/ali/1.0/">https://creativecommons.org/licenses/by-nc-nd/4.0/</ali:license_ref></license>
</permissions>

```

The idea is to make the content publicly accessible after a certain period. The start date is in the XML. The XML does _not_ say what license type is applicable before that time.

- [unhelpful JIRA ticket](https://jira.ingenta.com/jira/servicedesk/customer/portal/5/IEH-3693)
- [AUP-CR014 - Delayed Open Access](https://confluence.ingenta.com/confluence/display/AUP/AUP-CR014+-+Delayed+Open+Access)


## JATS/BITS

JATS has several elements that deal with the usage, permissions, and licensing. Some of these elements are taken from the NISO Access and License Indicators (ALI) 2015 Recommended Practice specification. The other element is JATS-specific and predates the NISO recommendation:

- `<ali:free_to_read>` — This NISO ALI element is a simple flag whose presence indicates that the document is free-to-read, without making statements about any additional reuse rights or restrictions. Date attributes can specify when the document is free to be read.
- `<ali:license_ref>` — This NISO ALI element points to a public license or waiver. By “public”, NISO means that the offer is generally and not privately offered. Such a license may be either human or machine-readable text that explains the terms of use or reuse for the content.
- `<license>` — A JATS-specific element whose content describes a set of conditions under which the content may be used, accessed, and distributed. This element was provided to hold the license text. The 2015 NISO ALI recommendation is to store in the XML document a URI that points to the license instead of the full license text. For users who adopt the NISO ALI recommendation, the `<license>` element could be used to hold a short representation of the license, a sentence or two to be used for display. Alternatively, a publisher could choose not to implement NISO ALI and to put the text of the license in `<license>`.
  The <license> element takes the `@xlink:href` attribute to point to the text of the license. However, the new NISO ALI element `<ali:license_ref>` performs the same pointing function. JATS best practice is to omit the `@xlink:href` attribute from `<license>` if a NISO ALI `<ali:license_ref>` is used.

This text seems to suggest `<ali:license_ref>` is the preferred tag for _all_ our license, in which case we would need to retag and reupload all content...
