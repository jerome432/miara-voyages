# Guide d'Utilisation - Miara Voyages

## 🎯 Comment utiliser votre site

---

## 📱 Accéder au site

### Sur ordinateur
1. Ouvrez votre navigateur
2. Allez sur : **https://miara-voyages.fr**

### Sur téléphone/tablette
1. Ouvrez Safari (iPhone) ou Chrome (Android)
2. Allez sur : **https://miara-voyages.fr**
3. Option : Ajoutez à l'écran d'accueil pour un accès rapide

---

## 🏠 Page d'accueil

La page d'accueil affiche :
- La liste de tous vos voyages
- Les statistiques globales (pays visités, km parcourus, etc.)
- Un bouton pour découvrir chaque voyage

**Cliquez sur un voyage** pour voir tous les détails.

---

## 📖 Page d'un voyage (ex: Adriatique 2026)

### Ce que vous voyez :
- **Timeline interactive** avec toutes les étapes
- **Dates précises** de chaque destination
- **Descriptions** style Voyageurs du Monde
- **Informations hôtels** avec liens Booking.com
- **Badge pays** (Italie/Croatie/Slovénie)

### Navigation :
- Cliquez sur **"← Retour"** en haut pour revenir à l'accueil
- Scrollez pour voir toutes les étapes

---

## 📸 Ajouter des photos (à venir avec Firebase)

**Actuellement :** Les photos ne sont pas encore intégrées.

**Bientôt :**
1. Connectez-vous avec votre compte
2. Allez sur une destination
3. Cliquez sur "Ajouter des photos"
4. Sélectionnez vos photos
5. Elles seront stockées dans le cloud Firebase

**Alternative actuelle :**
- Créez des albums Google Photos
- Partagez les liens
- On les intégrera dans une prochaine version

---

## 👥 Gestion des utilisateurs (à venir)

**Actuellement :** Pas encore actif.

**Bientôt :**
1. Connectez-vous en tant qu'admin
2. Allez dans "Gérer les utilisateurs"
3. Ajoutez des membres de la famille
4. Définissez leurs permissions (Admin/Famille)
5. Ils recevront un email d'invitation

---

## 🔐 Connexion

**Actuellement :** La page de connexion existe mais Firebase n'est pas encore configuré.

**Pour activer :**
1. Suivez le **GUIDE-FIREBASE.md**
2. Configurez Authentication
3. Créez votre compte admin
4. La connexion sera fonctionnelle

---

## ➕ Ajouter un nouveau voyage (futur)

**Fonctionnalité à venir :**
1. Connectez-vous en tant qu'admin
2. Cliquez sur "Ajouter un voyage"
3. Remplissez :
   - Titre du voyage
   - Dates
   - Pays
   - Étapes
4. Sauvegardez
5. Le voyage apparaît sur l'accueil

---

## 🌐 Partager avec la famille

### Option 1 : Lien direct
Donnez simplement l'URL : **https://miara-voyages.fr**

### Option 2 : QR Code
1. Allez sur https://www.qr-code-generator.com
2. Entrez : https://miara-voyages.fr
3. Générez le QR code
4. Partagez-le (WhatsApp, email, etc.)

### Option 3 : Comptes familiaux (avec Firebase)
1. Ajoutez les membres de la famille
2. Ils créent leur compte
3. Ils peuvent se connecter et voir les voyages

---

## 📱 Installer comme application (PWA)

### Sur iPhone :
1. Ouvrez le site dans Safari
2. Appuyez sur le bouton "Partager" (carré avec flèche)
3. Faites défiler et choisissez "Sur l'écran d'accueil"
4. Nommez-le "Miara Voyages"
5. L'icône apparaît sur votre écran d'accueil

### Sur Android :
1. Ouvrez le site dans Chrome
2. Appuyez sur les 3 points (menu)
3. Choisissez "Ajouter à l'écran d'accueil"
4. Confirmez

---

## 🔄 Mettre à jour le contenu

### Modifier un texte :
1. Allez sur GitHub : https://github.com/jerome432/miara-voyages
2. Cliquez sur le fichier à modifier (ex: `adriatique-2026.html`)
3. Cliquez sur l'icône crayon (Edit)
4. Modifiez le texte
5. Scrollez en bas, cliquez "Commit changes"
6. ⏳ Attendez 2-3 minutes
7. Rafraîchissez votre site → C'est à jour !

### Ajouter une nouvelle page :
1. Sur GitHub, cliquez "Add file" → "Create new file"
2. Nommez le fichier (ex: `barcelone-2027.html`)
3. Copiez/adaptez le code d'une page existante
4. Commit
5. Mettez à jour `index.html` pour ajouter le lien

---

## 🐛 Problèmes fréquents

### Le site ne s'affiche pas
- Vérifiez votre connexion internet
- Essayez en navigation privée
- Videz le cache du navigateur

### Mes modifications n'apparaissent pas
- Attendez 2-3 minutes après le commit
- Appuyez sur Ctrl+F5 (PC) ou Cmd+Shift+R (Mac) pour forcer le rafraîchissement
- Vérifiez que GitHub Pages est bien activé (Settings > Pages)

### La page de connexion ne marche pas
- C'est normal ! Firebase n'est pas encore configuré
- Suivez le GUIDE-FIREBASE.md pour l'activer

---

## 💡 Conseils

### Pendant le voyage :
- Prenez beaucoup de photos !
- Notez vos anecdotes dans un carnet
- Créez vos albums Google Photos au fur et à mesure

### Après le voyage :
- Ajoutez toutes vos photos
- Écrivez vos notes et souvenirs
- Partagez avec la famille

### Pour les prochains voyages :
- Dupliquez la structure d'Adriatique 2026
- Adaptez les dates et destinations
- Gardez le même style cohérent

---

## 📞 Support

**Questions GitHub/Technique ?**
- Relisez les guides (GUIDE-INSTALLATION.md, GUIDE-FIREBASE.md)
- Vérifiez la documentation GitHub : https://docs.github.com

**Questions Firebase ?**
- Documentation officielle : https://firebase.google.com/docs

---

Bon voyage ! 🌍✈️
```

4. **"Commit new file"**

---
