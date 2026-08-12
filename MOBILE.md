# Transformer PisciStat en vraie application mobile

Le projet est déjà une **PWA** (voir README, section 5) : installable dès maintenant depuis le
navigateur, sans rien compiler. C'est suffisant pour la grande majorité des usages terrain.

Si vous voulez une **vraie app native** (icône issue du Play Store / App Store, notifications
push, accès aux capteurs du téléphone), la voie la plus simple est **Capacitor** : il enveloppe
votre site déjà déployé sur Vercel dans une coquille Android/iOS. Vous continuez à coder dans
`src/`, vous déployez sur Vercel comme d'habitude, et l'app mobile se met à jour automatiquement
sans repasser par le Play Store à chaque changement.

⚠️ Ces étapes nécessitent un ordinateur avec Android Studio (gratuit) et/ou Xcode (Mac
uniquement, pour iOS) — impossible à faire depuis ce chat, qui n'a pas d'accès réseau ni ces
outils installés.

## Étapes (à exécuter sur votre machine)

```bash
npm install @capacitor/core @capacitor/cli @capacitor/android @capacitor/ios
npx cap init "PisciStat Samendéni" "com.piscistat.samendeni"
```

Remplacez ensuite le contenu de `capacitor.config.json` généré par celui fourni dans ce projet
(`capacitor.config.json`) — il pointe l'app vers votre URL Vercel déployée, ce qui évite de
reconstruire l'app à chaque changement de contenu.

```bash
npx cap add android      # génère le dossier android/
npx cap add ios          # génère le dossier ios/ (Mac uniquement)
npx cap open android     # ouvre Android Studio → Build > Generate Signed Bundle/APK
npx cap open ios         # ouvre Xcode → Product > Archive
```

## Publication sur les stores
- **Google Play** : compte développeur (25 $, paiement unique) → console.play.google.com →
  uploadez le fichier `.aab` généré par Android Studio.
- **Apple App Store** : compte développeur (99 $/an) → App Store Connect → soumettez via Xcode.

## Alternative plus simple : rester en PWA
Si la publication sur les stores n'est pas indispensable, la PWA (déjà en place) couvre
l'essentiel : icône sur l'écran d'accueil, plein écran, fonctionne hors-ligne pour les pages déjà
visitées — sans compte développeur ni validation par Apple/Google.
