# Site de l'Atelier — mode d'emploi

Le site est composé de deux parties :

- **le site public** (`index.html`, `page.html`, `style.css`), qui lit son contenu dans le dossier `content/` ;
- **l'administration** (`/admin`), où tu modifies ce contenu sans toucher au code : sessions, intervenants, collections, textes, photos, pages légales.

Quand tu cliques sur « Publier » dans l'administration, la modification est enregistrée sur GitHub, et Netlify remet le site à jour en une minute environ.

---

## Installation (une seule fois, environ une heure)

Les noms de menus de GitHub et Netlify changent de temps en temps : si un intitulé ne correspond pas exactement, cherche l'équivalent le plus proche.

### 1. Mettre les fichiers sur GitHub

1. Crée un compte gratuit sur github.com.
2. Crée un nouveau dépôt (« New repository ») nommé `latelier`. Il peut être privé.
3. Dans le dépôt, clique sur « Add file » puis « Upload files ». Glisse **le contenu** du dossier `latelier` (les fichiers et sous-dossiers, pas le dossier lui-même). Valide avec « Commit changes ».

### 2. Mettre le site en ligne avec Netlify

1. Crée un compte sur netlify.com en te connectant avec GitHub.
2. « Add new project », puis « Import an existing project », puis GitHub, et choisis le dépôt `latelier`.
3. Laisse la commande de build vide et le dossier de publication vide (ou `.`). Lance le déploiement.
4. Note l'adresse du site (du type `https://latelier-xxxx.netlify.app`).

### 3. Autoriser la connexion à l'administration

1. Sur GitHub : Settings (de ton compte), Developer settings, OAuth Apps, « New OAuth App ».
   - Homepage URL : l'adresse de ton site.
   - Authorization callback URL : `https://api.netlify.com/auth/done`
   - Crée l'application, puis génère un « client secret ». Garde l'identifiant (Client ID) et le secret sous la main.
2. Sur Netlify, dans ton projet : Project configuration, Access & security, OAuth, « Install provider », choisis GitHub et colle le Client ID et le secret.

### 4. Relier l'administration à ton dépôt

Sur GitHub, ouvre le fichier `admin/config.yml`, clique sur le crayon pour le modifier, et remplace :

- `TON-IDENTIFIANT-GITHUB/latelier` par ton identifiant GitHub suivi de `/latelier` ;
- les deux lignes `https://latelier.fr` par l'adresse réelle de ton site.

Valide avec « Commit changes ».

### 5. Première connexion

Va sur `https://ton-site/admin` et clique sur « Se connecter avec GitHub ». C'est prêt.

---

## Au quotidien

**Ajouter une session.** Agenda, Sessions, « Ajouter session ». Remplis les champs, colle le lien de paiement Stripe, clique sur « Publier ». La session disparaît toute seule du site le lendemain de sa date de fin.

**Mettre à jour les places.** Stripe t'envoie un e-mail à chaque paiement. Baisse alors le nombre de places restantes dans la session. À 0, le site affiche « Complet » et propose la liste d'attente. Le compteur ne se met pas à jour tout seul.

**Ajouter un intervenant.** La maison, Intervenants. L'identifiant doit être en minuscules, sans accent ni espace (ex. : `claire-dupont`), et ne doit plus changer ensuite, car les sessions s'y réfèrent.

**Ajouter une collection.** La maison, Collections. Choisis une couleur : le texte passe automatiquement en noir ou en blanc pour rester lisible, et les photos de la collection prennent sa teinte.

**Photos.** Importe-les directement dans les champs photo. Allège-les avant (moins de 500 Ko, 2 000 pixels de large au maximum), sinon le site devient lent sur mobile.

**Masquer quelque chose sans le supprimer.** Décoche « Afficher sur le site » pour une session, ou « Afficher la consigne de la semaine ».

**Donner accès à quelqu'un.** Ajoute la personne comme collaboratrice du dépôt sur GitHub (Settings, Collaborators). Attention : elle a alors accès à tout le site, pas seulement à l'agenda.

**Revenir en arrière.** Chaque publication est archivée sur GitHub et dans l'onglet Deploys de Netlify, d'où tu peux restaurer une version précédente en un clic.

---

## Avant l'ouverture

- Compléter les pages légales (mentions légales, CGV, confidentialité) : obligatoires pour vendre en ligne.
- Remplacer les textes provisoires : réponses « À compléter » dans les questions, extraits de participants, sticker « 12 max ».
- Ajouter le lien d'inscription à la newsletter (Brevo, Substack…) : tant qu'il est vide, le bouton est masqué.
- Ajouter les photos et les liens de paiement Stripe.
- Brancher le nom de domaine dans Netlify (Domain management).
