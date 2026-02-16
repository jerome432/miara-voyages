# Guide Firebase - Miara Voyages

## 🔥 Configuration de Firebase

Cette configuration permettra :
- 🔐 Authentification sécurisée
- 💾 Stockage des photos dans le cloud
- 👥 Gestion multi-utilisateurs
- 💬 Commentaires et notes

---

## ✅ ÉTAPE 1 : Prérequis

Vous avez déjà :
- ✅ Compte Google : jerome.miara@groupe-obea.com
- ✅ Projet Firebase : `miara-voyages`

---

## ✅ ÉTAPE 2 : Activer Authentication

1. Allez sur https://console.firebase.google.com

2. Sélectionnez le projet **"miara-voyages"**

3. Dans le menu de gauche, cliquez sur **"Build"** → **"Authentication"**

4. Cliquez sur **"Get started"**

5. Cliquez sur **"Email/Password"**

6. **Activez** le premier bouton (Email/Password)

7. Cliquez sur **"Save"**

✅ Authentication activée !

---

## ✅ ÉTAPE 3 : Activer Firestore Database

1. Dans le menu de gauche, cliquez sur **"Build"** → **"Firestore Database"**

2. Cliquez sur **"Create database"**

3. Sélectionnez **"Start in production mode"**

4. Location : Choisissez **"europe-west"** (Belgique)

5. Cliquez sur **"Enable"**

⏳ Attendez 1-2 minutes...

✅ Firestore activé !

---

## ✅ ÉTAPE 4 : Créer votre premier compte Admin

1. Retournez dans **"Authentication"**

2. Cliquez sur l'onglet **"Users"**

3. Cliquez sur **"Add user"**

4. Remplissez :
   - Email : `jerome.miara@groupe-obea.com`
   - Password : (choisissez un mot de passe fort, minimum 6 caractères)

5. Cliquez sur **"Add user"**

6. ✅ Votre compte est créé !

---

## ✅ ÉTAPE 5 : Récupérer la configuration

1. Cliquez sur l'icône **⚙️ (Settings)** en haut à gauche

2. Cliquez sur **"Project settings"**

3. Scrollez vers le bas jusqu'à **"Your apps"**

4. Cliquez sur l'icône **`</>`** (Web)

5. Donnez un nom : `miara-voyages-web`

6. Cliquez sur **"Register app"**

7. **Copiez le code qui apparaît** (ressemble à ça) :
```javascript
const firebaseConfig = {
  apiKey: "AIza...",
  authDomain: "miara-voyages.firebaseapp.com",
  projectId: "miara-voyages",
  storageBucket: "miara-voyages.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

8. **GARDEZ CE CODE** - On l'utilisera dans la prochaine étape

---

## ✅ ÉTAPE 6 : Configurer les règles de sécurité Firestore

1. Dans **"Firestore Database"**, cliquez sur l'onglet **"Rules"**

2. Remplacez tout le contenu par :
```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Fonction pour vérifier si l'utilisateur est admin
    function isAdmin() {
      return request.auth != null && 
             get(/databases/$(database)/documents/users/$(request.auth.uid)).data.role == 'admin';
    }
    
    // Fonction pour vérifier si l'utilisateur est connecté
    function isAuthenticated() {
      return request.auth != null;
    }
    
    // Collection des voyages
    match /voyages/{voyageId} {
      // Lecture : tous les utilisateurs authentifiés
      allow read: if isAuthenticated();
      
      // Écriture : seulement les admins
      allow write: if isAdmin();
    }
    
    // Collection des utilisateurs
    match /users/{userId} {
      // Lecture : utilisateur lui-même ou admin
      allow read: if request.auth.uid == userId || isAdmin();
      
      // Écriture : seulement le user lui-même ou admin
      allow write: if request.auth.uid == userId || isAdmin();
    }
    
    // Collection des photos
    match /photos/{photoId} {
      // Lecture : tous les utilisateurs authentifiés
      allow read: if isAuthenticated();
      
      // Écriture : seulement les admins
      allow write: if isAdmin();
    }
  }
}
```

3. Cliquez sur **"Publish"**

✅ Règles de sécurité configurées !

---

## ✅ ÉTAPE 7 : Créer le document utilisateur Admin

1. Dans **"Firestore Database"**, cliquez sur **"Data"**

2. Cliquez sur **"Start collection"**

3. Collection ID : `users`

4. Cliquez sur **"Next"**

5. Document ID : Utilisez l'UID de votre compte (copiez-le depuis Authentication > Users)

6. Ajoutez ces champs :
   - `email` (string) : `jerome.miara@groupe-obea.com`
   - `role` (string) : `admin`
   - `name` (string) : `Jérôme Miara`
   - `createdAt` (timestamp) : Cliquez sur l'horloge pour date actuelle

7. Cliquez sur **"Save"**

✅ Votre compte admin est configuré !

---

## 🎯 Récapitulatif

Vous avez maintenant :
- ✅ Firebase Authentication activé
- ✅ Firestore Database activé
- ✅ Compte admin créé
- ✅ Règles de sécurité configurées
- ✅ Configuration Firebase récupérée

---

## 📝 Prochaine étape

Dans la prochaine version du site, nous intégrerons :
1. La configuration Firebase dans le code
2. Le système de connexion fonctionnel
3. Le stockage des photos dans Firestore
4. La gestion multi-utilisateurs

---

## 🔐 Sécurité

**IMPORTANT :**
- Ne partagez JAMAIS votre configuration Firebase publiquement
- Les règles de sécurité protègent vos données
- Seuls les utilisateurs authentifiés peuvent accéder au site
- Seuls les admins peuvent modifier le contenu

---

Bon courage ! 🔥
```

4. **"Commit new file"**

---
