# ONIX

AUP uses ONIX to send product information to CB. ONIX files are sent from the Zeno ERM system (manually?) to a  CB ftp. The data are then ingested into CB Online (within 24 hrs).

The current format is ONIX 3.0.

## error 1

Apparently, sometimes an error is thrown in Zeno. In that case, no ONIX file ("ONIX30 message") is sent.

## error 2

Apparently, sometimes ONIX30 messages _are_ sent but "rejected" by CB. In that case, an error message is placed in the out folder of the ftp. The message disappear after a few days (?).

### example

- `84819142_0907_9789464562798_28528_onnx.err`

The `xml` extension is replaced by `err` and two CB prefixes are added. (Meaning?)

### causes

1. Missing contact data in the header. See [CB documentation](https://userguidescb.atlassian.net/wiki/spaces/BERDEFINTERN/pages/364998/Berichtdefinitie+ONIX+3.0+aanleveren+-+Publisher+to+CB#BerichtdefinitieONIX3.0(aanleveren)-PublishertoCB-H.4SenderName). Specifically, the element `<ContactName>` has a ‘No-flag’ which is not XSD valide.

```xml
<Header>
  <Sender>
    <SenderIdentifier>
      <SenderIDType>10</SenderIDType>
      <IDValue>7400597</IDValue>
    </SenderIdentifier>
    <SenderName>Amsterdam University Press b.V.</SenderName>
    <ContactName/>
    <EmailAddress>info@aup.nl</EmailAddress>
  </Sender>
 ```

#### important lead

1.	Er gaat nog steeds iets mis bij het exporteren vanuit het CRM van Walburg naar een ONIX30 bericht
2.	Er is geen controle of alle geëxporteerde ISBN’s in een ONIX30 bericht terechtkomen en ook in goede orde CB bereiken, 9789464564297 heeft CB niet bereikt
3.	Ontvangst- en Error-berichten op de ingediende berichten worden wel opgehaald uit het ftp account van AUP maar worden niet uitgelezen
4.	De output/foutmelding wordt dan ook niet gedeeld met de betrokkene, in dit geval Walburg Pers, gevolg iedereen tast in het duister.

## ONIX30 messages
Look like this:

- filename: `9789464563757_28845_onx.xml`


<!--
AUP has CB ftp account 7400597
AUP - or rather Walburg Pers Educatief - has CB RelatieID 7200421
-->
