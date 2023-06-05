# Backend-Grundlagen- [challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/backend-basics/challenges-backend-basics.md)


Bisher haben wir JavaScript nur im Browser verwendet. Aber JavaScript kann auch außerhalb des Browsers verwendet werden.

Node.js ist eine Laufzeitumgebung für JavaScript. Es ermöglicht uns, JavaScript außerhalb des Browsers auszuführen. Node.js unterscheidet sich in einigen Punkten vom Browser. Zum Beispiel besitzt Node.js kein DOM, aber es stellt einige APIs bereit, die im Browser nicht verfügbar sind. Zum Beispiel bietet Node.js eine API zum Zugriff auf das Dateisystem.

Eine Sache, die Node.js tun kann, ist das Erstellen eines Web-Servers. Ein Web-Server ist ein Programm, das auf Anfragen lauscht und Antworten an den Client zurückschickt. Der Web-Server kann verwendet werden, um Webseiten bereitzustellen oder eine API für eine Webanwendung anzubieten.

Ausführen eines Node-Programms
Um ein Node-Programm auszuführen, muss der node-Befehl verwendet werden. Der node-Befehl nimmt den Pfad zu einer JavaScript-Datei als Argument. Der folgende node-Befehl führt die JavaScript-Datei index.js im Stammverzeichnis des Projekts aus: node index.js.

Für Bequemlichkeit enthalten unsere Vorlagen ein Skript in der package.json, mit dem das Programm mit npm run start ausgeführt werden kann. Die Vorlage enthält einen Entwicklungsmodus, der das Programm automatisch neu startet, wenn Änderungen am Code vorgenommen werden. Um den Entwicklungsmodus zu starten, kannst du npm run dev verwenden. Schau dir die package.json-Datei an, um zu sehen, wie die Skripte definiert sind.

### Ein einfaches Node.js-Programm

Ein Node.js-Programm kann fast alles sein. Es kann ein Web-Server, ein Kommandozeilenwerkzeug oder ein Skript sein, das Berechnungen durchführt. Versuche ein Node.js-Programm zu erstellen, das "Hello World" in die Konsole druckt oder einige Berechnungen durchführt.

```js
console.log("Hello World");
const answer = 32 + 4;
console.log(answer);

```


Führe das Programm mit dem node-Befehl aus. Zum Beispiel, wenn du das Programm in einer Datei namens index.js speicherst, kannst du es mit node index.js ausführen.

💡 Du kannst die console.log-Funktion verwenden, um Werte in der Konsole auszugeben. Im Falle von Node.js ist die Konsole das Terminal und nicht die Browser-Konsole.

### Node.js-Server

Du kannst Node.js verwenden, um Web-Server zu erstellen. Dazu kannst du das http-Modul von Node.js verwenden.

Du kannst ein natives Node-Modul importieren, indem du das Präfix node: verwendest. Um zum Beispiel das http-Modul zu importieren, kannst du den folgenden Code verwenden:

```js
import { createServer } from "node:http";
```


Du musst das http-Modul nicht installieren. Es ist in Node.js enthalten.

### Erstellen eines Servers

Das http-Modul bietet eine Funktion namens createServer, die eine Rückruffunktion als Argument annimmt. Die Rückruffunktion wird jedes Mal aufgerufen, wenn eine Anfrage an den Server gestellt wird. Die Rückruffunktion wird mit zwei Argumenten aufgerufen: Anfrage (request) und Antwort (response). Das Anfrage-Objekt enthält Informationen über die Anfrage, die an den Server gestellt wurde. Das Antwort-Objekt wird verwendet, um eine Antwort an den Client zu senden.

```js
import { createServer } from "node:http";

export const server = createServer((request, response) => {
response.statusCode = 200;
response.end("Hello World");
});

```


Die Eigenschaft response.statusCode wird verwendet, um den Statuscode der Antwort festzulegen. Die Methode response.end nimmt einen String als Argument an. Der String wird an den Client gesendet.

Du kannst auf das Anfrage-Objekt zugreifen, um Informationen über die Anfrage abzurufen, die an den Server gestellt wurde. Zum Beispiel kannst du auf die Eigenschaft request.url des Anfrage-Objekts zugreifen, um die angeforderte URL zu erhalten.

```js
import { createServer } from "node:http";

export const server = createServer((request, response) => {
if (request.url === "/") {
response.statusCode = 200;
response.end("Hello World");
} else {
response.statusCode = 404;
response.end("Not Found");
}
});

```

💡 Im Internet findest du die Abkürzungen req und res für request und response. Dies ist eine gängige Konvention, aber req und res sind sehr schwer zu unterscheiden, daher verwenden wir in diesem Bootcamp die vollständigen Namen.

### Starten des Servers (Lauschen auf Anfragen)

Um den Server zu starten, musst du die Methode listen auf dem Serverobjekt aufrufen. Die Methode listen nimmt zwei Argumente an: die Portnummer und eine optionale Rückruffunktion. Die Rückruffunktion wird aufgerufen, wenn der Server bereit ist, Anfragen entgegenzunehmen.

Um den Code, der den Server erstellt, vom Code, der den Server startet, zu trennen, kannst du das Serverobjekt aus einer server.js-Datei exportieren und den Server in index.js starten:

```js
// index.js
import { server } from "./server.js";

const port = 8000;
server.listen(port, () => {
console.log(Server running at http://127.0.0.1:${port}/);
});
```

💡 Wenn du listen aufrufst, wird Node.js das Programm am Laufen halten, anstatt es sofort zu beenden. Dies ist notwendig, da das Programm weiterhin laufen muss, um Anfragen entgegenzunehmen.


## Resources

- [Node.js Website](https://nodejs.org/)
- [`http.createServer()` in the Node.js Docs](https://nodejs.org/api/http.html#httpcreateserveroptions-requestlistener)
- [`server.listen()` in the Node.js Docs](https://nodejs.org/api/http.html#serverlisten)


---

# Backend API-Routen

Lernziele

Verstehen, was serverlose Funktionen sind
Verstehen, wofür eine serverseitige API gedacht ist
Wissen, wie man Next.js-API-Routen implementiert
Statische API-Routen
Dynamische API-Routen
Wissen, wie man API-Routen mit console.log() debuggen kann


### Serverlose Funktionen

Es gibt verschiedene Ansätze zur Erstellung von Backend-Funktionen für Webanwendungen.

Ein traditioneller Webserver, zum Beispiel mit dem Node.js-Framework Express, ist ein Programm, das auf einem Server oder einer virtuellen Maschine läuft und auf eingehende HTTP-Anfragen lauscht - ähnlich wie ein Kellner in einem Restaurant, der darauf wartet, dass Kunden ihre Bestellungen aufgeben. Der Code für den Express-Server ist in der Regel in einer sogenannten monolithischen Struktur geschrieben, bei der alle verschiedenen Funktionen und Endpunkte vom selben Programm verwaltet werden.

Auf der anderen Seite sind serverlose Funktionen wie kleine Helfer, die nur bei Bedarf ausgeführt werden, d.h. wenn sie benötigt werden. Sie warten auf spezifische Ereignisse, z.B. wenn eine Webanwendung eine HTTP-Anfrage erhält oder wenn eine Datenbank aktualisiert wird. Wenn dies geschieht, führt die serverlose Funktion ihren Code aus, um die spezifische Aufgabe durchzuführen, für die sie programmiert wurde, und wird anschließend beendet. Serverlose Cloud-Anbieter wie Vercel kümmern sich um alle Details, wie z.B. die Einrichtung der für die Ausführung des Codes erforderlichen Computerressourcen und das Herunterfahren, wenn die Aufgabe erledigt ist. Es ist, als hätte man ein Team von Köchen, die in die Küche kommen, ein Gericht zubereiten und dann alles aufräumen, wenn sie fertig sind. Dadurch wird es für Entwickler einfacher, Code zu schreiben, ohne sich um das Management von Servern oder Ressourcen kümmern zu müssen.

> 💡 This is a very basic explanation. If you're interested in learning more about
> Vercel Serverless Functions, you can read about it [here](https://vercel.com/docs/concepts/functions/serverless-functions)

Wofür eine serverseitige API gedacht ist
Wie wir bereits in der JS Fetch-Sitzung gelernt haben, kann eine API (Application Programming Interface) aus verschiedenen Perspektiven betrachtet werden und auf verschiedenen Ebenen auftreten.

APIs, die auf einer Serverumgebung ausgeführt werden, werden serverseitige APIs genannt. Sie werden von einem Server bereitgestellt und stehen im Gegensatz zu den von den Browsern bereitgestellten APIs (auch als Client bezeichnet). Ein häufiger Anwendungsfall für solche serverseitigen APIs besteht darin, Daten zu erstellen, zu lesen, zu aktualisieren und zu löschen, also sogenannte CRUD-Operationen.

💡 Werfe einen Blick auf das Handout der JS Fetch-Sitzung, um dein Wissen über APIs aufzufrischen.

### Next.js-API-Routen

Unser Hauptziel ist es, eine Datenbank zu erstellen und ihre Daten in unserer Webanwendung zu verwalten. Dazu müssen wir unsere eigenen API-Routen innerhalb der Webanwendung erstellen und entscheiden, welche Informationen und Daten die Routen zurückgeben. Glücklicherweise bietet Next.js uns eine coole Funktion mit einfacher und intuitiver Syntax.

Es folgt eine einfache Ordnerstruktur: Jede Datei innerhalb des Ordners, z.B. pages/api/test/file.js, wird auf die entsprechende URL mit demselben Pfad, z.B. /api/test/file, abgebildet und als API-Endpunkt anstelle einer Seite behandelt.

In Next.js ist eine API-Route einfach ein JavaScript-Modul, das eine Standardfunktion exportiert. Zum Beispiel erstellt eine Datei namens pages/api/hello.js den API-Endpunkt /api/hello, der mit einer JSON-Nachricht "Hello neuefische!" antwortet. Die Handler-Funktion nimmt zwei Argumente entgegen: ein Anfrageobjekt und ein Antwortobjekt, die verwendet werden, um das serverlose Programm auf Vercel zu starten, eingehende Anfragen zu bearbeiten und Antworten an den Client zu senden.

```js
export default function handler(request, response) {
response.status(200).json({ message: "Hello neuefische!" });
}

```


💡 Weitere Informationen zu Next.js-API-Routen findest du hier.
> 💡 Further information about [Next.js API Routes](https://nextjs.org/docs/api-routes/introduction).

### Dynamische API-Routen

Next.js unterstützt dynamische API-Routen, um API-Endpunkte zu erstellen, die dynamische Parameter im URL-Pfad verarbeiten können. Dabei gelten die gleichen Dateinamensregeln wie für Seiten.

Wenn du z.B. einen API-Endpunkt erstellen möchtest, der Anfragen für einzelne Witze verarbeiten kann, könntest du eine Datei namens /pages/api/jokes/[id].js erstellen. Dadurch wird eine dynamische API-Route erstellt, bei der der id-Parameter einen beliebigen Wert annehmen kann. Wenn du einen einzelnen Witz abrufen möchtest, abhängig von der in der Browser-Route verwendeten id des Witzes, können wir über die Zerlegung des request.query-Objekts auf den id-Routenparameter zugreifen.

```js
export default function handler(request, response) {
const { id } = request.query;
//...
}
```

💡 Weitere Informationen zu Next.js-Dynamic API-Routen findest du hier.
> 💡 Further information about [Next.js Dynamic API Routes](https://nextjs.org/docs/api-routes/dynamic-api-routes).

Wie man mit console.log() Protokolle/Debugausgaben erstellt
Du kannst die Funktion console.log() verwenden, um deine Webanwendung zu debuggen und zu verstehen, was in deinen API-Routen passiert. Da die API-Handler auf dem Server ausgeführt werden, wird die Konsolenausgabe in deinem Terminal (localhost) angezeigt, in dem du den Entwicklungsserver gestartet hast (npm run dev), oder in der Vercel-Weboberfläche (Vercel Deployment).

Lokal: In Terminal / Server-Konsole anzeigen



local: shown in terminal / server console
![Example of `console.log()`in API route file](assets_backend/log-messages-api-route-file.png)

Vercel: shown in web interface
![Example of `console.log()`in API route file](assets_backend/log-messages-api-route-file-runtime-log.png)

![Example shown in Vercel web interfach](assets_backend/vercel-runtime-log.png)

> 💡 Further information about [Vercel Runtime Logs](https://vercel.com/docs/concepts/observability/runtime-logs)

---

## Resources

- [Next.js API Routes](https://nextjs.org/docs/api-routes/introduction)
- [Vercel Serverless Functions](https://vercel.com/docs/concepts/functions/serverless-functions)
- [Vercel Runtime Logs](https://vercel.com/docs/concepts/observability/runtime-logs)


---

# Backend MongoDB

Lernziele:

Den Unterschied zwischen einer Datenbank und einem Server verstehen
Den Unterschied zwischen relationalen und nicht-relationalen Datenbanken verstehen
Grundlagen von MongoDB und wichtige Begriffe verstehen
Grundkenntnisse in der Datenbankgestaltung haben:
Strukturierung von Sammlungen (Foreign Keys, Referenzen)
Strukturierung von Dokumenten (verschachtelte Objekte)
Eins zu Eins (1:1) Beziehungen
Eins zu Viele (1:n) Beziehungen
Viele zu Viele (n:m) Beziehungen


## Einführung: Datenbanken
### Was ist eine Datenbank?

Erinnern wir uns daran, was ein Server ist:

Ein Programm, das rund um die Uhr läuft und Dienste für andere Computer oder Geräte bereitstellt.
Er kann eine Vielzahl von Diensten hosten, wie z.B. einen Webserver, einen E-Mail-Server, einen Dateiserver oder einen Datenbankserver.
Wir haben Next.js API-Routen als Server verwendet, um Daten (aus einer data.js-Datei im selben Projekt) bereitzustellen.
Betrachten wir nun, was ein Datenbankserver ist:

Es handelt sich um ein Programm, das speziell dazu entwickelt wurde, eine Datenbank zu hosten und zu verwalten.
Es verwaltet die in der Datenbank gespeicherten Daten.
Es stellt sicher, dass die Daten Benutzern und Anwendungen zur Verfügung stehen, die darauf zugreifen müssen.
Die Datenspeicherung in einer Datenbank ist persistent.
Relationale vs. nicht-relationale Datenbanken
Es gibt einige Unterschiede zwischen relationalen und nicht-relationalen Datenbanken (auch SQL vs. NoSQL genannt):

### Relationale Datenbanken:

Daten werden in Tabellen gespeichert (ähnlich wie in Excel, Numbers, Tabellenkalkulationen usw.).
Die Tabellen sind miteinander verbunden.
Einschränkung: Für jede Spalte muss entschieden werden, was passiert, wenn nicht für alle Einträge in dieser Spalte Daten vorhanden sind.
Nicht-relationale Datenbanken:

Daten werden in JSON-ähnlichen Strukturen gespeichert.

Daten werden in Schlüssel-Wert-Paaren gespeichert.

Jeder Datensatz in der Datenbank kann eindeutige Schlüssel haben.

💡 Eine ausführliche Erklärung und Vergleich findest du hier.

> 💡 You can find an [in-depth explanation and comparison here](https://www.mongodb.com/compare/relational-vs-non-relational-databases).
> 
---

### MongoDB 

Als nicht-relationale Datenbank ist MongoDB weniger streng und leicht zu verwenden.

Der Name MongoDB setzt sich aus "humongous" (riesig) und "DB" (Datenbank) zusammen.

Der Name wurde gewählt, um die Skalierbarkeit und Flexibilität der Datenbank widerzuspiegeln.

#### MongoDB-Begriffe

#### Datenbank:

Eine MongoDB-Datenbank ist eine Sammlung von Daten, die mit dem MongoDB-Datenbankmanagementsystem organisiert und gespeichert werden.

Eine MongoDB-Datenbank kann mehrere Datensätze enthalten, die als Sammlungen bezeichnet werden.

#### Sammlung:

Eine Sammlung ist eine Gruppierung von MongoDB-Einträgen, die als Dokumente bezeichnet werden.

Eine Sammlung entspricht einer Tabelle in einem relationalen Datenbanksystem.

Eine Sammlung existiert innerhalb einer einzelnen Datenbank.


#### Dokument:

Ein MongoDB-Dokument ist eine JSON-ähnliche Datenstruktur, die aus Schlüssel-Wert-Paaren besteht.

Dokumente können verschiedene Felder haben.

Diese Schlüssel-Wert-Paare werden als Felder bezeichnet.

#### Feld:

In MongoDB ist ein Feld ein Schlüssel-Wert-Paar, das in einem Dokument gespeichert wird.

Der Feldschlüssel ist ein String, der das Feld identifiziert, und der Feldwert ist die im Feld gespeicherte Daten.

### MongoDB-Abfragen (Mongo-Queries)

Du kannst deine lokale MongoDB-Datenbank in MongoDB Compass durchsuchen. Dazu öffne die MongoDB-Shell am unteren Rand der Anwendung.

Häufig verwendete Befehle:

`dbs`: Zeigt alle Datenbanken an.

`db`: Zeigt den Namen der aktuellen Datenbank an.

`use jokes-database`: Wechselt zur Datenbank mit dem Namen jokes-database.


The following commands refer to a collection called `jokes`:
| | Query Methods (one) | Query Methods (many) |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- |
| **C**reate | `db.jokes.insertOne({joke: "What's the action like at a circus? In-tents."})` | `db.jokes.insertMany([{…}, {…}])` |
| **R**ead | `db.jokes.findOne({_id: ObjectId("[paste_id_here]")})` | `db.jokes.find(…)` |
| **U**pdate | `db.jokes.updateOne({ _id: ObjectId("[paste_id_here]") }, { $set: { joke: "What's the action like at a circus? In-tents." } })` | `db.jokes.updateMany(…)` |
| **D**elete | `db.jokes.deleteOne({_id: ObjectId("[paste_id_here]")})` | `db.jokes.deleteMany(…)` |

> 📙 See the [MongoDB documentation](https://www.mongodb.com/docs/mongodb-shell/crud/) for details how to use the query methods.

### Datenbankgestaltung

### Allgemeine Richtlinien:

Entwerfe deine Sammlungen und Dokumente entsprechend den zu speichernden Daten und den auszuführenden Abfragen.

Verwende Arrays, um Listen von zusammengehörigen Daten in einem einzigen Dokument zu speichern.

Versuche, tief verschachtelte Datenstrukturen zu vermeiden. Wenn deine Dokumente zu komplex werden, teile die Daten in mehrere Sammlungen auf und verbinde sie mit Referenzen (siehe Beispiel unten).

Wenn du auf ein Objekt verweisen möchtest, das in einer anderen Sammlung gespeichert ist, kannst du Fremdschlüssel verwenden:

Wenn du eine Benutzersammlung und eine Witze-Sammlung hast, kannst du in der Witze-Sammlung einen Fremdschlüssel verwenden, um eine Referenz auf den Benutzer zu speichern, der den Witz erstellt hat.

Dadurch kannst du Informationen über den Benutzer, der den Witz erstellt hat, speichern, ohne die Daten in der Witze-Sammlung zu duplizieren.

## Datenbankbeziehungen

Es gibt drei verschiedene Beziehungen zwischen Dokumenten:

### Eins zu Eins

Eine Eins-zu-Eins-Beziehung in MongoDB besteht, wenn ein Dokument in einer Sammlung genau mit einem Dokument in einer anderen Sammlung verknüpft ist.
Dies kann durch Speichern einer Referenz auf das verknüpfte Dokument in einer der beiden Sammlungen implementiert werden. Die Richtung spielt in diesem Fall keine Rolle. Eins-zu-Eins-Beziehungen ergeben nur in bestimmten Sonderfällen Sinn. Aus Gründen der Einfachheit sollte darüber nachgedacht werden, die Felder einer Sammlung zur anderen hinzuzufügen, anstatt eine separate Beziehung zu verwenden.

###Eins zu Viele

Eine Eins-zu-Viele-Beziehung in MongoDB besteht, wenn ein Dokument in einer Sammlung mit mehreren Dokumenten in einer anderen Sammlung verknüpft ist.
Dies kann durch Speichern einer Referenz auf das "eins"-Dokument in den verknüpften "viele"-Dokumenten implementiert werden.
Viele zu Viele

Eine Viele-zu-Viele-Beziehung in MongoDB besteht, wenn mehrere Dokumente in einer Sammlung mit mehreren Dokumenten in einer anderen Sammlung verknüpft sind, und umgekehrt.

Dies wird normalerweise durch Erstellen einer Zwischensammlung erreicht, deren Dokumente eine Referenz auf beide verknüpften Sammlungen haben (sie werden in zwei Eins-zu-Viele-Beziehungen aufgeteilt).

> 📙 Read more about these [relationships in the MongoDB documentation](https://www.mongodb.com/docs/manual/tutorial/model-embedded-one-to-one-relationships-between-documents/).

Beispielhafte Visualisierung

Die folgenden drei Sammlungen veranschaulichen bewährte Praktiken und Beziehungen, die oben erwähnt wurden.

![Database Collections Example](assets/database_collections.png)

```js
// Witze-Sammlung:
{
"_id": ObjectId("Witz1ID"),
"userId": ObjectId("Benutzer1ID"),
"witz": "Warum mögen Programmierer die Natur nicht? Sie hat zu viele Bugs.",
}

// Benutzer-Sammlung:
{
"_id": ObjectId("Benutzer1ID"),
"benutzername": "jane.doe",
"email": "jane.doe@example.com",
}

// Kommentare-Sammlung:
{
"_id": ObjectId("Kommentar1ID"),
"witzId": ObjectId("Witz1ID"),
"userId": ObjectId("Benutzer1ID"),
"kommentar": "Das ist ein guter Witz!"
}
```

### Anmerkungen:

Jedes Dokument in den Sammlungen hat ein _id-Feld, das eindeutige Identifikatoren sind.

Jedes Witze-Dokument hat ein witz-Feld, das den Text des Witzes und ein userId-Feld enthält, das die ID des Benutzers speichert, der den Witz erstellt hat. Dadurch wird eine Eins-zu-Viele-Beziehung zwischen der Witze- und der Benutzer-Sammlung hergestellt (ein Witz gehört einem Benutzer, aber ein Benutzer kann viele Witze besitzen).

Jedes Benutzer-Dokument hat ein benutzername-Feld, das den Benutzernamen des Benutzers speichert, und ein email-Feld, das die E-Mail-Adresse des Benutzers speichert.

Jedes Kommentar-Dokument hat ein witzId-Feld, das die ID des Witzes speichert, auf den sich der Kommentar bezieht, ein userId-Feld, das die ID des Benutzers speichert, der den Kommentar erstellt hat, und ein kommentar-Feld, das den Text des Kommentars speichert. Dadurch wird eine Eins-zu-Viele-Beziehung zwischen der Kommentare- und der Benutzer-Sammlung sowie zwischen der Kommentare- und der Witze-Sammlung hergestellt (ein Kommentar gehört einem Benutzer und einem Witz, aber ein Benutzer kann viele Kommentare erstellen und ein Witz kann viele Kommentare haben).

Dieses Beispiel veranschaulicht die Verwendung von Referenzen (IDs anderer Dokumente) zur Verknüpfung von Sammlungen und die Organisation von Daten in MongoDB. Es ist wichtig zu beachten, dass die spezifische Datenbankgestaltung von den Anforderungen deiner Anwendung abhängt. Du solltest die Struktur deiner Datenbank basierend auf den Abfragen und Operationen planen, die du durchführen möchtest, um die Leistung und Effizienz zu optimieren.

Notes:

- Each document in the collections has an `_id` field that is a unique identifier.
- Each joke document has a `joke` field that stores the text of the joke and a `userId` field that stores the ID of the user who created the joke. This establishes a **one-to-many** relationship between the joke and the user collection (one joke is owned by one user, but one user can own many jokes).

- Each user document has a `username` field that stores the user's username and an `email` field that stores the user's email address.

- Each comment document has a `jokeId` field that stores the ID of the joke that the comment is associated with, a `userId` field that stores the ID of the user who created the comment, and a `comment` field that stores the text of the comment.
- The `jokeId` field and `userId` field implement **one-to-many** relationships between the comments, jokes, and users collections, as a joke can have multiple comments and a user can create multiple comments, but each comment can only be associated with one joke and one user.

---

## Resources

- [Differences between relational and non-relational databases](https://www.mongodb.com/compare/relational-vs-non-relational-databases)
- [In-depth explanation and comparison relational/non-relational](https://www.mongodb.com/compare/relational-vs-non-relational-databases)
- [CRUD operations in MongoDB documentation](https://www.mongodb.com/docs/mongodb-shell/crud/)
