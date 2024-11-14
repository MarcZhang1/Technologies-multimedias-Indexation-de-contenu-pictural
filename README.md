
# Indexation de Contenu Pictural

Ce projet consiste à développer un algorithme permettant de retrouver une vidéo à partir d'une image donnée, en utilisant une banque de vidéos et des images de référence. L'algorithme identifie la vidéo correspondante et le minutage de l'image si celle-ci est présente dans la vidéo.

## Structure

Le projet est organisé autour de trois principales questions et étapes d'implémentation, explorant différentes méthodes pour améliorer la précision et les performances du système.

## Méthodes Utilisées

1. **Méthode des histogrammes** : Initialement basée sur l'algorithme de Carol, cette méthode compare l'image de requête avec des histogrammes de trames extraites toutes les secondes de chaque vidéo. Elle est performante sur les images PNG mais limitée pour les images JPEG en raison de la compression avec pertes.

2. **Utilisation des HOG (Histogram of Oriented Gradients)** : Alternative aux histogrammes, cette méthode génère des gradients pour comparer les images, bien que ses résultats en prédiction soient moins performants.

3. **Modèle ResNet** : Utilisation d'un modèle ResNet pré-entraîné, en extrayant les descripteurs d'une couche finale pour une comparaison plus avancée des images. Cette approche est plus performante pour les JPEG et PNG mais implique un temps de calcul accru.

4. **Combinaison ResNet + HOG** : La méthode finale combine ResNet pour la détection de la vidéo et HOG pour déterminer le minutage précis, permettant un équilibre entre précision et temps de calcul.

## Résultats

| Méthode                    | Taux de précision PNG | Taux de précision JPEG | Écart temporel moyen PNG | Écart temporel moyen JPEG |
|----------------------------|-----------------------|------------------------|--------------------------|---------------------------|
| Histogrammes de couleurs   | 78%                  | 70.3%                 | 0.47 s                   | 2.73 s                    |
| Combinaison ResNet + HOG   | 86.7%                | 84.3%                 | 0.32 s                   | 0.62 s                    |

---

## Installation

Installez les dépendances requises, notamment `tensorflow` et `opencv`, et exécutez les scripts pour tester l'algorithme.

## Auteur

Projet réalisé par Marc Zhang et Clément Auclin dans le cadre du cours INF8770 - Technologies multimédias.
