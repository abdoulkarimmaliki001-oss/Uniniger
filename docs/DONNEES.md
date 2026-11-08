# Structure de la base (Firestore)

Chaque document porte un champ `etab` (ex. `UAZ`) qui sépare les établissements.

- `users/{uid}` : role (`student`, `delegate`, `driver`, `admin`), status (`pending`, `valid`, `rejected`), name, card, phone, filiere, annee, etab, line (chauffeur), subs (arrêts suivis, ex. `A:2`)
- `announcements/{id}` : title, body, level (1 info, 2 important, 3 critique), scope (`private`, `national`), etab, author, badge, createdAt
- `events/{id}` : etab, date, time, title, place
- `lines/{id}` : etab, name, stops[], ints[] (minutes entre arrêts), sched[], state {idx, at, times}, dis {text, t}
- `groups/{id}` : etab, name, desc, members[]
- `lost/{id}` : etab, kind, text, place, uid, by, done, createdAt
- `classCodes/{id}` : etab, code, classe, uses

Notifications : Cloud Functions + Firebase Cloud Messaging, déclenchées à la modification de `lines/{id}.state` (alerte aux étudiants qui suivent l'arrêt) et à la création d'une annonce de niveau 3.
Les chauffeurs et délégués sont créés par l'administration (jamais par auto-inscription).
