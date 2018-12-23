# GPS

Eine der relevantesten Fortschritte in Bezug auf geografische Datenquellen sind globale Satellitennavigationssysteme (GNSS). Zu jedem Zeitpunkt und zu jeder Zeit können wir mit diesen Systemen die genaue Position dieses Punktes mit einer Genauigkeit von wenigen Metern oder weniger ermitteln. Um dies zu tun, verwenden sie eine Konstellation von Satelliten, zu denen Informationen von dem Untersuchungspunkt übertragen werden, und verwenden diese Übertragung, um die Koordinaten des Punktes zu berechnen.

Das erste und beliebteste dieser Systeme ist das Global Positioning System (GPS). Es hat 24 aktive Satelliten (das Satellitensegment) zusammen mit terrestrischen Stationen, um sie zu steuern (das Kontrollsegment) und es basiert auf Trilateration. Entfernungen werden von einer GPS-Einheit (dem Benutzersegment) zu einer bestimmten Anzahl von Satelliten gemessen. Mit diesen Entfernungen und der genauen Position der Satelliten kann die Position der Einheit berechnet werden. Die Position wird mit ihren x-, y- und z-Koordinaten berechnet. Das GPS-System verwendet WGS-84 als Referenzellipsoid.

Das Satellitennetzwerk soll gewährleisten, dass von jedem Punkt der Erdoberfläche aus und zu jeder Zeit eine GPS-Einheit die erforderliche Anzahl von Satelliten lokalisieren kann, um ihre Position zu berechnen.

Es gibt mehrere Fehlerquellen, die die Genauigkeit der von einer GPS-Einheit berechneten Position beeinflussen können. Unter ihnen finden wir Fehler in der Position von Satelliten, Fehler aufgrund der Wirkung der Erdatmosphäre auf das GPS-Signal, und auch Fehler, die durch Genauigkeitsprobleme mit den Uhren zur Messung der Signallaufzeit verursacht werden (die dann in Fahrdistanz umgewandelt wird) ). Die selektive Verfügbarkeit war ein zufälliger Fehler, der im GPS-Signal zu militärischen Zwecken eingeführt wurde. Es wurde jedoch am 2. Mai 2000 entfernt.

Unter den Techniken, die verwendet werden, um diese Fehler zu korrigieren oder zu minimieren, ist das differentielle GPS das wichtigste. Es wurde ursprünglich entwickelt, um den Effekt der selektiven Verfügbarkeit zu beseitigen, kann aber verwendet werden, um einen großen Teil der anderen Fehler, die das GPS-System beeinflussen, zu korrigieren.

Um Differential-GPS anzuwenden, wird zusammen mit der Empfängereinheit, für die seine Position berechnet werden soll, ein zweiter Empfänger benötigt. Es muss fixiert sein, nicht mobil, und seine Koordinaten müssen mit großer Genauigkeit bekannt sein. Dieser Empfänger ist selbst eine hochpräzise Einheit und sendet Informationen aus, die andere Einheiten verwenden können, um ihre Position zu korrigieren.

Die Idee ist, dass Fehler, die die mobile GPS-Einheit betreffen, auch die feste Referenz beeinflussen. Der Fehler für die Referenzeinheit kann berechnet werden, da seine Position bekannt ist, und unter Verwendung der Diskrepanz zwischen dieser realen Position und derjenigen, die unter Verwendung des GPS-Systems berechnet wurde, kann die Position anderer GPS-Einheiten korrigiert werden.

Mit dieser Differentialkorrektur kann ein normales GPS Koordinaten mit einer Genauigkeit von ungefähr 2 Metern in ihren x- und y-Komponenten und ungefähr 3 Metern in der z-Komponente erhalten. Ohne Differential-GPS ist eine Genauigkeit von nur 10 - 20 Metern zu erwarten.

Die Genauigkeit des GPS-Systems hängt von der GPS-Einheit ab. Es gibt viele Klassen von GPS-Empfängern, aber die wichtigsten, aus der Sicht von GIS, sind zwei:

- GPS für den allgemeinen Gebrauch. Diese Geräte sind kostengünstig, klein und portabel für Aktivitäten im Freien, wo eine hohe Genauigkeit nicht erforderlich ist. Die GPS-Empfänger in Smartphones fallen in diese Kategorie.
- GPS für die Vermessung. Größere Einheiten, normalerweise mit unabhängigen Antennen, die mit dem Empfänger verbunden sind, um die Genauigkeit zu erhöhen. Es sorgt auch für eine bessere Lokalisierung von Satelliten unter schwierigen Bedingungen, wie unter Baumkronen. Sie sind für den professionellen Einsatz konzipiert.

In Bezug auf seine Verbindung mit GIS können GPS-Einheiten Koordinaten sammeln und dann GIS-Schichten mit ihnen erstellen. Sie können Punkte speichern (in der üblichen GPS-Terminologie als Wegpunkte bezeichnet) oder den Pfad erfassen, den der Benutzer verfolgt (Track genannt). In diesem letzten Fall speichert der Empfänger Punkte in regelmäßigen Intervallen, so dass der Benutzer sich einfach bewegen kann und die Koordinaten nicht entlang der Route manuell speichern muss. Diese Information kann später in einem GIS zur weiteren Analyse oder Visualisierung eingeführt werden.


