# Guide Configuration Firebase - Miara Voyages

## 🎯 Objectif

Configurer Firebase pour votre interface admin afin de :
- 🔐 Gérer l'authentification
- 💾 Stocker vos voyages
- 📸 Héberger les photos
- 🔒 Sécuriser l'accès

---

## ✅ ÉTAPE 1 : Récupérer votre configuration Firebase

Vous avez déjà créé le projet `miara-voyages` sur Firebase.

### Actions :

1. Allez sur : https://console.firebase.google.com

2. Sélectionnez le projet **"miara-voyages"**

3. Cliquez sur l'icône **⚙️** (Settings) en haut à gauche

4. Cliquez sur **"Project settings"**

5. Scrollez jusqu'à **"Your apps"**

6. Si vous n'avez pas encore d'app web, cliquez sur **`</>`** (icône web)
   - Nom : `miara-voyages-web`
   - Cliquez "Register app"

7. **COPIEZ le code de configuration** qui ressemble à :

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyC...",
  authDomain: "miara-voyages.firebaseapp.com",
  projectId: "miara-voyages",
  storageBucket: "miara-voyages.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

8. **GARDEZ CE CODE** - vous en aurez besoin !

---

## ✅ ÉTAPE 2 : Activer Authentication

### Actions :

1. Dans Firebase Console, menu gauche → **"Build"** → **"Authentication"**

2. Cliquez sur **"Get started"**

3. Cliquez sur **"Email/Password"**

4. **Activez** le premier bouton (Email/Password)

5. Cliquez sur **"Save"**

✅ Authentication activée !

---

## ✅ ÉTAPE 3 : Créer votre compte admin

1. Dans **"Authentication"** → onglet **"Users"**

2. Cliquez sur **"Add user"**

3. Remplissez :
   - Email : `robertmeunier79@gmail.com` (ou votre email perso)
   - Password : (choisissez un mot de passe fort, minimum 6 caractères)

4. Cliquez sur **"Add user"**

5. **NOTEZ L'UID** qui apparaît (ex: `abc123def456...`)

✅ Compte créé !

---

## ✅ ÉTAPE 4 : Activer Firestore Database

1. Menu gauche → **"Build"** → **"Firestore Database"**

2. Cliquez sur **"Create database"**

3. Sélectionnez **"Start in production mode"**

4. Location : **"europe-west"** (Belgique)

5. Cliquez sur **"Enable"**

⏳ Attendez 1-2 minutes...

✅ Firestore créé !

---

## ✅ ÉTAPE 5 : Configurer les règles de sécurité Firestore

1. Dans **"Firestore Database"** → onglet **"Rules"**

2. **Remplacez TOUT le contenu** par :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    
    // Fonction : vérifier si admin
    function isAdmin() {
      return request.auth != null && 
             exists(/databases/$(database)/documents/users/$(request.auth.uid)) &&
             get(/databases/$(database)/documents/users/$(request.auth.uid)).data.role == 'admin';
    }
    
    // Fonction : vérifier si authentifié
    function isAuthenticated() {
      return request.auth != null;
    }
    
    // Collection VOYAGES
    match /voyages/{voyageId} {
      allow read: if isAuthenticated();
      allow write: if isAdmin();
    }
    
    // Collection USERS
    match /users/{userId} {
      allow read: if request.auth.uid == userId || isAdmin();
      allow write: if isAdmin();
    }
    
    // Collection PHOTOS
    match /photos/{photoId} {
      allow read: if isAuthenticated();
      allow write: if isAdmin();
    }
  }
}
```

3. Cliquez sur **"Publish"**

✅ Règles de sécurité configurées !

---

## ✅ ÉTAPE 6 : Créer le document utilisateur admin

1. Dans **"Firestore Database"** → onglet **"Data"**

2. Cliquez sur **"Start collection"**

3. Collection ID : `users`

4. Cliquez **"Next"**

5. **Document ID** : Collez l'UID de votre utilisateur (de l'étape 3)

6. Ajoutez ces champs :

| Field | Type | Value |
|-------|------|-------|
| email | string | robertmeunier79@gmail.com |
| role | string | admin |
| name | string | Jérôme Miara |
| createdAt | timestamp | [Cliquez sur l'horloge] |

7. Cliquez sur **"Save"**

✅ Votre compte admin est configuré dans Firestore !

---

## ✅ ÉTAPE 7 : Configurer Firebase dans vos fichiers

### Fichiers à modifier :

- `admin-login.html`
- `admin-dashboard.html`

### Actions :

1. Ouvrez `admin-login.html` sur GitHub

2. Cliquez sur l'icône **crayon** ✏️

3. Cherchez cette section (environ ligne 200) :

```javascript
const firebaseConfig = {
    apiKey: "VOTRE_API_KEY",
    authDomain: "VOTRE_PROJECT_ID.firebaseapp.com",
    projectId: "VOTRE_PROJECT_ID",
    storageBucket: "VOTRE_PROJECT_ID.appspot.com",
    messagingSenderId: "VOTRE_SENDER_ID",
    appId: "VOTRE_APP_ID"
};
```

4. **Remplacez avec VOTRE configuration** (de l'étape 1)

5. **Commit** : "Configuration Firebase"

6. **Répétez pour `admin-dashboard.html`**

✅ Firebase configuré dans vos fichiers !

---

## ✅ ÉTAPE 8 : Activer Storage (optionnel - pour photos)

1. Menu gauche → **"Build"** → **"Storage"**

2. Cliquez sur **"Get started"**

3. **Production mode** → **"Next"**

4. Location : **"europe-west"**

5. Cliquez sur **"Done"**

✅ Storage activé !

---

## ✅ ÉTAPE 9 : Tester la connexion

1. Allez sur :
   ```
   https://jerome432.github.io/miara-voyages/admin-login.html
   ```

2. Connectez-vous avec :
   - Email : `robertmeunier79@gmail.com`
   - Mot de passe : (celui que vous avez créé)

3. Si ça marche → ✅ Vous êtes redirigé vers le dashboard !

4. Si erreur → Vérifiez :
   - Configuration Firebase copiée correctement
   - Compte utilisateur créé
   - Document admin créé dans Firestore

---

## 🎯 RÉCAPITULATIF

**Configuration complète :**

✅ Projet Firebase : `miara-voyages`
✅ Authentication activée (Email/Password)
✅ Firestore activé (europe-west)
✅ Règles de sécurité configurées
✅ Compte admin créé : `robertmeunier79@gmail.com`
✅ Document admin dans Firestore
✅ Configuration dans fichiers HTML
✅ Storage activé (pour photos)

---

## 🔐 SÉCURITÉ

**Vos données sont protégées :**
- ✅ Seuls les utilisateurs authentifiés peuvent lire
- ✅ Seuls les admins peuvent écrire
- ✅ Firebase gère les mots de passe (cryptés)
- ✅ Règles Firestore empêchent les accès non autorisés

---

## 🆘 PROBLÈMES FRÉQUENTS

### "Email or password incorrect"
→ Vérifiez que le compte a bien été créé dans Authentication

### "Access denied"
→ Vérifiez que le document admin existe dans Firestore avec `role: admin`

### "Firebase config not found"
→ Vérifiez que vous avez bien remplacé la configuration dans les fichiers HTML

### "Network error"
→ Vérifiez que vous êtes bien en HTTPS (GitHub Pages)

---

## 📞 AIDE

Si vous êtes bloqué, vérifiez :
1. Configuration Firebase copiée exactement
2. Compte créé dans Authentication
3. Document créé dans Firestore avec bon UID
4. Règles de sécurité publiées
5. Fichiers HTML bien mis à jour sur GitHub

---

Bon courage ! 🚀
