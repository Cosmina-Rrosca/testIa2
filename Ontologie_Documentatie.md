# Documentație Ontologie: Mobile Robot Diagnosis
## Ontologie pentru Modelarea Problemei de Diagnoză a Robotului Mobil

**Versiune:** 1.0  
**Autor:** Generat automat  
**Compatibilitate:** Protégé 5.6.9+  
**Format:** OWL/XML (RDF)

---

## 1. PREZENTARE GENERALĂ

Această ontologie modelează domeniul de diagnoză pentru un robot mobil, permițând reprezentarea componentelor hardware, a senzorilor, actuatorilor, defectelor posibile și a relațiilor dintre acestea. Ontologia facilitează raționamentul automat pentru identificarea și diagnosticarea problemelor tehnice.

---

## 2. STRUCTURA CLASELOR (10 Clase)

### 2.1. Ierarhia Claselor

```
Componenta (Clasa de Bază)
├── Senzor
│   ├── SenzorLidar
│   └── SenzorUltrasonic
├── Actuator
│   ├── Motor
│   └── Roata
└── Defect
    ├── DefectSenzor
    └── DefectActuator
```

### 2.2. Descrierea Detaliată a Claselor

| Nr. | Nume Clasă | URI | Clasă Părinte | Descriere |
|-----|------------|-----|---------------|-----------|
| 1 | **Componenta** | `#Componenta` | - | Clasa de bază pentru toate componentele robotului mobil. Toate celelalte clase derivă direct sau indirect din aceasta. |
| 2 | **Senzor** | `#Senzor` | Componenta | Reprezintă senzorii utilizați pentru percepția mediului înconjurător. |
| 3 | **Actuator** | `#Actuator` | Componenta | Reprezintă actuatoarele responsabile pentru mișcarea și acțiunea robotului. |
| 4 | **Defect** | `#Defect` | Componenta | Clasă abstractă pentru reprezentarea tuturor tipurilor de defecte posibile. |
| 5 | **SenzorLidar** | `#SenzorLidar` | Senzor | Senzor LiDAR pentru detecția distanțelor și crearea de hărți ale mediului. |
| 6 | **SenzorUltrasonic** | `#SenzorUltrasonic` | Senzor | Senzor ultrasonic pentru detecția obstacolelor la distanțe scurte. |
| 7 | **Motor** | `#Motor` | Actuator | Motor electric pentru propulsia robotului. |
| 8 | **Roata** | `#Roata` | Actuator | Roți pentru locomoția robotului pe suprafață. |
| 9 | **DefectSenzor** | `#DefectSenzor` | Defect | Defecte specifice care pot apărea la senzori (calibrare, citire eronată, etc.). |
| 10 | **DefectActuator** | `#DefectActuator` | Defect | Defecte specifice care pot apărea la actuatoare (supraîncălzire, blocare, etc.). |

### 2.3. Clase Derivate (Minim 4 cerute - Avem 8)

Următoarele clase sunt derivate din alte clase de bază:

1. **Senzor** → derivată din **Componenta**
2. **Actuator** → derivată din **Componenta**
3. **Defect** → derivată din **Componenta**
4. **SenzorLidar** → derivată din **Senzor**
5. **SenzorUltrasonic** → derivată din **Senzor**
6. **Motor** → derivată din **Actuator**
7. **Roata** → derivată din **Actuator**
8. **DefectSenzor** → derivată din **Defect**
9. **DefectActuator** → derivată din **Defect**

---

## 3. PROPRIETĂȚI OBIECT (Object Properties) - 4 Sloturi

Proprietățile obiect definesc relații între indivizi din ontologie.

| Nume Proprietate | URI | Domeniu (Domain) | Codomeniu (Range) | Descriere |
|------------------|-----|------------------|-------------------|-----------|
| **areDefect** | `#areDefect` | Componenta | Defect | Relație care indică faptul că o componentă are un defect asociat. |
| **areParteDin** | `#areParteDin` | Componenta | Componenta | Relație de compunere care indică apartenența unei componente la o altă componentă. |
| **detecteaza** | `#detecteaza` | Senzor | Componenta | Relație care indică ce entitate este detectată de un senzor. |
| **actioneaza** | `#actioneaza` | Actuator | Componenta | Relație care indică asupra cărei componente acționează un actuator. |

---

## 4. PROPRIETĂȚI DE DATE (Data Properties) - 4 Sloturi

Proprietățile de date definesc relații între indivizi și valori literale (string, int, float, dateTime).

| Nume Proprietate | URI | Domeniu (Domain) | Tip Date (Range) | Descriere |
|------------------|-----|------------------|-----------------|-----------|
| **areValoareCitire** | `#areValoareCitire` | Senzor | xsd:float | Valoarea numerică citită de la un senzor (ex: distanță în metri). |
| **areNivelBaterie** | `#areNivelBaterie` | Componenta | xsd:integer | Nivelul bateriei exprimat ca procent (0-100). |
| **areCodEroare** | `#areCodEroare` | Defect | xsd:string | Codul alfanumeric de eroare asociat unui defect (ex: "E001"). |
| **areTimpDetectie** | `#areTimpDetectie` | Defect | xsd:dateTime | Data și ora când a fost detectat defectul (format ISO 8601). |

---

## 5. INDIVIZI (INSTANȚE) - 12 Indivizi

### 5.1. Instanțe din clasa SenzorLidar

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **lidarFrontal** | `#lidarFrontal` | areValoareCitire | 2.5 (metri) |
| **lidarPosterior** | `#lidarPosterior` | areValoareCitire | 1.8 (metri) |

### 5.2. Instanțe din clasa SenzorUltrasonic

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **ultrasonicStanga** | `#ultrasonicStanga` | areValoareCitire | 0.5 (metri) |
| **ultrasonicDreapta** | `#ultrasonicDreapta` | areValoareCitire | 0.7 (metri) |

### 5.3. Instanțe din clasa Motor

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **motorStanga** | `#motorStanga` | areNivelBaterie | 85 (%) |
| **motorDreapta** | `#motorDreapta` | areNivelBaterie | 90 (%) |

### 5.4. Instanțe din clasa Roata

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **roataStangaFata** | `#roataStangaFata` | - | - |
| **roataDreaptaFata** | `#roataDreaptaFata` | - | - |

### 5.5. Instanțe din clasa DefectSenzor

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **defectCalibrareLidar** | `#defectCalibrareLidar` | areCodEroare | "E001" |
| **defectCitireUltrasonic** | `#defectCitireUltrasonic` | areCodEroare | "E002" |

### 5.6. Instanțe din clasa DefectActuator

| Nume Individ | URI | Proprietăți | Valori |
|--------------|-----|-------------|--------|
| **defectSupraincalzireMotor** | `#defectSupraincalzireMotor` | areCodEroare | "E003" |
| **defectBlocareRoata** | `#defectBlocareRoata` | areCodEroare | "E004" |

---

## 6. RELAȚII ÎNTRE INDIVIZI

| Subiect | Predicat (Proprietate) | Obiect | Semnificație |
|---------|----------------------|--------|--------------|
| lidarFrontal | areDefect | defectCalibrareLidar | LiDAR-ul frontal are un defect de calibrare |
| motorStanga | areDefect | defectSupraincalzireMotor | Motorul stâng are un defect de supraîncălzire |
| roataStangaFata | areDefect | defectBlocareRoata | Roata stânga față are un defect de blocare |

---

## 7. INSTRUCTIUNI DE UTILIZARE ÎN PROTÉGÉ 5.6.9

### 7.1. Încărcarea Ontologiei

1. Deschideți Protégé 5.6.9
2. Mergeți la **File** → **Open from URL...** sau **File** → **Open from File...**
3. Selectați fișierul `MobileRobotDiagnosis.owl`
4. Ontologia se va încărca cu toate clasele, proprietățile și indivizii

### 7.2. Vizualizarea Elementelor

- **Clase**: Accesați tasta **Entities** → **Classes** pentru a vedea ierarhia claselor
- **Proprietăți**: Accesați **Entities** → **Object Properties** sau **Data Properties**
- **Indivizi**: Accesați **Entities** → **Individuals** pentru a vedea toate instanțele

### 7.3. Raționament (Reasoning)

1. Mergeți la **Reasoner** → **Start reasoner**
2. Selectați un reasoner (ex: HermiT, Pellet, sau FaCT++)
3. Reasoner-ul va infera noi relații și va valida consistența ontologiei

### 7.4. Interogări (DL Query)

Exemple de interogări în tab-ul **DL Query**:

```
// Găsește toți senzorii
Senzor

// Găsește toate componentele cu defecte
Componenta and areDefect some Defect

// Găsește toate defectele de senzor
DefectSenzor

// Găsește motoarele cu nivel baterie sub 90%
Motor and areNivelBaterie value < 90
```

---

## 8. SCENARII DE UTILIZARE

### 8.1. Diagnoza Automatizată

Ontologia permite:
- Identificarea componentelor defecte
- Clasificarea tipurilor de defecte
- Corelarea simptomelor cu cauzele posibile

### 8.2. Mentenanță Predictivă

Prin monitorizarea valorilor senzorilor și a codurilor de eroare, sistemul poate:
- Detecta anomalii înainte de producerea defectelor
- Programa intervenții de mentenanță

### 8.3. Suport pentru Decizie

Ontologia oferă o bază de cunoștințe structurată pentru:
- Sisteme expert de diagnoză
- Asistenți virtuali pentru tehnicieni
- Rapoarte automate de stare a robotului

---

## 9. EXTENSII VIITOARE

Posibile îmbunătățiri ale ontologiei:

1. **Adăugarea de reguli SWRL** pentru inferențe complexe
2. **Extinderea cu mai multe tipuri de senzori** (camere, IMU, GPS)
3. **Modelarea proceselor de diagnoză** ca fluxuri de lucru
4. **Integrarea cu sisteme IoT** pentru monitorizare în timp real
5. **Adăugarea de axiome de echivalență** pentru clase

---

## 10. REFERINȚE TEHNICE

- **Format ontologie**: OWL 2 DL
- **Namespace**: `http://www.semanticweb.org/robotdiag/ontologies/2024/1/MobileRobotDiagnosis#`
- **Encodare**: UTF-8
- **Limbaj etichete**: Română (ro)

---

## 11. REZUMAT STATISTICI

| Element | Count |
|---------|-------|
| Clase | 10 |
| Clase derivate | 9 |
| Object Properties | 4 |
| Data Properties | 4 |
| Indivizi | 12 |
| Relații între indivizi | 3 |

---

**Document generat pentru ontologia MobileRobotDiagnosis.owl**  
*Data generării: 2024*
