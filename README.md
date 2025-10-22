# UNLocBoX

# 🔬 TPE: Analyse Convexe et Optimisation Proximale avec UNLOCBOX

## Introduction

Ce projet porte sur l'exploration et l'application des concepts d'**Analyse Convexe** et d'**Optimisation Proximale** via la bo\^ite à outils MATLAB, **UNLOCBOX** (Unconstrained and non-smooth convex optimization using proximal algorithms).

L'objectif principal est de fournir une documentation complète et des exemples pratiques pour l'utilisation d'UNLocBox dans la résolution de problèmes inverses et de régularisation en traitement du signal et d'image.

---

## 🎯 Objectifs et Livrables du Projet

Le projet a été structuré autour de deux livrables majeurs :

### 1. Présentation Complète de UNLOCBOX (Slides)

Une présentation de **15 à 20 slides** décrivant l'environnement, les principes théoriques et l'application pratique d'UNLocBox.* `Presentation UNLocBoX_guide.pdf`

### 2. Tutoriels Détaillés avec Scripts MATLAB

Deux tutoriels au format PDF (générés en LaTeX) décrivant pas à pas l'implémentation de modèles d'optimisation clés, avec tous les scripts MATLAB joints.

| Tutoriel | Problème d'Analyse Convexe | Algorithme Principal | Fichiers Clés |
| :--- | :--- | :--- | :--- |
| **Tutoriel 1** | **Inpainting d'Image par Variation Totale (TV)** | Douglas-Rachford (Proximal-Proximal) | `Tutoriel1.pdf` |
| **Tutoriel 2** | **Débruitage par Pénalisation L1 ou L2** | FISTA (Proximal-Différentiable) | `Tutoriel_2.pdf` |

---

## 🛠️ Contenu du Repository

Ce repository est organisé autour des dossiers suivants :

* `./Doc/` : Contient les Cahiers de suivi de projet des différents membres.

---

## 🚀 Tutoriel 1 : Inpainting d'Image par Variation Totale (TV)

Ce tutoriel est crucial pour comprendre la résolution d'un problème impliquant **deux fonctions non-différentiables** (TV pour la régularisation et Projection L2 pour la contrainte de fidélité).

* **Problème** : $\min_{\mathbf{x}} ||\mathbf{x}||_{TV} \quad \text{s.c.} \quad ||\mathbf{A}\mathbf{x} - \mathbf{y}||_2 \leq \epsilon$
* **Solveur** : **Douglas-Rachford**, qui utilise les opérateurs `prox_tv` et `proj_l2_ball`.

### Aperçu de l'approche

L'inpainting est traité comme une minimisation de la TV (qui assure la régularité et les bords nets) soumise à une contrainte stricte de fidélité aux données observées. Le script illustre la définition des opérateurs $\mathbf{A}$ et $\mathbf{A}^\star$ pour le masquage/démasquage des pixels.

---

## 🌊 Tutoriel 2 : Débruitage par Pénalisation L1 ou L2

Ce tutoriel aborde le modèle standard de régularisation, souvent résolu par l'algorithme FISTA (Fast Iterative Shrinkage-Thresholding Algorithm).

* **Problème** : $\min_{\mathbf{x}} \frac{1}{2}||\mathbf{x}-\mathbf{y}||_{2}^{2} + \lambda R(\mathbf{x})$
* **Régularisation ($R(\mathbf{x})$)** :
    * **$L_1$ (Lasso)** : Favorise la **sparsité** et produit des solutions exactes (seuillage doux).
    * **$L_2$ (Tikhonov)** : Favorise la **douceur** et produit des solutions lissées.
* **Solveur** : **FISTA**, adapté lorsque l'une des fonctions est différentiable (terme de fidélité $L_2$).
