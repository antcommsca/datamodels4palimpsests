# Datamodels for describing palimpsests
Palimpsests are complex manuscripts that pose several accessibility challanges to scholars. However, they are also crucial artifacts for expanding our knowledge of ancient texts.
Describing accurately and in an standardized way their structure is a key step for progressing the study of these manuscripts.
In this repository we aim to share a data model that we built during [AntCom](https://antcom.eu/) European project, for describing palimpsests using standard guidelines and formats.

## TEI datamodel
We chose to use the standard produced by the [Text Ecoding Initiative (TEI)](https://www.tei-c.org/) because it is the _de facto_ standard for describing manuscripts.
The reference TEI files are contained in the `tei-xml` folder of this repository.

| File name           | Shelfmark    | Status             |
|---------------------|--------------|--------------------|
| CPVRm0120_0.tei.xml | CXX(110)     |Reference prototype.|
| CPVRm0134_0.tei.xml | CXXXIV (123) |Reference prototype.|
| CPVRm0040_0.tei.xml | XL (38)      |To be reviewed.     |
| CPVRm0062_0.tei.xml | LXII (60)    |To be reviewed.     |


### The structure
For each codicological unit we create a `<msPart>`. To describe if it belongs to the  _scriptio superior_ or the _scriptio inferior_ we use the attribute `type` with the respective value (`scriprion_superior` or `scriprion_inferior`).

```xml
<msPart n="1" type="scriptio_superior">...</msPart>
<msPart n="2" type="scriptio_inferior">...</msPart>
<msPart n="3" type="scriptio_inferior">...</msPart>
```

Inside `<msPart>` we have:

```xml
<msIdentifier>
   <idno>CPVRm0134_0A</idno>
   <msName xml:lang="el">Παρακλητική</msName>
   <msName xml:lang="en">Paracletica</msName>
</msIdentifier>
<msContents>
   <summary>Ioseph the Hymnographos' New Octoechos. The grave, plagal of the second and fourth tones (βαρύς, πλάγιος α΄, πλάγιος δ΄) survive, along with fragments of the third and plagal of the first tones (β΄, πλάγιος α΄).</summary>
   <textLang mainLang="grc">Ancient Greek (to 1453)</textLang>
   <msItem>
      <locus from="1r" to="79v">ff. 1-79</locus>
      <author xml:lang="en" ref="https://www.degruyterbrill.com/database/PMBZ/entry/PMBZ14598/html">Ioseph Hymnographos</author>
      <title xml:lang="el">Νέα Ὀκτάηχος</title>
      <title xml:lang="it">Nuovo Ottoeco</title>
   </msItem>
</msContents>
```

In cases of a non sequential or fragmented text, we use a parent `msItem` element that contains the overall _loci_ of the described codicological unit and the children `msItem`.

```xml
<msItem>
   <locusGrp>
      <locus from="6r" to="61v">ff. 6-61</locus>
      <locus from="68r" to="69v">68-69</locus>
      <locus from="71r" to="74r">71-74</locus>
      <locus from="76r" to="78v">76-78</locus>
   </locusGrp>
   <title type="desc">Menology of December</title>
   <msItem>
      <locus from="78r" to="78v">f. 78</locus>
      <title xml:lang="el">[ΑΘΛΗΣΙΣ ΤΩΝ ΑΓΙΩΝ ΤΟΥ ΧΡΙΣΤΟΥ ΜΑΡΤΥΡΩΝ ΑΚΕΨΙΜΑ, ΙΩΣΗΦ ΚΑΙ ΑΕΙΘΑΛΑ]</title>
   </msItem>
   ...
   <msItem>
      <locusGrp>
         <locus from="24r" to="24v">ff. 24</locus>
         <locus from="27r" to="27v">27</locus>
         <locus from="30r" to="30v">30</locus>
      </locusGrp>
      <title xml:lang="el">[ΜΑΡΤΥΡΙΟΝ ΤΟΥ ΑΓΙΟΥ ΜΑΡΤΥΡΟΣ ΒΟΝΙΦΑΤΙΟΥ]</title>
   </msItem>
</msItem>
```
