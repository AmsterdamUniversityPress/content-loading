# Usage

There are several ways to measure usage of online products/publications, e.g.

- statistics collected by Google Analytics or similar services
- altmetrics collected by Altmetric or similar services
- COUNTER

This page deals with COUNTER. COUNTER is a standardized usage measurement method required by academic libraries and other users. This means publishers _must_ provide COUNTER stats. COUNTER stats play a large role in measuring a publication's impact, and in the decision to subscribe. 

## COUNTER
AUP Online supports COUNTER. At the time of writing (2024-02-20), the implementation is as per the COUNTER 5 specifications provided at the [COUNTER site](https://www.projectcounter.org/code-of-practice-five-zero-two/). 

## magazines
In COUNTER terms, magazines are considered books. See below.

## books
AUP ONline supports _Book reports_ for COUNTER 5. They are visible under _Title reports_ and will show usage when authenticated institutional users access De Dikke Blauwe.

Usage information in general for downloads of De Dikke Blauwe can be obtained through publisher usage statistics. For example, if I look at https://www.aup-online.com/admin/reporting/usage/prepare.action?reportName=ftd_per_title_per_month for October to December, then I can see usage for the individual volumes of the magazine. Similarly you can see abstract views too.

For the magazine content, if users are authenticated as an institution when they access the full text then the usage will be recorded against their institutional account and will be visible in their COUNTER stats. For example, one of the magazine issues has usage from "Amsterdam University Press" (registration number 33264576 ) and HvA Hogeschool van Amsterdam (registration number cid-2865) have had downloads counted against their accounts - see the screenshots below from their TR_B1 COUNTER 5 reports.

 
The current subscribers report https://www.aup-online.com/admin/reporting/usage/prepare.action?reportName=current_subscribers available from the publisher statistics listing page should enable you to see a list of current subscribers per title.


## explanation
Ingenta's Confluence contains innformation on [View and manage COUNTER 5 Reports for Organization](https://confluence.ingenta.com/confluence/display/AUP/User+Management+Tool#UserManagementTool-11.ViewandmanageCOUNTER5ReportsforOrganization), as well as the previous COUNTER version, [4](https://confluence.ingenta.com/confluence/display/AUP/User+Management+Tool#UserManagementTool-11.ViewandmanageCOUNTER4ReportsforOrganization).

What counts as a download in publisher statistics? A click to get the full text whether PDF, HTML, EPUB or the e-reader view of an item counts as a download. 

What counts as an abstract view in publisher statistics? Accessing the homepage of a content item counts as an abstract view for publisher statistics.

## get COUNTER reports
An Ingenta's Confluence [page](https://confluence.ingenta.com/confluence/display/AUP/User+Management+Tool#UserManagementTool-11.ViewandmanageCOUNTER5ReportsforOrganization) explains how you can download COUNTER 5 Standard and Master reports for any institution when you are logged in as the site administrator.

Another [page]([https://confluence.ingenta.com/confluence/display/AUP/User+Management+Tool#UserManagementTool-11.ViewandmanageCOUNTER5ReportsforOrganization](https://confluence.ingenta.com/confluence/display/AUP/Institutional+Administrators+FAQs)) explains how institutional administrators can access their own COUNTER reports.

## Abstract views
You can see abstract views for content through the following reports in the publisher statistics list.

## SUSHI
https://www.aup-online.com/help/sushi is a public-facing help page which describes COUNTER 5 SUSHI setup.

## COUNTER 5.1
Ingenta is currently reviewing version 5.1 which becomes effective from January 2025.

## how to

1. login as site admin
2. go to the page for Institution usage (`/counterstats/requestform`). (There are three other pages with reports - Site uages, Site content, and Sales - but they do not concern us here).
3. On that page you  will find five report options for journals, four for books, and one for the platform as a whole.

### bookjs
- title requests
- section requests (this includes chapters)
- access denied
- total searches

