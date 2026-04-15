# Artefaktbildung durch kutane Pigmente in der Magnetresonanztomographie

***In vitro*- und *in vivo*-Analyse von Tattoos, Permanent Make-up und Kosmetika**

---

## Autorin & Einordnung

- **Autorin:** Calibran Muriel  
- **Institution:** BZG Bildungszentrum Gesundheit Basel-Stadt  
- **Bildungsgang:** Medizinisch-Technische Radiologie HF (BG MTR 23H)  
- **Eingereicht:** Münchenstein 01.05.2026

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

Ziel der Arbeit ist die systematische Quantifizierung von Suszeptibilitätsartefakten, die durch metallhaltige Pigmente in Alltagsprodukten verursacht werden, um die diagnostische Sicherheit zu erhöhen.

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
- `df_summary.csv`: Rohdaten aus `total_featuretable.csv` wurden verwendet. Duplikate (*in vivo*) und Triplikate (*in vitro*) wurden zu Mittelwerten und Standardabweichungen zusammengefasst und Probenspezifische Metadaten in den Datensatz integriert. Das resultierende `df_summary.csv` bildet die Grundlage für die statistische Auswertung.
---

## Statistische Auswertung

  

---

## Methodische Hinweise

- Artefaktflächen wurden manuell in cm² vermessen  
- Daten wurden in CSV-Dateien strukturiert erfasst  
- Die Analyse erfolgt in einer Python-Umgebung  

**Hinweis:**  
Dieses Projekt dient ausschließlich wissenschaftlichen Zwecken im Rahmen der Ausbildung *Medizinisch-Technische Radiologie HF*.
