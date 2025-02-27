# Einführung in APIs (Application Programming Interfaces)

## **1. Was ist eine API?**
API steht für **Application Programming Interface** und ist eine Schnittstelle, die es zwei Systemen (z. B. Softwareanwendungen) ermöglicht, miteinander zu kommunizieren. Eine API definiert Regeln, über die Programme Daten anfordern und senden können.

**Vergleich aus der echten Welt:**
Eine API funktioniert ähnlich wie eine **Speisekarte in einem Restaurant**.  
- Du (der Kunde) wählst aus der Speisekarte (API) eine Bestellung aus.  
- Der Kellner (API-Aufruf) nimmt deine Bestellung entgegen und gibt sie an die Küche (Server) weiter.  
- Die Küche bereitet das Essen zu und gibt es dem Kellner zurück.  
- Der Kellner liefert dir das fertige Essen (Daten).  

Du musst nicht wissen, **wie die Küche funktioniert** – du benutzt einfach die Speisekarte. Genau so verhält es sich mit APIs!

---

## 2. Warum brauchen wir APIs?
APIs ermöglichen es verschiedenen Systemen, **datenbasiert zu interagieren**.  
Beispiele für APIs:
- Websites rufen Wetterdaten von einer API ab.
- Eine Banking-App fragt den Kontostand über eine API ab.
- Eine E-Commerce-Website nutzt eine Zahlungs-API (z. B. PayPal oder Stripe).

APIs sind wichtig, weil sie:
- **Wiederverwendbarkeit** ermöglichen (einmal entwickelt, mehrfach nutzbar).
- **Automatisierung** von Aufgaben erlauben.
- **Daten sicher zwischen Anwendungen austauschen**.
- Entwicklern helfen, schneller Software zu schreiben, ohne alles von Grund auf neu zu entwickeln.

---

## 3. API-Grundstruktur mit Express.js
Hier ist eine einfache API, die mit **Node.js und Express** erstellt wurde. Sie speichert Benutzer und gibt sie als JSON zurück.

```javascript
const express = require('express'); // Express.js importieren
const app = express(); // Express-Anwendung erstellen
const port = 3000; // Port-Nummer festlegen

app.use(express.json()); // Middleware für JSON-Daten aktivieren

let users = [ // Beispiel-Datenbank (Array von Benutzern)
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" }
];

// GET-Route: Alle Benutzer abrufen
app.get('/users', (req, res) => {
    res.json(users);
});

// POST-Route: Neuen Benutzer hinzufügen
app.post('/users', (req, res) => {
    const newUser = { id: users.length + 1, name: req.body.name };
    users.push(newUser);
    res.status(201).json(newUser);
});

// Server starten
app.listen(port, () => console.log(`Server läuft auf Port ${port}`));
```

---

## 4. Erklärung des Codes

### 1. Express.js importieren
```javascript
const express = require('express');
```
- **`require('express')`** lädt das Express-Framework.
- **`const express`** speichert das Modul, damit wir es später verwenden können.

### 2. Express-Anwendung erstellen
```javascript
const app = express();
```
- **`express()`** erstellt eine neue **Express-App**.
- **`app`** speichert die Anwendung, sodass wir Routen definieren können.

### 3. Port-Nummer festlegen
```javascript
const port = 3000;
```
- Der Server lauscht auf Port **3000**.

### 4. Middleware für JSON aktivieren
```javascript
app.use(express.json());
```
- Ermöglicht das Empfangen von JSON-Daten in `req.body`.

### 5. Beispiel-Datenbank (Array von Benutzern)
```javascript
let users = [
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" }
];
```
- Ein Array als einfache Datenbank für Benutzer.

### 6. GET-Route: Benutzer abrufen
```javascript
app.get('/users', (req, res) => {
    res.json(users);
});
```
- Bei einer **GET-Anfrage** an `/users` sendet der Server die Benutzerliste als JSON.

### 7. POST-Route: Benutzer hinzufügen
```javascript
app.post('/users', (req, res) => {
    const newUser = { id: users.length + 1, name: req.body.name };
    users.push(newUser);
    res.status(201).json(newUser);
});
```
- Erstellt einen neuen Benutzer und speichert ihn im `users`-Array.
- **`res.status(201).json(newUser);`** gibt den neuen Benutzer zurück.

### 8. Server starten
```javascript
app.listen(port, () => console.log(`Server läuft auf Port ${port}`));
```
- Startet den Server auf **localhost:3000**.

---

## 5. API testen
### 1. Server starten
**Im Terminal ausführen:**
```
node server.js
```

### 2. GET `/users` aufrufen
```
GET http://localhost:3000/users
```
Antwort:
```json
[
    { "id": 1, "name": "Alice" },
    { "id": 2, "name": "Bob" }
]
```

### 3. POST `/users` (neuen Benutzer hinzufügen)
```
POST http://localhost:3000/users
Content-Type: application/json

{
    "name": "Charlie"
}
```
Antwort:
```json
{ "id": 3, "name": "Charlie" }
```

### 4. GET `/users` erneut aufrufen
Antwort:
```json
[
    { "id": 1, "name": "Alice" },
    { "id": 2, "name": "Bob" },
    { "id": 3, "name": "Charlie" }
]
```
🔄 **Der neue Benutzer wurde erfolgreich gespeichert!**

---

## 6. Fazit
- **Express.js** macht es einfach, APIs zu erstellen.
- **GET-Routen** holen Daten, **POST-Routen** erstellen neue Einträge.
- **Middleware (`express.json()`)** erlaubt die Verarbeitung von JSON-Daten.
- **Statuscodes** geben Feedback über den Erfolg oder Fehler einer Anfrage.

Diese Grundstruktur kann für komplexere APIs erweitert werden! 🚀

