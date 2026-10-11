> Detta plugin är skapat i samband med ett projekt och kommer inte att uppdateras efter projektets slut.

## 1. Överblick
Pluginapplikationen är skapad med syfte att förenkla importen av höjddata från filer som innehåller inbäddad geografisk metadata och georeferering (GeoTIFF) för användning tillsammans med Unreal Engines (UE) inbyggda lanskapfunktion.

- **Namn på plugin:** TiffToLandscape
- **Current Version:** 1.0.0
- **Supported Unreal Engine Versions:** 5.7+
- **Platforms:** Windows
- **Intended Audience:** Planeringsarkitekter, Landskapsarkitekter och övriga UEanvändare

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
1. Kopiera mappen `TiffToLandscape` och klistra in den i filsökvägen till ditt önskade UE projekt: /DittProjekt/Plugins .
2. Öppna eller starta om projektet för att importera de nya filerna.
3. Öppna **Edit → Plugins**.
4. Tillåt **TiffToLandscape**.Om alternativet inte dyker upp, öppna **Plugin Directories** och lägg till ett element under **Additional plugin directories**. Välj filsökvägen till den tillagda `TiffToLandscape` filen i ditt projekt.
7. Stäng ner fönstret och starta om Unreal Engine.
8. Öppna åter **Edit → Plugins**. Där bör du se **External → Others** i den vänstra kolumnnen.
9. Aktivera tillägget.
10. Starta om Unreal engine. Om mappen `TiffToLandscape` ligger i den korrekta filsökvägen så ska den även dyka upp i **Content Drawer**.

---

## 4. Instruktioner för användning

### 4.1 Aktivera plugin
Se till att tillägget är aktiverat genom att dubbelkolla att **TiffToLandscape** är tillåten.
**Edit → Plugins → Other → TiffToLandscape**

### 4.2 Arbetsflöde och användning
1. Öppna **Content Browser**.
2. Öppna **Plugins → TiffToLandscape → Editor**
3. Högerklicka på **Landscape_EUW** och välj sedan **Run Editor Utility Widget** i menyn.
4. Börja genom att trycka på den översta knappen märkt **Import**.
6. Navigera och välj en fil med geodata i formen `.TIFF` eller `.TIF` från hårddisken.
7. Därefter, välj även en filsökväg där texturen i formatet `.PNG` sparas samt filsökväg och namn på filen där höjddatan sparas `.NPY` eller `.txt`. En `.json` fil sparas även för att hantera utbredning och upplösning. Det är viktigt att inte redigera, flytta eller radera denna fil.
8. När importeringen och hanterinen är klar, klicka på knappen märkt **Load** och välj sedan din skapade höjdkarta `.PNG` och den sparade datan `.NPY` eller `.txt`.
9. Verktyget visar då all information som är nödvändig för att skapa ett landskap från höjdkartan i Unreal Engines landskapsverktyg:
    Höjkarta
    Maximala höjden
    Minimala höjden
    Skala för X, Y och Z.
11. Öppna **Landscape Mode → Manage → Import from File** och välj PNG-filen som Heightmap File. Ange sedan skalvärdena från widgeten samt klicka på **Fit to data** för att automatiskt justera övriga inställningar.

---

## 5. User Interface

### 5.1 Menu Entries
- **Toolbar:** `Import OBJ File`
- **Context Menu (Content Browser):** `Import → OBJ File`

### 5.2 Import Dialog
The import dialog allows users to configure scale and normal handling before importing.

---

## 6. Usage Guide

### 6.1 Importing an OBJ File
1. Click **Import OBJ File**.
2. Select a valid `.obj` file.
3. Set the desired import scale.
4. Enable or disable normal import.
5. Confirm to create the Static Mesh.

### 6.2 Import Settings

| Setting | Description | Default |
|-------|-------------|---------|
| Import Scale | Multiplier applied to mesh size | 1.0 |
| Import Normals | Uses normals from OBJ file | Enabled |
| Generate Collision | Automatically creates collision | Enabled |

---

## 7. Data Handling & Output
- **Asset Type:** Static Mesh
- **Naming Convention:** `<OBJFileName>_SM`
- **Destination Folder:** Currently selected Content Browser folder

---

## 8. Scripting / API Reference

### 8.1 Blueprint Support
This version does not expose Blueprint nodes.

### 8.2 C++ API
**Primary Class:**  
`SimpleOBJImporter`

**Key Methods:**
- `ImportOBJ(const FString& FilePath)`
- `CreateStaticMesh(...)`

---

## 9. Begränsningar
- 
---

## 10. Kända problem

| Problem | Anledning | Lösning |
|-----|------|----------|
| x | x | x |
| x | x | x |
| x | x | x |

---

## 11. Versionhistorik

| Version | Datum |
|-------|------|-------|
| 1.0.0 | 2026-10-xx | Publicering |

---

## 12. Kontaktinformation

- Email: tess04.tf@gmail.com
