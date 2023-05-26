
1. [Next.js-Grundlagen und Routing](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/nextjs-basics-and-routing/nextjs-basics-and-routing.md)[Challenges]()


2. [Dynamische Routen von Next.js](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/nextjs-basics-and-routing/nextjs-basics-and-routing.md)[Challenges]()




### 1. Next.js-Grundlagen und Routing



Lernziele
Den Unterschied zwischen einer Bibliothek und einem Framework kennen
Verstehen, warum Next.js ein so beliebtes Framework ist
Wissen, welche Funktionen während des Bootcamps genutzt werden
Die Grundkonzepte von Next.js verstehen:
Clientseitiges Routing
Seitennavigation mitnext/link
Bildoptimierung mitnext/image


Unterschied zwischen einer Bibliothek und einem Framework

Next.js ist ein React-Framework, das heißt, es baut auf der React-Bibliothek auf. Sowohl eine Bibliothek als auch ein Framework sind wiederverwendbarer Code, der von jemand anderem geschrieben wurde. Ihr Zweck besteht darin, Ihnen dabei zu helfen, häufig auftretende Probleme einfacher zu lösen.

Wenn Sie eine Bibliothek verwenden, haben Sie die Kontrolle darüber, welche Teile des Codes Sie wann verwenden. Im Gegensatz dazu ist ein Framework wie Next.js starrer: Sie haben nur wenige begrenzte Möglichkeiten, wann und wie Sie den gegebenen Code verwenden möchten. Wenn Sie diese Einschränkungen akzeptieren, nimmt Ihnen ein Framework im Hintergrund viel Arbeit ab.

Was ist Next.js?

Next.js ist ein React-Framework, das Ihnen Bausteine ​​zum Erstellen schneller Webanwendungen bietet. Diese Bausteine ​​bieten vorgefertigte Lösungen für die Hauptkonzepte, denen Sie beim Erstellen moderner Anwendungen begegnen, wie z. B. Benutzeroberfläche, Routing, Datenabruf, Infrastruktur usw.

> 📙 Read more about [N**ext.js** on the Next.js Homepage](https://nextjs.org/).

Welche Features von Next.js werden wir im Bootcamp nutzen?
Next.js hilft uns bei folgenden Themen:

Eine Vorlage als Ausgangspunkt
Ein Bundler, Transpiler und Entwicklungsserver
Routing: Navigieren zwischen Seiten, dynamisches Routing
Automatisch optimierte Bilder
API-Routen

> 📙 Next.js has a lot more to offer, which is why it is such a popular framework. To get an impression of all features, [have a quick look at the documentation](https://nextjs.org/docs).

.

Anleitung zu Next.js: Grundlagen

Unterschiede zum Erstellen einer React-App

Hier sehen Sie einen Vergleich einiger relevanter Unterschiede zwischen Next.js und Create React App (CRA):

Next.js (neu)	React App erstellen (alt)
Starten Sie den lokalen Entwicklungsserver	npm run dev	npm run start
Root-Komponente	_app.js	App.js
Dokumentieren	_document.js	public/index.html
Standardstil	CSS-Module*	CSS*
Rendern	Server- und Clientseite	Client-Seite
Routendefinition	Dateistruktur im pagesOrdner	n / A
Clientseitige Links	<Link>Komponente	n / A
Bildoptimierung	<Image>Komponente	n / A
Ändern<head>	<Head>Komponente	n / A
Laden der Schriftart	@next/fontPaket	n / A
API-Routen	pages/apiOrdner	n / A
ESLint	Next.js-spezifische Regeln	CRA-spezifische Regeln
Bundler + Transpiler	Webpack/Turbopack + SWC	Webpack + Babel
*Sowohl Next.js als auch CRA unterstützen alle modernen Styling-Lösungen.

Serverseitiges Rendering

Bei CRA lädt der Browser ein fast leeres HTML-Dokument ( public/index.html). Ihr React-Code wird nur im Browser ausgeführt.

Next.js verfügt über eine Funktion namens „serverseitiges Rendering“. Diese Funktion führt Ihre React-Komponenten auf dem Server aus, um ein vollständiges HTML-Dokument an den Client (den Browser) zu senden. Auf dem Client wird Ihr React-Code erneut ausgeführt.

Dies ermöglicht viele Optimierungstechniken, die wir nicht diskutieren werden. Es gibt jedoch eine wichtige Implikation, die Sie kennen müssen:

windowDa Ihr React-Code in einer Serverumgebung und nicht nur in einer Browserumgebung ausgeführt wird, müssen Sie bei der Verwendung von Browser-APIs (wie oder document) vorsichtig sein . Sie sind nur im Browser verfügbar und unterbrechen die App auf dem Server. Wenn Sie eine Browser-API verwenden, müssen Sie sicherstellen, dass Ihr Code nur auf dem Client ausgeführt wird. Beispielsweise useEffectwird Code innerhalb eines Hooks nur auf dem Client ausgeführt, da Effekte nicht auf dem Server, sondern nur auf dem Client ausgeführt werden. Auch Eventhandler wie onClickwerden nur auf dem Client ausgeführt.

```jsx
useEffect(() => {
  console.log(window.innerWidth);
}, []);

return <button onClick={() => console.log(window.innerWidth)}>Click me</button>;
```

Routenführung

Bisher zeigten unsere React-Anwendungen immer nur eine einzige Seite an. Der Vorgang des bedingten Renderns verschiedener Seiten basierend auf der URL (Pfadname) und des Navigierens zwischen diesen Seiten wird als Routing bezeichnet.

Da eine gute Routing-Lösung nicht einfach zu erstellen ist, verlassen sich fast alle React-Entwickler auf eine externe Routing-Bibliothek. Ist zum Beispiel react-routereine sehr beliebte Lösung.

Next.js bietet Routing als integrierte Funktion, sodass Sie keine weitere Bibliothek benötigen.

Das Routing in Next.js basiert auf dem Dateisystem im pagesOrdner:

- `pages/index.js` → `/` (`index.js` always implies the root route of a folder)
- `pages/about.js` → `/about`


Um komplexere Routen zu unterstützen, können Sie die entsprechende verschachtelte Ordnerstruktur erstellen:

- `pages/about/me.js` → `/about/me`
- `pages/about/all-others.js` → `/about/all-others`
- `pages/about/some/long/route.js` → `/about/some/long/route`


💡Sie können auch dynamische Routen (Routen mit dynamischen Parametern) definieren. Dies wird ein Thema einer zukünftigen Sitzung sein.

💡Dateibasiertes Routing kann mehrdeutig sein. Die Dateien pages/about/index.jsund pages/about.jssind beide mit verknüpft /about. In der Praxis stellt dies selten ein Problem dar. Dennoch sollte man sich dessen bewusst sein.

 📙 Read more about [**Routing** in the Next.js Docs](https://nextjs.org/docs/routing/introduction)..

###  <link> Komponente
Für clientseitige Übergänge zwischen Routen verwenden Sie die <Link>von next/link bereitgestellte Komponente. Gegeben ein pagesVerzeichnis mit

- `pages/index.js`
- `pages/about.js`
- `pages/about/me.js`,

Sie können auf jede dieser Seiten wie folgt verlinken:

```js
import Link from "next/link";

export default function Navigation() {
  return (
    <ul>
      <li>
        <Link href="/">Home</Link>
      </li>
      <li>
        <Link href="/about">About</Link>
      </li>
      <li>
        <Link href="/about/me">Me</Link>
      </li>
    </ul>
  );
}
```


> 📙 Read more about [**next/link** in the Next.js Docs](https://nextjs.org/docs/api-reference/next/link).

Bildoptimierung mitnext/image

Next.js verfügt über eine automatische Bildoptimierung – die next/image-Komponente. Diese Funktion vermeidet beispielsweise den Versand großer Bilder an Geräte mit einem kleineren Darstellungsbereich und Bilder werden standardmäßig verzögert geladen. Bedenken Sie, dass die Verwendung <Image>ein wenig Standardstil mit sich bringt.

Hier ist eine Beispielimplementierung. Beachten Sie, dass die Requisiten heightund widthdie gewünschte Rendergröße haben sollten, mit einem Seitenverhältnis, das mit dem des Quellbilds identisch ist.

```js
import Image from "next/image";

export default function AnimalImage() {
  <Image
    src="/images/a_small_dog.jpg"
    height={144}
    width={144}
    alt="A picture of a small dog"
  />;
}
```
Wenn Sie Bilder von externen Domänen verwenden, müssen Sie die zulässigen Domänen in der next.config.jsDatei konfigurieren:

```js
const nextConfig = {
  reactStrictMode: true,
  images: {
    domains: ["images.unsplash.com"],
  },
};
```


> 📙 Read more about [configuring **domains** for next/image](https://nextjs.org/docs/api-reference/next/image#domains) and [**next/image** in general in the Next.js Docs](https://nextjs.org/docs/api-reference/next/image).

---

## Resources

- [Next.js Homepage](https://nextjs.org/)
- [Next.js Docs](https://nextjs.org/docs)
- [Routing in the Next.js Docs](https://nextjs.org/docs/routing/introduction)
- [next/link in the Next.js Docs](https://nextjs.org/docs/api-reference/next/link)
- [next/image in the Next.js Docs](https://nextjs.org/docs/api-reference/next/image)
- [Difference between a Framework and a Library on freecodecamp](https://www.freecodecamp.org/news/the-difference-between-a-framework-and-a-library-bd133054023f/)

-------

2. [Dynamische Routen von Next.js](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/nextjs-basics-and-routing/nextjs-basics-and-routing.md)[Challenges]()


Dynamische Routen von Next.js

Lernziele

Das Konzept dynamischer Pfade verstehen
Wissen, wie man dynamische Pfade implementiert
Wissen, wie man Links dynamisch generiert
Wissen, wie man zwingendes Routing verwendet
Verstehen der Next/Head-Komponente

Konzept dynamischer Routen

Wenn Ihre App über viele mögliche Routen mit sich wiederholenden Mustern verfügt, wäre es schwierig bis unmöglich, pro Route eine JavaScript-Datei zu erstellen.

Mithilfe dynamischer Routen können Sie (Teile) des Pfads mithilfe von eckigen Klammern in dynamische Parameter umwandeln. Wenn die URL mit dem Pfad übereinstimmt, stellt Next.js die dynamischen Abfrageparameter mithilfe des useRouterHooks zur Verfügung.

![Dynamic Routing](dynamic-routes.excalidraw.png)

Dynamische Routen implementieren

Um eine dynamische Route zu erstellen, können Sie Datei- oder Ordnernamen im Seitenverzeichnis jeweils in eckige Klammern setzen: `pages/movies/[categorySlug]/page/[pageNumber].js`

Die folgenden Pfade sind diesem Beispiel zugeordnet:

- `movies/romance/page/12`
- - `categorySlug` is `"romance"`
  - `pageNumber` is `"12"`
- `movies/action/page/1`
- - `categorySlug` is `"action"`
  - `pageNumber` is `"1"`
- `movies/comedy/page/3`

  - `categorySlug` is `"comedy"`
  - `pageNumber` is `"3"`


Um auf die Abfrageparameter in einer Komponente zuzugreifen, verwenden Sie den useRouterHook importiert aus next/router:

```js
// pages/movies/categories/[categorySlug]/page/[pageNumber].js
import { useRouter } from "next/router";

export default function CategoryPage() {
  const router = useRouter();
  const { categorySlug, pageNumber } = router.query;

  return (
    <div>
      <p>Category Slug: {categorySlug}</p>
      <p>Page Number: {pageNumber}</p>
    </div>
  );
}
```

Dies gilt natürlich auch für ein einfacheres Beispiel mit einem einzigen dynamischen Abfrageparameter.


```js
// pages/movies/[slug].js
import { useRouter } from "next/router";

export default function MoviePage() {
  const router = useRouter();
  const { slug } = router.query;

  return (
    <div>
      <p>Slug: {slug}</p>
    </div>
  );
}
```


💡Der Name des Abfrageparameters wird immer dem Namen der Datei/des Verzeichnisses zugeordnet:`[slug].js` → `const { slug } = router.query;`

> 📙 Read more about [**Dynamic Routes** in the Next.js Docs](https://nextjs.org/docs/routing/dynamic-routes). .

Verknüpfung mit dynamischen Routen

Mit der Komponente können Sie `Link` eine Verknüpfung zu dynamischen Pfaden herstellen. Verwenden Sie die Zeichenfolgeninterpolation mit einer Vorlagenzeichenfolge, um die dynamischen Abfrageparameter in den Pfad einzufügen.

Betrachten Sie eine `Movies` Komponente, die eine Liste von Links zu allen Filmen rendert, interpolieren Sie diese slugals Abfrageparameter in den Pfad:

```js
import Link from "next/link";

export default function Movies({ movies }) {
  return (
    <ul>
      {movies.map(({ id, slug, title }) => (
        <li key={id}>
          <Link href={`/movies/${slug}`}>{title}</Link>
        </li>
      ))}
    </ul>
  );
}
```

> 📙 Read more about
> [**Linking to dynamic paths** in the Next.js Docs](https://nextjs.org/docs/routing/introduction#linking-to-dynamic-paths).

Imperatives Routing

Die Verwendung <Link>ist immer dann die beste Option, wenn der Benutzer selbstständig durch die App navigiert. Es gibt jedoch Situationen, in denen Sie eine LinkKomponente nicht verwenden können, weil Sie programmgesteuert zu einer anderen Seite navigieren möchten. Ein Beispiel für eine nicht direkte Benutzerinteraktion ist der Seitenwechsel nach dem Absenden eines Formulars:


```js
import { useRouter } from "next/router";

export default function Form() {
  const router = useRouter();

  function handleSubmit(event) {
    // some data handling … ✨

    router.push("/home");
  }

  return <form onSubmit={handleSubmit}>…</form>;
}
```
> 📙 Read more about [Routing **Imperatively** in the Next.js Docs](https://nextjs.org/docs/routing/imperatively).


## next/head component


Next.js verfügt über eine integrierte <Head>Komponente zum Anhängen von Elementen an den Kopf der Seite. Auf diese Weise können Sie die Metadaten der Seite wie das <title>HTML-Tag einfach ändern:

```js
import Head from "next/head";

export default function Movies() {
  return (
    <>
      <Head>
        <title>Movies</title>
        <meta name="viewport" content="initial-scale=1.0, width=device-width" />
      </Head>
      <ul>…</ul>
    </>
  );
}
```
> 📙 Read more about [**next/head** in the Next.js Docs](https://nextjs.org/docs/api-reference/next/head).

---

## Resources

- [Dynamic Routes in the Next.js Docs](https://nextjs.org/docs/routing/dynamic-routes)
- [Linking to dynamic paths in the Next.js Docs](https://nextjs.org/docs/routing/introduction#linking-to-dynamic-paths)
- [Routing Imperatively in the Next.js Docs](https://nextjs.org/docs/routing/imperatively)
- [next/head in the Next.js Docs](https://nextjs.org/docs/api-reference/next/head)
