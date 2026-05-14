# 🏢 Simulation d'un Ascenseur Intelligent

> Mini-projet Java — Programmation Concurrente avec Multithreading et Sémaphores

![Java](https://img.shields.io/badge/Java-17%2B-orange?style=flat-square&logo=java)
![Swing](https://img.shields.io/badge/GUI-Swing-blue?style=flat-square)
![Threads](https://img.shields.io/badge/Threads-Multithreading-green?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)

---

## 📋 Description

Simulation graphique d'un ascenseur intelligent dans un immeuble de **5 étages** (0 à 4).
Des personnes sont générées aléatoirement, attendent dans une file FIFO à leur étage,
et l'ascenseur les transporte selon sa direction courante avec une capacité maximale de **4 personnes**.

---

## 🎯 Fonctionnalités

- Génération aléatoire de personnes en temps réel
- Files d'attente FIFO par étage
- Capacité maximale stricte de 4 personnes (sémaphore)
- Stratégie de déplacement SCAN (l'ascenseur ne change de direction qu'aux extrêmes)
- Interface graphique Swing animée avec boutons START / STOP
- Panneau d'information : étage actuel, direction, passagers et destinations

---

## 🧵 Architecture Concurrente

| Thread | Rôle |
|--------|------|
| `Thread-Ascenseur` | Déplacement, embarquement, débarquement |
| `Thread-Generateur` | Création aléatoire de personnes toutes les secondes |

**Synchronisation :**
- `synchronized` sur toutes les méthodes accédant aux files d'attente
- `Semaphore(4)` pour la capacité de la cabine
- `wait() / notifyAll()` pour mettre l'ascenseur en veille quand personne n'attend

---

## 🗂️ Structure du projet

```
src/
└── org/
    └── services/
        ├── Personne.java           # Entité passager (données + état)
        ├── Etat.java               # Enum : WAITING, INSIDE, ARRIVE
        ├── Etage.java              # File FIFO synchronisée
        ├── Ascenseur.java          # Thread principal de déplacement
        ├── GenerateurPersonne.java # Thread de génération aléatoire
        └── SimulationGUI.java      # Interface Swing + main()
```

---

## 🚀 Lancer le projet

### Prérequis
- Java 17+
- Aucune dépendance externe

### Compilation et exécution

```bash
# Compiler
javac -d out src/org/services/*.java

# Lancer
java -cp out org.services.SimulationGUI
```

### Depuis IntelliJ / Eclipse
Ouvrir le projet, exécuter la méthode `main` dans `SimulationGUI.java`.

---

## 📸 Interface

<!-- Remplacez cette ligne par une vraie capture d'écran -->
> _Ajoutez ici une capture d'écran de la simulation en cours_

---

## 🔧 Concepts mis en pratique

- **Multithreading** — `Thread`, `Runnable`
- **Sémaphores** — `java.util.concurrent.Semaphore`
- **Synchronisation** — `synchronized`, `wait()`, `notifyAll()`
- **Collections** — `LinkedList` (FIFO), `Iterator` pour suppression sûre
- **Swing** — `JFrame`, `JPanel`, `paintComponent()`, `Timer`



> Projet réalisé dans le cadre du cours de Programmation Concurrente
