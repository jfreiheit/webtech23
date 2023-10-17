# HTML

## Einleitung

HTML steht für <b>H</b>yper<b>T</b>ext <b>M</b>arkup <b>L</b>anguage. HTML ist eine sogenannte *Auszeichnungssprache*. Das bedeutet, dass Textelementen sogenannte *Tags* (HTML-Elemente) zugeordnet werden, um dem Text, der von einem solchen Tag umschlossen wird, eine Bedeutung zuzuweisen - der Text wird ausgezeichnet.

**Beispiel:**

``` HTML
<h1>Große Überschrift</h1>
```

Im obigen Beispiel wurde der Text Große Überschrift durch das HTML-Element `h1` ausgezeichnet. Die Bedeutung dieses Elementes ist, dass es sich bei dem ausgezeichneten Text um eine Überschrift handelt. Es gibt 6 HTML-Elemente, die Überschriften charakterisieren: `h1`, `h2`, `h3`, `h4`, `h5`, `h6`. Die Nummern geben die Größe der Überschrift an: `h1` ist die größte Überschrift, `h6` die kleinste. Klicken Sie im folgenden Fenster auf den Reiter **"Result"**, um die Unterschiede zu sehen:

<iframe width="100%" height="300" src="//jsfiddle.net/jfreiheit/fze5kd0L/2/embedded/html,css,result/" allowfullscreen="allowfullscreen" allowpaymentrequest="" frameborder="0"></iframe>


## Hierarchische Anordnung der HTML-Elemente

HTML-Elemente bestehen - bis auf wenige Ausnahmen - aus einem Start-Tag `<tag>` und einem Ende-Tag `</tag>` (tag steht hier für den Namen eines beliebigen Elementes). Wird ein neues HTML-Element `el2` innerhalb eines anderen HTML-Elementes `el1` geöffnet, so muss `el2` auch geschlossen werden, bevor `el1` geschlossen wird.  

!!! success
    ```html
    <el1> diese Anordnung der
        <el2>
              Elemente ist korrekt
        </el2>
    </el1>
    ```

!!! failure
    ```html
    <el1> diese Anordnung der
        <el2>
               Elemente ist falsch
    </el1>
       </el2>
    ```

Es gibt nur wenige HTML-Elemente, die nicht aus einem Start- und einem Ende-Tag bestehen, sondern sogenannte *stand alone Tags* sind. Ein typisches Beispiel ist der Zeilenumbruch `<br>`. Um einerseits zu symbolisieren, dass es sich um Start- und Ende-Tag in einem handelt, insbesondere aber, um [XHTML](https://de.wikipedia.org/wiki/Extensible_Hypertext_Markup_Language)-konform zu sein, geben wir für solche stand-alone Tags den Slash vor der schließenden spitzen Klammer an, d.h. wir schreiben `<br />`.

## Grundgerüst einer HTML-Seite

Prinzipiell besteht eine HTML-Seite aus einem `<head>`- und einem `<body>`-Bereich. Im `<head>`-Bereich können Metadaten über die Seite definiert werden. Der `<body>`-Bereich definiert den sichtbaren Bereich der Seite, also das, was im Browser dargestellt wird. Eingeschlossen werden der `<head>`- und der `<body>`-Bereich von einem `<html>`-Element.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Seitentitel</title>
  </head>
  <body>
    <h1>Das ist eine große Überschrift</h1>
    <p>Das ist ein Absatz.</p>
  </body>
</html>
```


Das obige Beispiel zeigt ein Grundgerüst einer HTML-Seite. `<!DOCTYPE html>` gibt dem Browser an, dass es sich um eine HTML-Datei handelt, die vom Browser **"gerendert"**, d.h. dargestellt wird.

Der `<head>`-Bereich enthält in diesem Beispiel nur ein `<title>`-Element. Dieser Titel wird im Browser im Reiter (Tab) gezeigt. Außerdem wird der Titel in der Ergebnisliste einer Suchmaschine verwendet.

Das `<body>`-Element, also der im Browser dargestellte Bereich, enthält eine Überschrift (`<h1>`) und einen Absatz (`<p>`).

!!! question "Aufgabe:"
    Erstellen Sie eine Datei ```index.html``` und fügen Sie obigen HTML-Code ein. Rufen Sie die Datei im Browser auf.


## Metadaten im Head

Das `<head>`-Element ist der Container für (Meta-)Daten über das Webdokument. Das `<head>`-Element kommt in das `<html>`-Element und vor das `<body>`-Element. Die Metadaten werden nicht dargestellt. 
Typische HTML-Elemente für Metadaten sind: 

  - `<title>` : Titel des Dokumentes (im Tab und in der Such-Ergebnisliste, 
  - `<style>` : für Format-Angaben (CSS), 
  - `<meta>` : für die Festlegung von Zeichenkodierungen, Schlüsselwörter, Autor usw., 
  - `<link>` : zum Einbinden externer CSS-Dateien, 
  - `<script>` : zum Definieren von Client-seitigen JavaScript-Funktionen, 
  - `<base>` : zum Festlegen, der URL, von der aus alle Pfadangaben relativ sind. 

=== "Beispiel Metadaten"
    ```html
     <head>
      <meta charset="UTF-8">
      <meta name="description" content="meta data">
      <meta name="keywords" content="HTML, head, title, meta, link, style">
      <meta name="author" content="Jörn Freiheit">
      <meta http-equiv="refresh" content="30">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <link rel="stylesheet" href="mystyle.css">
      <style>
        body {background-color: #29e0e6;}        
        h1 {color: #ff6a3b;}        
        ul {color: #0000ff;}
      </style>
      <script>
        function myFunction() { 
          document.getElementById("demo").innerHTML = "Hallo FIW!";        
        }
      </script>
      <base href="localhost/Webtech20" target="_blank">
      <title>Metadaten</title>
    </head>
    ```


## Block- und Inline-Elemente

Generell wird zwischen zwei Arten von HTML-Elementen unterschieden:

- Blockelemente
- Inline-Elemente

**Blockelemente** verwenden die gesamte Breite der Browseransicht (des sogenannten **Viewports**). Das bedeutet, dass ein Blockelement stets in einer neuen Zeile beginnt und neben einem Blockelement kein weiteres Element ist (sondern in einer neuen Zeile beginnt).

**Inline-Elemente** nehmen genau so viel Breite ein, wie nötig (Breite des Inhalts) und beginnen nicht in einer neuen Zeile und enden auch nicht mit einem Zeilenumbruch.

Beispiele für Inline- und Blockelemente (Reiter "Result" wählen, um Ergebnis zu sehen):

<iframe width="100%" height="300" src="//jsfiddle.net/jfreiheit/fze5kd0L/4/embedded/html,css,result/" allowfullscreen="allowfullscreen" allowpaymentrequest="" frameborder="0"></iframe>

Eine Übersicht über alle HTML-Elemente mit Erläuterungen findet sich [**hier**](https://developer.mozilla.org/de/docs/Web/HTML/Element).

!!! question "kleine Übungsaufgabe:"
    Erweitern Sie Ihre Datei ```index.html``` und fügen Sie mindestens folgende Elemente ein:

    - 2 verschiedene Überschriften (`h1`, ..., `h6`)
    - eine nummerierte Liste (ordered list - `ol`) mit 3 Einträgen (list items - `li`)
    - eine Strichpunktliste (unordered list - `ul`) mit 3 Einträgen (`li`)
    - eine Tabelle (`table`); diese besteht aus einem Tabellenkopf (table head - `thead`) und einem Tabellenkörper (table body - `tbody`)
      - der thead enthält eine Zeile (table row - `tr`) als Tabellenüberschrift, wobei jede einzelne Überschrift (eine Spalte) als `th` definiert wird
      - der tbody enthält mehrere Zeilen (`tr`); jede Zeile enthält so viele Dateneinträge (table data - `td`) wie es Spalten gibt
    - einen Hyperlink (anchor - `a`), der ein Verweis auf die HTW-Seite enthält
    - ein Bild (image - `img`)

    Rufen Sie die Datei im Browser auf.

## Einige ausgewählte Elemente

#### Hyperlinks (Anchorelement)

Das HTML-Element für Hyperlinks ist ``<a>``. Ein Beispiel für die Anwendung dieses Elementes ist

```html
<a href="http://www.htw-berlin.de" target="_blank">HTW Berlin</a>
```

Das Beispiel erstellt einen Hyperlink. Auf der Webseite sichtbar ist der Inhalt des Elementes, nämlich ``HTW Berlin``. Wird auf den Link geklickt, so öffnet sich die Webseite der HTW (``www.htw-berlin.de``) in einem neuen Browser-Reiter (``target="_blank"``).

Weitere Beispiele:

```html
<a href="https://fiw.htw-berlin.de/fileadmin/HTW/Zentral/Rechtsstelle/Amtliche_Mitteilungsblaetter/2014/17_14.pdf">Studienordnung FIW</a>
<a href="mailto:freiheit@htw-berlin.de">E-Mail an Jörn Freiheit</a>
```

Das Anchorelement ist ein Inline-Element.

#### Bilder (Image)

Das HTML-Element für Bilder ist ``<img>``. Ein Beispiel für die Anwendung dieses Elementes ist

```html
<img src="../Logos/fiw.jpg" alt="FIW-Logo"/>
```

Das Beispiel zeigt das FIW-Logo auf der Webseite an. Es ist in der Datei ``fiw.jpg`` gespeichert, welche im Ordner ``Logos`` liegt. Der Ordner ``Logos`` befindet sich auf der gleichen Ordnerebene wie der Ordner, der die HTML-Datei enthält. Diesen Ordner muss man deshalb zunächst mithilfe von ``..`` verlassen. Das Attribut ``alt`` wird verwendet, um einen alternatioven Text anzugeben, der angezeigt wird, falls das Bild nicht geladen werden kann. Wichtig ist das ``alt``-Attribut aber insbesondere für die Barrierefreiheit. Ein Screenreader liest diesen Alternativtext vor. Sollte es sich bei dem Bild nur um ein dekoratives Element handeln (also nicht wirklich einen sinnvollen Inhalt haben), sollte man aus Gründen der Barrierfreiheit dafür ``alt=""`` angeben, dann überspringt der Screenreader dieses Bild. 

Es sei erwähnt, dass es auch sowohl das ``height``- als auch das ``width``-Attribut für ``<img>`` gibt, um die Höhe bzw. die Breite des Bildes zu setzen. Dies sollte aber besser CSS überlassen werden. 

Beachten Sie auch, dass es sich bei dem ``<img>``-Element um ein *stand alone Element* handelt. Wir beenden das Element deshalb mit ``/>``, um XML-konform zu sein. Das ``<img>``-Element ist ein Inline-Element.

#### Tabellen

Tabellen (``<table>``) bestehen aus einen Tabellenkopf (``<thead>``) und einem Tabellenkörper (``<tbody>``). Der Tabellenkopf enthält eine Tabellenzeile (``<tr>``) mit beliebig vielen Einträgen, den jeweiligen Spaltenüberschriften (``<th>``). Der Tabellenkörper enthält beliebig viele Zeilen (``<tr>``), die in jeder Spalten Dateneinträge (``<td>``) enthalten. Ein Beispiel für eine Tabelle:

```html
<table>
    <thead>
        <tr>
            <th>Spalte 1</th>
            <th>Spalte 2</th>
            <th>Spalte 3</th>
        </tr>
    </thead>
    <tbody>
    <tr>
        <td>1_1</td>
        <td>1_2</td>
        <td>1_3</td>
    </tr>
    <tr>
        <td>2_1</td>
        <td>2_2</td>
        <td>2_3</td>
    </tr>
    <tr>
        <td>3_1</td>
        <td>3_2</td>
        <td>3_3</td>
    </tr>
    </tbody>
</table>
```

Das Formatieren der Tabellen (Rahmen, rechtsbündig usw.) sollte stets CSS überlassen werden.

#### Listen

Es gibt nummerierte Listen (*ordered list* ``<ol>``) und nicht-nummerierte Listen (*unordered list* ``<ul>``). Die Einträge in einer Liste sind die *list items* ``<li>``. Listen können auch ineinander verschachtelt werden. Dabei ist nur zu beachten, dass Listen immer nur *list items* enthalten sollen und die list items dann selbst wieder eine neue Liste enthalten können.

=== "ordered list"
    ```html
    <ol>
      <li>eins</li>
      <li>zwei</li>
      <li>drei</li>
    </ol>
    ```
=== "unordered list"
    ```html
    <ul>
      <li>eins</li>
      <li>zwei</li>
      <li>drei</li>
    </ul>
    ```
=== "verschachtelte Liste"
    ```html
    <ol>
      <li>
          <ol>
              <li>eins_eins</li>
              <li>eins_zwei</li>
              <li>eins_drei</li>
          </ol>
      </li>
      <li>zwei</li>
      <li>
          <ul>
              <li>drei_eins</li>
              <li>drei_zwei</li>
              <li>drei_drei</li>
          </ul>
      </li>
    </ol>
    ```

#### Container-Elemente

Einige Elemente dienen nur der besseren Strukturierung des HTML-Codes und der besseren "Ansprechbarkeit" im CSS (d.h. für diese Elemente können dann eigene CSS-Eigenschaften zugewisen werden). Vor HTML 5 wurde dafür das Element ``<div>`` verwendet. Es existiert noch immer. Mit HTML 5 wurden aber weitere Container-Elemente hinzugefügt:

  * `<main>` - für den Hauptinhalt, sollte genau einmal im Dokument vorkommen
  * `<section>` - für größere Abschnitte (Teile); kann z.B. article enthalten
  * `<article>` - für Abschnitte (z.B. Blog-Einträge) in main 
  * `<aside>` - für z.B. News an der Seite
  * `<footer>` - für die Fußzeile (mit Impressum, Copyright, usw.)
  * `<header>` - für die Kopfzeile (mit Logo, Navigation usw.)
  * `<nav>` - für das Navigationsmenü

Container-Elemente sind nicht "sichtbar", jedoch Block-Elemente. Es ist empfehlenswert, die eigene Webseite mit solchen Container-Elementen zu strukturieren, um erstens einen besseren Überblick über die Seite zu bewahren und insbesondere gezielter die Formatierungseigenschaften von CSS verwenden zu können. Dies schließt das Layout ein. Die folgende Abbildung zeigt, wofür solche Container-Elemente gedacht sind.

![layout](./files/208_layout.gif)

Die Elemente ordnen sich aber z.B. nicht von alleine nebeneinander an. Dafür verwenden wir später CSS. Mithilfe von Container strukturieren wir jedoch den HTML-Code (vergleichbar mit `JPanel` in Java). Beispiel (aus [W3School](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_layout_float)):

```html
<!DOCTYPE html>
<html lang="en">
<head>
<title>CSS Template</title>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
</head>
<body>

<h2>CSS Layout Float</h2>
<p>In this example, we have created a header, two columns/boxes and a footer. On smaller screens, the columns will stack on top of each other.</p>
<p>Resize the browser window to see the responsive effect (you will learn more about this in our next chapter - HTML Responsive.)</p>

<header>
  <h2>Cities</h2>
</header>

<section>
  <nav>
    <ul>
      <li><a href="#">London</a></li>
      <li><a href="#">Paris</a></li>
      <li><a href="#">Tokyo</a></li>
    </ul>
  </nav>
  
  <article>
    <h1>London</h1>
    <p>London is the capital city of England. It is the most populous city in the  United Kingdom, with a metropolitan area of over 13 million inhabitants.</p>
    <p>Standing on the River Thames, London has been a major settlement for two millennia, its history going back to its founding by the Romans, who named it Londinium.</p>
  </article>
</section>

<footer>
  <p>Footer</p>
</footer>

</body>
</html>
```

In dem Beispiel dienen die Container nur der Strukturierung. Alles, was in den *Header* gehört, ist im `<header>`-Element (nicht zu verwechseln mit `<head>`!) und alles, was zum *Footer* gehört, kommt in das `<footer>`-Element. Der Hauptteil ist im `<section>`-Element, welches noch in `<nav>` und `<article>` unterteilt ist. 
 


#### Eingabe- bzw. Steuerelemente 

Es gibt viele Steuerelemente in HTML und die Auswahl wird kontinuierlich größer. Steuerelemente werden mit dem HTML-Element `<input>` definiert. Der Typ des Steuerelementes wird mit Attribut `type` definiert. Beispiele:

```html
<input type="button" value="Click" />
<input type="reset" />
<input type="submit" />
<input type="checkbox" />
<input type="color" />
<input type="date" />
<input type="file" />
<input type="number" />
<input type="radio" />
<input type="image" src="../Logos/fiw.jpg" width="40" alt="FIW-Logo"/>
<input type="range" min="10" max="100"/>
<input type="text" placeholder="Name"/>
<input type="email" placeholder="E-Mail"/>
<input type="password" />
```

Probieren Sie am besten diese Beispiele aus und schauen Sie sich die Darstellung an. Beachten Sie auch, dass die Elemente in den unterschiedlichen Browsern unterschiedlich dargestellt werden.

## Attribute

Wir haben in den obigen Beispielen bereits Attribute gesehen. In ``<a>`` wurden z.B. die Attribute ``href`` und ``target`` verwendet und in ``<img>`` die Attribute ``src`` und ``alt``. Attribute werden innerhalb der spitzen Klammern des Begin-Tags angegeben und haben die Form:

```
attribut = "wert"
```

Das heißt, auf der linken Seite steht das Attribut und auf der rechten Seite der Wert des Attributs in doppelten Hochkommata. Es gibt Attribute, die ohne Wert verwendet werden können, z.B. ``checked`` für ein Eingabeelement ``<input>``, z.B.

```html
<input type="checkbox" name="SG" value="FIW" checked /> FIW<br>
```

Um XML-konform zu sein, sollte man eigentlich besser `<input type="checkbox" name="SG" value="FIW" checked="checked" />` verwenden, macht aber niemand. Das Attribut `checked`ist ein Beispiel für ein Attribut, das speziell für ein HTML-Element zur Verfügung steht (hier für `<input>`). Die meisten Attribute existieren speziell für HTML-Elemente. 

Darüber hinaus gibt es noch sogenannte *globale* Attribute, die für alle HTML-Elemente verwendet werden können. Beispiele solcher Attribute sind 

| globales Attribut | Erläuterung |
|-------------------|-------------|
| `id`              | weist dem Element eine id zu; eine id sollte innerhalb eines HTML-Dokumentes eindeutig sein |
| `class`           | weist dem Element eine oder mehrere Klassen zu, deren Eigenschaften in CSS definiert werden können |
| `hidden`          | setzt das Element auf unsichtbar, es wird nicht angezeigt | 
| `title`           | weist einem Element textuelle Informationen zu, die bei längerem Mouseover angezeigt werden (tooltip) |

## Besondere Zeichen

Für einige Sonderzeichen gibt es vordefinierte Entitäten. Die folgende Tabelle zeigt ein paar Sonderzeichen. Sie können Sie beispielsweise per ```<span>&euro;</span>``` ergibt <code><span>&euro;</span></code> aufrufen. Es beginnt also immer mit einem `&` und endet mit einem `;`.

<table>
    <thead>
        <tr>
            <th>Entität</th>
            <th>Zeichen</th>
        </tr>
    </thead>
    <tbody>
    <tr>
        <td>&amp;euro;</td>
        <td>&euro;</td>
    </tr>
    <tr>
        <td>&amp;amp;</td>
        <td>&amp;</td>
    </tr>
    <tr>
        <td>&amp;lt;</td>
        <td>&lt;</td>
    </tr>
        <tr>
        <td>&amp;gt;</td>
        <td>&gt;</td>
    </tr>
    <tr>
        <td>&amp;quot;</td>
        <td>&quot;</td>
    </tr>
    <tr>
        <td>&amp;forall;</td>
        <td>&forall;</td>
    </tr>
    <tr>
        <td>&amp;exist;</td>
        <td>&exist;</td>
    </tr>
    <tr>
        <td>&amp;empty;</td>
        <td>&empty;</td>
    </tr>
    <tr>
        <td>&amp;isin;</td>
        <td>&isin;</td>
    </tr>
    <tr>
        <td>&amp;notin;</td>
        <td>&notin;</td>
    </tr>
    <tr>
        <td>&amp;ni;</td>
        <td>&ni;</td>
    </tr>
    <tr>
        <td>&amp;prod;</td>
        <td>&prod;</td>
    </tr>
    <tr>
        <td>&amp;sum;</td>
        <td>&sum;</td>
    </tr>
    </tr>
        <tr>
        <td>&amp;copy;</td>
        <td>&copy;</td>
    </tr>
    <tr>
        <td>&amp;reg;</td>
        <td>&reg;</td>
    </tr>
    <tr>
        <td>&amp;trade;</td>
        <td>&trade;</td>
    </tr>
    <tr>
        <td>&amp;larr;</td>
        <td>&larr;</td>
    </tr>
    <tr>
        <td>&amp;uarr;</td>
        <td>&uarr;</td>
    </tr>
    <tr>
        <td>&amp;rarr;</td>
        <td>&rarr;</td>
    </tr>
    <tr>
        <td>&amp;darr;</td>
        <td>&darr;</td>
    </tr>
    <tr>
        <td>&amp;harr;</td>
        <td>&harr;</td>
    </tr>
    <tr>
        <td>&amp;crarr;</td>
        <td>&crarr;</td>
    </tr>
    <tr>
        <td>&amp;spades;</td>
        <td>&spades;</td>
    </tr>
    <tr>
        <td>&amp;clubs;</td>
        <td>&clubs;</td>
    </tr>
    <tr>
        <td>&amp;hearts;</td>
        <td>&hearts;</td>
    </tr>
        <tr>
        <td>&amp;diams;</td>
        <td>&diams;</td>
    </tr>
    </tbody>
</table>

!!! question "Übung"
    Erstellen Sie die obige Tabelle in HTML (die ersten paar Zeilen genügen). Die Herausforderung besteht darin, einerseits den Code darzustellen und andererseits das Zeichen. 

In der UTF-8-Tabelle sind nicht nur Sonderzeichen enthalten, sondern auch Emojis. Diese werden über den Hexadezimalcode eingebunden, z.B. ```&#x1F600;``` ergibt &#x1F600;. Das Vorgehen ist das Folgende: Sie schauen z.B. [hier](https://unicode.org/emoji/charts/full-emoji-list.html) nach und suchen sich das passende Emoji in der Spalte `Browser`. Von dem links daneben stehenden Unicode (z.B. `U+1F600`) benötigen Sie nur den Hexadezimalwert (`1F600`). Diesen fügen Sie nach <code>&amp;#x</code> ein und hängen ein `;` an. Also bspw. ```&#x1F44D;``` ergibt &#x1F44D;.


## Relative Pfade

Wenn Sie z.B. Bilder in den HTML-Code einbinden oder Hyperlinks auf andere HTML-Dokumente angeben, dann müssen Sie angeben, wo diese jeweilige Ressource verfügbar ist. Beispiel:

```html
<img src="fiw.jpg" alt="FIW-Logo" />
<a href="index.html">Home</a>
``` 

Beachten Sie, dass sowohl in dem `src`-Attribut als auch in dem `href`-Attribut Pfade zur Ressource angegeben werden. Das heißt, dass z.B. `fiw.jpg` entspricht `./fiw.jpg` bzw. `index.html` entspricht `./index.html`. Das wiederum bedeutet, dass beide Ressourcen in demselben Ordner leigen müssen, in dem auch das aufrufende Dokument liegt. Das ist natürlich nur (sehr) selten der Fall.

Angenommen, wir haben eine Verzeichnisstruktur wie in der folgenden Abbildung gezeigt:

![pfade](./files/209_pfade.png){ width="400" }

- Angenommen, wir wollen aus der `index.html` heraus auf die `uebung1.html` verlinken, dann ist der Pfad `Uebung1/uebung1.html`, denn der Ordner `Uebung1` befindet sich direkt neben der `index.html`. 
- Angenommen, wir wollen aus der `uebung1.html` heraus auf die `uebung2.html` verlinken, dann ist der Pfad `../Uebung2/uebung2.html`, denn der Ordner `Uebung2` befindet sich direkt neben dem Ordner `Uebung1` (aus dem wir zunächst heraus müssen) und darin die `uebung2.html`. 
- Angenommen, wir wollen in der `uebung3.html` das Bild `fiw.jpg` einbinden, dann ist der Pfad `../Uebung1/images/fiw.jpg`, denn der Ordner `Uebung1` befindet sich direkt neben dem Ordner `Uebung3` (aus dem wir zunächst heraus müssen) und darin der Ordner `images` und darin das `fiw.jpg`. 

Geben Sie innerhalb Ihrer Webanwendung alle Pfade stets relativ und nie absolut an! Solche Pfade, wie z.B. `C:\Documents\xampp\htdocs\WT\Uebung1\uebung1.html` dürfen keinesfalls verwendet werden, denn sobald Sie Ihre Anwendung auf einen anderen Server überführen, würden solche absoluten Pfade nicht mehr stimmen.


## Clean Code HTML

Es ist noch nicht so lange her, da gab es zwei unterschiedliche Strömungen in der Weiterentwicklung von HTML: einerseits sollte HTML als Standard weiterentwickelt werden und andererseits gab es Bestrebungen, HTML dichter an XML zu koppeln. So entstand zunächst XHTML. Zum Glück wurden diese beiden Entwicklungen jedoch wieder zusammengeführt. Übrig blieben *Konventionen*, die eingehalten werden sollten, damit HTML auch XHTML-konform ist. Wir wollen diese Konventionen unbedingt beachten:

- alle HTML-Dokumente beginnen mit `<!DOCTYPE html>`
- die Elemente `<html>`, `<head>`, `<title>` und `<body>` sind Pflicht, 
- alle Elemente müssen korrekt verschachtelt sein (also innere Elemente erst schließen bevor das äußere Element geschlossen wird),
- alle Elemente müssen geschlossen werden (*Stand-alone-Elemente* sollten dann z.B. so geschrieben werden: `<br/>`),
- alle Elementnamen sollen vollständig kleingeschrieben werden,
- jedes Attribut sollte einen Wert haben und die Werte sollten in Anführungsstrichen stehen.

!!! question "Übung"
    Was ist hier jeweils falsch?

    - `<b><i>Some text</b></i>`
    - `<p>This is a paragraph
        <p>This is another paragraph`
    - `A break: <br>
        A horizontal rule: <hr>
        An image: <img src="happy.gif" alt="Happy face">`
    - `<P>This is a paragraph</P>`
    - `<input type="checkbox" name="vehicle" value="car" checked />
        <input type="text" name="lastname" disabled />`

Sie können Ihre HTML-Seite validieren lassen. Dazu gibt es Online-Validatoren, z.B. [hier](https://validator.w3.org/nu/?doc=https%3A%2F%2Fwww.w3schools.com%2Fhtml%2Fhtml_validate.html). 

## Weitere Informationen über HTML

- [Folien HTML](./files/01_WT_HTML.pdf)
- um das untenstehende Beispiel auszuführen, benötigen Sie die Datei [**fiw.jpg**](./files/fiw.jpg), die Sie in einem `Logos`-Ordner ablegen sollten, um wenig Änderungsaufwand bei der folgenden HTML-Datei zu haben

=== "alle Beispiele in einem"
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML Einführung</title>
</head>
<body>
<h3>Hyperlinks</h3>
<a href="http://www.htw-berlin.de" target="_blank">HTW Berlin</a>
<a href="https://fiw.htw-berlin.de/fileadmin/HTW/Zentral/Rechtsstelle/Amtliche_Mitteilungsblaetter/2014/17_14.pdf">Studienordnung FIW</a>
<a href="mailto:freiheit@htw-berlin.de">E-Mail an Jörn Freiheit</a>

<h3>Bilder</h3>
<img src="../Logos/fiw.jpg" alt="FIW-Logo"/>

<h3>Tabelle</h3>
<table>
    <thead>
        <tr>
            <th>Spalte 1</th>
            <th>Spalte 2</th>
            <th>Spalte 3</th>
        </tr>
    </thead>
    <tbody>
    <tr>
        <td>1_1</td>
        <td>1_2</td>
        <td>1_3</td>
    </tr>
    <tr>
        <td>2_1</td>
        <td>2_2</td>
        <td>2_3</td>
    </tr>
    <tr>
        <td>3_1</td>
        <td>3_2</td>
        <td>3_3</td>
    </tr>
    </tbody>
</table>

<h3>Listen</h3>
<ol>
    <li>eins</li>
    <li>zwei</li>
    <li>drei</li>
</ol>

<ul>
    <li>eins</li>
    <li>zwei</li>
    <li>drei</li>
</ul>

<ol>
    <li>
        <ol>
            <li>eins_eins</li>
            <li>eins_zwei</li>
            <li>eins_drei</li>
        </ol>
    </li>
    <li>zwei</li>
    <li>
        <ul>
            <li>drei_eins</li>
            <li>drei_zwei</li>
            <li>drei_drei</li>
        </ul>
    </li>
</ol>

<h3>Eingabeelemente</h3>
<input type="checkbox" name="SG" value="AI"/> AI<br>
<input type="checkbox" name="SG" value="FIW" checked/> FIW<br>

<input type="button" value="Click" />
<input type="reset" />
<input type="submit" />
<input type="checkbox" />
<input type="color" />
<input type="date" />
<input type="file" />
<input type="number" />
<input type="radio" />
<input type="image" src="../Logos/fiw.jpg" width="40" alt="FIW-Logo"/>
<input type="range" min="10" max="100"/>
<input type="text" placeholder="Name"/>
<input type="email" placeholder="E-Mail"/>
<input type="password" />


</body>
</html>
```

---


## HTTP (Vertiefung)

HTTP steht für Hypertext Transfer Protocol. Es wurde von [**Tim Berners Lee**](https://de.wikipedia.org/wiki/Tim_Berners-Lee) zusammen mit HTML, dem [**ersten Webserver**](https://de.wikipedia.org/wiki/CERN_httpd) und dem [**ersten Browser**](https://de.wikipedia.org/wiki/WorldWideWeb) Anfang der 1990er Jahre am CERN entwickelt. Die Idee von HTTP ist einfach: der Nutzer stellt unter Eingabe einer URL (die Adresse des Webservers) eine Anfrage (*request*) an den Webserver. Der Webserver antwortet darauf mit einer *response*. Diese enthält einige Metadaten und die angefragte Webseite (im HTML-Format), wenn die Anfrage ordnungsgemäß beantwortet werden kann. 

### HTTP-Anfragemethoden

Für die Anfrage des Browsers an den Webserver stellt HTTP verschiedene Anfragemethoden zur Verfügung. Diese unterscheiden sich in ihrer Bedeutung dahingehend, was mit der angefragten Ressource (den Daten oder der Webseite) geschehen soll. 

<table>
  <thead>
    <tr>
      <th> Anfragemethode </th> 
      <th> Erläuterung </th>
    </tr>
  </thead>
  <tbody>
<tr>
  <td> <code>GET</code> </td> 
  <td> ist die einfachste und meistverwendete Anfragemethode; dient dazu, eine Ressource (typischerweise eine HTML-Datei) vom Webserver anzufordern; z.B. `GET /index.html` fordert die `index.html` vom Webserver an. </td>
</tr>
<tr>
  <td> <code>POST</code>    </td>      
  <td> fordert ebenfalls eine Ressource vom Webserver an; der Unterschied zwischen <code>GET</code> und <code>POST</code> besteht beim Mitsenden von Daten, z.B. Suchanfragen oder Login-Daten. Während beim <code>GET</code> die übermittelten Daten in die URL geschrieben werden, werden diese bei einem <code>POST</code> in den HTTP-Header eingefügt. Das heißt, dass beim `GET` die an den Webserver übergebenen Daten sichtbar sind, beim <code>POST</code> nicht. Für die Übertragung sensibler Daten sollte also <code>POST</code> verwendet werden. </td> 
</tr>
<tr>
  <td> <code>HEAD</code>  </td>       
  <td> fragt nur den Response-Header ab, nicht die Daten selbst. So kann z.B. bei einem Download zunächst die Größe der Datei abgefragt werden, bevor man die Datei selbst (mit <code>GET</code> oder <code>POST</code>) herunterlädt. </td> 
</tr> 
  </tbody>
</table>

Neben diesen "HTTP-Standardmethoden" gibt es noch spezielle Anfragemethoden, die beim einfachen Surfen keine Rolle spielen, für uns in der Webprogrammierung jedoch von Bedeutung sind. Wir werden diese im Zusammenhang mit dem Programmierparadigma `REST` (*Representational State Transfer*) verwenden. Sie unterscheiden sich dahingehend, wie mit den angeforderten Ressourcen umgegangen wird, also ob sie unverändert bleiben, angelegt oder geändert werden.

<table>
  <thead>
    <tr>
      <th> Anfragemethode </th> 
      <th> Erläuterung </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td> <code>GET</code> </td> 
      <td> lässt die angefragte Ressource unverändert und ruft sie nur ab  </td>
    </tr>
    <tr>                                                                                          
      <td> <code>POST</code>   </td>       
      <td> erstellt eine neue Ressource oder verändert sie; wir werden <code>POST</code> zum Erstellen verwenden    </td>  
    </tr>
    <tr>
      <td> <code>PUT</code>   </td>        
      <td> sehr ähnlich zu <code>POST</code>, aber <code>POST</code> ist ein wenig genereller. Wird mit <code>PUT</code> eine neue Ressource angelegt, so wird der Name in der URL angegeben, während bei <code>POST</code> der Name durch den Server vergeben kann; wir werden <code>PUT</code> zum Ändern verwenden </td> 
    </tr>
    <tr>
      <td> <code>DELETE</code>  </td>
      <td> löscht die angegebene Ressource vom Server   </td> 
    </tr> 
  </tbody>
</table>


Wichtig ist zu beachten, dass HTTP ein **zustandsloses Protokoll** ist. Das bedeutet, dass die Anfragen prinzipiell unabhängig voneinander sind und dass es keine Anfragehostorie gibt. Wird soetwas benötigt, wie z.B. beim Online-Einkauf, dann muss dies über andere Mechanismen (z.B. Anmelden/Registrieren) realisiert werden. 

### HTTP-Statusmeldungen

HTTP sieht verschiedene Meldungen des Servers an den Client vor. Diese werden im Response-Header versendet. Hier ein paar Beispiele:

<table>
  <thead>
    <tr>
      <th> HTTP Statusmeldung </th> 
      <th> Erläuterung </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td> <code>200 OK</code> </td>  
      <td> Request wurde vollständig und erfolgreich bearbeitet </td> 
    </tr>
    <tr>
      <td> <code>201 Created</code> </td> 
      <td> Request wurde bearbeitet und die neue Ressource wurde erstellt </td> 
    </tr>
    <tr>
      <td> <code>301 Moved Permanently</code> </td> 
      <td> die angeforderte Ressource wurde an eine andere URL bewegt </td> 
    </tr>
    <tr>
      <td> <code>400 Bad Request</code> </td> 
      <td> Der Request kann nicht bearbeitet werden, da er (syntaktische) Fehler enthält. </td> 
    </tr>
    <tr>
      <td> <code>401 Unauthorized</code> </td>  
      <td> Request ist ok, aber der Zugriff auf die Ressource ist nicht autorisiert </td> 
    </tr>
    <tr>
      <td> <code>404 Not Found</code> </td>  
      <td> die angegebene Ressource existiert nicht </td> 
    </tr>
    <tr>
      <td> <code>500 Internal Server Error</code> </td>  
      <td> der Webserver ist down bzw. hat einen Fehler </td> 
    </tr> 
  </tbody>
</table>

### URLs

URL steht für *Uniform Resource Locator* und ist eine Adresse, die auf eine Ressource auf einem Server zeigt sowie das Protokoll, mit dem auf diese Adresse zugegriffen wird. Der allgemeine Aufbau einer URL sieht so aus: 

```
<schema>:<ressourcen-adresse>
```

`<schema>` können verschiedene Protokolle sein, z.B. `http`, `https`, `ftp`, `mailto`, `news`, `file` usw. Für die Zugriffe auf Webservern wierden  `http` bzw. `https` verwendet. 

Die `<ressourcen-adresse>` kann unterschiedlich komplex sein. Der allgemeine Fall für den Zugriff auf eine Ressource auf einem Webserver kann so aussehen:

```
//user:password@www.example.org:80/index.html?key1=value1&key2=value2
```

Darin möchte ein Nutzer `user` mit dem Passwort `password` auf den Server (host) `www.example.org` über den Port `80` auf die Ressource `index.html` zugreifen (mit GET) und übergibt dabei 2 Werte, nämlich `value1` für den Schlüssel (die Variable) `key1` und `value2` für den Schlüssel `key2`. In den meisten Fällen wird weder `user` noch `password` angegeben, oft auch nicht der Port und viele Anfragen auch ohne angehängte Schlüssel-Werte-Paare.

Die URL darf bestimmte Zeichen nicht enthalten, z.B. Leerzeichen, Klammern usw. Diese werden *maskiert*, d.h. in sogenante Prozentdarstellung umgewandelt. Ein Leerzeichen wird in `%20` umgewandelt, ein Punkt in `%2E` usw. Daraus ergeben sich manchmal etwas "kryptische" URLs (siehe z.B. [**https://www.w3schools.com/tags/ref_urlencode.ASP** ]( https://www.w3schools.com/tags/ref_urlencode.ASP )).

### Domain Name Service (DNS)

Prinzipiell sind die Rechner im Internet durch IP-Adressen adressiert. `IPv4`-Adressen bestehen aus vier Zahlenblöcken (jeweils im Bereich von 0 bis 255), die durch einen Punkt getrennt sind. `IPv4`-Adressen werden in 32 Bit gespeichert. Es gibt somit theoretisch 2^32 = 4.294.967.296 verschiedene Adressen, d.h. gut 4 Mrd adressierbare Rechner im Internet. Da dies nicht ausreicht, wurde in Version 6 des IP-Protokolls eine neue Dressierbarkeit eingeführt, in dem nun 128 Bit für die Speicherung einer Adresse zur Verfügung stehen. Eine `IPv6`-Adresse besteht aus acht Blöcken, welche durch Doppelpunkte getrennt sind. Jeder Block besteht aus 4 Hexadezimalstellen. 

Damit man sich zum Surfen im World Wide Web nicht IP-Adressen merken muss, wurden Webservern Namen zugeordnet. Somit muss man nicht die IP-Adressen in das Adressfeld als URL eingeben, sondern kann sprechende Namen verwenden, wie z.B. `htw-berlin.de`. `de`ist dabei eine sogenannte Top-Level-Domain und `htw-berlin`eine Subdomain. Den DNS kann man sich wie ein Telefonbuch vorstellen, in dem für eine sprechende Adresse die zueghörige IP-Adresse steht. Die Anfrage wird dann per TCP/IP an die IP-Adresse geschickt. 

Abfrage nach dem Root-DNS-Server für die Domain `htw-berlin.de`:

```bash
% dig htw-berlin.de @a.root-servers.net

; <<>> DiG 9.10.6 <<>> htw-berlin.de @a.root-servers.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38694
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 6, ADDITIONAL: 13
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;htw-berlin.de.     IN  A

;; AUTHORITY SECTION:
de.     172800  IN  NS  s.de.net.
de.     172800  IN  NS  n.de.net.
de.     172800  IN  NS  a.nic.de.
de.     172800  IN  NS  f.nic.de.
de.     172800  IN  NS  l.de.net.
de.     172800  IN  NS  z.nic.de.

;; ADDITIONAL SECTION:
s.de.net.   172800  IN  A 195.243.137.26
s.de.net.   172800  IN  AAAA  2003:8:14::53
n.de.net.   172800  IN  A 194.146.107.6
n.de.net.   172800  IN  AAAA  2001:67c:1011:1::53
a.nic.de.   172800  IN  A 194.0.0.53
a.nic.de.   172800  IN  AAAA  2001:678:2::53
f.nic.de.   172800  IN  A 81.91.164.5
f.nic.de.   172800  IN  AAAA  2a02:568:0:2::53
l.de.net.   172800  IN  A 77.67.63.105
l.de.net.   172800  IN  AAAA  2001:668:1f:11::105
z.nic.de.   172800  IN  A 194.246.96.1
z.nic.de.   172800  IN  AAAA  2a02:568:fe02::de

;; Query time: 140 msec
;; SERVER: 198.41.0.4#53(198.41.0.4)
;; WHEN: Tue Sep 29 08:44:58 CEST 2020
;; MSG SIZE  rcvd: 412

``` 

Die Domain `htw-berlin.de` wird von mehreren DNS verwaltet: `s.de.net`, `n.de.net`, `a.nic.de`, ... (siehe AUTHORITY SECTION). Beispielsweise leitet der Root-DNS-Server `a.nic.de` die Auflösung der Domain an die beiden DNS `infobloxv.htw-berlin.de` (IP-Adresse `141.45.65.100`) und `dns-2.dfn.de` weiter:

```bash
% dig htw-berlin.de @a.nic.de

; <<>> DiG 9.10.6 <<>> htw-berlin.de @a.nic.de
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1455
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 2, ADDITIONAL: 2
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;htw-berlin.de.     IN  A

;; AUTHORITY SECTION:
htw-berlin.de.    86400 IN  NS  infobloxv.htw-berlin.de.
htw-berlin.de.    86400 IN  NS  dns-2.dfn.de.

;; ADDITIONAL SECTION:
infobloxv.htw-berlin.de. 86400  IN  A 141.45.65.100

;; Query time: 2 msec
;; SERVER: 194.0.0.53#53(194.0.0.53)
;; WHEN: Tue Sep 29 08:45:47 CEST 2020
;; MSG SIZE  rcvd: 106

```

Die aktuelle IP-Adresse des Servers `htw-berlin.de` ist `141.45.66.214`:

```bash
% dig htw-berlin.de @dns-2.dfn.de

; <<>> DiG 9.10.6 <<>> htw-berlin.de @dns-2.dfn.de
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 21529
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
;; WARNING: recursion requested but not available

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;htw-berlin.de.     IN  A

;; ANSWER SECTION:
htw-berlin.de.    28800 IN  A 141.45.66.214

;; Query time: 11 msec
;; SERVER: 193.174.75.54#53(193.174.75.54)
;; WHEN: Tue Sep 29 08:46:53 CEST 2020
;; MSG SIZE  rcvd: 58


```

Die IP-Adresse der Domain (und die verantwortlichen DNS) hätte man auch mit `nslookup` herausbekommen:

```bash
% nslookup -q=any htw-berlin.de

Server:   141.45.2.100
Address:  141.45.2.100#53

htw-berlin.de
  origin = infoblox1.htw-berlin.de
  mail addr = net-rz.htw-berlin.de
  serial = 2009121336
  refresh = 10800
  retry = 3600
  expire = 2419200
  minimum = 900
Name: htw-berlin.de
Address: 141.45.66.214
htw-berlin.de mail exchanger = 50 mail1.rz.htw-berlin.de.
htw-berlin.de text = "ZOOM_verify_stchLGrGQgO-9ACdBPKPRw"
htw-berlin.de text = "v=spf1 ip4:141.45.10.64/26 ip4:141.45.70.64/26 ~all"
htw-berlin.de nameserver = dns-2.dfn.de.
htw-berlin.de nameserver = infobloxv.htw-berlin.de.

```

