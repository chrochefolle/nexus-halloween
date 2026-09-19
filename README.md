# NEXUS // Cyber-Daemon Halloween Missions

> Une expérience web bilingue FR/EN pour une soirée Halloween cyberpunk : les invités reçoivent des missions secrètes, les font valider, accumulent des pactes et voient leur niveau de difficulté progresser.

**Statut :** prototype local / MVP visuel.  
**Thème :** terminal Matrix, fond noir, texte rouge, pluie de code et interface cyber-démoniaque.

---

## Fonctionnalités actuelles

- Interface **français / anglais** avec bascule instantanée `FR / EN`
- Une mission secrète active par joueur
- Score de `pactes validés`
- Progression par cinq niveaux :
  1. `Initié / Initiate`
  2. `Glitcheur / Glitcher`
  3. `Invokateur / Invoker`
  4. `Archonte / Archon`
  5. `Daemon / Daemon`
- Montée de niveau après chaque tranche de trois pactes validés
- Trois vies : abandonner une mission consomme une vie
- Refus de validation par la cible : mission close, **sans vie perdue**
- Option `Mode avion` : la cible est retirée du ciblage pour la session locale
- Anti-répétition : le moteur évite les trois dernières cibles du joueur
- Répartition simple : le moteur privilégie les cibles les moins sollicitées
- Banque de missions graduelles, allant d’une question légère à une création collective
- Journal local des événements et classement fictif
- Aucun backend, aucun compte, aucune collecte de données : tout s’exécute dans le navigateur

---

## Lancer le prototype

Le projet est actuellement constitué d’un seul fichier autonome :

```text
nexus-halloween-mvp-bilingual.html
```

Tu peux le renommer en `index.html` pour le publier facilement.

### Ouvrir sur ordinateur

Double-clique sur le fichier HTML, ou ouvre-le depuis Chrome, Edge, Firefox ou Safari.

> Le prototype utilise JavaScript et fonctionne mieux lorsqu’il est servi par un petit serveur web plutôt qu’ouvert directement depuis le système de fichiers.

### Servir localement avec Python

Place `index.html` dans un dossier, ouvre un terminal dans ce dossier puis lance :

```bash
python3 -m http.server 8080
```

Sous Windows, si `python3` ne fonctionne pas :

```powershell
py -m http.server 8080
```

Ouvre ensuite :

```text
http://localhost:8080
```

Le serveur reste disponible tant que le terminal reste ouvert.

---

## Tester sur iPhone

L’ouverture directe d’un fichier `.html` depuis l’app Fichiers iOS n’est pas fiable pour une application JavaScript. Utilise plutôt un serveur local ou un hébergement web.

### Depuis le même Wi‑Fi

1. Lance le serveur Python sur ton ordinateur :

   ```bash
   python3 -m http.server 8080
   ```

2. Récupère l’adresse IP locale de ton ordinateur.

   Sur macOS :

   ```bash
   ipconfig getifaddr en0
   ```

   Sur Windows :

   ```powershell
   ipconfig
   ```

   Cherche l’`Adresse IPv4` de la carte Wi‑Fi, par exemple `192.168.1.42`.

3. Connecte l’iPhone au **même réseau Wi‑Fi**.

4. Ouvre Chrome ou Safari sur l’iPhone, puis saisis :

   ```text
   http://192.168.1.42:8080
   ```

5. Si la page ne s’ouvre pas :
   - vérifie que le terminal tourne encore ;
   - vérifie que l’iPhone et l’ordinateur sont sur le même Wi‑Fi ;
   - accepte l’autorisation du pare-feu si Windows ou macOS la demande ;
   - évite un réseau invité qui empêche les appareils de communiquer entre eux.

### Ajouter à l’écran d’accueil

Une fois l’URL ouverte sur iPhone :

- Dans Safari : bouton Partager → **Sur l’écran d’accueil**
- Dans Chrome : menu `…` → **Ajouter à l’écran d’accueil**, si l’option est proposée

---

## Déployer sur GitHub Pages

Pour une démo accessible depuis n’importe quel téléphone :

1. Crée un dépôt GitHub, par exemple `nexus-halloween`.
2. Ajoute le fichier sous le nom `index.html` à la racine du dépôt.
3. Envoie les changements :

   ```bash
   git init
   git add index.html README.md
   git commit -m "Initial NEXUS Halloween prototype"
   git branch -M main
   git remote add origin https://github.com/VOTRE_COMPTE/nexus-halloween.git
   git push -u origin main
   ```

4. Dans GitHub : `Settings` → `Pages`.
5. Dans **Build and deployment**, sélectionne :
   - Source : `Deploy from a branch`
   - Branch : `main`
   - Folder : `/ (root)`
6. Enregistre. GitHub génère une URL publique après le déploiement.
7. Ouvre cette URL sur téléphone, puis génère un QR code vers cette adresse pour les invités.

> GitHub Pages permet de partager l’interface, mais cette version reste locale : chaque navigateur possède ses propres score, vies et historique.

---

## Déployer sur Azure Static Web Apps

Azure Static Web Apps constitue une bonne base si le projet doit ensuite évoluer vers une vraie application multi-utilisateur avec API, SignalR et stockage partagé.

### Pré-requis

- Un compte Azure
- Un dépôt GitHub ou Azure DevOps
- `index.html` à la racine du dépôt

### Étapes

1. Dans le portail Azure, crée une ressource **Static Web App**.
2. Connecte le dépôt GitHub ou Azure DevOps.
3. Sélectionne la branche `main`.
4. Configure les chemins :

   ```text
   App location: /
   API location: (vide)
   Output location: (vide)
   ```

5. Termine la création : Azure ajoute un pipeline de déploiement au dépôt.
6. Après le premier workflow, ouvre l’URL fournie par Azure.
7. Crée un QR code pointant vers cette URL.

---

## Règles de jeu recommandées

Le jeu fonctionne mieux lorsque le cadre est communiqué avant le début de la soirée : les missions précises restent secrètes, mais les invités savent qu’ils peuvent être invités à participer à des interactions légères et fictionnelles.

- Une mission est une invitation, jamais un ordre
- Une réponse brève, un refus, l’absence de réponse ou un changement de sujet clôt la tentative
- Une cible peut utiliser `Mode avion` sans devoir se justifier
- Un refus de la cible ne retire pas de vie au joueur
- Le joueur perd une vie seulement en cas d’abandon de sa propre mission
- Aucune mission ne doit exiger d’alcool, d’argent, de contact physique, de révélation personnelle, de contenu sexuel, d’humiliation ou de photo/vidéo sans accord distinct
- Une seule tentative explicite par mission
- Le même duo ne doit pas s’enchaîner
- Les missions plus élevées doivent être plus créatives ou collaboratives, jamais plus intrusives

---

## Limites du MVP

Cette version est une démonstration locale. Elle ne propose pas encore :

- de session partagée entre plusieurs téléphones ;
- d’authentification ou de création de pseudonyme ;
- d’import de participants ;
- de QR code de validation réellement séparé ;
- de validation par le téléphone de la cible ;
- de synchronisation temps réel des scores ;
- de persistance des données après fermeture du navigateur ;
- de console organisateur ;
- de génération automatique de QR codes ;
- de classement multi-joueurs réel.

---

## Architecture cible

Pour une version jouable pendant la soirée, l’architecture recommandée est :

```text
Téléphone invité (PWA Angular ou React)
            │
            ├── HTTPS / API REST ──► ASP.NET Core Minimal API
            │
            └── SignalR ──────────► Synchronisation temps réel
                                        │
                                        ├── PostgreSQL / Azure SQL
                                        └── Redis optionnel pour présence et état éphémère

Écran organisateur (web)
            │
            ├── Import des participants
            ├── Gestion des missions et catégories
            ├── Modération : pause, exclusion, annulation
            └── Classement / affichage collectif
```

### Entités principales

```text
Participant
- id
- alias
- statut : actif | pause | spectre | parti
- vies_restantes
- score
- niveau

Mission
- id
- niveau
- catégorie
- texte_fr
- texte_en
- contraintes

Pacte
- id
- initiateur_id
- cible_id
- mission_id
- statut : attribué | validation_en_attente | validé | refusé | abandonné | expiré
- créé_le
- fermé_le

HistoriqueInteraction
- initiateur_id
- cible_id
- mission_id
- issue
- date_heure
```

### Règles de matching

Une cible est éligible lorsqu’elle est active, disponible, compatible avec la mission et qu’elle ne forme pas un duo récent avec le joueur :

```text
eligible(joueur, cible) =
  cible.active
  AND NOT duo_recent(joueur, cible)
  AND NOT cible.occupee
  AND cible.nombre_solicitations < plafond
  AND mission_compatible(joueur, cible)
```

Pour un petit groupe, prévois une solution de repli : une mission sans cible directe, une mission d’observation ou une mission collective entièrement volontaire.

---

## Structure suggérée du dépôt

```text
nexus-halloween/
├── index.html
├── README.md
├── LICENSE
└── docs/
    ├── game-rules.md
    ├── mission-bank.md
    └── architecture.md
```

Lors du passage à une version full-stack :

```text
nexus-halloween/
├── apps/
│   ├── player-web/          # PWA des invités
│   └── host-console/        # Console organisateur
├── services/
│   └── nexus-api/           # API .NET + SignalR
├── docs/
├── infra/                   # Bicep ou Terraform
└── README.md
```

---

## Idées de prochaines étapes

1. Ajouter un écran d’entrée avec alias et sélection de langue.
2. Créer un écran organisateur permettant de saisir ou importer les participants.
3. Rendre le moteur de sélection réellement multi-joueurs.
4. Ajouter une session temporaire, par exemple `HALLOWEEN-666`, accessible avec un QR code.
5. Produire un QR code de validation à usage unique pour chaque mission.
6. Connecter la validation au téléphone de la cible.
7. Ajouter SignalR pour mettre à jour score, vies, niveau et classement en direct.
8. Mettre en place un tableau de modération et un bouton `Mode avion` global.
9. Enrichir la banque de missions et les tags de compatibilité.
10. Ajouter un mode projection / écran collectif pour le classement et les événements du NEXUS.

---

## Licence

À définir. Pour un projet personnel, tu peux laisser ce dépôt privé ou ajouter une licence adaptée lorsque tu souhaites le partager.
