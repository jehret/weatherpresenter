# Challenge Java - Miss Météo : Programmation par contrat

## Dates : du 15/09/24 au 13/10/24

## Difficulté : élevée

## Technologies cibles : 
- Spring Boot 3
- Spring 6
- Java 17+

## Description

Ce challenge vous invite à mettre en pratique la programmation par contrat, un concept fondamental dans l'écosystème Spring. Cette approche permet d'utiliser des méthodes publiques (APIs) sans connaître leurs détails d'implémentation, en se concentrant uniquement sur leurs entrées et sorties attendues. En Java, cela se traduit généralement par l'utilisation d'interfaces ou de classes abstraites.

Pour un rappel sur ce concept, vous pouvez consulter cette vidéo extraite du cours "Bien débuter avec Spring et Spring Boot" disponible sur [apprendre-java.com](https://apprendre-java.com) : [Vidéo explicative](https://www.youtube.com/watch?v=V3aS8jbcyK0)

## Objectif

Développer une application Java avec Spring Boot capable de fournir les prévisions météorologiques du lendemain à midi (12h) via une API REST : `/weather/{city-name}`

### Format de réponse attendu (JSON) :

```json
{
  "weather": "Partly Cloudy",
  "temperature": 6
}
```
On utilisera l'anglais pour le temps et les degrés Celsius pour le température.

## Exigences

Il existe de nombreux services météo en ligne, parmi lesquels :
   - [WeatherAPI](https://www.weatherapi.com/)
   - [Météo Concept](https://api.meteo-concept.com/)
   - [OpenWeatherMap](https://openweathermap.org/) (plus complexe)

Or aucun de ces services tiers ne répond parfaitement aux attentes de notre chef de produit (pour l’instant) et on ne sait pas lequel sera sélectionné lors de la mise en prod.

Pour minimiser les risques, on va donc créer 2 implémentations, exploitant chacune un service tiers distinct (de la liste plus haut ou d'ailleurs, c'est au choix).

L’un des principaux problèmes que l’on souhaite éviter, c’est de ne pas pouvoir répondre à l’utilisateur parce que l’API tierce est hors service.
Or, les premier tests ont montré que plus de la moitié des demandes sont pour la ville de Paris. 
Aussi, on décide de créer une 3ème implémentation qui va stocker 3 jours à l’avance la météo de Paris dans un fichier sur le disque. 
Tant que le service fonctionne, ces données sont maintenues à jour chaque nuit à minuit.
Notre API météo consiste alors non plus à retourner en temps réel le résultat d’un service tiers, mais la valeur la plus fraîche que l’on à réussi à récupérer les jours précédents, si celle-ci est disponible.

Vous testerez les 3 implémentations, Spring et Spring Boot doivent vous faciliter la tâche.

Vous pouvez allez aussi loin que vous le souhaitez dans les détails avec pourquoi pas gestion d'erreurs et tests.

## Bonus (Pour aller plus loin)

- Créez un petit client Web
- Implémentez un système de cache pour optimiser les performances.
- Mettez en place un mécanisme de fallback entre les différentes sources de données.

## Critères d'évaluation

- Couverture fonctionelle
- Qualité et lisibilité du code
- Respect des principes SOLID
- Utilisation appropriée des fonctionnalités de Spring et Spring Boot

## Livraison

- Code source sur un dépôt GitHub public
- Copie du lien GitHub sur le canal reponse-challenges
- Durée recommandée : 4-8 heures

N'hésitez pas à poser vos questions sur le Discord de la communauté si vous avez besoin d'éclaircissements. Bon courage à tous les participants !

## Récompenses
- Vainqueur : 20 pts
- 2ème : 10 pts
- 3ème : 5 pts

Rappel: Les participants accumulent des points en fonction de leur performance dans les challenges. Ces points peuvent être convertis en cartes cadeaux Prezzy, utilisables pour des achats en ligne ou en magasin dans n'importe quelle devise.
