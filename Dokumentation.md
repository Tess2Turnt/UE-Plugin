> Detta plugin är skapat i samband med ett projekt och kommer inte att uppdateras efter projektets slut.

## 1. Överblick
Pluginapplikationen är skapad med syfte att förenkla importen av höjddata från filer som innehåller inbäddad geografisk metadata och georeferering (GeoTIFF) för användning tillsammans med Unreal Engines (UE) inbyggda lanskapfunktion.

- **Namn på plugin:** TiffConversion
- **Version:** 1.0.0
- **Stödda Unreal Engine Versioner:** 5.7+
- **Plattformar:** Windows
- **Målgrupp:** Planeringsarkitekter, Landskapsarkitekter och övriga UEanvändare

---

## 2. Egenskaper
- Möjliggör import av data direkt från `.TIF/.TIFF` filer till Unreal engine.
- Skapar och importerar en textur i PNG format för höjdvärden lagrade i TIF/TIFF filen.
- Beräknar utifrån skala och upplösning, indata som användaren bör använda under lanskapskreationen för att uppnå önskad effekt.

---

## 3. Installation

### 3.1 Krav
- Unreal Engine 5.7 eller nyare versioner av programvaran.
- Windows 10 eller senare versioner av programvaran.

### 3.2 Installation steg för steg
1. Kopiera mappen `TiffConversion` och klistra in den i filsökvägen till ditt önskade UE projekt: /DittProjekt/Plugins .
2. Öppna eller starta om projektet för att importera de nya filerna.
3. Öppna **Edit → Plugins**.
4. Tillåt **TiffToLandscape**.Om alternativet inte dyker upp, öppna **Plugin Directories** och lägg till ett element under **Additional plugin directories**. Välj filsökvägen till den tillagda `TiffConversion` filen i ditt projekt.
7. Stäng ner fönstret och starta om Unreal Engine.
8. Öppna åter **Edit → Plugins**. Där bör du se **External → Others** i den vänstra kolumnnen.
9. Aktivera tillägget.
10. Starta om Unreal engine. Om mappen `TiffConversion` ligger i den korrekta filsökvägen så ska den även dyka upp i **Content Drawer**.

---

## 4. Instruktioner för användning

### 4.1 Aktivera plugin
Se till att tillägget är aktiverat genom att dubbelkolla att **TiffConversion** är tillåten.
**Edit → Plugins → Other → TiffConversion**

### 4.2 Arbetsflöde och användning
1. Öppna **Content Browser**.
2. Öppna **Plugins → TiffConversion → Editor**
3. Högerklicka på **Landscape_EUW** och välj sedan **Run Editor Utility Widget** i menyn.
4. Börja genom att trycka på den översta knappen märkt **Convert TIFF**.
6. Navigera och välj en fil med geodata i formen `.TIFF` eller `.TIF` från hårddisken.
7. Därefter, välj även en filsökväg där texturen i formatet `.PNG` sparas samt filsökväg och namn på filen där höjddatan sparas `.NPY` eller `.txt`. En `.json` fil sparas även för att hantera utbredning och upplösning. Det är viktigt att inte redigera, flytta eller radera denna fil.
9. Verktyget visar då all information som är nödvändig för att skapa ett landskap från höjdkartan i Unreal Engines landskapsverktyg:
    Höjkarta
    Maximala höjden
    Minimala höjden
    Skala för X, Y och Z.
11. Öppna **Landscape Mode → Manage → Import from File** och välj PNG-filen som Heightmap File. Ange sedan skalvärdena från widgeten samt klicka på **Fit to data** för att automatiskt justera övriga inställningar.
12. Om du vill hantera och se relevanta värden för redan konverterad data, då istället klicka på knappen märkt **ILoad data** och välj sedan din skapade höjdkarta `.PNG` och den sparade datan `.NPY` eller `.txt`.

---

## 5. Användargränssnitt

### 5.1 Widgetens olika delar
| Element | Användning |
|-------|-------------|
|Open in browser|Öppnad sökvägen till dokumentationen i din valda webbläsare.|
|Convert TIFF|Konvertering av en vald TIFF till PNG och höjddata.|
|Load data|Inläsning av sparade höjdvärden, höjdkarta och data.|
|Maximum/Minimum|Högsta och lägsta höjd i originaldatan.|
|Scale X,Y,Z|Värden att skriva in i tillhörande input för skala vid landscape-importen.|
|Heightmap|Förhandsvisning av den skapade höjdkartan.|

### 5.2 Fildialoger
Plugin-programmet använder vanliga Windows-fönster för att välja och spara filer. Fönstren öppnas överst.

---

## 6. Användarguide

### 6.1 Konvertera en TIFF fil
- Tryck på Convert TIFF i widgeten.
- Välj en GeoTIFF-fil (.tif eller .tiff) i filfönstret.
- Välj en mapp där PNG-bilden ska sparas.
- Välj filnamn och plats för höjddatan (.npy eller .txt).
- Vänta tills konverteringen är klar. Förloppet visas i Output Log, och meddelandet "Conversion complete" visas när programmet är färdigt, samt att relevanta värden visas i widgeten.
- I Unreal Engines lanskapsläge kan nu ett motsvarande landskap skapas med höjdkartan samt värdena för skalan.

När konverteringen är klar så har det skapats:
- **x.png** En PNG fil i formen av en höjdkarta i 16-bitars gråskala.
- **x.npy, x.txt** En NPY eller TXT fil som innehåller data över landskapets höjdvärden i meter.
- **x.json** En fil innehållandes landskapets utbredning och bildens upplösning.
> Byt ej namn eller flytta på JSON filen då detta kan förhindra att skalvärdena läses in.

### 6.2 Inställningar

| Inställning | Beskrivning | Värde |
|-------|-------------|---------|
| Utdataupplösning | Storlek på PNG-filen | 3049 × 3049 |
| Bitdjup | Höjdkartans precision | 16-bitar |
| Nodata-värde | Pixlar med värde ≤ -9999 sätts till lägsta höjd | -9999 |

### 6.2 Skalformler

- Skala X = TexturStorlekX / UpplösningX * 100
- Skala Y = TexturStorlekY / UpplösningY * 100
- Skala Z = (MaxHöjd - MinHöjd) / 512 * 10000

## 7. Datahantering och utdata
 - Heightmap: PNG, 16 bitar, gråskala, importeras till /Game/Heightmaps
 - Höjddata: NPY eller TXT med originalets höjdvärden i meter
 - Metadata: JSON med extentX, extentY, resX, resY
 - Namngivning: PNG och JSON får samma namn som TIFF-filen

---

## 8. Skript / API-referens

### 8.1 Blueprintstöd

Widgeten anropar Python via Execute Python Script, och variabler används för att lagra värden samt visa dessa i widgeten.

|Utgång|Typ|Variabel|
|------|---|--------|
|png_height|Texture2D|Heightmap|
|min_height_value|Float|Min Height|
|max_height_value|Float|Max Height|
|scale_x|Float|X|
|scale_y|Float|Y|
|scale_z|Float|Z|

### 8.2 Python API (Converter.py)

| Funktion |Beskrivning av funktion|
|-------|-------------|
|executeAll()|	Hela flödet: välj TIFF, konvertera, spara|
|tifToData(path)|Konverterar TIFF till PNG och skriver JSON|
|getTiffExtent(img)|Läser GeoTIFF-taggen och räknar ut utbredning i meter|
|heightValuesFromPNG(data)|Sparar höjddata som .npy/.txt|
|scaleCalcultions(...)|	Räknar ut skala X och Y|
|importHeightForBlueprint()|Importerar PNG till Unreal och returnerar värden till widgeten|

---

## 9. Begränsningar
 - Endast TIFF filer i gråskala stöds.
 - Skalan kan bara räknas ut om filen är en GeoTIFF med meter som enhet.
 - Utdata är alltid 3049 × 3049. En icke-kvadratisk TIFF sträcks ut till en kvadrat.
 - Pixlar med nodata (≤ -9999) blir lägsta höjd.
 - Maxstorlek är 500 miljoner pixlar på originalfilen.
 - Konverteringen sker i editorn och fungerar inte i en byggd applikation.
 - Kräver aktiverat Python-plugin.
 - PNG:n lagrar bara relativa höjder. Riktiga höjder kräver .npy/.txt-filen.
---

## 10. Kända problem

| Problem | Anledning | Lösning |
|-----|------|----------|
| Load misslyckas | JSON-filen saknas bredvid PNG:n | Kör **Import** igen och byt inte namn på filerna |
| Skala i z axeln visar fel värde | Fel värde i python-funktion **importHeightUnreal()** | Värde förändrat från 100 till 10000 i uträkning av Z-skala|
| Långa väntetider vid användning av konverteraren | Stora TIFF filer | Välj mer begänsade filer för att minska tiden|

---

## 11. Versionhistorik

| Version | Datum | Typ |
| 1.0.0 | 2026-10-25 | Publicering |

---

## 12. Kontaktinformation

- Email: tess04.tf@gmail.com
