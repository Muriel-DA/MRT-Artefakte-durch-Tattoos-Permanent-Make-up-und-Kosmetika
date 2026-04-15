# Artefaktbildung durch kutane Pigmente in der Magnetresonanztomographie

**In vitro- und in vivo-Analyse von Tattoos, Permanent Make-up und Kosmetika**

---

## Autorin & Einordnung

- **Autorin:** Calibran Muriel  
- **Institution:** BZG Bildungszentrum Gesundheit Basel-Stadt  
- **Bildungsgang:** Medizinisch-Technische Radiologie HF (BG MTR 23H)  
- **Eingereicht am:** *[Datum ergänzen, z.B. Mai 2026]*  

---

## Inhaltsverzeichnis

1. [Projektübersicht](#projektübersicht)  
2. [Methodik](#methodik)  
3. [Zentrale Ergebnisse & Abbildungen](#zentrale-ergebnisse--abbildungen)  
4. [Repository-Struktur](#repository-struktur)  
5. [Installation & Nutzung](#installation--nutzung)  
6. [Methodische Hinweise](#methodische-hinweise)  

---

## Projektübersicht

Dieses Repository enthält Rohdaten, Bildmaterialien und Auswertungsskripte einer wissenschaftlichen Untersuchung zu MRT-Artefakten.

Ziel der Arbeit ist die systematische Quantifizierung von Bildstörungen, die durch Pigmente in:
- Tattoos  
- Permanent Make-up (PMU)  
- Kosmetika  

verursacht werden.

**Untersuchungsfaktoren:**
- **Magnetfeldstärke:** 1.5 Tesla vs. 3.0 Tesla  
- **MRT-Sequenzen:** T1, T2, SWI, VIBE etc.  
- **Untersuchungssetting:** Phantom vs. In-vivo  

---

## Methodik

Die Datenerhebung erfolgte zweistufig:

### 1. In-vitro (Phantom-Setup)
- Kontrollierte Messung von Pigmenten und Kosmetika  
- Applikation auf Kunsthaut und synthetischen Wimpern  
- Ziel: Isolierte Analyse der Materialeigenschaften  

### 2. In-vivo (Probanden)
- Validierung der klinischen Relevanz  
- Beispiele: Eyeliner, Mascara  

### Datenauswertung
- Vermessung der Artefaktflächen in **cm²**  
- Statistische Analyse mittels Python  

---

## Zentrale Ergebnisse & Abbildungen

Die finalen Grafiken sind im Repository als PDF-Dateien enthalten.

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

```
├── data/
│   ├── *.csv
│   │   ├── metadata.csv
│   │   ├── total_featuretable.csv
│   │   ├── df_summary.csv
│   │   └── spezifische_datensaetze.csv
│
├── images/
│   ├── *.png  (MRT-Aufnahmen nach Sequenz & Setting)
│
├── results/
│   ├── *.pdf  (finale Abbildungen)
│
├── notebooks/
│   └── muriel_auswertunge.ipynb
│
└── README.md
```

**Datensätze:**
- `metadata.csv`: Probenparameter (Sample_ID, Feldstärke, Objekt, Träger, Mode, Inhaltsstoffe)  
- `total_featuretable.csv`: Rohdaten  
- `df_summary.csv`: Aggregierter Datensatz  

---

## Installation & Nutzung

### 1. Voraussetzungen

Python sowie folgende Bibliotheken:

```python
import os
import numpy as np
import pandas as pd
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_theme(style="whitegrid")
```

---

### 2. Durchführung

1. Repository klonen oder Dateien lokal speichern  
2. Sicherstellen, dass sich `total_featuretable.csv` im selben Verzeichnis wie das Notebook befindet  
3. Jupyter Notebook starten:

```bash
jupyter notebook muriel_auswertunge.ipynb
```

4. Alle Zellen der Reihe nach ausführen  

---

## Methodische Hinweise

- Artefaktflächen wurden manuell in **cm²** vermessen  
- Daten wurden in CSV-Dateien strukturiert erfasst  
- Analyse erfolgt vollständig in einer Python-Umgebung  

**Hinweis:**  
Dieses Projekt dient ausschließlich wissenschaftlichen Zwecken im Rahmen der Ausbildung *Medizinisch-Technische Radiologie HF*.
