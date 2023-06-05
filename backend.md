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
![Example of `console.log()`in API route file](assets/log-messages-api-route-file.png)

Vercel: shown in web interface
![Example of `console.log()`in API route file](assets/log-messages-api-route-file-runtime-log.png)

![Example shown in Vercel web interfach](assets/vercel-runtime-log.png)

> 💡 Further information about [Vercel Runtime Logs](https://vercel.com/docs/concepts/observability/runtime-logs)

---

## Resources

- [Next.js API Routes](https://nextjs.org/docs/api-routes/introduction)
- [Vercel Serverless Functions](https://vercel.com/docs/concepts/functions/serverless-functions)
- [Vercel Runtime Logs](https://vercel.com/docs/concepts/observability/runtime-logs)


