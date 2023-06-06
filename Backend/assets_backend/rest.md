#REST

REST steht für "Representational State Transfer" und ist ein architektonischer Stil für verteilte hypermediale Systeme. Es wurde erstmals 2000 von Roy Fielding in seiner berühmten Dissertation vorgestellt.

REST hat seine Leitprinzipien und Einschränkungen, die erfüllt sein müssen, damit eine Service-Schnittstelle als RESTful bezeichnet werden kann.

Eine Web-API (oder ein Web-Service), die dem REST-Architekturstil entspricht, wird als REST-API bezeichnet.

## Leitprinzipien von REST

Die sechs Leitprinzipien oder Einschränkungen der RESTful-Architektur sind:

### 1.1. Einheitliche Schnittstelle

Durch die Anwendung des Prinzips der Allgemeingültigkeit auf die Schnittstellenkomponenten können wir die Gesamtarchitektur des Systems vereinfachen und die Sichtbarkeit von Interaktionen verbessern.

Mehrere architektonische Einschränkungen helfen dabei, eine einheitliche Schnittstelle zu erreichen und das Verhalten der Komponenten zu lenken.

Die folgenden vier Einschränkungen können eine einheitliche REST-Schnittstelle erreichen:

Identifizierung von Ressourcen: Die Schnittstelle muss jede am Austausch zwischen Client und Server beteiligte Ressource eindeutig identifizieren.
Manipulation von Ressourcen durch Darstellungen: Die Ressourcen sollten einheitliche Darstellungen in der Serverantwort haben. API-Konsumenten sollten diese Darstellungen verwenden, um den Zustand der Ressourcen auf dem Server zu ändern.

Selbstbeschreibende Nachrichten: Jede Ressourcendarstellung sollte ausreichend Informationen enthalten, um zu beschreiben, wie die Nachricht verarbeitet werden soll. Sie sollte auch Informationen über zusätzliche Aktionen bereitstellen, die der Client mit der Ressource ausführen kann.

Hypermedia als Motor des Anwendungsstatus:Der Client sollte nur die anfängliche URI der Anwendung haben. Die Clientanwendung sollte alle anderen Ressourcen und Interaktionen dynamisch mit Hilfe von Hyperlinks steuern.

### 1.2. Client-Server

Das Client-Server-Entwurfsmuster erzwingt die Trennung von Verantwortlichkeiten, was den unabhängigen Fortschritt der Client- und Serverkomponenten ermöglicht.

Durch die Trennung der Benutzeroberflächenbelange (Client) von den Datenspeicherbelangen (Server) verbessern wir die Portabilität der Benutzeroberfläche auf verschiedenen Plattformen und verbessern die Skalierbarkeit, indem wir die Serverkomponenten vereinfachen.

Während der Client und der Server sich weiterentwickeln, müssen wir sicherstellen, dass die Schnittstelle/der Vertrag zwischen dem Client und dem Server nicht gebrochen wird.

### 1.3. Zustandslos

Zustandslosigkeit bedeutet, dass jede Anfrage des Clients an den Server alle Informationen enthalten muss, die erforderlich sind, um die Anfrage zu verstehen und zu bearbeiten.

Der Server kann keine zuvor gespeicherten Kontextinformationen auf dem Server nutzen.

Aus diesem Grund muss die Clientanwendung den gesamten Sitzungszustand vollständig beibehalten.

### 1.4. Cachebar

Die Cachebarkeits-Einschränkung besagt, dass eine Antwort sich implizit oder explizit als cachebar oder nicht-cachebar kennzeichnen sollte.

Wenn die Antwort cachebar ist, erhält die Clientanwendung das Recht, die Antwortdaten später für äquivalente Anfragen und einen bestimmten Zeitraum erneut zu verwenden.

### 1.5. Schichtensystem

Der schichtengebundene Systemstil ermöglicht es, eine Architektur aus hierarchischen Schichten aufzubauen, indem das Verhalten der Komponenten eingeschränkt wird.

Beispielsweise kann in einem schichtengebundenen System jede Komponente nicht über die unmittelbare Schicht hinaus sehen, mit der sie interagiert.

### 1.6. Code bei Bedarf (optional)

REST ermöglicht es auch, die Client-Funktionalität durch Herunterladen und Ausführen von Code in Form von Applets oder Skripten zu erweitern.

Der heruntergeladene Code vereinfacht Clients, indem er die Anzahl der vorimplementierten Funktionen reduziert. Server können einen Teil der Funktionen als Code an den Client übermitteln, und der Client muss nur den Code ausführen.

Was ist eine Ressource?

Die zentrale Abstraktion von Informationen in REST ist eine Ressource. Jede Information, die wir benennen können, kann eine Ressource sein. Eine REST-Ressource kann beispielsweise ein Dokument, ein Bild, ein zeitlicher Dienst, eine Sammlung anderer Ressourcen oder ein nicht virtuelles Objekt (z. B. eine Person) sein.
Der Zustand der Ressource zu einem bestimmten Zeitpunkt wird als Ressourcendarstellung bezeichnet.

Die Ressourcendarstellungen bestehen aus:

den Daten
den Metadaten, die die Daten beschreiben
und den Hypermedia-Links, die den Clients beim Übergang zum nächsten gewünschten Zustand helfen können.
Eine REST-API besteht aus einer Sammlung von miteinander verknüpften Ressourcen. Diese Ressourcensammlung wird als Ressourcenmodell der REST-API bezeichnet.

### 2.1. Ressourcenidentifikatoren

REST verwendet Ressourcenidentifikatoren, um jede Ressource zu identifizieren, die an den Interaktionen zwischen den Client- und Serverkomponenten beteiligt ist.

### 2.2. Hypermedia

Das Datenformat einer Darstellung wird als Medientyp bezeichnet. Der Medientyp identifiziert eine Spezifikation, die definiert, wie eine Darstellung verarbeitet werden soll.

Eine RESTful-API sieht aus wie Hypertext. Jede adressierbare Informationseinheit hat eine Adresse, entweder explizit (z. B. durch Link- und id-Attribute) oder implizit (z. B. abgeleitet aus der Medientypdefinition und der Darstellungsstruktur).

Hypertext (oder Hypermedia) bedeutet die gleichzeitige Präsentation von Informationen und Steuerelementen, so dass die Informationen die Möglichkeit bieten, durch die der Benutzer (oder Automat) Auswahlmöglichkeiten erhält und Aktionen auswählt.

Beachten Sie, dass Hypertext nicht unbedingt HTML (oder XML oder JSON) auf einem Browser sein muss. Maschinen können Links folgen, wenn sie das Datenformat und die Beziehungstypen verstehen.

### 2.3. Selbstbeschreibend

Darüber hinaus sollten Ressourcendarstellungen selbstbeschreibend sein: Der Client muss nicht wissen, ob eine Ressource ein Mitarbeiter oder ein Gerät ist. Er sollte entsprechend des mit der Ressource verknüpften Medientyps handeln.

In der Praxis werden wir daher viele benutzerdefinierte Medientypen erstellen - normalerweise ein Medientyp, der mit einer Ressource verknüpft ist.

Jeder Medientyp definiert ein Standardverarbeitungsmodell. Zum Beispiel definiert HTML einen Rendering-Prozess für Hypertext und das Browserverhalten für jedes Element.

Medientypen stehen in keiner Beziehung zu den Ressourcenmethoden GET/PUT/POST/DELETE/... abgesehen davon, dass einige Medientypelemente ein Prozessmodell definieren, das wie folgt aussieht: "Anker-Elemente mit einem href-Attribut erstellen einen Hypertext-Link, der bei Auswahl eine Abrufanfrage (GET) auf den URI auslöst, der dem CDATA-kodierten href-Attribut entspricht".

Ressourcenmethoden

Eine weitere wichtige Sache, die mit REST verbunden ist, sind Ressourcenmethoden. Diese Ressourcenmethoden werden verwendet, um den gewünschten Übergang zwischen zwei Zuständen einer Ressource durchzuführen.
Viele Menschen bringen Ressourcenmethoden fälschlicherweise mit HTTP-Methoden (z. B. GET/PUT/POST/DELETE) in Verbindung. Roy Fielding hat niemals eine Empfehlung dazu gemacht, welche Methode in welcher Situation verwendet werden soll. Er betont lediglich, dass es sich um eine einheitliche Schnittstelle handeln sollte.

Wenn wir beispielsweise entscheiden, dass die Anwendungs-APIs HTTP POST zur Aktualisierung einer Ressource verwenden sollen - anstatt wie von den meisten Menschen empfohlen HTTP PUT -, ist das in Ordnung. Die Anwendungsschnittstelle ist immer noch RESTful.

Idealerweise sollte alles, was für den Übergang des Ressourcenzustands erforderlich ist, Teil der Ressourcendarstellung sein - einschließlich aller unterstützten Methoden und in welcher Form sie die Darstellung verlassen werden.

Wir sollten eine REST-API ohne vorheriges Wissen über den initialen URI (ein Lesezeichen) und einen Satz standardisierter Medientypen betreten, die für die beabsichtigte Zielgruppe geeignet sind (d. h. von jedem Client verstanden werden, der die API verwenden könnte).

Von diesem Punkt an müssen alle Anwendungszustandsübergänge durch die Auswahl serverseitig bereitgestellter Auswahlmöglichkeiten in den empfangenen Darstellungen oder durch die Benutzermanipulation dieser Darstellungen bestimmt werden.

Die Übergänge können durch das Wissen der Clients über Medientypen und Ressourcenkommunikationsmechanismen bestimmt (oder begrenzt) werden, von denen beide dynamisch verbessert werden können (z. B. Code-on-Demand). [Ein Scheitern bedeutet hier, dass Informationen außerhalb des Bandes die Interaktion steuern, anstatt Hypertext.]

### REST und HTTP sind nicht dasselbe

Viele Menschen ziehen es vor, HTTP und REST als synonym zu verwenden, was jedoch nicht korrekt ist. REST ist ein Architekturstil, während HTTP ein Protokoll ist.
Obwohl REST am häufigsten mit HTTP verwendet wird, ist es möglich, REST mit anderen Protokollen wie SMTP oder FTP zu implementieren. Allerdings passt das REST-Modell gut zum Web und seinen Protokollen wie HTTP.

HTTP bietet bereits viele der benötigten Funktionen, wie z. B. eine einheitliche Schnittstelle (HTTP-Methoden), Zustandslosigkeit (HTTP-Anfragen enthalten alle notwendigen Informationen), Caching-Unterstützung (durch Cache-Header), Schichtensystem (Proxy-Server) und Code bei Bedarf (z. B. durch JavaScript-Code in einer Webanwendung).

Allerdings kann eine HTTP-API nicht automatisch als RESTful bezeichnet werden. Sie muss die oben genannten REST-Prinzipien und -Einschränkungen erfüllen, um als RESTful zu gelten.

### Zusammenfassung

REST ist ein architektonischer Stil für verteilte hypermediale Systeme. Eine REST-API folgt den REST-Prinzipien und -Einschränkungen und ermöglicht es Clients, mit Ressourcen über eine einheitliche Schnittstelle zu interagieren.
Eine Ressource ist eine abstrakte Informationseinheit, die durch einen Ressourcenidentifikator identifiziert wird. Die Zustände einer Ressource werden durch Ressourcendarstellungen repräsentiert, die Daten, Metadaten und Hypermedia-Links enthalten können.

REST und HTTP sind nicht dasselbe, obwohl REST oft mit HTTP implementiert wird. HTTP bietet bereits viele Funktionen, die mit REST vereinbar sind, aber eine HTTP-API muss die REST-Prinzipien erfüllen, um als RESTful zu gelten.
