# Association Stock Manager

Petite application web pour gérer le stock d'une association. Les données sont conservées en mémoire : elles disparaissent au redémarrage du serveur.

## Prérequis
- Node.js 20 ou supérieur
- npm

## Installation
Dans un terminal ouvert à la racine du projet :

```bash
npm install
```

## Lancer les tests
```bash
npm test
```

## Démarrer l'application
```bash
npm start
```

Puis ouvrir http://localhost:3000 dans le navigateur.

## Fonctionnalités
- Ajouter un article avec son nom, sa catégorie, sa quantité et son seuil d'alerte.
- Enregistrer une entrée ou une sortie de stock.
- Rechercher par nom et filtrer par catégorie.
- Repérer les articles dont la quantité est inférieure ou égale au seuil d'alerte.
- Supprimer un article.

## Règles métier
- Le nom est obligatoire.
- Les quantités et seuils sont des nombres entiers positifs ou nuls.
- Une sortie ne peut pas dépasser le stock disponible.
- Les noms d'articles sont uniques, sans distinction entre majuscules/minuscules et espaces extérieurs.
- Un seuil d'alerte est atteint quand `quantité <= seuil`.

## Architecture
- `src/domain` : modèle et règles élémentaires du domaine.
- `src/application` : cas d'utilisation et orchestration métier.
- `src/ports` : contrats utilisés par le service.
- `src/adapters` : stockage en mémoire et notifications.
- `src/web` : serveur Express et routes HTTP.
- `src/public` : interface web.
- `tests` : tests unitaires et d'intégration.

## À compléter pour le TP
Ce dépôt est un squelette fonctionnel de départ, pas encore la preuve de toutes les notions du sujet. Pour le dossier de conformité, ajoutez :
1. Les cycles TDD rouge/vert pour au moins deux règles.
2. Deux refactorings documentés avec avant/après.
3. Des mesures réelles d'écoconception avant/après.
4. Une justification de l'architecture et des principes SOLID.
5. Le journal de prompts de chaque membre et les deux bilans individuels.

## Limites
- Pas de base de données ni de persistance sur disque.
- La notification web est renvoyée dans la réponse HTTP et affichée par l'interface. L'adapter simulé est utilisé dans les tests.
- L'asynchronisme est illustré par une fonction de notification asynchrone simple, sans file de messages externe.
