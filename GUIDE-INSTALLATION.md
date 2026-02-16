# Guide d'Installation - Miara Voyages

## 🎯 Objectif

Mettre en ligne votre site sur **miara-voyages.fr**

---

## ✅ ÉTAPE 1 : Activer GitHub Pages

### Actions :

1. Sur votre repository `miara-voyages`, cliquez sur **"Settings"** (en haut)

2. Dans le menu de gauche, cliquez sur **"Pages"**

3. Sous **"Source"** :
   - Branch : Sélectionnez **`main`**
   - Folder : Laissez **`/ (root)`**

4. Cliquez sur **"Save"**

5. ⏳ Attendez 2-3 minutes

6. 🎉 Votre site est en ligne sur : `https://jerome432.github.io/miara-voyages/`

---

## ✅ ÉTAPE 2 : Connecter le domaine OVH

### A) Sur OVH

1. Connectez-vous sur https://www.ovh.com/manager/

2. Allez dans **"Domaines"** → **"miara-voyages.fr"**

3. Cliquez sur **"Zone DNS"**

4. Supprimez les enregistrements A existants (s'il y en a)

5. **Ajoutez 4 enregistrements A :**

   Cliquez sur **"Ajouter une entrée"** → **"A"**
   
   - Type : A
   - Sous-domaine : (laissez vide ou mettez `@`)
   - Cible : `185.199.108.153`
   
   Répétez pour ces 3 autres adresses :
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`

6. **Ajoutez 1 enregistrement CNAME pour www :**

   Cliquez sur **"Ajouter une entrée"** → **"CNAME"**
   
   - Type : CNAME
   - Sous-domaine : `www`
   - Cible : `jerome432.github.io.` (avec le point à la fin !)

7. Cliquez sur **"Valider"**

8. ⏳ Attendez 5-30 minutes (propagation DNS)

---

### B) Sur GitHub

1. Retournez sur votre repository **"Settings"** → **"Pages"**

2. Sous **"Custom domain"**, entrez :
```
   miara-voyages.fr
```

3. Cliquez sur **"Save"**

4. ✅ Cochez **"Enforce HTTPS"** (après quelques minutes)

---

## ✅ ÉTAPE 3 : Vérifier

1. Ouvrez votre navigateur

2. Allez sur : **https://miara-voyages.fr**

3. 🎉 Votre site est en ligne !

---

## ⏰ Temps de propagation DNS

- **Minimum :** 5 minutes
- **Maximum :** 48 heures (rare)
- **Moyenne :** 15-30 minutes

Pendant ce temps, vous pouvez voir :
- "Site not found"
- "DNS_PROBE_FINISHED_NXDOMAIN"
- C'est normal ! ☕ Patience...

---

## 🐛 Problèmes fréquents

### "Site not found"
→ Attendez encore un peu la propagation DNS

### "Not secure" / Pas de HTTPS
→ Sur GitHub Pages, cochez "Enforce HTTPS" (après 10-15 min)

### "www.miara-voyages.fr ne marche pas"
→ Vérifiez que vous avez bien ajouté l'enregistrement CNAME pour `www`

---

## 🎯 Résultat final

Vous aurez :
- ✅ https://miara-voyages.fr → Fonctionne
- ✅ https://www.miara-voyages.fr → Fonctionne
- ✅ HTTPS activé (cadenas vert 🔒)
- ✅ Site accessible partout dans le monde

---

## 📞 Besoin d'aide ?

Si vous êtes bloqué, vérifiez :
1. Que les 4 enregistrements A sont bien configurés sur OVH
2. Que l'enregistrement CNAME pour www est configuré
3. Que le fichier CNAME existe dans votre repository
4. Attendez au moins 30 minutes après les modifications DNS

---

Bon courage ! 🚀
```

4. **"Commit new file"**

---
