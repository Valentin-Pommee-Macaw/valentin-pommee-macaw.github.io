# Klötze-Stapeln - 15.03.2016
(Generiert mit http://dillinger.io/)
Unser heutiges Ziel soll es sein, dass wir dynamisch Kästchen erzeugen und eine Art Tetris bauen.
 
## Übung 1: Ein Alert ausgeben
>Ziel: Wir wollen eine Dialog-Box ausgeben, um erste Berührungspunkte mit JavaScript zu knüpfen.
## Vorausgesetztes Wissen
### HTML
Der Aufbau unserer HTML-Seite ist:
```html
<html>
    <head>
        <script type="text/javascript">
            ... JavaScript hier ...
        </script>
    </head>
<body>
    ... Inhalt hier ...
</body>
</html>
```
### JavaScript
JavaScript wird vom Browser ausgeführt. Es wird immer von oben nach unten ausgeführt (eine Ausnahme bildet Code in sog. Funkionen).

## Aufgabe
Erstelle ein Datei namens "index.html"
Füge den Standard-Inhalt in diese Datei ein.
Schreibe in den JavaScript Abschnitt statt "... JavaScript hier ..." folgenden Code:
```js
alert('Hallo Welt');
```
Öffne deine index.html im Browser. Evtl. erscheint eine Meldung, ob du das JavaScript ausführen möchtest. Bestätige dies.
Du solltest nun eine Dialogbox sehen.

## Übung 2: Eine Funktion erstellen
>Ziel: Wir lernen Funktionen kennen.

## Vorausgesetztes Wissen
Eine Funktion ist ein Code-Stück, welches wir bei Bedarf aufrufen können.
Außerdem lassen sich sog. Parameter übergeben, mit dem wir die Ausgabe oder den Ablauf unserer Funktion beeinflussen können.

Eine einfache Funktion sieht so aus:
```js
function SagHallo() {
 alert('Hallo Welt');
}
```
Man beachte die runden Klammern hinter dem Namen der Funktion und die geschweiften Klammern, die den eigentlichen Code umfassen.
Wenn wir einen Schritt weitergehen, ermöglichen wir die Übergabe von Parametern an die Funktion, die diese dann auswerten kann.
```js
function SagHalloMitNamen(person) {
 alert('Hallo ' + person);
}
```
Hier sehen wir, dass ein Parameter ```person``` übergeben wird. Und darüber hinaus noch eine sog. String-Verkettung mit dem Plus-Zeichen.
Wenn dieser Code ausgeführt wird, gibt er ein "Hallo" gefolgt von dem übergebenen Namen aus.

## Aufgabe
Entferne das ```alert``` der ersten Aufgabe aus deiner index.html.
Füge beide oben genannten Funktionen in den JavaScript Abschnitt ein.
Schreibe unter die Funktionen (aber immer noch im JavaScript Block) folgenden Code:
```js
SagHallo();
SagHalloMitNamen('Nils');
```
Du solltest nun zwei Dialogboxen sehen.

## Übung 3: Auf einen Klick reagieren
>Ziel: Weil es am einfachsten ist, mit einem Knopf Code zu testen, erstellen wir uns jetzt einen Button und binden einen Klick daran.

## Vorausgesetztes Wissen
Im ```<body>```-Bereich der Seite wird alles eingefügt, was als Element auf der Seite erscheinen soll.
Ein Button sähe folgendermaßen aus:
```html
<input type="button" value="Klick mich" onclick="FUNCTIONSNAME();" />
```
Der Wert von ```onclick``` wird ausgeführt, wenn man mit der Maus auf den Button drückt. Genau wie im oberen Abschnitt "Funktionen" wird dann in den Anführungszeichen die genannte Funktion aufgerufen.

## Aufgabe
Erstelle einen Button und sorge dafür, dass er "Hallo Welt" ausgibt, wenn du darauf klickst.

## Übung 4: Ein DOM-Element erstellen
(DOM = Document Object Model)
>Ziel: In dieser Übung erstellen wir ein frei-positionierbares DIV auf der Seite.

## Vorausgesetztes Wissen
Ein DIV ist ein sog. Block-Element. Es steht immer alleine in einer Zeile. Wir können es jedoch mit dem sog. Style-Attribut so verändern, dass wir es irgendwo auf der Seite positionieren können.
```html
<div id="MeinDiv" style="position:absolute; top:100px; left:100px;
width:100px; height:100px; background-color:red;"></div>
```

## Aufgabe
Erstelle das oben genannte DIV.
Spiele etwas damit herum - verschiebe es auf der Seite und ändere die Farbe, um ein Gefühl für die Abstände zu bekommen.
Probiere aus, wie weit du das DIV nach unten schieben kannst, bis es am unteren Ende anschlägt.

## Übung 5: Das DOM-Element verschieben
>Ziel: In dieser Übung wollen wir das erste Mal in Richtung Animation gehen, indem wir anfangen, das Element langsam zu verschieben.

## Vorausgesetztes Wissen - Teil 1
Um mit JavaScript ein Element zu verschieben, braucht man nur zwei Schritte
Man muss das Element auf der Seite finden.
Man muss dem Element über seine ```style```-Eigenschaft einen neuen Wert zuweisen.
```js
var mein_gefundenes_div = document.getElementById('MeinDiv');
mein_gefundenes_div.style.top = '200px';
```

## Aufgabe - Teil 1
Erstelle eine Funktion ```VerschiebeDiv```, welche dein existierendes DIV basierend auf seiner ID (```"MeinDiv"```) sucht und den ```top```-Wert auf ```"200px"``` verändert.
Rufe diese Funktion beim Klick auf den Button auf, so dass das DIV runter springt, wenn du auf den Button drückst.

## Vorausgesetztes Wissen - Teil 2
Wir wollen nun eine "richtige Animation" aus der Style-Veränderung machen. Dazu müssen wir zuerst die vorherige Position des DIVs auslesen und diesen Wert dann verändern.
```js
var mein_gefundenes_div = document.getElementById('MeinDiv');
var alter_top_wert = parseInt(mein_gefundenes_div.style.top);
mein_gefundenes_div.style.top = (alter_top_wert + 1) + 'px';
```

## Aufgabe - Teil 2
Ändere die Funktion wie oben angegeben ab.
Drücke jetzt so oft auf den Button, bis sich das Element um 100px verschoben hat.
Wie kannst du das DIV schneller machen?

## Vorausgesetztes Wissen - Teil 3
Nun sind wir zwar schon sehr nahe an einer echten Animation, aber den Button die ganze Zeit drücken zu müssen ist natürlich sehr unschön.
Darum sollten wir den Funktionsaufruf statt im Button mit einem Timeout erledigen. Ein Timeout nimmt einen Funktionsnamen als ersten Parameter an und eine Zeit in Millisekunden als zweiten Parameter:
```js
window.setTimeout("VerschiebeDiv();", 500);
```

## Aufgabe - Teil 3
Erstelle eine Funktion ```StarteTimeout``` und füge den oben genannten Code dort ein.
Statt ```VerschiebeDiv``` rufe jetzt ```StarteTimeout``` vom Button aus auf.
Du wirst feststellen, dass das Verschieben des Elements nach dem Button-Druck jetzt einfach um 500ms verzögert ist.
Um eine automatische Animation daraus zu machen, Rufe ```StarteTimeout``` am Ende der Funktion ```VerschiebeDiv``` erneut auf.
Nach einem einmaligen Klick auf den Button sollte das DIV jetzt alle 500ms verschoben werden.
Probiere das auch mit größeren Schritten in der Animation oder einem kleineren Zeitintervall.

## Übung 6: Ein DOM-Element dynamisch erzeugen
>Ziel: Gerade bei Spielen ist vorher nie abzusehen, wie viele Elemente später einmal auf der gesamten Fläche zu sehen sein werden.
Deshalb müssen wir in der Lage sein Elemente dynamisch zu erzeugen, wenn wir sie brauchen.
In dieser Übung wollen wir DIVs erstellen, ohne sie vorher in den BODY zu schreiben.

## Vorausgesetztes Wissen
Wir benötigen die Funktionen ```createElement``` und ```appendChild```.
```js
// Erstellt ein neues DIV
var neues_element = document.createElement('div');
// Setzt die Style-Werte des neuen DIVs
neues_element.style.position = 'absolute';
neues_element.style.top = '100px';
neues_element.style.left = '300px';
neues_element.style.width = '100px ';
neues_element.style.height = '100px';
// Attribute, die sonst durch Bindestrich getrennt sind, werden bei jedem Wort nach einem Strich groß geschrieben.
// background-color => backgroundColor
neues_element.style.backgroundColor = 'green';
// Fügt das neue Element in den BODY-Bereich ein und zeigt es dadurch an.
document.body.appendChild(neues_element);
```

## Aufgabe
Erstelle eine Funktion ```ErstelleElement``` und füge den oben genannten Code ein.
Erstelle einen zweiten Button auf der Seite mit der Beschriftung ```neues Element```.
Sorge dafür, dass man beim Klick auf den neuen Button ein neues Element erzeugt.

## Übung 7: Zufallszahlen
>Ziel: Um das Spiel interessant zu halten, sollte der Ablauf natürlich nicht immer gleich sein.
Darum bringen wir ein paar Zufallszahlen in das Spiel.

## Vorausgesetztes Wissen
Funktionen für die Berechnung einer Zufallsposition innerhalb des Fensters.
```js
// Diese Funktion gibt eine Zahl zwischen 0 und 1 zurück.
Math.random()
// Enthält den Wert der Breite des Fensters.
document.body.offsetWidth
// Rundet die Zahl ab.
Math.floor(zahl)
```
Aus Funktionen kann man auch einen Wert mit ```return``` zurückgeben.
```js
function ErrechneEtwas(a, b) {
 return a * b;
}
var ergebnis = ErrechneEtwas(4, 5);
// Dieses Dialogfenster sollte "20" ausgeben.
alert(ergebnis);
```

## Aufgabe
Erstelle eine Funktion ```ZufallsXImFenster```, die einen Pixel-Wert ausgibt zwischen 0 und der Breite des Fensters.
Verändere deine Funktion ```ErstelleElement``` so, dass das Element an einem zufälligen Ort erscheint.

## Übung 8: Ein Array als Gedächtnis
>Ziel: Elemente in einer Sammlung speichern.

## Vorausgesetztes Wissen
Ein "Array" ist einfach eine Liste von Dingen. In JavaScript kann man ein Array einfach über eckige Klammern erzeugen:
```js
var mein_array = [];
```
Ein Array hat eine Funktion ```push```, mit der man neue Elemente in das Array legen kann.
```js
mein_array.push(neues_element);
```
Außerdem kann man abfragen, wieviele Elemente in dem Array sind über die Eigenschaft ```length```.
```js
var anzahl_der_elemente = mein_array.length;
```
Um Code auf jedes Element eines Arrays auszuführen, kann man eine sog. ```for```-Schleife verwenden.
```js
// Diese Schleife läuft von 0 bis Elemente im Array minus eins.
for (var i = 0; i < mein_array.length; i++) {
    // Angenommen wir haben DOM-Elemente im Array, können wir sie dort direkt verändern.
    // Für jedes Element lesen wir den alten style.top Wert aus, erhöhen ihn um 1 und schreiben ihn zurück.
    mein_array[i].style.top = (parseInt(mein_array[i].style.top) + 1) + 'px';
}
```

## Aufgabe
Erstelle direkt unter dem script-Tag ein Array ```alle_elemente```.
Füge am Ende von ```ErstelleElement``` jeweils das neue Element in das Array hinzu.
Erstelle eine Funktion ```BewegeAlleElemente```.
Führe hier eine ```for```-Schleife über ```alle_elemente``` durch und bewege alle Elemente um einen px nach unten.
Rufe die ```BewegeAlleElemente``` Funktion vom Timeout aus auf, so dass sich dauerhaft alle Elemente bewegen.

## Finale Aufgabe
Wir haben jetzt alle Informationen über die Elemente und sind in der Lage neue Elemente auf Knopfdruck zu erstellen.
**Wenn du noch Zeit hast:**
Frage in der ```BewegeAlleElemente``` Methode jeweils alle anderen Elemente ab und suche mit Hilfe von ```top```, ```left```, ```width``` und ```height``` nach Kollisionen.
Wenn das Element bereits am unteren Ende angekommen ist, stoppe seine Bewegung dann.
Erstelle ein neues Element automatisch, wenn das letzte Element am unteren Ende angekommen ist.