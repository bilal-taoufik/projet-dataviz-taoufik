# Projet Data Viz - Analyse des décès en France

## Sommaire

1. [Présentation du projet](#présentation-du-projet)
2. [Source](#source)
3. [Volume des données](#volume-des-données)
4. [Structure des données](#structure-des-données)
5. [Persona](#persona)
6. [Problématique](#problématique)

## Présentation du projet

Ce projet a pour objectif de concevoir un dashboard interactif permettant d'explorer et d'analyser les décès enregistrés en France à partir des données disponibles sur data.gouv.fr.

L'analyse portera principalement sur la comparaison du nombre annuel moyen de décès entre les périodes 2015-2019 et 2020-2022, afin d'identifier les départements présentant les augmentations les plus importantes.

Le projet s'appuie sur une architecture de traitement de données utilisant :

- Docker
- Spark
- Delta Lake
- PostgreSQL
- Streamlit

## Source

**Nom :** Agrégation des fichiers des personnes décédées

**Période :** De janvier 1970 jusqu'en octobre 2026 (mis à jour tous les mois)

**Source :** [data.gouv.fr](https://www.data.gouv.fr/datasets/agregation-des-fichiers-des-personnes-decedees)

**Origine :** Fichiers des personnes décédées produits par l'INSEE, agrégés sur data.gouv.fr

**Format utilisé :** Parquet

**Licence :** Licence Ouverte

**Dernière mise à jour indiquée :** 16 octobre 2026

## Volume des données

Une première exploration du fichier Parquet avec PySpark a permis d'identifier :

**29 411 388 lignes**

Le volume des données dépasse donc le minimum de 2 millions de lignes demandé dans le cadre du projet.

## Structure des données

Le jeu de données contient les informations suivantes :

| Colonne | Description |
| :--- | :--- |
| `nom` | Nom de famille |
| `prenoms` | Prénoms, séparés par des virgules |
| `sexe` | Sexe (M pour masculin, F pour féminin) |
| `date_naissance` | Date de naissance au format AAAAMMJJ (des 0 indiquent une partie inconnue) |
| `code_insee_naissance` | Code INSEE du lieu de naissance |
| `commune_naissance` | Nom de la commune de naissance |
| `pays_naissance` | Pays de naissance |
| `date_deces` | Date de décès au format AAAAMMJJ (des 0 indiquent une partie inconnue) |
| `code_insee_deces` | Code INSEE du lieu de décès |
| `numero_acte_deces` | Numéro d'acte de décès |
| `fichier_origine` | Fichier source dont provient l'enregistrement |
| `opposition` | Booléen indiquant si une opposition a été enregistrée (True ou False) |

## Persona

### Profil

**Fonction :** Journaliste spécialisé dans l'analyse de données.

**Mission :** Comprendre et expliquer l'évolution des décès en France à travers des chiffres et des graphiques accessibles au grand public.

### Besoins

Le journaliste souhaite :

- Comparer le nombre de décès entre les périodes 2015-2019 et 2020-2022.
- Identifier les départements où le nombre de décès a le plus augmenté.
- Visualiser les différences entre les départements.
- Repérer les territoires qui méritent une analyse plus approfondie.
- Utiliser les graphiques du dashboard pour préparer ses articles.

### Fréquence d'utilisation

Le tableau de bord sera utilisé lors de la préparation d'articles ou de reportages, notamment pour analyser les tendances annuelles et comparer différentes périodes.

## Problématique

**Quels départements français ont connu les plus fortes augmentations du nombre annuel moyen de décès sur la période 2020-2022, par rapport à la période 2015-2019 ?**

L'objectif du dashboard est de permettre au journaliste d'identifier rapidement les tendances importantes et de les présenter au grand public à travers des visualisations simples et compréhensibles.

Décision éditoriale : sélectionner les départements à étudier en priorité pour préparer un article sur l'évolution des décès durant la période 2020-2022.