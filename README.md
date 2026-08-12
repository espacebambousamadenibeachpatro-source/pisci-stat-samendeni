# PisciStat Samendéni

Application de gestion piscicole (pisciculteurs, cages, organisations) — React + Supabase, déployée sur Vercel.

## 1. Supabase
1. Créez un projet sur [supabase.com](https://supabase.com).
2. Dans **SQL Editor**, collez et exécutez le contenu de `supabase/schema.sql`.
3. Dans **Authentication → Users**, cliquez "Add user" et créez votre compte administrateur (email + mot de passe).
4. Copiez son UUID, puis dans **SQL Editor** :
   ```sql
   insert into profiles (id, role) values ('UUID-COPIÉ', 'admin');
   ```
5. Dans **Project Settings → API**, notez : `Project URL`, `anon public key`, `service_role key`.

## 2. En local
```bash
npm install
cp .env.example .env   # puis remplissez les 4 clés
npm run dev
```

## 3. GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/VOTRE-COMPTE/pisci-stat-samendeni.git
git push -u origin main
```

## 4. Vercel
1. [vercel.com](https://vercel.com) → "Add New Project" → importez le dépôt GitHub.
2. Dans **Settings → Environment Variables**, ajoutez les 4 variables de `.env.example` (avec vos vraies valeurs).
3. Déployez. Votre app est en ligne sur `https://votre-projet.vercel.app`.

## 5. Installer comme application mobile (PWA)
Une fois déployée, ouvrez l'URL sur un téléphone :
- **Android (Chrome)** : menu ⋮ → "Ajouter à l'écran d'accueil"
- **iPhone (Safari)** : bouton Partager → "Sur l'écran d'accueil"

L'app s'ouvre alors en plein écran, avec sa propre icône, comme une vraie application.

Pour aller plus loin (publication sur Play Store / App Store), voir `MOBILE.md`.
