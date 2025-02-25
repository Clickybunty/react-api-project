# 📌 API-Dokumentation

Diese API bietet CRUD-Funktionalitäten für die Verwaltung von Items. Sie basiert auf **Node.js** mit **Express.js** und stellt eine REST-API bereit.

## 📂 Basis-URL

```
http://localhost:5001/api
```

---

## 📌 Endpunkte & Methoden

### **🔵 1. GET /api/items** → Alle Items abrufen

**Beschreibung:** Gibt eine Liste aller gespeicherten Items zurück.

**Beispiel-Antwort:**

```json
[
  { "id": 1, "name": "Item 1" },
  { "id": 2, "name": "Item 2" }
]
```

---

### **🟢 2. POST /api/items** → Neues Item hinzufügen

**Beschreibung:** Fügt ein neues Item hinzu.

**Anfrage (Body JSON):**

```json
{
  "name": "Neues Item"
}
```

**Erfolgreiche Antwort:**

```json
{
  "id": 3,
  "name": "Neues Item"
}
```

**Fehlermeldungen:**

- `400 Bad Request` → Falls `name` fehlt oder leer ist

---

### **🟡 3. PUT /api/items/:id** → Item aktualisieren

**Beschreibung:** Aktualisiert den Namen eines bestehenden Items.

**Anfrage (Body JSON):**

```json
{
  "name": "Geändertes Item"
}
```

**Erfolgreiche Antwort:**

```json
{
  "id": 1,
  "name": "Geändertes Item"
}
```

**Fehlermeldungen:**

- `400 Bad Request` → Falls `name` fehlt oder leer ist
- `404 Not Found` → Falls `id` nicht existiert

---

### **🔴 4. DELETE /api/items/:id** → Item löschen

**Beschreibung:** Löscht ein Item anhand seiner ID.

**Erfolgreiche Antwort:**

```json
{
  "id": 2,
  "name": "Item 2"
}
```

**Fehlermeldungen:**

- `404 Not Found` → Falls `id` nicht existiert

---

## 📄 Fehlerbehandlung

Die API gibt standardisierte HTTP-Fehlercodes zurück:
| Fehlercode | Bedeutung |
|------------|----------|
| `400` | Ungültige Anfrage (z. B. fehlende Felder) |
| `404` | Ressource nicht gefunden |
| `500` | Interner Serverfehler |

---

## 🚀 Nutzungshinweise

- Alle Anfragen müssen das **JSON-Format** verwenden.
- Verwende `Content-Type: application/json` in Headern bei **POST** & **PUT**.
- Stelle sicher, dass das Backend unter **http://localhost:5001** läuft, bevor du Anfragen sendest.

---

## 📄 Weiterentwicklung & ToDos

- 🔜 Datenbank-Anbindung mit MongoDB oder MySQL
- 🔜 Authentifizierung mit JWT
- 🔜 Erweiterung um Kategorien für Items

---

### 🎉 Viel Erfolg mit der API! 🚀
