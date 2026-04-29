# Artefaktbildung durch kutane Pigmente in der Magnetresonanztomographie

***In vitro*- und *in vivo*-Analyse von Tattoos, Permanent Make-up und Kosmetika**

---

## Autorin & Einordnung

- **Autorin:** Calibran Muriel  
- **Institution:** BZG Bildungszentrum Gesundheit Basel-Stadt  
- **Bildungsgang:** Medizinisch-Technische Radiologie HF (BG MTR 23)  
- **Eingereicht:** Münchenstein 26.04.2026

---

## Inhaltsverzeichnis

1. [Projektübersicht](#projektübersicht)  
2. [Methodik](#methodik)  
3. [Zentrale Ergebnisse & Abbildungen](#zentrale-ergebnisse--abbildungen)  
4. [Repository-Struktur](#repository-struktur)  
5. [Statistische Auswertung](#statistische-auswertung)  
6. [Methodische Hinweise](#methodische-hinweise)  

---

## Projektübersicht: MRT-Artefakte durch kutane Pigmente

Dieses Repository enthält die Forschungsdaten, MRI Bilder und das Auswertungsskript der Diplomarbeit **"Artefaktbildung durch kutane Pigmente in der Magnetresonanztomographie: *In-vitro*- und *in-vivo*-Analyse von Tattoos, Permanent Make-up und Kosmetika"**.

Ziel der Arbeit ist die Quantifizierung von Suszeptibilitätsartefakten, die durch metallhaltige Pigmente in Alltagsprodukten verursacht werden, um die diagnostische Sicherheit zu erhöhen.

### Untersuchungsdesign & Methodik
Die Diplomarbeit basiert auf einem systematischen Vergleich von Einflussfaktoren in einem kontrollierten Versuchsaufbau:

* **Material:** Analyse von 15 Produkten (6x Tattoo-Farben, 4x PMU, 5x dekorative Kosmetik).
* **Mess-Settings:** Vergleich zwischen standardisiertem Phantom-Setup (wasserbasiert dotiert mit Nickel-(II)-Sulfat-Hexahydrat, D165, Siemens Healthineers) und *in-vivo*-Messungen am Probanden.
* **Hardware:** Durchführung an 1.5 Tesla und 3.0 Tesla MRT-Systemen.
* **Sequenzprotokolle:** T2-TSE, SWI, T1-FLD2, T2-TIRM, PD-TSE Dixon, T1-VIBE, T1-TSE

### Zentrale Forschungsergebnisse
* **Selektive Artefaktbildung:** Messbare Bildstörungen traten ausschliesslich bei dekorativer Kosmetik auf (Mascara/Eyeliner).
* **Sicherheitsaspekt:** Tattoos und PMU-Pigmente zeigten unter den gewählten Parametern keine messbaren Artefakte oder Sicherheitsrisiken.
* **Sequenz-Einfluss:** Die SWI-Sequenz erwies sich als bester Indikator für Pigmentartefakte, während klassische Spin-Echo-Sequenzen eine deutlich höhere Robustheit aufwiesen.
* **Feldstärke:** Zwischen 1.5 T und 3.0 T zeigten sich keine signifikanten Unterschiede in der Artefaktausdehnung.
* **Transfer:** Die Ergebnisse im Phantom sind stärker ausgeprägt als *in-vivo*.

---

## Methodik

Die Datenerhebung erfolgte zweistufig:

### 1. *In-vitro* (Phantom-Setup)
- Kontrollierte Messung von Pigmenten und Kosmetika  
- Applikation auf Kunsthaut und synthetischen Wimpern  
- Ziel: Isolierte Analyse der Materialeigenschaften  

### 2. *In-vivo* (Probanden)
- Validierung der klinischen Relevanz  

### Datenauswertung
- Vermessung der Artefaktflächen in cm²
- Statistische Analyse in einer Pythonumgebung

---

## Zentrale Ergebnisse & Abbildungen

Die finalen Statistiken sind in der GitHub-Ablage als PDF-Dateien gespeichert.

### Abbildung 1: Prävalenz nach Pigmentkategorie
- Gesamtanzahl getesteter Pigmente/Produkte (n = 15)  
- Aufteilung nach Kategorien  

### Abbildung 2: Einfluss der Magnetfeldstärke
- Artefaktflächen (> 0 cm²)  
- Vergleich zwischen 1.5T und 3.0T (n = 70 pro Feldstärke)  

### Abbildung 3: Artefaktfläche nach MRT-Sequenz
- Mittelwerte und Standardabweichungen  
- Abhängigkeit von Sequenz und Feldstärke (n = 10)  

### Abbildung 4: Phantom vs. Proband
- Vergleich der Artefaktgrößen  
- n = 70 pro Setting  

### Abbildung 5: Einfluss des Trägermaterials
- Analyse von Mascara-Produkten (n = 56)  
- Vergleich: Kunsthaut vs. synthetische Wimpern  

---

## Repository-Struktur

```text
├── Bilder/
│   └── [Sämtliche MRT-Aufnahmen nach Sequenz & Setting geordnet]
│
├── Code/
│   └── muriel_auswertung.ipynb      # Jupyter Notebook für die statistische Analyse
│
├── Daten/
│   ├── metadata.csv                 # Probenparameter (Inhaltsstoffe, IDs, Hersteller)
│   └── total_featuretable.csv       # Rohdaten der Artefaktvermessung
│
├── Resultate/
│   ├── [Tabelle für Statistik].csv  # Zusammengefasste Daten
│   └── [Grafik Statistik].pdf       # Finale Abbildungen für die Diplomarbeit
│
└── README.md                        # Dokumentation Repository
```

**Datensätze:**
- `metadata.csv`: Probenparameter (Sample_ID, Feldstärke, Objekt, Träger, Mode, Inhaltsstoffe)  
- `total_featuretable.csv`: Rohdaten  
- `df_summary.csv`: Rohdaten aus `total_featuretable.csv` wurden verwendet. Duplikate (*in vivo*) und Triplikate (*in vitro*) wurden zu Mittelwerten und Standardabweichungen zusammengefasst und Probenspezifische Metadaten in den Datensatz integriert. Das resultierende `df_summary.csv` bildet die Grundlage für die statistische Auswertung.
---

## Statistische Auswertung

Die statistische Auswertung erfolgt via einer python basierten Pipeline in einem Jupyter Notebook.

### 1. Bibliotheken und Setup
Zu Beginn werden alle benötigten Python-Bibliotheken geladen.

### 2. Definition der Eingabe- und Ausgabeordner
Die Pipeline benötigt drei zentrale Pfade, die manuell im Code gesetzt werden:
* **Eingabedatei:** Rohdaten (`total_featuretable.csv`)
* **Ausgabeordner für Daten:** Speicherung von CSV-Tabellen
* **Ausgabeordner für Ergebnisse:** Speicherung von Grafiken (PDF)

**WICHTIG:** Pfade im Code anpassen!
Bevor das Skript ausgeführt wird, müssen folgende Datenpfade angepasst werden:
* Suchen Sie ganz oben im Code den Abschnitt **`# 1. SETUP UND DATEIPFADE`**.
* Ändern Sie die Pfade bei `out_dir_data` und `out_dir_result` so, dass sie auf einen gewünschten Ordner auf Ihrem Computer zeigen:
```python
out_dir_data = ''
out_dir_result = ''
```

### 3. Definition von Zuordnungstabellen (Metadaten)
Es werden Zuordnungstabellen definiert, um den rohen Daten Kontext zu geben:
* **Messmodi:** MRT-Sequenzen (z. B. SWI, T1-TSE, T2-TSE)
* **Farbcodes:** Zuordnung zu konkreten Produkten oder Pigmenten
* **Materialinformationen:** Hersteller, Inhaltsstoffe und Produktnamen

### 4. Einlesen und Vorverarbeitung
Die Datei `total_featuretable.csv` wird eingelesen und für die weitere Verarbeitung vorbereitet.

### 5. Extraktion von Metadaten aus Spaltennamen
Informationen im Dateinamen werden aufgeteilt:
* **Magnetfeldstärke:** (z. B. 1.5T oder 3.0T)
* **Objektdaten:** (Phantom oder Proband)
* **MRT-Sequenz:** (Mode)
* **Farbcode**
* **Replikatnummer**
* **Trägermaterial** (Wimpern/Kunsthaut)
* **Pigmentkategorie** (Kosmetik, Tattoo, PMU) hinzugefügt.

### 6. Berechnung der Messgrösse (Artefaktfläche)
Die Rohmessdaten werden wie folgt ausgewertet:

$$\text{Artefaktfläche} = \text{Breite} \times \text{Tiefe}$$

Diese Grösse beschreibt die Ausdehnung eines Bildartefakts in cm².

### 7. Transformation und Datengrundlage
Die Daten werden in ein Analyseformat überführt und über die **Sample-ID** mit den Metadaten zusammengeführt. Die resultierende Tabelle enthält alle relevanten Informationen (Messwert, Feldstärke, Objekt, Material, Farbe, Sequenz) für die Statistik.

### 8. Statistische Aggregation
Die Daten werden nach Gruppen (z. B. Feldstärke, Pigmentkategorie, Hersteller) zusammengefasst. Für jede Gruppe werden berechnet:
* **Mittelwert** der Artefaktfläche
* **Standardabweichung**

### 9. Export und Visualisierungs-Setup
* **Export:** Die Ergebnisse werden als CSV-Dateien gespeichert.
* **Styling:** Definition Layout Parameter.  
* **Hilfsfunktionen:** Definition der Messachsengrössen sowie Identifikation von Ausreissern.

### 10. Visualisierungen und Ergebnisausgabe
Die Analyse erzeugt mehrere grafische Darstellungen (Export als PDF):

* **10.1 Artefaktentstehung:** Vergleich der Häufigkeit nach Pigmentkategorie.
* **10.2 Feldstärken:** Vergleich 1.5 T vs. 3.0 T mittels Boxplots.
* **10.3 MRT-Sequenzen:** Vergleich der verschiedenen Sequenzen mittels Balkendiagramm.
* **10.4 Modelle:** Vergleich Phantom vs. Proband sowie Kunsthaut vs. Wimpern.

## Ergebnis der Pipeline
Nach vollständiger Ausführung liegen vor:
* **Annotierte Datensätze:** Vollständig strukturierte Tabellen.
* **Statistische Auswertungen:** CSV-Exporte für Mittelwerte und Gruppenvergleiche.
* **Grafiken:** Abbildungen im PDF-Format.

---

## Methodische Hinweise

- Artefaktflächen wurden manuell in cm² vermessen  
- Daten wurden in CSV-Dateien strukturiert erfasst  
- Die Analyse erfolgt in einer Python-Umgebung  

**Hinweis:**  
Dieses Projekt dient ausschliesslich wissenschaftlichen Zwecken im Rahmen der Ausbildung *Medizinisch-Technische Radiologie HF*.
