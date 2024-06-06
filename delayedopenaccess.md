# Delayed Open Access

Delayed Open Access (DOA) is a business model where a publication "flips" to Open Access after a period of subscribed-to access. This embargo period gives the publisher an opportunity to recoup costs.

## OA or not?
Current AUP practice is to open all back list content after 24 months. Is this DOA or simply free access? Certainly it is referred to as DOA. Some argue that DOA is not OA at all because OA should be immediate. Hence delayed open access journals are not included in the Directory of Open Access Journals ([DOAJ](https://doaj.org/)).

## AUP Online
AUP Online does not functionally support DOA at the moment. This means licenses must be changed manually after the embargo period, and content reloaded. DOES THAT ACTUALLY HAPPEN?

## tagging
The XML of DOA content requires two licenses, and at least one has to have a start date (= the end of the embargo period). This is an example from the JATS site. The essential thing is the use of the `<ali:license_ref>` element.

```xml
<permissions>
 <license>
  <ali:license_ref xmlns:ali="http://www.niso.org/schemas/ali/1.0/" start_date="2014-02-03">
   http://www.psychoceramics.org/license_v1.html</ali:license_ref>
  <ali:license_ref xmlns:ali="http://www.niso.org/schemas/ali/1.0/" start_date="2015-02-03">
   http://creativecommons.org/licenses/by/3.0/</ali:license_ref>
 </license>
</permissions>
```
 

And this is how Crius tagged it experimentally (recent and older example).

```xml
<permissions>
    ...
    <license license-type="free"><ali:license_ref start_date="2024-05-15"></ali:license_ref></license>
</permissions>
```

```xml
<permissions>
    ....
    <license><ali:license_ref content-type="open-access" start_date="2023-07-05" xmlns:ali="http://www.niso.org/schemas/ali/1.0/">https://creativecommons.org/licenses/by-nc-nd/4.0/</ali:license_ref></license>
</permissions>
```

These examples are missing the references to the subscribed-to license. This raises the question where that license may be found online. 

A more comprehensive tagging compliant with the NISO/JATS approach would be

```xml
<permissions>
 <license>
  <license-p>This content is under a proprietary license until 2026-05-01 when it will be Open Access</license-p>
  <ali:license_ref xmlns:ali="http://www.niso.org/schemas/ali/1.0/" start_date="2024-05-01">
   https://www.aup.nl/en/publish/rights-and-permissions</ali:license_ref>
  <ali:license_ref xmlns:ali="http://www.niso.org/schemas/ali/1.0/" start_date="2026-05-01">
   xmlns:ali="http://www.niso.org/schemas/ali/1.0/">https://creativecommons.org/licenses/by-nc-nd/4.0/</ali:license_ref>
 </license>
</permissions>

```

 
<!--
<license license-type="" 
    <license-p 
        <graphic 
            CDATA 
            <ext-link 

 

JATS zegt: 

<license @license-type @xlink-href (link naar CC) 
    <license-p> 

Wat maakt dit uit? 
-->

## see also
- [Delayed open-access journal in Wikipedia](https://en.wikipedia.org/wiki/Delayed_open-access_journal)
- [JATS License Information](https://jats.nlm.nih.gov/archiving/tag-library/1.3/element/license.html)
- [JATS License Reference (NISO and Access License Indicators)](https://jats.nlm.nih.gov/archiving/tag-library/1.3/element/ali-license_ref.html)
- [NISO Access License and Indicators](https://groups.niso.org/higherlogic/ws/public/download/14226/rp-22-2015_ALI.pdf)
