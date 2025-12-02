# xai_iot — Internship Research: Enabling XAI in IoT‑enhanced Spaces

Ce projet a été réalisé dans le cadre d’un stage de recherche, et explore l’application de l’**Explainable AI (XAI)** dans des environnements IoT (objets/espaces connectés), avec un accent particulier sur la **détection et l’explication des data‑drifts**.

---

## 📌 Sommaire

- [xai\_iot — Internship Research: Enabling XAI in IoT‑enhanced Spaces](#xai_iot--internship-research-enabling-xai-in-iotenhanced-spaces)
  - [📌 Sommaire](#-sommaire)
  - [🎯 Objectif du projet](#-objectif-du-projet)
  - [✨ Fonctionnalités / Approches principales](#-fonctionnalités--approches-principales)
  - [🧩 Structure du projet / Architecture](#-structure-du-projet--architecture)
  - [🚀 Installation \& Déploiement](#-installation--déploiement)
  - [🛠️ Technologies \& Outils utilisés](#️-technologies--outils-utilisés)
  - [👥 Auteur \& Licence](#-auteur--licence)
  
---

## 🎯 Objectif du projet

- **Détecter les data drifts** (variations dans la distribution des données d’entrée) grâce à des techniques statistiques et des détecteurs adaptés.  
- **Analyser la corrélation entre data drift et concept drift** : comprendre quand un changement dans la distribution des données affecte le comportement ou la performance d’un modèle prédictif.  
- **Expliquer l’impact des data drifts** : identifier les variables/features responsables du changement, et observer comment elles influencent les performances ou les décisions du modèle.  

---

## ✨ Fonctionnalités / Approches principales

- Implémentation d’un **détecteur HDDDM** pour la détection de data drift (via le dossier `HDDDM`).  
- Utilisation de plusieurs **detecteurs de concept drift / data drift** (via le dossier `data-drifts-detection`) — comme D3, ADWIN, EDDM — combinés à des métriques de divergence (ex : distance de Hellinger, divergence KL) pour quantifier les changements.  
- Prise en charge de **datasets variés** (depuis `concept-drift-datasets-scikit-multiflow-master`) pour tester les détections sur des cas réels ou réalistes.  
- Scripts pour exécuter les détecteurs avec paramètres customisés, analyser les résultats et générer des visualisations / statistiques.  
- Un dossier `results` contenant les résultats des expérimentations — utile pour comparer les performances, visualiser les drifts, etc.  

---

## 🧩 Structure du projet / Architecture

```text
/ (racine)
├── HDDDM/                 # Implémentation du détecteur HDDDM (data drift)
├── data-drifts-detection/ # Autres détecteurs de drift (D3, ADWIN, EDDM, etc.) + versions avec Hellinger/KL
    └── results/              # Résultats des analyses / expérimentations
└── concept-drift-datasets-scikit-multiflow-master/ # Jeux de données utilisés pour les tests
```

---

## 🚀 Installation \& Déploiement

Exemple d’utilisation :

```python
# Pour exécuter le détecteur D3 sur un dataset
python .\data-drifts-detection\<detector.py> <dataset> <size of the old data> <percentage of new data with respect to old> <threshold for auc>

# Exemple
python ./data-drifts-detection/D3.py ./concept-drift-datasets-scikit-multiflow-master/real-world/elec.csv 100 0.1 0.7

# Pour exécuter ADWIN ou EDDM :
python .\data-drifts-detection\<detector.py> <dataset> <size of the old data> <percentage of new data with respect to old>

# Exemple
python ./data-drifts-detection/ADWIN.py ./concept-drift-datasets-scikit-multiflow-master/real-world/elec.csv 100 0.1

# Pour générer les versions avec Hellinger + KL divergence :
python ./data-drifts-detection/D3_hellinger_kl.py ...
```

- Les paramètres attendus sont, par exemple :

1. Le chemin vers le dataset CSV,
2. La taille de l’ancien segment de données,
3. Le pourcentage de nouvelles données,
4. Un seuil éventuellement (pour AUC ou autre selon le détecteur).

- Les résultats (indicateurs de drift, alertes, graphiques, logs) seront sauvegardés dans le dossier results/.

---

## 🛠️ Technologies & Outils utilisés

| Technologie         | Rôle              |
| ------------------- | ----------------- |
| **Python**          | Langage principal des scripts et notebooks |
| **Jupyter Notebook**             | Expérimentation, analyse des résultats et visualisation |
| **Bibliothèques (pandas, numpy, …)**          | Manipulation des données et calculs statistiques |
| **Détecteurs de drift (HDDDM, ADWIN, EDDM, D3…)**             | Identifier des changements dans les flux de données |
| **Métriques statistiques**             | Comparer distributions d’avant vs après |

---

## 👥 Auteur & Licence

- **Auteur** : Nathan Chrismant — Étudiant M2 Informatique, ENSEA / Cergy Paris Université.

Projet distribué sous licence **Open Source**.
