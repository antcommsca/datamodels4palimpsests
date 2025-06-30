# Datamodels for describing palimpsests
Palimpsests are complex manuscripts that pose several accessibility challanges to scholars. However, they are also crucial artifacts for expanding our knowledge of ancient texts.
Describing accurately and in an standardized way their structure is a key step for progressing the study of these manuscripts.
In this repository we aim to share a data model that we built during [AntCom](https://antcom.eu/) European project, for describing palimpsests using standard guidelines and formats.

## Related works
Others institutions dealt we palimpsest ([Todd R. Hanneken 2024](https://palimpsest.stmarytx.edu/thanneken/2024/dh/)),  ([Magrini, Pasini, and Arduini 2005](https://pascal-francis.inist.fr/vibad/index.php?action=getRecordDetail&idt=16825319)).

## TEI datamodel
We chose to use the standard produced by the [Text Ecoding Initiative (TEI)](https://www.tei-c.org/) because it is the _de facto_ standard for describing manuscripts.
The reference TEI files are containe in the `TEIfiles` folder of this repository.

| File name           | Shelfmark |
|---------------------|-----------|
| CPVRm0120_0.tei.xml | CXX(110)  |


### The structure
For each codicological unit we create a `<msPart>`, to describe if it is a _scriptio superior_ or _inferior_ we use the attribute `type`.
.
```xml
<msPart n="1" type="scriptio-superior">...</msPart>
<msPart n="2" type="scriptio-inferior">...</msPart>
<msPart n="3" type="scriptio-inferior">...</msPart>
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
      <author xml:lang="en" ref="https://www.degruyterbrill.com/database/PMBZ/entry/PMBZ14598/html">Ioseph Hymnographos</author>
      <title xml:lang="el">Νέα Ὀκτάηχος</title>
      <title xml:lang="it">Nuovo Ottoeco</title>
   </msItem>
</msContents>
```

