# Metadaten

Unabhängig von ihrer Herkunft benötigen Daten möglicherweise zusätzliche Daten, die interpretiert werden müssen. Wenn wir zum Beispiel die Koordinaten eines Punktes haben, um ihn richtig zu interpretieren, brauchen wir unter anderem das Koordinatensystem, in dem diese Koordinaten ausgedrückt werden. Die Daten, mit denen wir arbeiten (die Koordinaten), sollten mit zusätzlichen Daten (wie dem EPSG-Code des Koordinatensystems) versehen sein.

Diese Zusatzdaten werden als Metadaten bezeichnet. Metadaten sind Daten über die Daten und dienen dazu, die Bedeutung der Daten zu erklären. Das heißt, sie helfen dem Benutzer, die Bedeutung der Daten und der darin enthaltenen Informationen besser zu verstehen. Metadaten sind ein zusätzliches Dokument, das die Daten begleitet und eine bessere Verwaltung und Verwendung ermöglicht.

Innerhalb von GIS werden Metadaten in der Regel einer Ebene und ihrem Inhalt zugeordnet und können auf beide Komponenten (räumlich und thematisch) bezogen werden.

Das Konzept der Metadaten schließt digitale geografische Daten nicht aus. Eine gedruckte Karte hat Metadaten in einer bestimmten Art und Weise. Eine Legende oder ein Text am Rand mit Informationen über das Erstellungsdatum sind ebenfalls Metadaten. Bei digitalen Metadaten sind die Metadaten unabhängig von den Daten selbst. Dadurch können wir Operationen getrennt von den Metadaten ausführen, was viele Möglichkeiten eröffnet und ihnen einen höheren Wert verleiht.

Zwei der Hauptfunktionen von Metadaten sind die Gewährleistung der korrekten Verwendung von Daten und die Erleichterung ihrer Verwaltung, Ermittlung und Nutzung.

Geographische Daten werden, wie bei vielen anderen Arten von Daten, normalerweise für einen bestimmten Zweck erstellt, und dieser Zweck muss nicht in den Daten selbst enthalten sein oder leicht aus ihnen abgeleitet werden. Wenn Daten dann für einen anderen Zweck verwendet werden, können Probleme auftreten, da die Daten in diesem neuen Kontext möglicherweise einige Mängel aufweisen. Mit Hilfe von Metadaten kann dies gelöst werden. Metadaten können zum Beispiel helfen, die Verwendung veralteter oder ungenauer Datensätze zu vermeiden. Wenn wir die Parameter kennen, die einen Datensatz definieren (ursprüngliche Skala, Datum usw.), können wir besser beurteilen, ob sie für eine bestimmte Aufgabe verwendet werden sollen oder nicht.

Datenersteller müssen ihnen genügend Metadaten hinzufügen, und Benutzer müssen die zugehörigen Metadaten konsultieren, bevor sie Daten verwenden.

In Bezug auf das Datenmanagement erleichtern Metadaten Operationen wie das Durchsuchen von Daten in größeren Datensätzen oder Datensammlungen. Metadaten können eine Zusammenfassung der vollständigen Daten enthalten, die sie begleiten, und sie können verwendet werden, um Suchvorgänge effizienter zu gestalten, wenn sie geografische Kriterien verwenden. Wenn ein Benutzer beispielsweise ermitteln möchte, ob eine Datensammlung Daten für einen bestimmten Bereich enthält, sollte der gesamte Inhalt jeder Vektorschicht in der Sammlung überprüft werden, um festzustellen, ob eine seiner Geometrien in den angeforderten Bereich fällt. Dies kann eine langwierige Operation sein. Wenn jeder Ebene Metadaten mit ihrer Ausdehnung zugeordnet sind, kann die Abfrage mit den Metadaten ausgeführt werden, was viel schneller ist, da sie unabhängig von der Anzahl der Features in der Ebene ist. Dies ist von grundlegender Bedeutung beim Erstellen von Datenkatalogen, die auf Benutzeranfragen basierend auf den in den Metadaten enthaltenen Informationen reagieren.

## Inhalt von Metadaten. Metadaten erstellen

Die Informationen, die in den mit geographischen Daten verbundenen Metadaten enthalten sind, hängen von Parametern wie dem verwendeten Repräsentationsmodell, dem Format, in dem Daten gespeichert werden (Dateiformat, Datenbank usw.), der für die Daten oder das Element verantwortlichen Organisation, Entität oder Person ab (s) mit denen sie verbunden sind (Menge von Schichten, Layer, Feature, etc.).

Einige der gemeinsamen Elemente, die bei geografischen Daten den Metadaten hinzugefügt werden, sind Identifikationsinformationen (um sie auf einzigartige Weise zu identifizieren und von anderen Daten zu unterscheiden), Informationen über ihre Qualität (einschließlich ihrer Herkunft und der Herkunft der Daten) sie können von der Datenherkunft stammen) oder Informationen über ihre Verteilung (Zugang, Lizenz, etc.). Metadaten können am Datenursprung erstellt werden, während die Daten selbst erstellt werden. Es kann auch später von Datenverteilern, Managern oder Benutzern erweitert werden.

Der Großteil des Metadateninhalts wird manuell mithilfe bestimmter Anwendungen erstellt, die manchmal mit Desktop-GIS-Tools verbunden sind. Metadatenelemente, die aus den Daten selbst extrahiert werden können (z. B. der Datenumfang), können automatisch erstellt werden.

Metadaten werden im Allgemeinen als zusätzliche Dateien gespeichert, die den Datendateien beigefügt sind, oder sie werden als Teil einer Datenbank gespeichert.


