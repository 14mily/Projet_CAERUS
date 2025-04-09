# Rapport Technique Projet CAERUS - 🔊 Générateur d’Impulsions pour Capteur HC-SR04

## 📑 Sommaire

1. [📚 Description du projet](#-description-du-projet)

2. [🎯 Objectifs pédagogiques et techniques](#-objectifs-pédagogiques-et-techniques)

3. [⚙️ Spécifications techniques](#-spécifications-techniques)

4. [🧩 Architecture du circuit](#-architecture-du-circuit)

5. [🔍 Choix et calcul des composants](#-choix-et-calcul-des-composants)

      - [⏱ Durée de l’impulsion – NE555](#-durée-de-limpulsion--ne555)
      
      - [⚡ Seuil de déclenchement – LT1011](#-seuil-de-déclenchement--lt1011)

6. [🧪 Méthodologie de développement](#-méthodologie-de-développement)

7. [🛠️ Problèmes rencontrés et solutions](#️-problèmes-rencontrés-et-solutions)

8. [🌱 Éco-Conception : Analyse du cycle de vie](#-éco-conception--analyse-du-cycle-de-vie)

      - [🌍 Fabrication](#-fabrication)
      
      - [🚛 Transport](#-transport)
      
      - [🔌 Utilisation](#-utilisation)
      
      - [🔄 Fin de vie](#-fin-de-vie)
      
      - [💡 Pistes d’amélioration](#-pistes-damélioration)

9. [✅ Résultats et intégration](#-résultats-et-intégration)

10. [🖼️ Annexes disponibles](#-annexes-disponibles)

11. [👩‍💻 Équipe projet](#-équipe-projet)
    
---

## 📚 Description du projet

Ce projet s’inscrit dans le cadre du module d’électronique analogique du semestre 5 à l'[ESEO](https://www.eseo.fr/). Il constitue le second volet du projet **CAERUS**, axé sur la **conception, simulation et réalisation de circuits électroniques analogiques**.

Le système développé est un **générateur d’impulsions monostable**, destiné à piloter le capteur ultrason **HC-SR04**, en produisant une impulsion stable de **10 µs toutes les 100 ms** sur l'entrée TRIG.

---

## 🎯 Objectifs pédagogiques et techniques

- Appliquer les connaissances en électronique analogique : NE555, comparateurs, transistors
- Utiliser des outils professionnels : **LTSpice**, **oscilloscope**, **générateur de fonctions**
- Réaliser un circuit électronique **réel**, à partir d'une **spécification technique précise**
- Intégrer une démarche **d’éco-conception** dans un projet d’électronique

---

## ⚙️ Spécifications techniques

| Paramètre                  | Valeur                            | Raison / Impact                      |
|---------------------------|-----------------------------------|--------------------------------------|
| Largeur d’impulsion        | 10 µs                             | Nécessaire pour activer le HC-SR04   |
| Période                    | 100 ms                            | Permet au capteur de traiter les échos |
| Alimentation               | 5 V DC                            | Compatible avec le module HC-SR04    |
| Consommation               | Faible                            | Utilisation dans systèmes embarqués  |
| Format de signal TRIG     | Carré, 0-5V                       | Respect des niveaux logiques requis  |

---

## 🧩 Architecture du circuit

Le montage s’articule en **3 blocs fonctionnels** :

1. **Détection du signal d’entrée** :  
   - Composant : **LT1011**
   - Fonction : Comparaison de la tension d’entrée avec un seuil (2.5 V)

2. **Génération de l’impulsion** :  
   - Composant : **NE555 en mode monostable**
   - Fonction : Génère une impulsion précise de 10 µs

3. **Adaptation et amplification** :  
   - Composants : **Transistors 2N2222 (NPN) et 2N2905A (PNP)**
   - Fonction : Adapter le signal à la charge du HC-SR04

---

## 🔍 Choix et calcul des composants

### ⏱ Durée de l’impulsion – NE555

- Formule : `t = 1.1 × R × C`
- Valeurs utilisées :
  - `R = 10 kΩ`
  - `C = 1 nF`
- Résultat : `t ≈ 11 µs` (légèrement au-dessus de la cible, acceptable en pratique)

### ⚡ Seuil de déclenchement – LT1011

- Formule : `Vref = Vcc × (R2 / (R1 + R2))`
- Objectif : `Vref = 2.5 V`
- Valeurs choisies : `R1 = R2 = 1 kΩ`

---

## 🧪 Méthodologie de développement

### 1. **Simulation sous LTSpice**

- Simulation par blocs :
  - Comparateur seul
  - NE555 monostable
  - Transistors
- Validation des signaux de sortie (forme, durée, niveaux logiques)

### 2. **Montage physique sur breadboard**

- Alimentation : alimentation stabilisée 5 V
- Générateur de signaux : entrées test carrées / rampes
- Observation : oscilloscope pour signaux en sortie du NE555 et LT1011

### 3. **Tests et validation**

- Largeur d’impulsion mesurée : ~11 µs
- Période mesurée : ~95 ms
- Résultat : fonctionnel et conforme aux contraintes du HC-SR04

---

## 🛠️ Problèmes rencontrés et solutions

| Problème                                  | Solution appliquée                           |
|------------------------------------------|----------------------------------------------|
| Largeur d’impulsion trop longue          | Ajustement des valeurs R/C + resimulation    |
| Problème de déclenchement instable       | Ajout du comparateur LT1011 pour stabilité   |
| Signal trop faible pour HC-SR04          | Intégration des transistors pour adaptation  |
| Écart simulation / réalité               | Prise en compte des tolérances et pertes     |

---

## 🌱 Éco-Conception : Analyse du cycle de vie

### 🌍 Fabrication

- Consommation estimée : **~7.4 kWh**
- Émissions associées : **~4 kg CO₂**
- Matières premières : silicium, plastique, aluminium

### 🚛 Transport

- Distance estimée : 10 000 km
- Impact carbone : **~0.5 kg CO₂**

### 🔌 Utilisation

- Durée de vie : 5 ans
- Consommation cumulée : **~8.76 kWh**
- Émissions : **~5 kg CO₂**

### 🔄 Fin de vie

- Recyclabilité partielle (10-15%)
- Poids déchets électroniques : ~50g

### 💡 Pistes d’amélioration

- Réduction du nombre de composants passifs
- Composants intégrés multifonctions
- Alimentation solaire / batteries rechargeables
- Documentation de maintenance (approche “réparable”)

---

## ✅ Résultats et intégration

- Le circuit s’intègre parfaitement au **projet de mesure de distance**
- Les impulsions générées déclenchent correctement le HC-SR04
- Les mesures obtenues sont fiables, stables et régulières
- L'ensemble respecte les contraintes de consommation, coût, et taille

---

## 🖼️ Annexes disponibles

### Schémas LTSpice (par blocs et final)

<img align = left src="https://github.com/user-attachments/assets/8b433a8c-a161-45cd-984c-6aad9a738680" alt="NE555" width="70%">
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🔧 Circuit de simulation du NE555** : Cette simulation montre la configuration du NE555 en mode monostable, utilisée pour générer l'impulsion de 10 µs. Les composants R et C sont sélectionnés pour calibrer précisément cette durée.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/ba6a4b94-07de-40d6-ac1d-0b9f679fd8b8" alt="Resultats NE555" width="70%">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**📈 Résultats de la simulation du NE555** : Visualisation de l’impulsion carrée générée par le NE555. L’oscillogramme confirme la bonne largeur temporelle du signal requis pour le TRIG du HC-SR04.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/a31a09b9-6721-42bb-8196-f1a98f75551d" alt="TL081" width="70%">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🧠 Circuit de simulation du TL081** : Ce montage alternatif testait l’utilisation du TL081 en tant que comparateur. Bien que fonctionnel, il a été remplacé par le LT1011 pour des raisons de stabilité temporelle et d’impulsion de sortie plus nette.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/25424ad5-8ca8-4cb3-adbe-90a6b308765d" alt="Resultats TL081" width="70%">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**📉 Résultats de la simulation du TL081** : Les résultats révèlent une réponse moins franche du comparateur TL081 par rapport au LT1011. Le front montant est plus lent, ce qui a motivé son remplacement.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/60d5f901-18ac-4894-90c9-8226715e565f" alt="Final" width="70%">
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🔁 Circuit de simulation final du projet** : Schéma complet incluant les trois blocs : détection, génération, et adaptation. Chaque composant interagit pour produire une impulsion stable, amplifiée et conforme aux besoins du module HC-SR04.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/14bb64e5-0c5c-4502-8661-e3083896eae6" alt="Final Resultat" width="70%">
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🔬 Résultats de la simulation du circuit** : Oscillogramme du circuit global. On y observe les interactions entre les blocs, notamment la stabilité de l’impulsion et la réponse rapide du système à l’entrée.

<br clear = left>
<br>

### Pé-Routage et PCB sur Altium Designer

<img align = left src="https://github.com/user-attachments/assets/e864ef39-869f-4ed7-ab2c-e167a530e516" alt="Altium Final" width="70%">
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**📐 Circuit final du projet sur Altium Designer** : Représentation CAO du circuit complet sur Altium Designer. Positionnement logique et compact des composants pour minimiser la longueur des pistes.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/67acebcb-1b8e-418a-a989-e7ed4fb6c983" alt="Routage" height="30%">

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🔌 Pré-routage du projet sur Altium Designer** : Cette simulation montre la configuration du NE555 en mode monostable, utilisée pour générer l'impulsion de 10 µs. Les composants R et C sont sélectionnés pour calibrer précisément cette durée.

<br clear = left>
<br>

<img align = left src="https://github.com/user-attachments/assets/3381babe-6712-406e-b492-3db8672d11fa" alt="PCB" height="30%">
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**🧾 PCB du projet sur Altium Designer** : Version finale du circuit imprimé, ce PCB reflète la structure validée à la fois en simulation et sur breadboard.

<br clear = left>
<br>

---

## 👩‍💻 Équipe projet

- 👩‍🔬 Émilie GNASSINGBE [@14mily](https://github.com/14mily/)
- 👨‍🔬 Kenneth NONVIGNON [@purplekan](https://github.com/purplekan/)
