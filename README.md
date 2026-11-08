# UniNiger

Application des campus du Niger : bus arrêt par arrêt, planning, annonces officielles, groupes, objets perdus, SOS.
Un espace par établissement (UniAgadez en pilote).

## Contenu de ce dépôt

| Fichier | Rôle |
|---|---|
| `public/demo.html` | Démonstration complète (données fictives, tout reste dans le navigateur). Sert de maquette fonctionnelle. |
| `firestore.rules` | Règles de sécurité de la base : qui peut lire et écrire quoi. |
| `firebase.json` | Configuration de l'hébergement et de la base. |
| `docs/DONNEES.md` | Structure de la base de données. |
| `docs/PROMPT_DEVELOPPEUR.md` | Cahier des charges à donner à un développeur ou à une IA pour brancher l'application sur Firebase. |

Ce dépôt prépare le terrain. La démonstration n'est pas encore branchée sur Firebase : les comptes et le suivi des bus partagés entre téléphones restent à développer.

## Mise en ligne (une seule fois, environ 15 minutes)

1. Créez un projet sur https://console.firebase.google.com
2. Dans le projet, activez : **Authentication** (méthode « Téléphone »), **Firestore Database**, **Hosting**.
3. Sur votre ordinateur, installez Node.js puis :
   ```
   npm install -g firebase-tools
   firebase login
   cp .firebaserc.example .firebaserc      # puis remplacez l'identifiant du projet
   firebase deploy --only firestore:rules,hosting
   ```
4. Le site est en ligne sur `https://VOTRE-PROJET.web.app`.

## À vérifier avant d'ouvrir à de vrais étudiants

- Prix actuel des SMS de Firebase et arrivée des SMS sur les opérateurs du Niger. Sinon, prévoir un fournisseur de SMS local.
- Accord écrit de l'université (utilisation du nom, du logo et de la liste ou du processus de validation des étudiants).
- Numéros d'urgence et contacts du campus à confirmer (valeurs d'exemple dans la démonstration).
- Politique de confidentialité et charte relues par l'établissement.

Les règles de sécurité n'ont pas été testées avec l'émulateur Firebase : lancez `firebase emulators:start` et testez-les avant la mise en service.
