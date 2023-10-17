# Callbacks und Promises

Manche Konzepte sind in JavaScript bzw. TypeScript für Java-Programmiererinnen zunächst ungewöhnlich. Dazu gehören *Callbacks* und *Promises*. Diese Konzepte werden hier etwas näher beleuchtet. 

## Callbacks

Zunächst einmal sind *Callbacks* Funktionen, die anderen Funktionen als Parameter übergeben werden. Wir betrachten folgendes Beispiel:

```javascript linenums="1"
let x = function () {
    console.log ("Ausgabe der Funktion x");
}

let y = function () {
    console.log ("Ausgabe der Funktion y");
}

let z = function (callback) {
    console.log("Ausgabe der Funktion z - vor Aufruf von callback");
    callback();
    console.log("Ausgabe der Funktion z - vor Aufruf von callback");
}
```

Wir haben drei Funktionen. Diese werden als anonyme Funktionen definiert, aber die Funktionsdefinitionen werden sofort einer Variablen zugewiesen. Das bedeutet, dass z.B. der Wert der Variablen `x` die Funktionsdefinition 
```js
function () {
    console.log ("Ausgabe der Funktion x");
}
```
ist. Wenn wir nun z.B. `console.log(x)` aufrufen, dann erhalten wir folgende Ausgabe auf der Konsole:
```bash
ƒ () {
    console.log ("Ausgabe der Funktion x");
}
```
Wenn wir aber `x();`, also sozusagen, die Variable als Funktion aufrufen, dann wird die Funktion ausgeführt und wir erhalten auf der Konsole die Ausgabe
```bash
Ausgabe der Funktion x
```

Wenn wir nun `z(x);` aufrufen, dann wird die in den Zeilen `9-12` definierte Funktion aufgerufen, wobei der Parameter `callback` als Wert die Funktionsdefinition von `x` übergeben wird. In Zeile `11` erfolgt dann mithilfe von `callback();` eigentlich der Aufruf `x();`. 

Wir können aber auch z.B. `z(y);` aufrufen. Dann wird `z` nicht die Funktion `x`, sondern die Funktion `y` übergeben und der Aufruf `callback();` in Zeile `11` entspricht somit dem Aufruf `y();`. 

Ein großer Vorteil dieser *Callbacks*  bestehen darin, dass der Aufruf *asynchron* erfolgt. Schauen wir uns z.B. einmal an, wie die mögliche Ausgabe der Aufrufe 
```javascript
z(x);
z(y);
```
aussehen **könnte**:
```bash
Ausgabe der Funktion z - vor Aufruf von callback
Ausgabe der Funktion x
Ausgabe der Funktion z - vor Aufruf von callback
Ausgabe der Funktion z - vor Aufruf von callback
Ausgabe der Funktion y
Ausgabe der Funktion z - vor Aufruf von callback
```

Wichtig ist, dass *Callbacks* die aufrufende Funktion nicht blockieren, sondern *asynchron* ausgeführt werden. Dieses einfache Beispiel soll das demonstrieren:
```javascript linenums="1"
setTimeout( function() {
    console.log('Ausgabe A');
}, 3000);

console.log('Ausgabe B');
```
Wir haben zwei Anweisungen: eine `setTimeout()`-Anweisung und eine `console.log('Ausgabe B');`-Anweisung, die nacheinander aufgerufen werden (`setTimeout()` vor `console.log()`). Innerhalb der `setTimeout()`-Anweisung wird eine Funktion als *Callback* übergeben. Innerhalb dieser Funktion erfolgt der Aufruf von `console.log('Ausgabe A');`.

Das Ausführen des Programms ergibt folgende Ausgabe:
```bash
Ausgabe B
Ausgabe A
```

Die Ausgabe von `Ausgabe A` erfolgt ca. 3 Sekunden nach `Ausgabe B`. Das liegt daran, dass die *Callback*-Funktion asynchron ausgeführt wird und alle weiteren Ausführungen nicht blockiert. Das bedeutet, dass wir mithilfe von *Callbacks* eine asynchrone Ausführung unseres JavaScript-Codes erreichen. Der einzelne JavaScript-Thread wird also für den Aufruf der *Callbacks* verwendet und irgendwann sind diese *Callback*-Aufrufe beendet. Ein gegenseitiges Blockieren findet nicht statt, sondern es bleibt sogar noch Platz für weitere Aufrufe (hellgrüne Bereiche im folgenden Bild):

![thread](./files/29_thread.png)

Das problem mit diesen *Callback* ist, dass sie sehr schnell sehr unübersichtlich werden. Man spricht von der *Callback-Hölle*, in der man sehr schnell ist, sobald genügend viele *Callbacks* asynchron (nebenläufig) ausgeführt werden, diese sogar ineinander verschachtelt sind (*Callbacks* in *Callbacks*) und man gar nicht weiß, wann welche *Callbacks* beendet sind. Sobald man aber erst die Ausführung eines *Callbacks* abwarten **muss**, weil man die Resultate dieses *Callbacks* weiterverarbeiten möchte, entstehen wieder synchrone Aufrufe und der Vorteil der asynchronen Abarbeitung ist dahin. Um dieses Problem zu lösen, wurden *Promises* entwickelt. 

## Promises

Ein *Promise* ist zunächst einmal ein JavaScript-Objekt. Es enthält einerseits den Code zum Erzeugen eines *Promise*-Objektes (*producing code*) und anderseits auch den Code zum Verarbeiten eines solchen *Promise*-Objektes (*consuming code*). Dabei können zwei Sachen verarbeitet werden:

- entweder das `Promise`-Objekt wurde erfolgreich abgearbeitet (`resolve`) oder
- das `Promise`-Objekt wurde **nicht** erfolgreich abgearbeitet (`reject`). 

Die allgemeine Syntax eines solchen `Promise`-Objektes sieht so aus (siehe z.B. [w3scool](https://www.w3schools.com/js/js_promise.asp)):

```javascript linenums="1"
let myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise)
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);
```

Betrachten wir das obere Beispiel genauer:

- in Zeile `1` erstellen wir eine Variable `myPromise`, die wir natürlich nennen können, wie wir möchten
- diese Variable zeigt auf ein `Promise`-Objekt, das ebenfalls in Zeile `1` mithilfe von `new` und dem Aufruf des Konstruktors erzeugt wird
- einem `Promise`-Objekt (dem Konstruktor) wird immer eine Funktion übergeben, der wiederum zwei *Callback*-Funktionen als Parameter übergeben werden
- die erste *Callback*-Funktion, die hier `myResolve` heißt (aber meistens nur `resolve`), wird aufgerufen, wenn das `Promise`-Objekt erfolgreich abgearbeitet wurde (Zeile `4`)
- die zweite *Callback*-Funktion, die hier `myReject` heißt (aber meistens nur `reject`), wird aufgerufen, wenn das `Promise`-Objekt **nicht** erfolgreich abgearbeitet wurde (Zeile `5`)
- den Aufruf des `promise`-Objektes sehen wir in Zeile `9`. Ein `Promise`-Objekt durchläuft durch den Aufruf 2 der folgenden 3 Zustände:
	
	- `pending`: das `Promise`-Objekt wird abgearbeitet und hat noch kein Resultat (`undefined`),
	- `fulfilled`: das `Promise`-Objekt wurde erfolgreich abgearbeitet und liefert den entsprechenden Resultatwert zurück **oder**
	- `rejected`: das `Promise`-Objekt wurde nicht erfolgreich abgearbeitet und liefert ein `Error`-Objekt zurück

- es gibt aber keine Möglichkeiten, auf diese Zustände eines `Promise`-Objektes zuzugreifen und auch nicht direkt auf den Resultatwert oder das Fehlerobjekt; stattdessen muss eine entsprechende Funktion des `Promise`-Objektes aufgerufen werden, die selbst wieder ein `Promise`-Objekt zurückgibt, nämlich `then()`
- der Aufruf von `then()` ist ebenfalls in Zeile `9` gezeigt; diese Funktion hat zwei Parameter: dem ersten Parameter wird der Resultatwert übergeben (wenn das `Promise`-Objekt den `fulfilled`-Zustand erreicht hat) und dem zweiten Parameter wird das Fehlerobjekt übergeben (wenn das `Promise`-Objekt den `rejected`-Zustand erreicht hat). Beide Parameter sind wiederum *Callbacks*.

Wir werden sehen, dass wir den `rejected`-Zustand auch mit `catch()` abfangen können, aber dazu kommen wir später. Zunächst noch einmal zur Vertiefung unser obiges *Callback*-Beispiel mit `setTimeout()` als *Promise*:

```javascript linenums="1"
let promise = new Promise(function(resolve, reject) {
    setTimeout( function() {
        resolve('resolve -- Ausgabe A');
    }, 3000);
});

promise.then(
    function(value) {
        console.log(value);
    }
    // (noch) keine Funktion für error
);

console.log('Ausgabe B');
```

Die Ausgabe in Zeile `14` hat nichts mit dem `Promise` zu tun, aber wir lassen sie mal im Code, um das gleiche Beispiel wie oben zu haben. Es erfolgt zunächst die Ausgabe `Ausgabe B` auf der Konsole und 3 Sekunden später die Ausgabe `resolve -- Ausgabe A`. Rein funktional hat sich also nichts geändert. Wie Sie den Parameter für den `resolve`-Fall (und dann auch für den `reject`-Fall) nennen, bleibt ganz Ihnen überlassen; hier `value` (Zeile `8`).

Dieses Mal heißt unser `Promise`-Objekt `promise` und die beiden *Callback* -Funktionen `resolve` und `reject` (Zeile `1`). Der *producing code*  enthält nur die Implementierung von `resolve`. In dem Beispiel gibt es also (noch) kein `reject`. In den Zeilen `7`-`12` sehen wir den *consuming code* der *Promise*, auch hier wieder nur für `resolve`. Es erfolgt die Ausgabe des Wertes, den `resolve` übergeben hat. 

### Promises in Arrow-Notation

Weil wir es mitlerweile häufig sehen und weil wir uns auch angewöhnen wollen, diese selbst zu benutzen, hier das gleiche Beispiel nochmal in [Arrow-Notation](../serviceworker/#arrow-notation-verwenden):

```javascript linenums="1"
let promise = new Promise((resolve, reject) => {
    setTimeout( () => {
        resolve('resolve -- Ausgabe A');
    }, 3000);
});

promise.then(
    value => {
        console.log(value);
    }
    // (noch) keine Funktion für error
);

console.log('Ausgabe B');
```

Es ist auch noch zu erwähnen, dass Sie nur selten selbst *Promises* erstellen, sondern diese viel häufiger nutzen werden. Das heißt, Sie werden nicht so häufig *producing code*, sondern viel häufiger *consuming code* schreiben. Beispielsweise gibt die [Registrierung](../serviceworker/#registrierung-eines-service-workers) eines *service workers* ein *Promise* zurück:

```javascript linenums="1"
// scope defaults to the path the script sits in
// "/" in this example
navigator.serviceWorker.register("/serviceworker.js").then(registration => {
  console.log("success!");
  if (registration.installing) {
    registration.installing.postMessage("Howdy from your installing page.");
  }
}, err => {
  console.error("Installing the worker failed!", err);
});
```

Ein großer Vorteil von *Promises* ist, dass Sie die Verarbeitung *verketten* können. Die `then()`-Funktion liefert selbst wieder ein `Promise` zurück, so dass Sie erneut dieses `Promise` mit `then()` behandeln können. Wir kommen darauf in den Anwendungen nochmal zurück. 

### Der `reject`-Fall

Wir schauen uns jetzt an, wie wir den Fall am besten behandeln, wenn das `Promise` nicht in den `fulfilled`, sondern in den `rejected`-Zustand übergeht, wenn also nicht `resolve`, sondern `reject` ausgeführt wird. Wir ändern unser Beispiel einmal entsprechend:

```javascript linenums="1" hl_lines="3 4"
let promise = new Promise((resolve, reject) => {
    setTimeout( () => {
        // resolve('resolve -- Ausgabe A');
        reject({code: 500, message: 'An error occurred'});
    }, 3000);
});

promise.then(
    value => {
        console.log(value);
    }
    // (noch) keine Funktion für error
);

console.log('Ausgabe B');
```

Wir haben also Zeile `3` auskommentiert (`resolve`) und stattdessen `reject` eingefügt (Zeile `4`). Im Gegensatz zu `resolve` geben wir jetzt mal keinen einfachen `string`, sondern ein JavaScript-Objekt zurück (erkennbar an `{ }`). Wir sind darin völlig frei, was zurückgegeben wird, aber es bietet sich an, ein Error-Objekt zu erzeugen. Die `then()`-Behandlung des `Promise`-Objekt lassen wir zunächst unverändert (Zeilen `8-13`). 

Wenn wir diesen Code ausführen, dann wird erneut `Ausgabe B` ausgegeben (Zeile `15` - hat nichts mit dem `Promise` zu tun), aber nach 3 Sekunden erfolgt keine Ausgabe auf der Konsole, sondern stattdessen erscheint auf der Konsole:
![promise](./files/30_promise.png)

#### Error-Behandlung in der `then()`-Funktion

Wir behandeln den geworfenen Fehler nicht, da wir in unserer `then()`-Behandlung bis jetzt nur den `resolve`-Fall behandeln (Zeilen `9-11`). Das ändern wir nun:

```javascript linenums="1" hl_lines="12-14"
let promise = new Promise((resolve, reject) => {
    setTimeout( () => {
        // resolve('resolve -- Ausgabe A');
        reject({code: 500, message: 'An error occurred'});
    }, 3000);
});

promise.then(
    value => {
        console.log(value);
    },
    err => {
        console.log(err.code, err.message);
    }
);

console.log('Ausgabe B');
```

In den Zeilen `12-14` wurde die Behandlung des Fehlerfalls hinzugefügt (beachten Sie auch das zusätzliche Komma in Zeile `11`). Wie Sie die Variable `err` nennen, bleibt Ihnen überlassen. Sie bekommt den Wert, den das `Promise` für den `reject`-Fall übergibt, in unserem Beispiel also ein JavaScript-Objekt:

```json
{
	code: 500, 
	message: 'An error occurred'
}
```

weil wir das in Zeile `4` so definiert haben. Wir greifen also auf die Werte der Schlüssel `code` und `message` zu und lassen diese auf die Konsole ausgeben (Zeile `13`). Auf der Konsole erscheint 3 Sekunden nach der Ausgabe `Ausgabe B` die Ausgabe `500 An error occurred`. 

#### Error-Behandlung im `catch()`-Block

Es ist ungewöhnlich, den Fehlerfall in der `then()`-Funktion zu behandeln, obwohl es, wie wir gesehen haben, möglich ist. Stattdessen verwendet man für den Fehlerfall besser `catch()`:

```javascript linenums="1" hl_lines="14-18"
let promise = new Promise((resolve, reject) => {
    setTimeout( () => {
        // resolve('resolve -- Ausgabe A');
        reject({code: 500, message: 'An error occurred'});
    }, 3000);
});

promise
    .then(
        value => {
            console.log(value);
        }
    )
    .catch(
        err => {
            console.log(err.code, err.message);
        }
    );

console.log('Ausgabe B');
```

### async/await

Die Verkettung von `.then()`-Pfaden kann zu unübersichtlichem Code führen. Deshalb wurden die Schlüsselwörter `async` und `await` eingeführt (siehe z.B. [hier](https://javascript.info/async-await), [hier](https://www.mediaevent.de/javascript/async-await.html), [hier](https://www.w3schools.com/js/js_async.asp) oder [hier](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)).

Wir betrachten ein Beispiel, das wir zunächst mit `.then()`-Verkettung anwenden und danach mit `async/await`. gegeben sind die beiden folgenden JavaScript-Funktionen:

```js
function makeRequest(file) {
    return new Promise( (resolve, reject) => {
        console.log('making request for ' + file);
        if(file == 'index.html') {
            resolve('index.html exists')
        } else {
            reject(file + ' does not exist')
        }
    });
}

function processRequest(response) {
    return new Promise( (resolve, request) => {
        console.log('processing response');
        resolve('processing done for ' + response)
    })
}
```

Die Anwendung dieser Funktionen könnte wie folgt aussehen: 

```js
makeRequest('index.html')               // resolve-Fall
.then( response => {
    console.log('response received');
    console.log(response)
    return processRequest(response)
})
.then( processedResponse => {
    console.log(processedResponse)
})
.catch( error => console.log(error))
```

erzeugt folgende Ausgabe:

```bash
making request for index.html
response received
index.html exists
processing response
processing done for index.html exists
```

bzw., wenn der übergebene Dateiname nicht `index.html` entspricht:


```js
makeRequest('index1.html')               // jectect-Fall
.then( response => {
    console.log('response received');
    console.log(response)
    return processRequest(response)
})
.then( processedResponse => {
    console.log(processedResponse)
})
.catch( error => console.log(error))
```

erzeugt folgende Ausgabe:

```bash
making request for index1.html
index1.html does not exist
```

Dem Aufruf von `makeRequest()` (und auch dem von `processRequest()`) könnten wir jedoch auch das Schlüsselwort `await` voranstellen. Dabei ist jedoch zu beachten, dass Aufrufe von `await` nur in als `async` deklarierten Funktionen erfolgen kann. Wir bauen deshalb obige Aufrufe in einer JavaScript-Funktion nach:

```js
async function testPromises() {
    try {
        let response = await makeRequest('index1.html');        // reject-Fall
        console.log('response received');
        let processedResponse = await processRequest(response);
        console.log(processedResponse);
    } catch(error) {
        console.log(error)
    }
}
```

bzw. 

```js
async function testPromises() {
    try {
        let response = await makeRequest('index.html');        // resolve-Fall
        console.log('response received');
        let processedResponse = await processRequest(response);
        console.log(processedResponse);
    } catch(error) {
        console.log(error)
    }
}
```

Dies erzeugt jeweils die gleichen Ausgaben wie oben gezeigt. 



