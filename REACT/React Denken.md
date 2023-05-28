React kann Ihre Einstellung zu den Designs, die Sie sich ansehen, und den Apps, die Sie erstellen, verändern. Wenn Sie mit React eine Benutzeroberfläche erstellen, zerlegen Sie diese zunächst in Teile, die als Komponenten bezeichnet werden . Anschließend beschreiben Sie die unterschiedlichen visuellen Zustände für jede Ihrer Komponenten. Schließlich verbinden Sie Ihre Komponenten miteinander, sodass die Daten durch sie fließen.

Stellen Sie sich vor, Sie verfügen bereits über eine JSON-API und ein Modell eines Designers

Um eine Benutzeroberfläche in React zu implementieren, befolgen Sie normalerweise die gleichen fünf Schritte.

1.Um die Benutzeroberfläche in React in Komponenten aufzuteilen, sollten Sie Kästchen um jede Komponente zeichnen und diese benennen. Sie können die Aufteilung basierend auf Programmierprinzipien, CSS oder Designprinzipien vornehmen. Die Komponenten sollten idealerweise nur eine Aufgabe haben und können bei Bedarf in Unterkomponenten aufgeteilt werden. Eine gut strukturierte Datenmodellierung passt häufig natürlicherweise zur Komponentenstruktur der Benutzeroberfläche. Jede Komponente sollte einem Teil des Datenmodells entsprechen.

2.Nachdem Sie nun Ihre Komponentenhierarchie haben, ist es an der Zeit, Ihre App umzusetzen. Der einfachste Ansatz besteht darin, eine Version zu erstellen, die die Benutzeroberfläche aus Ihrem Datenmodell rendert, ohne jegliche Interaktivität hinzuzufügen... zumindest noch nicht! Es ist oft einfacher, zuerst die statische Version zu erstellen und später die Interaktivität hinzuzufügen. Das Erstellen einer statischen Version erfordert viel Tipparbeit und wenig Denken, während das Hinzufügen von Interaktivität viel Denken erfordert, aber weniger Tipparbeit

<img src=""/>

beispiel

3.Schritt 3: Minimale, vollständige Darstellung des UI-Zustands finden

Um das UI interaktiv zu gestalten, verwenden Sie den Zustand, um Benutzern die Änderung des Datenmodells zu ermöglichen. Der Zustand ist die minimale Menge an sich ändernden Daten, die die App behalten muss. Strukturieren Sie den Zustand, indem Sie ihn DRY (Don't Repeat Yourself) halten. Identifizieren Sie den minimalen Zustand, den Ihre Anwendung benötigt, und berechnen Sie alles andere bei Bedarf. In einem Beispiel mit einer Einkaufsliste werden beispielsweise die Artikel als Array im Zustand gespeichert. Die Anzahl der Artikel kann aus der Länge des Arrays abgeleitet werden. Im Beispiel werden nur der Suchtext und der Wert der Checkbox als Zustand betrachtet, während die ursprüngliche Liste der Produkte und die gefilterte Liste nicht zum Zustand gehören.


Es gibt zwei Arten von "Modell"-Daten in React: props und state. Die beiden sind sehr unterschiedlich:
Props sind ähnlich wie Argumente, die du einer Funktion übergibst. Sie ermöglichen es einem übergeordneten Komponente, Daten an eine untergeordnete Komponente zu übergeben und deren Erscheinungsbild anzupassen. Zum Beispiel kann ein Formular eine Farb-Prop an einen Button übergeben.
State ist wie das Gedächtnis einer Komponente. Es ermöglicht einer Komponente, Informationen zu speichern und sie in Reaktion auf Interaktionen zu ändern. Zum Beispiel kann ein Button den Zustand "isHovered" verfolgen.
Props und state sind unterschiedlich, aber sie arbeiten zusammen. Eine übergeordnete Komponente behält häufig einige Informationen im Zustand (damit sie diese ändern kann) und gibt sie als Props an untergeordnete Komponenten weiter



Schritt 4: Ermitteln Sie, wo sich Ihr Zustand befinden sollte

Nachdem Sie die minimale Zustandsdaten Ihrer App ermittelt haben, müssen Sie feststellen, welche Komponente für die Änderung dieses Zustands verantwortlich ist oder den Zustand besitzt. Denken Sie daran: React verwendet einen Einweg-Datenfluss, bei dem Daten von der übergeordneten Komponente an die untergeordnete Komponente weitergegeben werden. Es ist möglicherweise nicht sofort klar, welche Komponente welchen Zustand besitzen sollte. Dies kann eine Herausforderung sein, wenn Sie neu in diesem Konzept sind, aber Sie können es herausfinden, indem Sie diesen Schritten folgen!
Für jedes Stück Zustand in Ihrer Anwendung:
Ermitteln Sie jede Komponente, die etwas basierend auf diesem Zustand rendert.
Finden Sie ihren gemeinsamen übergeordneten Komponenten - eine Komponente über ihnen in der Hierarchie.
Entscheiden Sie, wo der Zustand leben sollte:
Oft können Sie den Zustand direkt in ihrem gemeinsamen übergeordneten Komponenten platzieren.
Sie können den Zustand auch in einer Komponente über ihrem gemeinsamen übergeordneten Komponenten platzieren.
Wenn Sie keine Komponente finden können, in der es sinnvoll ist, den Zustand zu besitzen, erstellen Sie eine neue Komponente, die ausschließlich für das Halten des Zustands verantwortlich ist, und fügen Sie sie irgendwo in der Hierarchie über der gemeinsamen übergeordneten Komponente hinzu.
Im vorherigen Schritt haben Sie zwei Zustandsstücke in dieser Anwendung gefunden: den Sucheingabetext und den Wert der Checkbox. In diesem Beispiel treten sie immer zusammen auf, daher macht es Sinn, sie an derselben Stelle zu platzieren.
Folgen wir nun unserer Strategie für sie:
Ermitteln Sie die Komponenten, die den Zustand verwenden:
ProductTable muss die Produktliste basierend auf diesem Zustand (Suchtext und Checkbox-Wert) filtern.
SearchBar muss diesen Zustand (Suchtext und Checkbox-Wert) anzeigen.
Finden Sie ihren gemeinsamen übergeordneten Komponenten: Die erste übergeordnete Komponente, die beide Komponenten gemeinsam haben, ist FilterableProductTable.
Entscheiden Sie, wo der Zustand lebt: Wir werden die Filtertext- und Checked-Zustandswerte in FilterableProductTable behalten.
Daher werden die Zustandswerte in FilterableProductTable leben.
Fügen Sie dem Komponenten mit dem useState() Hook den Zustand hinzu. Hooks sind spezielle Funktionen, mit denen Sie sich an React "anhaken" können. Fügen Sie zwei Zustandsvariablen oben in FilterableProductTable hinzu und geben Sie ihren anfänglichen Zustand an.

<img src=""/>

Schritt 5: Umkehren des Datenflusses hinzufügen


Aktuell rendert Ihre App korrekt mit Props und dem Zustand, der die Hierarchie hinunterfließt. Aber um den Zustand entsprechend der Benutzereingabe zu ändern, müssen Sie auch den Datenfluss in die andere Richtung unterstützen: Die Formularkomponenten tief in der Hierarchie müssen den Zustand in FilterableProductTable aktualisieren können.
React macht diesen Datenfluss explizit, er erfordert jedoch etwas mehr Tipparbeit als die bidirektionale Datenbindung. Wenn Sie im obigen Beispiel versuchen, in das Textfeld zu tippen oder das Kontrollkästchen zu aktivieren, werden Sie feststellen, dass React Ihre Eingabe ignoriert. Das ist beabsichtigt. Durch die Verwendung von <input value={filterText} /> haben Sie die value-Prop des Eingabefelds so gesetzt, dass es immer dem filterText-Zustand entspricht, der von FilterableProductTable übergeben wird. Da der filterText-Zustand nie geändert wird, ändert sich das Eingabefeld nie.
Sie möchten erreichen, dass immer wenn der Benutzer die Formularfelder ändert, der Zustand aktualisiert wird, um diese Änderungen widerzuspiegeln. Der Zustand wird von FilterableProductTable verwaltet, daher kann nur diese Komponente setFilterText und setInStockOnly aufrufen. Damit SearchBar den Zustand von FilterableProductTable aktualisieren kann, müssen Sie diese Funktionen an SearchBar weitergeben.


function FilterableProductTable({ products }) {
  const [filterText, setFilterText] = useState('');
  const [inStockOnly, setInStockOnly] = useState(false);

  return (
    <div>
      <SearchBar 
        filterText={filterText} 
        inStockOnly={inStockOnly}
        onFilterTextChange={setFilterText}
        onInStockOnlyChange={setInStockOnly} />
<img src=""/>



Im Inneren SearchBarfügen Sie die onChangeEreignishandler hinzu und legen daraus den übergeordneten Status fest:


<input 
  type="text" 
  value={filterText} 
  placeholder="Search..." 
  onChange={(e) => onFilterTextChange(e.target.value)} />
