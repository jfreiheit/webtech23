# JSON und Direktiven

In diesem Kapitel geht es darum, wie wir innerhalb einer Komponente mit TypeScript Daten verwalten und diese Daten im HTML verwenden, um sie entweder anzuzeigen oder die Struktur des HTML-Codes mit diesen Daten zu ändern. Außerdem betrachten wir, wie in TypeScript auf Ereignisse reagieren können, die die Nutzerinnen beim Verwenden der Anwendung auslösen. Um die Verwaltung von Daten zu diskutieren, betrachten wir zunächst, wie Daten in TypeScript/JavaScript notiert werden. 

## JavaScript Object Notation (JSON)

Eine kurze Einführung zu Objekten in JavaScript haben wir bereits im [**JavaScript-Kapitel**](../javascript/#objekte) gegeben. Dort haben wir auch gesagt, dass wir auf die Notation solcher Objekte in JavaScript nochmal genauer eingehen wollen. Dies geschieht hier. *JavaScript Object Notation (JSON)* ist ein Datenaustauschformat, das einerseits einfach für Menschen zu lesen und zu schreiben ist und andererseits gut von Maschinen *geparst* (analysiert) und erzeugt werden kann. Ein Objekt in JSON beginnt mit einer geschweiften Klammer `{` und endet mit `}`. JSON besteht im wesentlichen aus Schlüssel-Werte-Paaren, die durch Komma getrennt sind. 

```bash
{
	"schlüssel1": wert1,
	"schlüssel2": wert2,
}
```

Die *Schlüssel* sind Strings in doppelten Hochkamma (`""`), dann folgt ein Doppelpunkt `:` und dann folgt der Wert. *Werte* können Strings, Zahlen, Wahrheitswerte, Arrays, Funktionen und Objekte (und `null`) sein. 

Hier ein Beispiel (erweitert [**aus**](https://wiki.selfhtml.org/wiki/JSON)):

```json linenums="1"
{
  "name": "Georg",
  "alter": 47,
  "verheiratet": false,
  "beruf": null,
  "kinder": [
    {
      "name": "Lukas",
      "alter": 19,
      "schulabschluss": "Gymnasium"
    },
    {
      "name": "Lisa",
      "alter": 14,
      "schulabschluss": null
    }
  ],
  "biografie": function() {
            return this.name + " ist " + this.alter + " und hat " + this.kinder.length + " Kinder.";
  },

}
```

- Der Wert zum Schlüssel `"name"` in Zeile `2` ist ein String (`string`). 
- Der Wert zum Schlüssel `"alter"` in Zeile `3` ist eine Zahl (`number`). 
- Der Wert zum Schlüssel `"verheiratet"` in Zeile `4` ist ein Wahrheitswert (`boolean`). 
- Der Wert zum Schlüssel `"kinder"` in Zeilen `6-17` ist Array. 
- Die Elemente in diesem Array sind selbst wieder Objekte in JavaScript Object Notation, bestehend aus jeweils drei Schlüssel-Werte-Paaren.
- Das `"kinder"`ist numerisch indiziert, d.h. wir können über den Index `0` auf das erste Kind (`"Lukas"`) und über den Index `1` auf das zweite Kind (`"Lisa"`) zugreifen

### Zugriff auf ein JSON

Der Zugriff auf die Werte eines JSON erfolgt mittels Punktnotation über den Schlüssel. Wir nehmen obiges Beispiel und speichern es in einer Variablen `georg`:

```javascript linenums="1"
let georg = {
			  "name": "Georg",
			  "alter": 47,
			  "verheiratet": false,
			  "beruf": null,
			  "kinder": [
			    {
			      "name": "Lukas",
			      "alter": 19,
			      "schulabschluss": "Gymnasium"
			    },
			    {
			      "name": "Lisa",
			      "alter": 14,
			      "schulabschluss": null
			    }
			  ],
			  "biografie": function() {
			            return this.name + " ist " + this.alter + " und hat " + this.kinder.length + " Kinder.";
			  },
			};
```

Dann können wir auf die einzelnen Werte wie folgt zugreifen:

```javascript
georg.name 		// "Georg"
georg.alter 	// 47
let kinder = georg.kinder; 	// Array aus 2 Objekten
kinder[0].name		// "Lukas"
kinder[1].name 		// "Lisa"
georg.biografie()	// "Georg ist 47 und hat 2 Kinder."
```

Man kann übrigens auch anstelle der Punktnotation ein JSON wie ein assoziatives Array auffassen und z.B. anstelle von `georg.name` über `georg['name']` auf den Wert `"Georg"` zugreifen. 

Es wäre auch möglich, das "Kinder"-Array in ein weiteres JSON umzuwandeln:

```javascript linenums="1" hl_lines="2 3 8 13 15 16 21 26"
// anstelle von:
  "kinder": [
    {
      "name": "Lukas",
      "alter": 19,
      "schulabschluss": "Gymnasium"
    },
    {
      "name": "Lisa",
      "alter": 14,
      "schulabschluss": null
    }
  ],
// ginge z.B. auch:
  "kinder": {
    "erstesKind" : {
      "name": "Lukas",
      "alter": 19,
      "schulabschluss": "Gymnasium"
    },
    "zweitesKind" : {
      "name": "Lisa",
      "alter": 14,
      "schulabschluss": null
    }
  },
```

Dann ist der Zugriff über den Index (also z.B. `georg.kinder[0]`) nicht mehr möglich. Stattdessen aber:

```javascript
georg.kinder.erstesKind.name
georg.kinder.zweitesKind.alter
```

### Viele Objekte im Array

Wenn Sie viele "gleiche" Objekte speichern, dann in einem Array. Die folgende Datei zeigt viele Objekte in JSON, die in einem Array abgelegt sind:

??? "data/members.json"
    ```json
    {
      "members": [
        {
          "forename": "Catherine",
          "surname": "Williams",
          "email": "cwilliamsl@360.cn"
        },
        {
          "forename": "Adam",
          "surname": "Anderson",
          "email": "aanderson8@google.fr"
        },
        {
          "forename": "Susan",
          "surname": "Andrews",
          "email": "sandrewsn@google.co.jp"
        },
        {
          "forename": "Catherine",
          "surname": "Andrews",
          "email": "candrewsp@noaa.gov"
        },
        {
          "forename": "Alan",
          "surname": "Bradley",
          "email": "abradley1c@globo.com"
        },
        {
          "forename": "Anne",
          "surname": "Brooks",
          "email": "abrooks16@bravesites.com"
        },
        {
          "forename": "Russell",
          "surname": "Brown",
          "email": "rbrownq@nifty.com"
        },
        {
          "forename": "Ryan",
          "surname": "Burton",
          "email": "rburton18@foxnews.com"
        },
        {
          "forename": "Roy",
          "surname": "Campbell",
          "email": "rcampbell1@geocities.com"
        },
        {
          "forename": "Russell",
          "surname": "Campbell",
          "email": "rcampbell17@eventbrite.com"
        },
        {
          "forename": "Bonnie",
          "surname": "Coleman",
          "email": "bcoleman11@fc2.com"
        },
        {
          "forename": "Ernest",
          "surname": "Coleman",
          "email": "ecoleman15@businessweek.com"
        },
        {
          "forename": "Richard",
          "surname": "Cruz",
          "email": "rcruz7@unc.edu"
        },
        {
          "forename": "Sean",
          "surname": "Cruz",
          "email": "scruz10@answers.com"
        },
        {
          "forename": "Rebecca",
          "surname": "Cunningham",
          "email": "rcunninghamd@mac.com"
        },
        {
          "forename": "Margaret",
          "surname": "Evans",
          "email": "mevansh@pcworld.com"
        },
        {
          "forename": "Jeffrey",
          "surname": "Ford",
          "email": "jford14@cnet.com"
        },
        {
          "forename": "Andrea",
          "surname": "Gardner",
          "email": "agardnerv@woothemes.com"
        },
        {
          "forename": "Deborah",
          "surname": "George",
          "email": "dgeorge6@furl.net"
        },
        {
          "forename": "Sean",
          "surname": "Gibson",
          "email": "sgibsony@alexa.com"
        },
        {
          "forename": "Virginia",
          "surname": "Graham",
          "email": "vgrahamk@aol.com"
        },
        {
          "forename": "Steven",
          "surname": "Hamilton",
          "email": "shamiltonu@state.tx.us"
        },
        {
          "forename": "Virginia",
          "surname": "Hawkins",
          "email": "vhawkinsf@ehow.com"
        },
        {
          "forename": "Edward",
          "surname": "Hicks",
          "email": "ehicksc@pcworld.com"
        },
        {
          "forename": "Mark",
          "surname": "Johnson",
          "email": "mjohnsonj@hostgator.com"
        },
        {
          "forename": "Ruth",
          "surname": "Jordan",
          "email": "rjordan1a@smugmug.com"
        },
        {
          "forename": "Antonio",
          "surname": "Kim",
          "email": "akim4@odnoklassniki.ru"
        },
        {
          "forename": "Jennifer",
          "surname": "Marshall",
          "email": "jmarshallt@gnu.org"
        },
        {
          "forename": "Eric",
          "surname": "Matthews",
          "email": "ematthews5@independent.co.uk"
        },
        {
          "forename": "Raymond",
          "surname": "Mcdonald",
          "email": "rmcdonald2@ihg.com"
        },
        {
          "forename": "Eric",
          "surname": "Miller",
          "email": "emillere@creativecommons.org"
        },
        {
          "forename": "Jonathan",
          "surname": "Morales",
          "email": "jmoralesa@ovh.net"
        },
        {
          "forename": "Marie",
          "surname": "Morgan",
          "email": "mmorganb@cloudflare.com"
        },
        {
          "forename": "Amanda",
          "surname": "Nelson",
          "email": "anelson13@indiatimes.com"
        },
        {
          "forename": "Lisa",
          "surname": "Olson",
          "email": "lolsonr@telegraph.co.uk"
        },
        {
          "forename": "Alice",
          "surname": "Ortiz",
          "email": "aortizw@histats.com"
        },
        {
          "forename": "Peter",
          "surname": "Phillips",
          "email": "pphillipss@1688.com"
        },
        {
          "forename": "Matthew",
          "surname": "Porter",
          "email": "mporter9@europa.eu"
        },
        {
          "forename": "Tammy",
          "surname": "Ray",
          "email": "trayx@weather.com"
        },
        {
          "forename": "Mark",
          "surname": "Richardson",
          "email": "mrichardson1d@ihg.com"
        },
        {
          "forename": "Joan",
          "surname": "Roberts",
          "email": "jroberts12@alibaba.com"
        },
        {
          "forename": "Kathleen",
          "surname": "Rose",
          "email": "kroseg@pinterest.com"
        },
        {
          "forename": "Steve",
          "surname": "Sanders",
          "email": "ssanders1b@wikispaces.com"
        },
        {
          "forename": "Shirley",
          "surname": "Scott",
          "email": "sscottm@macromedia.com"
        },
        {
          "forename": "Lillian",
          "surname": "Stephens",
          "email": "lstephens19@hugedomains.com"
        },
        {
          "forename": "Nicole",
          "surname": "Thompson",
          "email": "nthompson3@admin.ch"
        },
        {
          "forename": "Marie",
          "surname": "Thompson",
          "email": "mthompsonz@yelp.com"
        },
        {
          "forename": "Alan",
          "surname": "Vasquez",
          "email": "avasquezo@miibeian.gov.cn"
        },
        {
          "forename": "Mildred",
          "surname": "Watkins",
          "email": "mwatkins0@miibeian.gov.cn"
        },
        {
          "forename": "Eugene",
          "surname": "Williams",
          "email": "ewilliamsi@deliciousdays.com"
        }
      ]
    }
    ```

Ein Array ist stets numerisch indiziert, d.h. Sie können unter Verwendung des Index die einzelnen Objekte auslesen. 

### Operatoren über Arrays

Angenommen, wir haben obiges Objekt in `membersJSON` gespeichert, dann ist der Wert der Variable `membersArray` das darin enthaltene Array, wenn wir `let membersArray = membersJSON.members` definieren.

#### `length`

`length` gibt die Länge des Arrays zurück, z.B. `membersArray.length // 50`. 

#### `foreach`

`foreach()` ist eine Möglichkeit, für alle Elemente eines Arrays eine Funktion auszuführen, z.B.:

```js
let liste = "<ul>";
membersArray.forEach(createListItem);
liste += "</ul>";

function createListItem(value) {
    liste += `<li> <a href='mailto: ${value.email}'>${value.forename} ${value.surname}</a></li>`;
}

document.getElementById('listDiv').innerHTML = liste;
```

ergibt 

![arrays](./files/264_arrays.png)

#### `push()`

Mithilfe von `push` kann einem Array ein weiteres Element hinzugefügt werden, z.B. 

```js
membersArray.push({
        forename: "Maria",
        surname: "Mueller",
        email: "maria@mueller.org"
    })
```

Wir hätten denselben Effekt auch erzielen können, indem wir 

```js
membersArray[membersArray.length] = {
        forename: "Maria",
        surname: "Mueller",
        email: "maria@mueller.org"
    }
```

geschrieben  und somit die Arraylänge als neuen Index verwendet hätten. Das Hinzufügen von Elementen über die Index-Schreibweise birgt jedoch die Gefahr des Überschreibens (wenn der Index bereits existiert) oder des Entstehens von "Löchern", wenn ein Index verwendet wird, der sich nicht an den letzten Index anschließt.

#### `pop()`

`pop` entfernt das letzte Element aus dem Array und gibt es zurück, z.B. 

```js
let lastElement = membersArray.pop()
console.log(lastElement)    // das letzte Element
console.log(membersArray)   // letzte Element ist entfernt
```

#### `shift()`

`shift` entfernt das erste Element aus dem Array und gibt es zurück. Alle nachfolgenden Elemente rücken nach vorne auf, so dass der Index weiterhin mit `0` beginnt, z.B. 

```js
let firstElement = membersArray.shift()
console.log(firstElement)    // das letzte Element
console.log(membersArray)   // erstes Element ist entfernt und alle 
                            // nachfolgenden Elemente sind nach 
                            // vorne gerueckt
```


#### `unshift()`

`unshift` fügt ein Element an die erste Stelle des Arrays ein und "shifted" alle nachfolgenden Elemente um eine Stelle nach hinten. Die `unshift()`-Funktion gibt die neue Länge des Arrays zurück, z.B. 

```js
let newLength = membersArray.unshift({
        forename: "Maria",
        surname: "Mueller",
        email: "maria@mueller.org"
    })
```

#### `delete`

`delete` löscht Elemente im Array unter Angabe des Index. Allerdings hinterlässt `delete` "Löcher" im Array (Elemente, die `undefined` sind). `pop` und `shift` sind deutlich besser, da sie keine "Löcher" hinterlassen. Deshalb sollte `delete` nur vernünftig verwendet werden, nämlich indem nach `delete` die nachfolgenden Elemente nach vorne shiften. 

```js
let indexDelete = 13;
delete membersArray[indexDelete];   // membersArray[13] nun undefined
console.log(membersArray)           // Laenge immernoch 50
console.log(membersArray[13])       // undefined
for(let i = indexDelete; i < membersArray.length; i++) {
    membersArray[i] = membersArray[i+1]     // alle nachfolgenden nach links shiften
}
membersArray.pop()                  // letztes Element ist undefined und wird entfernt
```

Für Löschen von Elementen aus Arrays siehe auch [hier](https://love2dev.com/blog/javascript-remove-from-array/).

#### `concat()`

`concat()` ist hauptsächlich dazu da, mehrere Arrays zu einem zu verschmelzen. Angenommen, Sie haben ein Array `arr1` und ein Array `arr2`. Dann können Sie `let arr3 = arr1.concat(arr2);` schreiben und in `arr3` sind dann alle Elemente aus `arr1` (zuerst) **und** `arr2` (folgend). Beachten Sie, dass `arr1` dabei unverändert bleibt, d.h. nur `arr1.concat(arr2);` hat keinen Effekt. Sie müssten dann `arr1 = arr1.concat(arr2);` schreiben. 

Sie können `concat()` auch dazu verwenden, ein einzelnes Element dem Arry hinzuzufügen, z.B. 

```js
membersArray = membersArray.concat({
        forename: "Maria",
        surname: "Mueller",
        email: "maria@mueller.org"
    })
```

Sie können auch mehrere Arrays in einem Schritt miteienander verbinden, z

#### `splice()`

`splice()` kann verwendet werden, um entweder Elemente zu einem Array an einer bestimmten Position hinzuzufügen oder um eine bestimmte Anzahl von Elementen zu löschen. Dazu erwartet `splice()` zunächst zwei Parameter. Der erste Parameter gibt den Index an, von dem entweder gelöscht oder eingefügt werden soll. Der zweite Parameter gibt entweder die Anzahl der zu löschenden Elemente an oder er ist `0`, dann soll eingefügt werden. Ist der zweite Parameter größer als `0` und es folgen weitere Parameter, dann handelt es sich um Ersetzen von Elementen im Array. Beispiele:

```js
membersArray.splice(13, 4);              // loescht 4 Elemente beginnend bei Index 13
membersArray.splice(13, 0, ob1, obj2);   // fuegt die beiden Objekte obj1 und obj2 ab Index 13 hinzu
membersArray.splice(13, 2, ob1, obj2);   // ersetzt die beiden Objekte in Index 13 und 14 durch obj1 und obj2
```

Die Rückgabe von `splice()` ist das Array der gelöschten (ersetzten) Elemente. 

#### `slice()`

`sclice()` erzeugt ein neues Array aus einem gegebenen Array und kopiert in das neue Array die Elemente ab dem Index, der in `slice()` als Parameter übergeben wird. Wird ein zweiter Parameter angegeben, handelt es sich dabei um die Anzahl der zu kopierenden Elemente. 


```js
let newArray = membersArray.slice(13);    // kopiere alle Elemente ab Index 13 nach newArray
newArray = membersArray.splice(13, 5);    // kopiere 5 Elemente ab Index 13 nach newArray
```
#### `sort()`

`sort()` sortiert ein Array. Allerdings ist zu beachten, dass `sort()` nur korrekt funktioniert, wenn es sich bei den Elementen um Strings handelt. Zahlen würden z.B. falsch sortiert werden, da `2` z.B. größer als `10` wäre, da `"2"` lexikographisch nach `"10"` (`"1"`) käme. Um z.B. Zahlen zu sortieren, könnte der `sort()`-Funktion z.B. folgende Funktion als Callback übergeben werden:

```js
numbersArrayToBeSorted.sort(function(a, b){return b - a});
```

Damit wird eine `compare()`-Methode implementiert. Gibt diese Methode für `b-a` einen Wert größer als `0` zurück, dann ist `b` größer als `a`, gibt sie einen Wert kleiner als `0` zurück, dann ist `a` größer als `b` und wenn der Rückgabewert `0` ist, dann gilt `a == b`. 

Um z.B. das `membersArray` nach der Eigenschaft `forename` zu sortieren, kann folgende Funktion verwendet werden: 

```js
membersArray.sort(function(a,b) {
  let a1 = a.forename.toLowerCase();
  let b1 = b.forename.toLowerCase();
  if(a1 < b1) return -1;
  if(a1 > b1) return 1;
  return 0;
});
```

In Arrow-Notation sieht die Funktion wie folgt aus:

```js
membersArray.sort((a,b) => {
  let a1 = a.forename.toLowerCase();
  let b1 = b.forename.toLowerCase();
  if(a1 < b1) return -1;
  if(a1 > b1) return 1;
  return 0;
});
```

Wir wandeln zunächst alle Vornamen in Strings mit Kleinbuchstaben um und implementieren dann eine `compare()`-Funktion wie oben. Sollte z.B. nach der Eigenschaft `surname` sortiert werden, müsste im Code `forename` durch `surname` ersetzt werden. 

#### `map()`

`map()` wird verwendet, um eine Funktion auf alle Elemente des Arrays anzuwenden. Diese Funktion wird der `map()`-Funktion als Callback übergeben. Folgender Code stellt allen E-Mailadressen aus `membersArray` ein "mailto:" voran:

```js
let mailTo = membersArray.map( (value) => {
    return value['email'] = "mailto: " + value['email'];
})
```

Das `mailTo`-Array enthält dann nur alle Werte der `email`-Eigenschaft, sieht also so aus:

```bash
['mailto: aanderson8@google.fr', 'mailto: abradley1c@globo.com', 'mailto: avasquezo@miibeian.gov.cn', 'mailto: aortizw@histats.com', 'mailto: anelson13@indiatimes.com', 'mailto: agardnerv@woothemes.com', 'mailto: abrooks16@bravesites.com', 'mailto: akim4@odnoklassniki.ru', 'mailto: bcoleman11@fc2.com', 'mailto: candrewsp@noaa.gov', 'mailto: dgeorge6@furl.net', 'mailto: ehicksc@pcworld.com', 'mailto: ematthews5@independent.co.uk', 'mailto: emillere@creativecommons.org', 'mailto: ecoleman15@businessweek.com', 'mailto: ewilliamsi@deliciousdays.com', 'mailto: jford14@cnet.com', 'mailto: jmarshallt@gnu.org', 'mailto: jroberts12@alibaba.com', 'mailto: jmoralesa@ovh.net', 'mailto: kroseg@pinterest.com', 'mailto: lstephens19@hugedomains.com', 'mailto: lolsonr@telegraph.co.uk', 'mailto: mevansh@pcworld.com', 'mailto: maria@mueller.org', 'mailto: maria@mueller.org', 'mailto: mmorganb@cloudflare.com', 'mailto: mthompsonz@yelp.com', 'mailto: mjohnsonj@hostgator.com', 'mailto: mrichardson1d@ihg.com', 'mailto: mporter9@europa.eu', 'mailto: mwatkins0@miibeian.gov.cn', 'mailto: nthompson3@admin.ch', 'mailto: pphillipss@1688.com', 'mailto: rmcdonald2@ihg.com', 'mailto: rcunninghamd@mac.com', 'mailto: rcruz7@unc.edu', 'mailto: rcampbell1@geocities.com', 'mailto: rbrownq@nifty.com', 'mailto: rcampbell17@eventbrite.com', 'mailto: rjordan1a@smugmug.com', 'mailto: rburton18@foxnews.com', 'mailto: sgibsony@alexa.com', 'mailto: sscottm@macromedia.com', 'mailto: ssanders1b@wikispaces.com', 'mailto: shamiltonu@state.tx.us', 'mailto: sandrewsn@google.co.jp', 'mailto: trayx@weather.com', 'mailto: vgrahamk@aol.com', 'mailto: vhawkinsf@ehow.com']
```

Wenn `mailTo` alle Objekte vollständig enthalten sollte, dann müsste die Funktion so aussehen:

```js
let mailTo = membersArray.map( (value) => {
    value['email'] = "mailto: " + value['email'];
    return value;
})
```

Da es sich bei den Elementen im Array um Objekte handelt, sind auch die Einträge im `membersArray` entsprechend geändert. Das wäre bei Nicht-Objekten (z.B. Strings oder Numbers)  nicht der Fall.

Die Callback-Funktion könnte auch drei Parameter erwarten: `(value, index, array)`, wobei es sich bei `array` um das Array selbst, also `membersArray` handelt.

#### `filter()`

Mithilfe der `filter()`-Funktion können Elemente aus einem Array gefiltert und in ein neues Array kopiert werden. Angenommen, wir wollen alle Elemente, in denen der Vorname mit `R` beginnt, herausfiltern:

```js
let forenamesStartingWithR = membersArray.filter ( (value) => {
    if(value.forename.startsWith("R"))
    {
        return value;
    }
})
```

Dann sieht `forenamesStartingWithR` so aus:

```bash
0 : {forename: 'Raymond', surname: 'Mcdonald', email: 'mailto: rmcdonald2@ihg.com'}
1 : {forename: 'Rebecca', surname: 'Cunningham', email: 'mailto: rcunninghamd@mac.com'}
2 : {forename: 'Richard', surname: 'Cruz', email: 'mailto: rcruz7@unc.edu'}
3 : {forename: 'Roy', surname: 'Campbell', email: 'mailto: rcampbell1@geocities.com'}
4 : {forename: 'Russell', surname: 'Brown', email: 'mailto: rbrownq@nifty.com'}
5 : {forename: 'Russell', surname: 'Campbell', email: 'mailto: rcampbell17@eventbrite.com'}
6 : {forename: 'Ruth', surname: 'Jordan', email: 'mailto: rjordan1a@smugmug.com'}
7 : {forename: 'Ryan', surname: 'Burton', email: 'mailto: rburton18@foxnews.com'}
```

#### Weitere Array-Funktionen

Auch die folgenden Funktionen erwarten eine Callback-Funktion als Parameter.

- `reduce()` reduziert ein Array auf einen einzigen Wert. Wird z.B. für ein Array aus lauter Zahlen angewendet, um die Gesamtsumme der Zahlen zu ermitteln oder den Durchschnitt. 
- `every()` prüft, ob **alle** Elemente des Arrays eine bestimmte Bedingung erfüllen, z.B. größer als `0` sind oder ungleich `undefined`. Gibt ein `true` zurück, wenn die Bedingung für alle gilt, `false` sonst.
- `some()` prüft, ob **mindestens ein** Element des Arrays eine bestimmte Bedingung erfüllen, z.B. größer als `0` ist oder ungleich `undefined`. Gibt ein `true` zurück, wenn die Bedingung für mindestens ein Element gilt, `false` sonst.
- `find()` gibt das erste Element zurück, für das eine bestimmte Bedingung gilt. `find()` muss nicht zwingend eine Callback-Funktion übergeben werden, kann auch ein Wert für ein Element sein.
- `findIndex()` gibt den Index des ersten Elementes zurück, für das die übergebene Funktion passt.

Die folgenden Funktionen erwarten keine Callback-Funktion:

- `includes()` prüft, ob ein Element im Array existiert. Das Element wird als Parameter übergeben. Gibt `true` zurück, wenn das Element existiert, `false` sonst.
- `entries()` gibt ein Array aus den Schlüssel-Wertepaaren des Arrays zurück.
- `keys()` gibt ein Array aller Schlüssel (Indizes) des Arrays zurück.
- `indexOf()` gibt den (ersten) Index des Elementes im Array zurück, welches als Parameter übergeben wird.
- `lastIndexOf()` gibt den (letzten) Index des Elementes im Array zurück, welches als Parameter übergeben wird.


## Bindings und Direktiven

### {{ Interpolation }}

*Interpolation* ist die einfachste Form des *data binding*. Syntaktisch erkennt man Interpolation an den doppelten geschweiften Klammern `{{ Interpolation }}`. 

=== "Beispiel"
``` javascript linenums="1"
import { Component } from '@angular/core';

@Component({
  selector: 'app-lesson',
  template: `
    <h1>{{ headline }}</h1>
    <p>Hier steht {{name}}</p>
  `,
  styleUrls: ['./lesson.component.css']
})
export class LessonComponent {
  headline = 'Mein Titel';
  name = 'mein Name';
}
```

Im obigen Beispiel hat die Komponente `LessonComponent` zwei Eigenschaften: `headline` und `name`. In obiger Komponente wird (zur Anschauung) sogenanntes *inline templating* verwendet, d.h. es gibt keine eigene `lesson.component.html`-Datei, in der der HTML-Code steht, sondern der HTML-Code wird direkt in die `template`-Eigenschaft der Typescript-Datei `lesson.component.ts`eingefügt (siehe Zeilen 5-8 im obigen Beispiel). Der HTML-Code wird in *backticks* eingefasst (` `` `), nicht zu verwechseln mit den einfachen Anführungsstrichen (` '' `).

Damit inline templating möglich ist, wird die Komponente mit dem Flag `-t` erzeugt (`inlineTemplate=true`), d.h. unsere Lesson-Komponente wurde mithilfe der CLI wie folgt erzeugt:

```
ng g c lesson -t
```

Eine Interpolation kann auch Ausdrücke enthalten, die aufgelöst werden, z.B.

``` html
<p>1 + 2 = {{1 + 2}}.</p>
```

Man kann mithilfe einer [Direktive](./#direktiven) durch ein Array laufen und jedes einzelne Element mithilfe von Interpolation ausgeben:

``` javascript
@Component({
  selector: 'app-lesson',
  template: `
    <ol>
      <li *ngFor="let day of weekdays">{{ day }}</li>
    </ol>
  `,
  styleUrls: ['./lesson.component.css']
})
export class LessonComponent {
  weekdays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'];
}
```

Oder es ist möglich, Attributen von HTML-Elementen mithilfe von Interpolation Werte zuzuordnen:

``` javascript
@Component({
  selector: 'app-lesson',
  template: `
    <img src="{{ imgUrl }}" />
  `,
  styleUrls: ['./lesson.component.css']
})
export class LessonComponent {
  imgUrl = 'https://www.dpunkt.de/common/images/cover_masterid/800/12400.jpg';
}
```

Für unser `first`-Beispiel ist ein ganz einfaches Beispiel für die `main`-Komponente gezeigt:

=== "main.component.ts"
    ```js linenums="1" hl_lines="9"
    import { Component, OnInit } from '@angular/core';

    @Component({
      selector: 'htw-main',
      templateUrl: './main.component.html',
      styleUrls: ['./main.component.css']
    })
    export class MainComponent implements OnInit {
      headline = 'This is main';

      constructor() { }

      ngOnInit(): void {
      }

    }
    ```

=== "main.component.html"
    ```html linenums="1" hl_lines="3"
    <div id="main">
      <h3>
          {{ headline }}
      </h3>
      <div id="row">
          <div id="left">
              <htw-left>
              </htw-left>
          </div>
          <div id="right">
              <htw-right>
              </htw-right>
          </div>
      </div>
    </div>
    ```

### #Elementreferenzen

Über eine *Elementreferenz*, die man im HTML-Code mittels des Rautensymbols definiert, kann in Angular sehr einfach auf das Element zugegriffen werden. Das folgende Beispiel zeigt eine solche *Elementreferenz*:

```html
<input #id type="text" value="Elementreferenz" />
{{ id.value }}
```

In dem Beispiel wurde einem Textfeld die Elementreferenz `id` zugewiesen (kann jeder Name sein), erkennbar an `#id`. Über diese Elementreferenz (den Namen) lässt sich nun direkt auf dieses Element zugreifen. Im obigen Beispiel wird die `value`-Eigenschaft ausgelesen, also der Wert, der in das Textfeld eingegeben wird (oder, wie oben, vordefiniert ist). Beachten Sie jedoch, dass der Wert nicht automatisch angepasst wird, sobald eine Eingabe erfolgt. Dies muss durch ein Ereignis (z.B. `change` oder `input`) getriggert werden. 



### [Property Bindings]

Insbesondere, wenn Attributen von HTML-Elementen Werte zugeordnet werden sollen (so wie beim `imgUrl`-Beispiel des Abschnitts [**{{Interpolation}}**](./#interpolation)), spricht man von *property binding*. Property binding spielt eine große Rolle beim Datenfluss von Eltern-Komponenten auf Kind-Komponenten. Die generelle Idee dabei ist, dass mithilfe von *property binding* Werte (Daten) an Attribute von HTML-Elementen bindet. Diese HTML-Elemente können auch Komponenten sein.

Wir betrachten zunächst die unterschiedlichen Arten (Notationen) von property binding:

``` html
<element [property]="ausdruck"></element>
```

D.h. ein *ausdruck* wird übergeben, der zu einem Wert aufgelöst wird und dieser Wert wird dem Attribut `property` übergeben. Betrachten wir nochmals das letzte Beispiel aus dem Abschnitt [**{{Interpolation}}**](./#interpolation)). Bei diesem Beispiel haben wir Interpolation verwendet, um dem Attribut `src` des HTML-Elementes `img` einen Wert zuzuweisen. Das exakt gleiche Verhalten lässt sich auch mittels *property bindings* erzeugen:

``` html
<img [src]="imgUrl" />

<!-- imgUrl = 'https://www.dpunkt.de/common/images/cover_masterid/800/12400.jpg'; -->
```

Das bedeutet für unser `first`-Beispiel, dass die beiden `<img>`-Definitionen gleich sind:


=== "header.component.html"
    ```html linenums="1" hl_lines="2-3"
    <p>header works!
        <img src="{{ imgUrl }}" alt="{{ description }}" width="53px;" />
        <img [src]="imgUrl" [alt]="description" width="53px;" />
    </p>
    ```
 
=== "header.component.ts"
    ```js linenums="1" hl_lines="9-10"
    import { Component, OnInit } from '@angular/core';

    @Component({
      selector: 'htw-header',
      templateUrl: './header.component.html',
      styleUrls: ['./header.component.css']
    })
    export class HeaderComponent implements OnInit {
      imgUrl = '/assets/images/fiw.jpg';
      description = 'FIW Logo';

      constructor() { }

      ngOnInit(): void {
      }

    }
    ```



Neben diesen "allgemeinen" property bindings gibt es auch noch "spezielle" property bindings, nämlich *class bindings* und *style bindings*. Bei *class bindings* wird das Präfix `class` vor die property (die entsprechende CSS-Klasse) gesetzt:

``` html
<element [class.class1]="class1enabled"
         [class.class2]="class2enabled" ... ></element>
```

D.h. die CSS-Klasse `class1`ist genau dann wirksam, wenn der Ausdruck `class1enabled` true ist und `class2`ist genau dann wirksam, wenn der Ausdruck `class2enabled` true ist usw.

Bei den *style bindings* werden jedoch gar keine Ausdrücke, sondern Werte übergeben:

``` html
<element [style.color]
```



### (Event Bindings)

In den *property bindings* haben wir gesehen, wie Werte Attributen (Eigenschaften) von Elementen zugeordnet werden können. Aus JavaScript ist auch bekannt, dass Ereignisse Attribute von Elementen sein können, z.B. `onClick`, `onKeyup`, `onChange` usw. Dabei handelt es sich um sogenannte *native DOM-Ereignisse*. Neben der Möglichkeit, solche nativen DOM-Ereigniss zu behandeln, bietet Angular auch die Möglichkeit, eigene Ereignisse zu definieren und diese zu behandeln. Wir betrachten beide Möglichkeiten und beginnen mit den nativen Ereignissen.

#### Native DOM-Ereignisse

In HTML sieht das unter Aufruf einer JavaScript-Funktion für die Ereignisbahandlung dann typischerweise (hier das Click-Ereignis für einen Button) wie folgt aus:

=== "HTML"
    ``` html
    <button onClick="doSomething()">Click here!</button>
    ```
=== "JavaScript"
    ``` javascript
    function doSomething() 
    {
      // something to do
    }
    ```

In Angular ist das Prinzip das gleiche, nur dass das Ereignis in runden Klammern genannt und an dieses Ereignis die Ereignisbehandlung gebunden wird (*event binding*). Das bedeutet, das Angular-Template für das obige Beispiel sieht wie folgt aus:

=== "Angular-Template"
    ``` html
    <button (click)="doSomething()">Click here!</button>
    ```
=== "Angular-Typescript"
    ``` javascript
    export class EventsComponent {

       doSomething() {
          // something to do
       }
    }
    ```

Dieses Prinzip gilt für alle nativen DOM-Ereignisse. Hier ein kurzer Überblick über die wichtigsten (für eine umfangreichere Liste siehe [hier](https://developer.mozilla.org/en-US/docs/Web/Events#Standard_Events) oder [hier](https://www.w3schools.com/jsref/dom_obj_event.asp)):

| Ereignis        | Beschreibung                                       |
|-----------------|----------------------------------------------------|
| `click`         | Mausklick auf das Element                          |
| `change`        | Der Inhalt/Wert eines Elementes hat sich geändert  |
| `mouseover`     | die Maus wird über das Element bewegt              |
| `mouseout`      | die Maus wird vom Element wegbewegt                |
| `keydown`       | eine Taste der Tastatur wird gedrückt              |
| `keyup`         | Loslassen einer Taste                              |
| `load`          | der Browser hat die Seite vollständig geladen      |
| `focus`         | Fokussieren des Elements (z.B. Anklicken)          |
| `blur`          | Verlieren des Fokus (z.B. Klick außerhalb)         |
| `submit`        | Abschicken eines Formulars                         |
| `copy`, `paste` | Kopieren, Einfügen von Text                        |

Einen kleinen Unterschied gibt es noch bei der Übergabe des Ereignisses an die das Ereignis behandelnde Funktion zu beachten. Während in plain JavaScript das Ereignis mit `event` der Funktion übergeben wird, erfolgt die Übergabe des Ereignisses in Angular mit `$event`. Beispiel:

=== "Angular-Template"
    ``` html
    <input (change)="showPayload($event)" type="text" />
    ```
=== "Angular-Typescript"
    ``` javascript
    export class EventsComponent {

      showPayload(e: Event) {
        console.log(e);
      }
    }
    ```

Alle Events (in TypeScript/Angular) sind vom Typ `Event`. Es gibt noch speziellere Eventtypen, die aber alle auf dem Interface `Event` basieren, z.B. `MouseEvent`, `InputEvent`, `KeyboardEvent`, `UIEvent`, `ClipboardEvent`. Weitere Details siehe [hier](https://developer.mozilla.org/en-US/docs/Web/API/Event).

Die einfache JavaScript-Attributschreibweise kann in Angular nicht verwendet werden, sondern immer nur die *event binding*-Schreibweise von Angular (mit den runden Klammern)!


#### Eigene Ereignisse

Für eine Komponente kann ein eigenes - nicht natives - Ereignis definiert werden. Dies geschieht, indem für eine Komponente eine neue Eigenschaft (z.B. `myEvent`) definiert wird und diese vom Typ `EventEmitter` deklariert wird. Mithilfe von Generics kann der Typ des Events angegeben werden, der ausgelöst werden soll - wenn Sie den Typ nicht genau kennen, verwenden Sie `any`. Soll das Ereignis an die Elternkomponente weitergeleitet werden, was meistens der Fall ist, wird der Decorator `@Output()`verwendet. 
Das Auslösen des Events geschieht dann durch die `emit()`-Methode von `EventEmitter`. Hier ein typisches Beispiel (zunächst die Kindkomponente `EventsComponent` - also `events.component.html` und `events.component.ts`):

=== ".html"
    ``` html
    <button (click)="emitMyEvent()">Click here!</button>
    ```
=== ".ts"    
    ``` javascript linenums="1"
    import {Component, EventEmitter, Output} from '@angular/core';

    @Component({
      selector: 'app-events',
      templateUrl: './events.component.html',
      styleUrls: ['./events.component.css']
    })
    export class EventsComponent {
      @Output() myEvent = new EventEmitter<any>();

      emitMyEvent() {
        this.myEvent.emit();
      }

    }
    ``` 

Die `.html`-Datei definiert einen Button mit dem nativen Ereignis `click`. Dieses wird durch die Methode `emitMyEvent()` behandelt. 

In der `.ts`-Datei ist diese Methode definiert (Zeilen 11-13). Darin wird das eigene Event `myEvent` ausgelöst. Dieses Event ist ein Objekt vom Typ `EventEmitter`, typisiert als `any` (beliebiger Typ). Das Auslösen dieses Events wird an die aufrufende Komponente (die Elternkomponente) ausgegeben (Decorator `@Output()`). Deklaration der Eigenschaft und Dekorieren mit `@Output()` in Zeile 9. Das Auslösen des eigenen Events erfolgt durch den Aufruf der Methode `emit()` aus `EventEmitter` (Zeile 12).

In der Elternkomponente kann dieses Ereignis nun empfangen werden (Beispiel einer Elternkomponente `AppComponent` - also `app.component.html` und `app.component.ts`):

=== ".html"
    ``` html
    <app-events (myEvent)="handleEventFromEventsComponent()"></app-events>
    ```
=== ".ts"    
    ``` javascript linenums="1"
    import { Component } from '@angular/core';

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {

      handleEventFromEventsComponent() {
        console.log('myEvent in der Kindkomponente ausgelöst');
      }

    }
    ``` 

In der `AppComponent` (das kann natürlich eine beliebige Komponente sein), wird die `EventsComponent` eingebunden (siehe `<app-events>` im Template der `AppComponent`). Dadurch entsteht die Hierarchie Elternkomponente `AppComponent` --> Kindkomponente `EventsComponent` im DOM. 

Mithilfe von *event binding* wird die Behandlung des Ereignisses `myEvent` an die Methode `handleEventFromEventsComponent()` gebunden. In dieser Methode erfolgt hier einfach nur eine Ausgabe auf die Konsole. 

Interessant ist, dass wir dadurch die Möglichkeit haben, Daten von der Kindkomponente zur Elternkomponente fließen zu lassen. Dazu übergeben wir diese Daten als `payload` des Ereignisses. Dafür typisieren wir `EventEmitter` mit dem Typ, von dem wir Daten übergeben wollen (z.B. `Book` - siehe [Bücher-App](./books/#event-binding)). Die beiden obigen Beispiele sehen dann wie folgt aus (zuerst wieder `EventsComponent`): 

=== ".html"
    ``` html
    <button (click)="emitMyEvent(book)">Click here!</button>
    ```
=== ".ts"    
    ``` javascript linenums="1"
    import {Component, EventEmitter, Output} from '@angular/core';

    @Component({
      selector: 'app-events',
      templateUrl: './events.component.html',
      styleUrls: ['./events.component.css']
    })
    export class EventsComponent {
      @Output() myEvent = new EventEmitter<Book>();

      emitMyEvent(book: Book) {
        this.myEvent.emit(book);
      }

    }
    ``` 

Im Template (HTML) werden die Daten der Ereignisbehandlung übergeben. Das `EventEmitter`-Objekt ist mit dem konkreten Datentyp typisiert. Bei Aufruf der Methode `emit()` werden die Daten an die Elternkomponente übergeben. 

Die Elternkomponente (hier wieder `AppComponent` kann diese Daten, die von der Kindkomponente an die Elternkomponente via Ereignis geflossen sind, nun weiterverarbeiten bzw. darstellen):

=== ".html"
    ``` html
    <app-events (myEvent)="handleEventFromEventsComponent($event)"></app-events>
    ```
=== ".ts"    
    ``` javascript linenums="1"
    import { Component } from '@angular/core';

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {

      handleEventFromEventsComponent(book: Book) {
        console.log(book.title);
      }

    }
    ``` 

Wichtig beim *event binding* der Elternkomponente ist, dass der *payload* des Ereignisses mit `$event` übergeben wird (siehe auch [Native DOM-Ereignisse](./#native-dom-ereignisse)). 

!!! success "Zusammenfassung"
    In den letzten drei Abschnitten Interpolation, Property Binding und Event Binding haben wir uns mit Datenfluss beschäftigt. Interpolation wird verwendet, um innerhalb einer Komponente die in der TypeScript-Klasse definierten Daten im Template darzustellen. Mithilfe von Property Binding kann die aufrufende Komponente (Elternkomponente) der aufgerufenen Kopmponente (Kindkomponente) Daten übergeben. Mithilfe von Event Binding kann die Kindkomponente der Elternkomponente mithilfe eines eigenen Ereignisses Daten übergeben.
    Für die Anwendung dieser Konzepte schauen Sie sich [**Bücher-App-->Datenfluss zwischen Komponenten**](./books/#datenfluss-zwischen-komponenten) an. 


### Direktiven

In Angular gibt es 3 Arten sogenannter *Direktiven* (engl. *Directives*):

- Komponentendirektiven (Components—directives) 
- Attributdirektiven (Attribute Directives)
- Strukturdirektiven (Structural-Direktives)

Komponentendirektiven sind die meistverwendete Art und bereits in [**Angular --> Kompnenten**](./#komponenten) betrachtet. Attribut- und Strukturdirektiven können als HTML-Attribute verstanden werden, die dem HTML-Element ein zusätzliches Verhalten hinzufügt. Attributdirektiven wirken sich das innere Verhalten eines HTML-Elementes aus (z.B. können damit CSS-Eigenschaften geändert, hinzugefügt oder gelöscht werden). Mit Strukturdirektiven kann die Struktur des DOMs geändert werden (z.B. können ganze HTML-Elemente dem DOM-Baum hinzugefügt werden).

#### Strukturdirektiven

Strukturdirektiven beginnen immer mit einem Stern `*`. Die bekanntesten Vertreter sind 

- `*ngFor` 
- `*ngIf`
- `*ngSwitch`

Diese sind auch in [angular.io](https://angular.io/guide/structural-directives) erläutert. Wir erläutern die darin aufgeführten Beispiele und beginnen mit `*ngIf`:

```html linenums="1"
<p *ngIf="true">
  Expression is true and ngIf is true.
  This paragraph is in the DOM.
</p>
<p *ngIf="false">
  Expression is false and ngIf is false.
  This paragraph is not in the DOM.
</p>
```

Die Direktive `*ngIf` wird also wie ein Attribut des `<p>`-Elementes behandelt. Das Attribut `*ngIf` hat entweder den Wert `"true"` oder den Wert `"false"`. Ja nach Wert des Attributes wird das jeweilige `<p>`-Element in den DOM-Baum eingebunden. Also entweder das `<p>`-Element aus den Codezeilen `1`-`4` (bei Wert `"true"`) oder das `<p>`-Element aus den Codezeilen `5`-`8` (bei Wert `"false"`). In einer echten Anwendung ergibt sich der Wert des Attributes/der Direktive meistens aus dem Wert einer boole'schen Variablen oder einem anderen boole'schen Ausdruck.

Das nicht dargestellte Element ist auch nicht Teil des DOMs! Es ist also nicht einfach nur auf `hide` gesetzt, sondern es ist gar nicht im DOM vorhanden. 

Intern wird aus der `*ngIf`-Direktive übrigens ein sogenanntes [*Property-Binding*](./#property-bindings):

```html
<ng-template [ngIf]="true">
  <p>
    Expression is true and ngIf is true.
    This paragraph is in the DOM.
  </p>
</ng-template>
<ng-template [ngIf]="false">
  <p>
    Expression is false and ngIf is false.
    This paragraph is not in the DOM.
  </p>
</ng-template>
```

Die `*ngFor`-Direktive ist etwas komplexer als `*ngIf`. Für `*ngFor` benötigen wir mindestens eine Liste (oder ein Array) und eine Laufvariable, die die Werte aus der Liste annehmen kann. Im folgenden Beispiel ist `i` unsere laufvariable und `[1, 2, 3, 4, 5, 6]` unser Array.

``` html
<div *ngFor="let i of [1, 2, 3, 4, 5, 6]">
  {{ i }}
</div>
``` 

Für jeden Wert aus der Liste wird ein eigenes `<div>`- Element erzeugt. Der DOM-Baum sieht für obiges Beispiel also wie folgt aus (Angular-Attribute weggelassen):

``` html
<div> 1 </div>
<div> 2 </div>
<div> 3 </div>
<div> 4 </div>
<div> 5 </div>
<div> 6 </div>
```

Außerdem stellt `*ngFor` noch einige Hilfsvariablen zur Verfügung, die ebenfalls genutzt werden können:

- `index` (Index des aktuellen Elementes `0, 1, 2, ... `)
- `first` (ist `true`, wenn *erstes* Element, sonst `false`)
- `last` (ist `true`, wenn *letztes* Element, sonst `false`)
- `even` (ist `true`, wenn *Index gerade*, sonst `false`)
- `odd` (ist `true`, wenn *Index ungerade*, sonst `false`)

Folgend ein komplexeres Beispiel unter Verwendung einiger Hilfsvariablen:

``` html linenums="1"
<div *ngFor="let value of [1, 2, 3, 4, 5, 6];
                 index as i;
                 first as f;
                 last as l;
                 odd as o;">
  <div *ngIf="f">Start</div>
  <div [style.color]="o ? 'red' : 'blue'">{{ i }} : {{ value }}</div>
  <div *ngIf="l">Ende</div>
</div>
```

In Zeile `1` ist unsere Laufvariable durch das Array nun `value`. Außerdem wird der jeweilige Wert von `index` in der Variablen `i` (Zeilennummer `2`)
gespeichert, der Wert von `first` in der Variablen `f`(Zeilennummer `3`), der Wert von `last` in der Variablen `l`(Zeilennummer `4`) und der Wert von `odd` in der Variablen `o`(Zeilennummer `5`) - die Hilfsvariable `even` betrachten wir hier nicht, da deren Wert genau der Negation von `odd` entspricht. In Zeile `6` wenden wir die `*ngIf`-Direktive an: ein `<div>` mit dem Inhalt `Start` wird vor dem ersten Element aus dem Array ausgegeben. Für jedes weitere Element nicht mehr. In Zeile `7` erfolgt ein *Property Binding*: die `color`-Eigenschaft bekommt einen Wert zugewiesen. Der Wert ist jedoch abhängig davon, ob `o` wahr ist (dann Wert `red`) oder falsch (dann Wert `blue`).   Zeile `7` zeigt außerdem wie mithilfe von *Interpolation* der Wert von `i` und der Wert von `value`, getrennt mit ` : ` ausgegeben werden. Die Ausgabe ist also:

![ngfor](./files/12_ngfor.png)

!!! question "Aufgabe"
    Informieren Sie sich auch über die `*ngSwitch`-Direktive. Implementieren Sie ein Beispiel, in dem Sie die 3 Direktiven `*ngIf`, `*ngFor` und `*ngSwitch` anwenden. 


