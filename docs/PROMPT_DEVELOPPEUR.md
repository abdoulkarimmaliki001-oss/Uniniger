# Cahier des charges : brancher UniNiger sur Firebase

Contexte : `public/demo.html` est une démonstration complète en un seul fichier (interface, parcours, logique). Elle stocke tout dans `localStorage`. Mission : en faire une application réelle, multi-utilisateurs, sans changer l'interface ni les parcours.

## À faire
1. Reprendre l'interface de `demo.html` (couleurs marine #042C53 et or #C99A2E, police Public Sans, thème clair et sombre) en application web installable (PWA), idéalement React ou Next.js.
2. Authentification par téléphone (Firebase Auth) : l'inscription envoie un vrai SMS. Remplacer le code simulé à l'écran.
3. Remplacer `localStorage` par Firestore, selon `docs/DONNEES.md`, avec écoute en temps réel (`onSnapshot`) pour le bus et les annonces.
4. Garder `firestore.rules` et l'adapter si besoin. Tester avec l'émulateur Firebase.
5. Notifications push (FCM) et Cloud Functions : alerte quand le bus est à un arrêt suivi ; alerte à tous pour une annonce critique.
6. Comptes chauffeur, délégué et admin créés par l'administration uniquement.
7. Photo de carte facultative à l'inscription : stockée de façon privée, supprimée après la décision du délégué.
8. Mode hors ligne : horaires théoriques en cache. SMS de secours : à étudier avec un fournisseur local.

## Règles à respecter
- Pas d'import de listes d'étudiants : vérification par SMS + validation par un délégué ou code d'activation de classe.
- Un espace par établissement ; annonces « Mon campus » ou « National ».
- Données personnelles minimales, chiffrées en transit, visibles seulement des délégués et administrateurs de l'établissement.
- Logos et noms d'établissements : uniquement avec l'accord de chacun.
- Interface en français.
