# resources

## JATS

- [NLM JATS elements](https://jats.nlm.nih.gov/archiving/tag-library/1.3/element/arc-elem-sec-intro.html)
- [JATS Home](https://jats.nlm.nih.gov/index.html)
- create test ISSNs ??? <!-- https://www.issn.org/ and https://portal.issn.org/ not very helpful -->

## BITS

- [NLM BITS elements](https://jats.nlm.nih.gov/extensions/bits/tag-library/2.1/element/bits-elem-sec-intro.html)
- [Random ISBN Generator](https://www.lambdatest.com/free-online-tools/random-isbn-generator) (good site 👍)

## other publishers

- [Brill Public](https://connect.brill.com/display/BP/Brill+Public), specifically the file naming conventions and the XML and PDF instructions
- [Brill gitbook on JATS and BITS](https://brillpublishers.gitlab.io/jats-and-bits/)
- [TandF issue XML](https://jats.taylorandfrancis.com/tfjats/doc/#concept/issue-xml.html) Interestingly, Taylor and Francis created their own JATS variant (you're encouraged to do so) with special tags for journal issues.
- [TandF keywords](https://jats.taylorandfrancis.com/tfjats/doc/#concept/languages-translations.html)

### T&F JATS example:
```xml
<?xml version="1.0" encoding="ISO646-US"?>
<!DOCTYPE tf:issue-manifest 
    PUBLIC "-//TF//DTD JATS (Z39.96) v1.0 Taylor and Francis Journal Content v1.0//EN" 
    "http://cats.informa.com/tfjats/1.0/dtd/tfjats1.dtd">
<tf:issue-manifest xmlns:xlink="http://www.w3.org/1999/xlink"
    xmlns:tf="http://cats.informa.com/tfjats" 
    xmlns="http://jats.nlm.nih.gov" tf:schema-version="1.0">
  <tf:issue-status stage="final">
    <tf:tagger name="VendorName"/>
  </tf:issue-status>
  <journal-meta>
    <journal-id journal-id-type="publisher-id">RGAM</journal-id>
    <journal-id journal-id-type="title-id">rgam20</journal-id>
    <journal-title-group>
      <journal-title>Journal of Global Scholars of Marketing Science</journal-title>
      <journal-subtitle>Bridging Asia and the World</journal-subtitle>
    </journal-title-group>
    <issn pub-type="ppub">2163-9159</issn>
    <issn pub-type="epub">2163-9167</issn>
    <publisher>
      <publisher-name>Routledge</publisher-name>
    </publisher>
  </journal-meta>
  <tf:issue-meta>
    <pub-date date-type="control" iso-8601-date="2013-01-01"/>
    <pub-date date-type="cover">
      <string-date>January 2013</string-date>
    </pub-date>
    <volume>23</volume>
    <issue>1</issue>
  </tf:issue-meta>
  <tf:toc>
    <tf:toc-section>
      <tf:toc-article xlink:href="RGAM_A_744505/RGAM_A_744505_J.xml" article-id="744505" doi="10.1080/21639159.2012.744505"/>
      <tf:toc-article xlink:href="RGAM_A_744506/RGAM_A_744506_J.xml" article-id="744506" doi="10.1080/21639159.2012.744506"/>
      <tf:toc-article xlink:href="RGAM_A_744507/RGAM_A_744507_J.xml" article-id="744507" doi="10.1080/21639159.2012.744507"/>
      <tf:toc-article xlink:href="RGAM_A_744510/RGAM_A_744510_J.xml" article-id="744510" doi="10.1080/21639159.2012.744510"/>
      <tf:toc-article xlink:href="RGAM_A_744511/RGAM_A_744511_J.xml" article-id="744511" doi="10.1080/21639159.2012.744511"/>
      <tf:toc-article xlink:href="RGAM_A_744512/RGAM_A_744512_J.xml" article-id="744512" doi="10.1080/21639159.2012.744512"/>
      <tf:toc-article xlink:href="RGAM_A_744513/RGAM_A_744513_J.xml" article-id="744513" doi="10.1080/21639159.2012.744513"/>
      <tf:toc-article xlink:href="RGAM_A_744515/RGAM_A_744515_J.xml" article-id="744515" doi="10.1080/21639159.2012.744515"/>
    </tf:toc-section>
  </tf:toc>
</tf:issue-manifest>
```

