# ONIX

## uploading books onto CB
This is a two-step process: first a metadata record is created, then the actual content is uploaded. The metadata record is an ONIX file and is created in Zeno and automatically sent to CB Online. 

The upload in CB Online is a manual process. 

### registring books at CB

1. in Zeno, complete the record for the ebook (epub/e-pdf)
2. in Zeno, set status to **Production**
3. in Zeno, select **ONIX 3** (three dots top right) and **Verstuur naar CB** ("send to CB")
4. in Zeno, confirm your choices in two pop-up windows

At most 24 hours later, a record for the book is created in the CB Online environment. 

### uploading books at CB Online
Once the record is created, you can upload the book. 

1. Go to [CB Online](https://cbonline.boekhuis.nl) and login
2. Go to **Uitgeverij** ("Publisher"). Enter the book's e-isbn and click on the pencil to edit the data
3. Go to e-Bookbestand > Wilt u het e-bookbestand vervangen > ja. Volg de instructies op.
4. Go to bovenin naar Beschikbaarheid ("Availability"). All options need to be selected, except Google. **Make sure the Google option is not active or else the book content will be available on Google Books!** 
5. Dan ga je boven in naar Metadata. > check of zowel voorplat als achterplat zijn upgeload. Is dit niet het geval dan graag alsnog doen.

Note 1. Most books uploaded to CB are not Open Acces and so will not be available on OAPEN. However, for books that _Aae_ OA, all bookshops need to be deselected, **except AUP**!

Note 2. Bij een bijdruk hoeft enkel het ebookbestand opnieuw geupload.

### ONIX problems
Als de ONIX er niet doorkomt bij het CB is de oorzaak vaak:

-	Zeno-record staat niet op Productie
-	Verschijningsdatum is een zaterdag, zondag of maandag
-	Er zit een harde return in de titel of ondertitel die je in Zeno niet ziet. Je ziet hem wel als je hem kopieert en in Word plakt

Als alles goed staat maar de upload lukt toch niet dan graag melding maken bij Inge en verdere instructies afwachten.

## dinges
AUP uses ONIX to send product information to CB. ONIX files are sent from the Zeno ERM system (manually?) to a  CB ftp. The data are then ingested into CB Online (within 24 hrs).

The current format is ONIX 3.0.

## error 1

Apparently, sometimes an error is thrown in Zeno. In that case, no ONIX file ("ONIX30 message") is sent.

## error 2

Apparently, sometimes ONIX30 messages _are_ sent but "rejected" by CB. In that case, an error message is placed in the out folder of the ftp. The message disappears after a few days (?). 

Apparently, the error messages are also sent to an AUP email address. Unfortunately, that address is defunct. How to change it?

### example

- `84819142_0907_9789464562798_28528_onnx.err`

The `xml` extension is replaced by `err` and two CB prefixes are added. (Meaning?)

### causes

1. Missing contact data in the header. See [CB documentation](https://userguidescb.atlassian.net/wiki/spaces/BERDEFINTERN/pages/364998/Berichtdefinitie+ONIX+3.0+aanleveren+-+Publisher+to+CB#BerichtdefinitieONIX3.0(aanleveren)-PublishertoCB-H.4SenderName). Specifically, the element `<ContactName>` is empty which is not XSD valid. Or, as CB puts it, "has a ‘No-flag’" - is this the same? (I associate it with a Boolean Y/N).

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

## Zeno (SPECULATION, WIP)
"Sending" an ONIX30 message from Zeno is in fact **exporting** an ONIX30 message and then placing it on the ftp. (Unless that is done automatically?). It works as follows:

1. select approproate fields in Zeno
2. export in appropriate format (`.onx`)
3. find the file in the ??? folder and do ???

### an important table
Fields in Zeno can have a different name from fields in CB Online. Here is a correspondence table.

Veld in BooksOnix	|	Veld in Zeno	|	Locatie Zeno
----- | ----- | -----
zeno_a_pk 	|	Nummer	|	Publicaties
verschijningsdatum 	|	Versch. Datum	|	Publicaties
aant_pag 	|	Pagina's	|	Publicaties - Tabblad Specificatie
afm_h 	|	Formaat -> Hoogte	|	Publicaties - Tabblad Specificatie
afm_b 	|	Formaat -> Breedte	|	Publicaties - Tabblad Specificatie
afm_imperial_h 	|	Formaat -> Hoogte	|	Publicaties - Tabblad Specificatie
afm_imperial_b 	|	Formaat -> Breedte	|	Publicaties - Tabblad Specificatie
fonds_asw 	|	Fonds code	|	Publicaties - Tabblad Groepen
relatie_nr 	|	Relatienummer	|	Relaties (via gekopelde royalties)
relatie_titel_code 	|	Titulatuur code	|	Relaties (via gekopelde royalties)
relatie_titel_achter 	|	Titulatuur achter naam	|	Relaties (via gekopelde royalties)
relatie_voornaam 	|	Voornaam	|	Relaties (via gekopelde royalties)
relatie_voorletter 	|	Voorletter	|	Relaties (via gekopelde royalties)
relatie_achternaam 	|	Achternaam	|	Relaties (via gekopelde royalties)
relatie_tussenvoeg 	|	Tussenvoegsels	|	Relaties (via gekopelde royalties)
relatie_rol 	|	Rol	|	Royalty ('Hoofdauteur', 'Auteur','Subsidieverstrekker', 'Overig','Vertaler','Illustrator', 'Redacteur'
relatie_cv_en 	|	CV auteur ENG	|	Relaties - Tabblad Overig
relatie_cv_nl 	|	CV auteur NED	|	Relaties - Tabblad Overig
codegroep 	|	Codering -> Groep	|	Publicaties - Tabblad Coderingen
codering_code 	|	Codering -> Code	|	Publicaties - Tabblad Coderingen
codering_naam 	|	Codering -> Naam	|	Publicaties - Tabblad Coderingen
afwerking 	|	Bindwijze/Afwerking	|	Publicaties - Tabblad Specificatie
dnummer 	|	D-nummer (uniek nummer voor artikelen zonder ISBN)	|	\<Niet zichtbaar in scherm\> 
druk 	|	Druk/editie	|	Publicaties - Druk
verk_prijs_eur_incl_btw 	|	Verkoopprijs incl. BTW	|	Publicaties - Prijs excl. BTW
verk_prijs_eur_excl_btw 	|	Verkoopprijs excl. BTW	|	Publicaties - Prijs incl. BTW
valuta_code 	|	Valuta code	|	Publicaties - Tabblad Valuta
valuta_prijs 	|	Valuta prijs	|	Publicaties - Tabblad Valuta
gewicht 	|	Gewicht (gram)	|	Publicaties - Tabblad Specificatie
illustraties 	|	Illustraties	|	Publicaties - Tabblad Specificatie
ill_zwart_wit 	|	Illustratie - tekenen	|	Publicaties - Tabblad Specificatie
ill_kleur 	|	Illustratie - scannen	|	Publicaties - Tabblad Specificatie
imprint 	|	Redactie	|	Publicaties - Tabblad Specificatie
eigenaar_nr 	|	Relatienummer	|	Relaties (via gekoppelde relatie Eigenaar zeno)
eigenaar_naam 	|	Bedrijfsnaam	|	Relaties (via gekoppelde relatie Eigenaar zeno)
isbn 	|	ISBN/EAN nummer	|	Publicaties
jpg_omslag 	|	Auteurs omslag	|	Publicaties - Tabblad Specificatie
lead_ws_en 	|	Lead website (Engels)	|	Publicaties - Tabblad Overig
lead_ws_nl 	|	Lead website (Ned)	|	Publicaties - Tabblad Overig
plan_stat_status_code 	|	Planning status code	|	Planningen - Tabblad Planningstatus
subtitel 	|	Subtitel	|	Publicaties
trefwoorden 	|	Trefwoorden	|	Publicaties - Tabblad Overig
drukwerk_binnen 	|	Drukwerk binnen	|	Publicaties - Tabblad Specificatie
drukwerk_omslag 	|	Drukwerk omslag	|	Publicaties - Tabblad Specificatie
begeleider_label 	|	Begeleider redactie, productie, overig 1, overig 2	|	Constantenkaart (Begeleider redactie, productie, overig 1, overig 2)
opmerkingen 	|	Opmerkingen	|	Publicaties - Tabblad Specificatie
laminaat 	|	Gelamineerd	|	Publicaties - Tabblad Specificatie
papier_binnen 	|	Papier binnen	|	Publicaties - Tabblad Specificatie
subs_vers_nr 	|	Relatienummer	|	Relaties (via subsidieverstrekker)
subs_vers_titel_code 	|	Titulatuurcode	|	Relaties (via subsidieverstrekker)
subs_vers_titel_achter 	|	Titulatuur achter naam	|	Relaties (via subsidieverstrekker)
subs_vers_voornaam 	|	Voornaam	|	Relaties (via subsidieverstrekker)
subs_vers_voorletter 	|	Voorletter	|	Relaties (via subsidieverstrekker)
subs_vers_achternaam 	|	Achternaam	|	Relaties (via subsidieverstrekker)
subs_vers_tussenvoeg 	|	Tussenvoegsels	|	Relaties (via subsidieverstrekker)
subs_vers_rol 	|	Rol	|	Relaties (via subsidieverstrekker)
subs_vers_toelichting 	|	Toelichting	|	Relaties (via subsidieverstrekker)
versch_vorm 	|	Verschijningsvorm	|	Publicaties - Tabblad Groepen
status 	|	Status	|	Publicaties
quotes 	|	Quotes 	|	Publicaties - Tabblad Overig
rechten 	|	Opmerkingen rechten	|	Publicaties - Tabblad Specificatie
bullets_cat 	|	Bullets cat.	|	Publicatie - Tabblad Overig
serie 	|	Serie	|	Publicaties - Tabblad Groepen
deel 	|	Deel	|	Publicaties - Tabblad Groepen
taal 	|	Taal	|	Publicaties - Tabblad Groepen
tekst_ws_en 	|	Tekst website ENG	|	Publicaties - Tabblad Overig
tekst_ws_nl 	|	Tekst website NL	|	Publicaties - Tabblad Overig
titel 	|	Titel	|	Publicaties
inhoudsopgave 	|	Inhoudsopgave	|	Publicaties - Tabblad Groepen
vellen 	|	Vellen	|	Publicaties - Tabblad Specificatie
uitgever_nam 	|	Naam	|	Gebruikers (via Publicaties Uitgever)
cat_pp_item_nr 	|	Catalogus pp en Item nr	|	Publicaties - Tabblad Overig
project_code 	|	Project code	|	Publicaties - Tabblad Groepen
technische_voorraad 	|	Vooraad	|	Publicaties - Tabblad Voorraad
svs_nummer 	|	SVS nummer	|	Publicaties - Tabblad Groepen
kortinggroep_code 	|	Kortinggroep code	|	Publicaties - Tabblad Groepen
kortinggroep_naam 	|	Kortinggroep naam	|	Publicaties - Tabblad Groepen
asw 	|	Asw codering	|	Publicaties - Tabblad Coderingen
disciplines 	|	Disciplines	|	Publicaties - Tabblad Coderingen
valuta_prijs_incl_btw 	|	Valuta prijs incl. BTW	|	Publicaties - Tabblad Valuta
usd_prijs_incl_btw 	|	Valuta prijs alleen USD incl. BTW	|	Publicaties - Tabblad Valuta
gbp_prijs_incl_btw 	|	Valuta prijs alleen GBP incl. BTW	|	Publicaties - Tabblad Valuta
publicatie_type	|	Type	|	Publicaties - Tabblad Overig


<!--

ONIX bestanden
Vanuit Zeno kan van een publicatie een ONIX bestand gemaakt worden met gegevens van die publicatie. Daarmee kan de publicatie bij het CB ingevoerd worden. Nu kan het voorkomen dat de codering in Zeno afwijkt van wat er in het Cb nodig is; daarvoor kunnen vertalingen aangemaakt worden. In dit bestand staan de volgende gegevens:
-	ISBN
-	Titel
-	Subtitel
-	Verschijningsvorm: ProductForm in Onix. Er is wel een vertaling nodig tussen de Zeno codering en de ONIX codering
-	Hoogte/breedte/dikte in mm
-	Gewicht in gram
-	Aantal pagina’s
-	Fonds: Productclassification met type 06 in ONIX: Er is wel een vertaling nodig tussen de Zeno codering en de ONIX codering
-	Serie en deel in de serie
-	Auteurs, vertalers, illustrators, redacteuren
o	Van auteurs kan een biografie worden meegegeven Dat kan een biografie zijn die bij een auteur opgeslagen is, dan is dit bij elk boek voor deze auteur dezelfde biografie, of bij een boek, dan geef je bij een boek opnieuw de biografie van de auteur(s) op 
-	Druknummer
-	Taal: Er is wel een vertaling nodig tussen de Zeno codering en de ONIX codering
-	Indicatie ‘geïllustreerd’ of niet 
-	NUR codering
-	BIC codering
-	BISAC codering
-	Flaptekst (ONIX veld textType=02) (Zeno veld omschrijving, maar kan ook naar ander veld verwijzen)
-	Boekbeschrijving (ONIX veld textType=05) (Zeno veld Doelgroep, maar kan ook naar ander veld verwijzen)
-	Inhoudsopgave (ONIX veld textType=03) (Zeno veld Toelichting, maar kan ook naar ander veld verwijzen)
-	Uitgever 
-	Status
-	Verschijningsdatum
-	Koppelingen naar ander boek (is vertaling van, is ebook van, is POD vervanging van)
-	Verkoopprijs
-	AWS code
-	BTW code

Vertalingen
In de ONIX bestanden worden soms specifieke codes gevraagd en de codes in Zeno zijn vaak anders. Voor de volgende entiteiten is het mogelijk de Zeno code te vertalen naar een ONIX code:
-	Fonds
-	Verschijningsvorm
-	BTW
-	Taal

-->
