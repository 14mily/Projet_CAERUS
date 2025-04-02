# Rapport Technique Projet CAERUS - Générateur d'Impulsions

## Sommaire
1. [Introduction](#introduction)
2. [Analyse Fonctionnelle](#analyse-fonctionnelle)
3. [Matériel et Logiciels Utilisés 🖥️](#matériel-et-logiciels-utilisés)
4. [Schéma de Conception](#schéma-de-conception)
5. [Bancs de test et Validation](#bancs-de-test-et-validation)
6. [Démarche d'éco-conception](#démarche-d-éco-conception)
7. [Conclusion](#conclusion)
   
---

## Introduction
Dans le cadre des travaux pratiques en électronique analogique au semestre 5, nous avons eu à réaliser un projet nommé **CAERUS**. Il vise à mettre en application l’ensemble des connaissances acquises lors du semestre 5 à travers la conception, la simulation et la réalisation de circuits électroniques.

Le projet **CAERUS** est divisé en deux sous-projets : le convertisseur temps/amplitude et le générateur d’impulsions, un élément clé pour les applications de détection par ultrasons. C’est ce dernier qui fera l’objet de notre rapport.

### Objectifs 🎯
Le projet **CAERUS - Générateur d'Impulsions** vise à concevoir un circuit capable de générer une impulsion de **10 µs** sur une période de **100 ms** pour piloter le capteur **HC-SR04**. Ses objectifs sont :
- Concevoir un générateur d'impulsions fiable et stable.
- Utiliser des composants analogiques pour assurer la robustesse du système.
- Respecter une démarche d'éco-conception.
- Tester et valider le circuit sur breadboard avant intégration finale.
  
---
## Analyse Fonctionnelle

### Spécifications Techniques 🛠️
Le projet générateur d’impulsions a vu le jour dans un seul but : répondre aux besoins spécifiques qu’impliquent le bon fonctionnement du module
 **HC-SR04**. Ses spécifications techniques principales comprennent :
- la largeur d’impulsion : le module **HC-SR04** requiert une impulsion
 précise de **10µ𝑠** sur son entrée **TRIG** afin de déclencher l’émission du signal sonore
- la période : il doit y avoir un délai de **60ms** entre deux impulsions pour que le capteur puisse efficacement traiter les échos reçus. Dans le souci de garantir une marge, une période de **100ms** a été choisie pour nos impulsions.
- la tension d’alimentation : notre circuit doit être alimentée par une tension de **5V**
  
 Ces besoins exigent un circuit en mesure de produire une impulsion précise tout en répondant aux contraintes de coût, de consommation énergétique et de mise en œuvre.
 Ci-après, un tableau résumant les spécifications techniques de notre circuit :

| **Spécifications techniques**   | **Valeur**                            | **Description**                                          |
|---------------------------------|---------------------------------------|----------------------------------------------------------|
|  **Largeur d'impulsion**        | **10µs**                              | Valeur nécessaire pour l'activation du **HC-SR04**       |
|  **Période**                    | **100ms**                             | Espacement recommandé des impulsions                     |
|  **Tension d'alimentation**     | **5V**                                | En accord avec les spécifications du module              |
|  **Consommation énergétique**   | Faible                                | Important pour des systèmes embarqués à faible puissance |

---

## Matériel et Logiciels Utilisés
### Tableau des composants
| **Composant**         | **Référence** | **Rôle**                      | **Caractéristiques Principales**                  |
|-----------------------|---------------|-------------------------------|---------------------------------------------------|
| ⏱️ **Timer**          | **NE555**     | Génération du signal carré    | **Alimentation : 4.5V- 15V**, Fréquence ajustable |
| ⚖️ **Comparateur**    | **LT1011**    | Détection du seuil de tension | Faible consommation, sortie en collecteur ouvert  |
| 🔺 **Transistor PNP** | **2N2905A**   | Amplification et commutation  | **Courant max : 600mA**, **Tension max : 60V**    |
| 🔻 **Transistor NPN** | **2N2222**    | Commutation rapide            | **Courant max : 800mA**, **Tension max : 40V**    |
| 💡 **Diode** x 2      | **1N4148**    | Protection et redressement    | Diode rapide, faible capacité parasite            |
| 📡 **Capteur**        | **HC-SR04**   | Mesure de distance            | **Portée : 2cm - 400cm**, **Fréquence : 40 kHz**  |

### Logiciels
- LTSpice pour la simulation
- Altium Designer pour la conception du PCB

## Schéma de Conception
Un schéma du circuit sera ajouté ici (schéma LTSpice ou capture d’écran).

## Méthodologie
1. **Analyse fonctionnelle** : Définition des exigences et des contraintes.
2. **Simulation LTSpice** : Validation théorique du circuit.
3. **Montage sur breadboard** : Test pratique et ajustements.
4. **Validation avec oscilloscope** : Mesure des signaux générés.
5. **Optimisation et éco-conception** : Minimisation des pertes d'énergie.

## Résultats et Tests
- Capture d’oscilloscope des signaux obtenus.
- Comparaison entre simulation et résultats pratiques.
- Ajustements apportés si nécessaire.

## Conclusion
Un bilan des performances du circuit et des éventuelles améliorations futures.
