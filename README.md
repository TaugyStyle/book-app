# Mes Livres — PWA de résumés

Une Progressive Web App installable sur mobile pour stocker les résumés de tes livres de développement personnel, générés par l'IA **Google Gemini** (gratuit).

## Fonctionnalités

- ✨ **Génération IA (Gemini Flash — gratuit)** : tape le titre, l'IA génère un résumé structuré
- 🔍 **Autocomplete Google Books** : suggestions avec couvertures dès 3 lettres tapées
- 🏷️ **Tags automatiques** générés par l'IA, modifiables
- 🔎 **Recherche** : titre, auteur, contenu, tags, citations, notes
- 💬 **Citations favorites** et 📝 **notes perso** par livre
- 📱 **Installable** sur écran d'accueil iOS / Android
- 🌙 **Mode sombre** auto + fonctionne hors-ligne (sauf la génération IA)
- 💾 **Tout reste sur ton téléphone** (localStorage) + export JSON

## Étape 1 — Récupérer une clé Gemini gratuite

1. Va sur https://aistudio.google.com/apikey
2. Connecte-toi avec un compte Google
3. Clique **"Create API key"** → choisis un projet ou crée-en un
4. Copie la clé (elle ressemble à `AIzaSy...`)

**Quotas gratuits** (largement suffisants pour un usage perso) :
- ~15 requêtes / minute
- ~1 500 requêtes / jour
- Aucune carte bancaire requise

## Étape 2 — Déployer l'app

### Option rapide : Netlify Drop (2 min, gratuit, HTTPS inclus)
1. Va sur https://app.netlify.com/drop
2. Glisse-dépose le dossier `booksummary` entier
3. Tu obtiens une URL du style `https://nom-random.netlify.app`

### Alternatives
- **Vercel** : `npm i -g vercel` puis `vercel` dans le dossier
- **GitHub Pages** : uploade dans un repo → Settings → Pages → Source : `main`
- **Cloudflare Pages** : similaire à Netlify

⚠️ **HTTPS obligatoire** pour une PWA installable. Les services ci-dessus le fournissent automatiquement.

## Étape 3 — Installer sur ton téléphone

### iPhone (iOS)
1. Ouvre l'URL dans **Safari** (obligatoire)
2. Bouton Partager → **"Sur l'écran d'accueil"**

### Android
1. Ouvre l'URL dans **Chrome**
2. Menu (⋮) → **"Installer l'application"**

## Étape 4 — Première utilisation

1. Appuie sur **+** en bas à droite
2. Tape quelques lettres du titre → choisis dans les suggestions Google Books
3. Appuie sur **✨ Générer le résumé IA**
4. La première fois, l'app te demande ta clé Gemini → colle-la
   - Elle est stockée **uniquement dans ton navigateur** (localStorage)
   - Elle ne quitte jamais ton appareil sauf pour parler à Google
5. Le résumé est généré en ~3 secondes

## Gestion de la clé API

- ⚙ en haut à droite : réinitialiser la clé (utile si tu veux en changer)
- ⇪ en haut à droite : exporter tous tes livres en JSON (sauvegarde)

## Sécurité

✅ La clé API est stockée **localement sur ton appareil**, pas dans le code déployé
✅ Chaque utilisateur saisit sa propre clé
✅ Même si quelqu'un trouve l'URL de ton app, il ne peut pas voler ta clé

## Coût

**0 €** tant que tu restes dans les quotas gratuits de Gemini Flash. Pour un usage perso de résumés de livres, tu ne t'en approcheras pas.

## Personnalisation

- **Couleurs** : dans `index.html`, section `:root` et media query `prefers-color-scheme: light`
- **Modèle Gemini** : variable `GEMINI_MODEL` en haut du script
  - `gemini-2.0-flash` (par défaut, rapide et gratuit)
  - `gemini-2.5-flash` ou `gemini-2.5-pro` (plus précis)
- **Prompt** : fonction `generateSummary()`, cherche la variable `prompt`

## Fichiers

- `index.html` — l'application complète
- `manifest.json` — config PWA (nom, icônes, couleurs)
- `sw.js` — service worker (fonctionnement hors-ligne)
- `icon-192.png`, `icon-512.png` — icônes d'installation
