# Formulaire Artiste (Google Sheets Sync)

Un formulaire HTML simple qui envoie les réponses vers une Google Sheet via Google Apps Script.

## 🚀 Étapes de configuration

### 1. Créer la Google Sheet
- Ajoute un onglet nommé `Réponses HTML`
- Ligne 1 : `Horodatage | Nom | Email | Message`

### 2. Coller le script Apps Script

Ouvre Google Sheets > Extensions > Apps Script :

```javascript
function doPost(e) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Réponses HTML");
  sheet.appendRow([
    new Date(),
    e.parameter.nom,
    e.parameter.email,
    e.parameter.message
  ]);
  return ContentService.createTextOutput("OK");
}
```

### 3. Déployer comme Web App

- Déployer → Nouveau déploiement → Type : Application Web
- Exécuter en tant que : Moi-même
- Accès : Tout le monde (même anonymes)
- Clique sur Déployer et copie l’URL

### 4. Modifier `index.html`

Remplace `TON_URL_WEBAPP` par l’URL copiée.

### 5. Héberger sur GitHub Pages

1. Pousse le projet dans un repo GitHub public
2. Paramètres > Pages > Source : branche `main`, dossier `/root`
3. Le site sera accessible sur :
   `https://tonpseudo.github.io/formulaire-artiste/`

## 🎉 Résultat

- Le formulaire HTML est visible sur GitHub Pages
- Les réponses arrivent automatiquement dans ta Google Sheet