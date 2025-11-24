QGIS - Workflow zum darstellen von Gefügeelementen auf einer Karte

Dieser Workflow dient für das Darstellen von Gefügeelementen in QGIS, da dies nicht mittels einer integrierten Funktion möglich ist muss ein Trick angewendet werden, den ich in diesem Workflow erläutere.
Die zur Darstellung verwendeten Symbole, welche in QGIS integriert werden müssen, sind ebenfalls im Ordner unter "Geological Symbols" enthalten.

Download und Integrieren der Symbole in QGIS:
1. Download der Symbole und entpacken
2. Öffnen des QGIS-Programmordners 
3. Unter "\apps\qgis" findet sich ein Ordner "svg" in diesem müssen die Symbole abgelegt werden

Darstellen von Gefügeelementen auf einer Karte:
1. Erstellen einer neuen Shape-Datei:	- Geometrietyp => Punkte
					- Hinzufügen von Feldelementen -> ID
									  TYPE (Für die Benennung um welches Gefügeelement es sich handelt)
									  Strike_Trend (Für die Streichrichtung)
									  Dip_Plunge (Für das Fallen bzw. Tauchen)
									  D_P_Azimuth (Für die Fallrichtung)
					-> alle Felder bis auf "TYPE" sollte ein "ganzzahliger Integer" sein
2. Erstellen von Punkten an gewünschten Stellen oder an vorher integrierten Koordinatenpunkten
3. Für jeden Punkt die Daten des Gefügeelements angeben und bestätigen
4. Öffnen der "Layergestaltung" um den Punkten die gewünschten *.svg Symbole zuzuweisen
	- Unter dem Punkt 'Symbolisierung' den Punkt "Kategorisiert" auswählen und nach dem Feld "TYPE" Kategorisieren
	- Öffnen der Punktgestaltung für die einzelnen Typen und Umstellen von "Einzelsymbol" auf "svg-Markierung"
	- gewünschtes geologisches Symbol für die einzelnen Typen wählen
	- für die richtige Rotation des Gefügeelements unter "Rotation" nach dem Feld " D_P_Azimuth"
	=> bestätigen und für jedes Gefügeelement wiederholen (für jeden Typ)
5. Beschriftung der Gefügeelemente
	- Unter dem Punkt 'Beschriftung' den Modus "Abstand vom Punkt wählen" und unter Wert "Dip_Plunge" auswählen
	- Unter X,Y Offset bearbeiten wählen und folgendes einfügen: to_string((sin(radians("D_P_Azim")) * 2 )||','||(cos(radians( "D_P_Azim" )) * -2))
	=> bestätigen und für jedes Gefügeelement wiederholen (für jeden Typ)
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Enthalten sind die Gefügeelemente:	- Klüfte (Joints)
					- Schichten_horizontal (Beds)
					- Lineare (Lineation)
					- Schieferungen_1_2
					- Überkippung
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Autor: Maurizio Gioia