# 🏆⛵ ScoringChamp

*Outil de classement pour championnats de voile — fichier HTML autonome, sans installation.*

[![GitHub License](https://img.shields.io/github/license/Mttwt9/scoringChamp?style=flat-square&color=blue)](LICENSE)
[![GitHub Release](https://img.shields.io/github/v/release/Mttwt9/scoringChamp?style=flat-square&label=lastRelease&color=magenta)](https://github.com/Mttwt9/scoringChamp/releases/latest)

---

## 📖 Présentation

**ScoringChamp** est un outil de gestion et de publication de classements pour les championnats de voile FFVoile. Il s'agit d'un fichier HTML unique (sans dépendance externe, sans serveur) que vous ouvrez dans votre navigateur pour :

- importer les fichiers CSV notamment produits par la FFVoile étape par étape,
- calculer automatiquement le classement selon la règle A8 (Total, puis scores triés, puis ordre inverse des courses),
- configurer les pénalités DNA et Absent, les retraits (discards) par palier d'étapes, et les catégories de bateaux,
- publier le classement sous deux formes prêtes à l'emploi : **widget JavaScript** à coller dans WordPress ou tout CMS, et **page HTML autonome** téléchargeable.

---

## ✨ Fonctionnalités

- **Import multi-étapes** — un ou plusieurs fichiers CSV SCORE par étape, avec détection automatique du délimiteur et du type de fichier (intersérie / série).
- **Catégories et supports** — organisation en catégories (Dériveur, Wing, Multicoques…) avec supports inter ou non, classement intersérie scratch automatique.
- **Règle A8 FFVoile** — tri par total, puis par scores triés (meilleur en premier), puis ordre inverse des courses. Le tri s'applique sur les scores **après retraits**.
- **Retraits (discards)** — système polyvalent par paliers (ex : 1 retiré dès 4 étapes, 2 retirés dès 7…). Les scores retirés s'affichent barrés en diagonale ; la colonne Total affiche `Net [Brut]`. Le seuil est calculé sur le nombre d'étapes effectivement courus **par la série**, pas globalement.
- **Étapes non-retirables** — une case à cocher par étape pour protéger une course du retrait.
- **Filtres d'affichage** — par support (vue intersérie), catégorie d'âge et genre, sans recalcul des places.
- **Fusion manuelle de coureurs** — pour réconcilier des doublons sans numéro de licence.
- **Export CSV** — depuis toutes les vues (bouton par tableau), avec colonne Support systématique et notation `[score]` pour les scores retirés.
- **Impression / PDF** — bouton 🖨️ qui génère un en-tête (championnat, série, filtres actifs, date) et une légende des codes, puis ouvre le dialogue d'impression du navigateur (→ « Enregistrer en PDF »).
- **Widget WordPress** — classement interactif (onglets, filtres, recherche, export CSV) généré en JavaScript pur, à coller dans n'importe quel éditeur de code.
- **Page HTML autonome** — fichier HTML complet téléchargeable pour publier le classement sans CMS.
- **Thèmes** — clair, sombre, chaud. Persisté dans `localStorage`.
- **Sauvegarde/restauration** — état complet sauvegardé automatiquement dans `localStorage` et exportable en JSON pour archivage ou partage.

---

## 🚀 Utilisation

Aucune installation requise.

1. Cliquer ici pour démarrer l'application ou télécharger le fichier `scoringChamp.html` [![GitHub Release](https://img.shields.io/github/v/release/Mttwt9/scoringChamp?style=flat-square&label=dernière%20version&color=magenta)](https://github.com/Mttwt9/scoringChamp/releases/latest) pour l'utiliser en mode hors-ligne.
2. [Uniquement pour le mode offline] Ouvrir le fichier `scoringChamp.html` dans votre navigateur (Chrome ou Firefox recommandé).
3. Dans l'onglet **Étapes**, ajouter chaque étape et y glisser-déposer les fichiers CSV SCORE correspondants.
4. Dans l'onglet **Catégories**, configurer les supports, les catégories et les pénalités.
5. Cliquer sur **Calculer le classement**.
6. Dans l'onglet **Résultats**, consulter, filtrer et exporter le classement.
7. Dans l'onglet **Exports & Intégration**, récupérer le widget WordPress ou le fichier HTML autonome.

---

## 📂 Format des fichiers CSV attendus

L'outil accepte les exports CSV produits par la **FFVoile**, à l'aide du bouton _Exporter_ puis _Exporter en CSV_ dans la page d'un résultat (le bouton est à la fin de la page sur la droite). 

Les colonnes utilisées sont : numéro de voile, nom du coureur, numéro de licence, club, catégorie, genre, place, points.
Le délimiteur (virgule, point-virgule ou tabulation) est détecté automatiquement.

---

## ⚙️ Codes d'affichage

| Affichage | Signification |
|---|---|
| `1 (5)` | Place 1 — 5 points CSV |
| `ABS (28)` | Absent à l'étape — 28 points de pénalité |
| `DNA (31)` | Non classé sur l'épreuve (ex. DNF sur toutes les courses) — 31 points de pénalité |
| `—` | Pas de classement pour cette série à cette étape |
| Score barré en diagonale | Score retiré (discard) |
| `11 [19]` | Total net 11, total brut 19 (avant retrait) |
| `[8]` dans le CSV | Score retiré dans l'export |

---

## 🏗️ Architecture

Le projet tient entièrement dans **un seul fichier HTML**, sans dépendance externe ni framework. Il embarque :

- le moteur de parsing CSV et de calcul du classement,
- l'interface d'administration (gestion des étapes, catégories, paramètres),
- deux surfaces de publication : widget JavaScript (`simpleJS`) pour intégration dans un CMS et page HTML autonome (`widgetJS`),
- les styles pour trois thèmes (clair / sombre / chaud).

Toutes les modifications apportées à la logique de classement doivent être répercutées dans les trois surfaces.

---

## 📝 Licence

Ce projet est distribué sous licence [GNU AGPL v3](LICENSE).

En résumé : vous êtes libre d'utiliser, modifier et redistribuer ce code, y compris dans un contexte en ligne (hébergement, plugin CMS…), à condition de rendre disponible le code source de votre version modifiée sous la même licence.

---

## 🙋 Support / Contact

Pour toute question, suggestion ou bug, ouvrez une [issue sur GitHub](https://github.com/Mttwt9/scoringChamp/issues).
