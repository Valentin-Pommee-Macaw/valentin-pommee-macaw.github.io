# Klötze-Stapeln nach Mattes – Version ohne Hinweise
02.12.2024\
(Generiert mit https://dillinger.io/)\
Unser heutiges Ziel soll es sein, dass wir dynamisch Kästchen erzeugen und eine Art Tetris bauen\

## Vorbereitung
Lege eine ```index.html```Datei an. In dieser Datei fügst du den klassischen HTML-Frame ein:
```html
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Klötze-Stapeln</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
        }
    </style>
    <script>
        // Dein JavaScript kommt hierhin
    </script>
</head>
<body>
    // Dein HTML kommt hierhin
</body>
</html>
```

## 1. Eine Funktion erstellen
>Ziel: Eine Funktion erstellen und ausführen.

Schreibe eine Funktion ```sagHallo```, die einen alert mit "Hallo Welt" ausgibt.
Erweitere die Funktion so, dass ein Name als Parameter übergeben werden kann. Beispiel: ```sagHallo("Nils");``` gibt "Hallo Nils" aus.
Teste die Funktion, indem du sie im Skript aufrufst.

## 2. Einen Button hinzufügen
>Ziel: Reagiere auf Benutzerinteraktionen.

Füge im ```<body>``` einen ```<button>``` ein, der beim Anklicken ```sagHallo()``` aufruft.
Teste, ob die Funktion durch den Klick ausgeführt wird.

## 3. Ein DIV-Element erstellen
>Ziel: Dynamisch ein sichtbares Element auf der Seite erzeugen.

Schreibe eine Funktion erstelleDiv, die ein neues ```<div>``` erstellt.
Setze folgende Eigenschaften **mit Javascript**:
```css
{
position: absolute
top: 100px
left: 100px
width: 100px
height: 100px
background-color: red
}
```
Füge das DIV mit ```document.body.appendChild()``` in den DOM ein.
Teste die Funktion, indem du sie genau wie die erste Funktion aufrufst.

## 4. Ein DIV-Element verschieben
>Ziel: Manipuliere ein DOM-Element durch JavaScript.

Schreibe eine Funktion ```verschiebeDiv```, die ein vorhandenes DIV sucht (z. B. mit ```getElementById```).
Ändere seinen top-Wert auf ```200px```.
Rufe diese Funktion über einen Button-Klick auf und prüfe, ob sich das DIV bewegt.
Hinweis: Der ```top```-Wert muss als String mit "px" am Ende angegeben werden.

## 5. Animation mit einem Timeout
>Ziel: Bewege das Element automatisch.

Ändere die Funktion ```verschiebeDiv```, sodass sie den aktuellen ```top```-Wert ausliest, um 1 Pixel erhöht und wieder setzt.
Nutze ```setTimeout```, um die Funktion nach 500 ms erneut aufzurufen. Beispiel:
```javascript
window.setTimeout("verschiebeDiv()", 500);
```
Schreibe eine zusätzliche Funktion ```starteAnimation```, die ```verschiebeDiv``` einmalig startet.

## 6. Mehrere DIVs dynamisch erstellen
>Ziel: Erstelle neue Elemente bei Bedarf.

Erweitere die Funktion erstelleDiv, sodass die Position (top und left) zufällig gesetzt wird.
Nutze ```Math.random()``` und ```window.innerWidth``` oder ```window.innerHeight```, um die Position zu berechnen.
Erstelle einen weiteren Button "Neues Element", der ein neues DIV erzeugt, wenn er geklickt wird.

## 7. Elemente speichern
>Ziel: Speichere alle erzeugten DIVs in einem Array.

Initialisiere ein leeres Array ```alleElemente```.
Füge jedes neu erzeugte DIV in das Array ein, wenn ```erstelleDiv``` aufgerufen wird.
Teste, ob das Array die richtigen Elemente enthält, indem du die Länge (```alleElemente.length```) prüfst.

## 8. Alle Elemente bewegen
>Ziel: Bewege mehrere Elemente gleichzeitig.

Schreibe eine Funktion ```bewegeAlleElemente```, die alle Elemente im ```alleElemente```-Array durchgeht.
Bewege jedes Element in der Schleife um 1 Pixel nach unten (wie in Aufgabe 4).
Führe diese Methode wie in Aufgabe 5 automatisch immer wieder aus.

>Jetzt haben wir schon ziemlich viel gemacht.
>Aber wir bauen hier ja "Blöcke stapeln", und aktuell stapelt sich hier noch nichts...

# Erweiterte Aufgaben
## 9. Kollisionserkennung
>Ziel: Prüfe, ob Elemente kollidieren.

Schreibe eine Funktion ```prüfeKollision```, die zwei Elemente als Parameter nimmt.
Prüfe, ob sich die Positionen (```top```, ```left```, ```width```, ```height```) der beiden Elemente überlappen.
Teste diese Funktion, indem du Kollisionen zwischen zwei vorhandenen DIVs prüfst.

## 10. Automatisches Erstellen neuer Elemente
>Ziel: Generiere neue Elemente basierend auf Spielzuständen.

Überprüfe in ```bewegeAlleElemente```, ob ein Element den unteren Rand des Fensters erreicht hat.
Wenn ein Element am Rand ist, füge ein neues DIV hinzu.
Verhindere, dass ein Element weiter nach unten geht, sobald es den Rand erreicht hat.

# Noch mehr erweiterte Aufgaben
## 11. Punktestand
>Ziel: Einen Counter hinzufügen, der die Anzahl der DIVs auf dem Bildschirm zählt.

Erstelle im ```<body>``` ein statisches ```<div>```, das die aktuelle Anzahl der DIVs anzeigt.
Positioniere es mit ```position: absolute``` in der oberen rechten Ecke.
Schreibe eine Funktion ```updateCounter```, die die Anzahl der auf dem Bildschirm befindlichen DIVs zählt und den Inhalt des Counter-Elements mit ```innerHTML``` entsprechend aktualisiert.
Überlege, in welchen Situationen diese Funktion aufgerufen werden sollte.

## 12. Game Over
>Ziel: Ein "Game Over"-Szenario erstellen

Wenn ein Block den oberen Bildschirmrand erreicht, ist in Tetris das Spiel vorbei.
Schreibe hierzu eine Funktion ```gameOver```, die das ganze Spiel stoppt.
Überlege dir hierzu, was genau die Funktion tun muss, damit das Spiel auch wirklich final beendet wird.
Bearbeite nun die Funktion, die deine DIVs verschiebt, sodass sie erkennt, wenn das Element die obere Bildschirmkante berührt, und ```gameOver``` aufruft.