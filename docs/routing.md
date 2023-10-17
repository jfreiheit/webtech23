# Routing und Services


## Single- vs. Multi-Page-Applikationen

Wenn wir durch z.B. dieses Skript hangeln oder Wikipedia, dann stellen wir fest, dass sich nach jedem Klick auf einen Link eine neue HTML-Seite öffnet. Das wird insbesondere deutlich wenn die Entwicklungstools geöffnet sind. Jeder Klick auf einen Hyperlink erwirkt eine neue Anfrage an einen Webserver mit dem Request, eine neue HTML-Seite von diesem Webserver zu laden und im Browser zu öffnen. Es handelt sich dabei also um eine Webanwendung mit vielen (Unter-)Seiten, eine sogenannte *Multi-Page-Applikation (MPA)*. 

Wenn wir stattdessen z.B. die Angular-Seite `https://angular.io` öffnen und uns die Developertools anschauen, dann stellen wir fest, dass kaum HTML-Code im `<body>`-Element enthalten ist. Stattdessen wird der gesamte HTML-Code per JavaScript im Browser eingebunden. Damit werden Inhalte in die Seite immer genau dann eingebunden, wenn sie angezeigt werden sollen. Um zwischen einzelnen Ansichten der Webanwendung zu wechseln, wird keine neue Webseite vom Webserver geholt. Stattdessen bleiben wir stets in derselben HTML-Seite (*Single-Page-Applikation (SPA)*), was sehr gut sichtbar wird, wenn wir die Developertools eingeschaltet lassen und innerhalb der Webanwendung umhernavigieren. Stattdessen werden nur Inhalte (über eine REST-API) vom Server geladen. 

Das Hyperlink-Konzept bei Single-Page-Applikationen ist also ein anderes, als bei Multi-Page-Applikationen. Während in MPAs Hyperlinks verwendet werden, sprechen wir bei SPAs von *Routen*. Das dazugehörige Konzept heißt *Routing*. 

## Aktivieren von Routing

Die einfachste Methode, das Routing für ein Angular-Projekt zu aktivieren, besteht darin, das Projekt mithilfe von 

```bash
ng new projektName
```

zu erzeugen und auf die Frage:

```bash
? Would you like to add Angular routing? (y/N)
```

durch die Eingabe eines `y` zu antworten. Sie müssen explizit `y` eingeben, da die Standardantwort `N`, also `no` ist. Wenn Sie die Frage mit `yes` beantwortet haben, dann wird das neue Projekt mit der Datei `app-routing.module.ts` im Ordner `src/app` erzeugt. Sollte Ihnen diese Datei fehlen, dann können Sie nachträglich das Routing zu einem existierenden Projekt hinzufügen. 

Sie können gleich bei Erstellung des Projektes angeben, dass Routing erwünscht ist, indem Sie 

```bash
ng new projektName --routing
```

eingeben. Dann werden Sie gar nicht mehr nach Routing gefragt, sondern dieses wird sofort mitinstalliert. 

Sollten Sie keine Datei `app-routing.module.ts` im `src/app`-Ordner haben, dann können Sie das Routing auch noch nachträgöich aktivieren, indem Sie in Ihrem Projektordner

```bash
ng generate module app-routing --flat --module=app
```

ausführen. Dann entsteht eine solche Datei und das `AppRoutingModule` wird in der `app.module.ts` importiert: 

=== "app.module.ts"
	```js linenums="1" hl_lines="5 13"
	import { NgModule } from '@angular/core';
	import { BrowserModule } from '@angular/platform-browser';

	import { AppComponent } from './app.component';
	import { AppRoutingModule } from './app-routing.module';

	@NgModule({
	  declarations: [
	    AppComponent
	  ],
	  imports: [
	    BrowserModule,
	    AppRoutingModule
	  ],
	  providers: [],
	  bootstrap: [AppComponent]
	})
	export class AppModule { }
	```	

Die Datei `app-routing.module.ts` sieht zunächst so aus (wenn Routing über die CLI mit dem Befehl `ng generate module app-routing --flat --module=app` aktiviert wurde):

=== "app-routing.module.ts"
	```js linenums="1"
	import { NgModule } from '@angular/core';
	import { CommonModule } from '@angular/common';

	@NgModule({
	  declarations: [],
	  imports: [
	    CommonModule
	  ]
	})
	export class AppRoutingModule { }
	```

Wir passen diese Datei zunächst wie folgt an:

=== "app-routing.module.ts"
	```js linenums="1" hl_lines="2 4 9 11-12"
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';

	const routes: Routes = [];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }

	```

In das `routes`-Array werden wir im Folgenden unsere Routen eintragen. 

## Erste einfache Routen

Um das Routing auszuprobieren, benötigen wir zunächst ein paar Komponenten, zwischen denen wir wechseln können. Deshalb erstellen wir uns folgende Komponenten:

```bash
ng g c nav
ng g c home
ng g c login
ng g c about
ng g c footer
```

Außerdem fügen wir unserem Projekt noch Bootstrap hinzu, damit wir ein besseres Design erzielen (hat aber nichts mit Routing zu tun):

```bash
ng add @ng-bootstrap/ng-bootstrap
```

Sollten Sie beim Hinzufügen von Bootstrap einen `not compatible`-Fehler bekommen, dann versuchen Sie `npm install @ng-bootstrap/ng-bootstrap@bootstrap5`. Nach dem Hinzufügen von Bootstrap sollten Sie nochmals `npm install` ausführen, um das Bootstrap-Modul auch tatsächlich zu installieren. 

Die Komponenten können Sie wie folgt implementieren: 


=== "nav.component.html"
	```html linenums="1"
	<nav class="sticky-top navbar navbar-expand-lg navbar-light bg-light">
	    <div class="container-fluid">
	        <a class="navbar-brand" href="#">Webtech</a>
	        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
	      <span class="navbar-toggler-icon"></span>
	    </button>
	        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
	            <div class="navbar-nav">
	                <a class="nav-link" href="#">Home</a>
	                <a class="nav-link" href="#">Login</a>
	                <a class="nav-link" href="#">About</a>
	            </div>
	        </div>
	    </div>
	</nav>
	```

=== "footer.component.html"
	```html linenums="1"
	<div class="fixed-bottom text-white-50 bg-dark p-3 text-center">
		Routing
	</div>
	```

=== "home.component.html"
	```html linenums="1"
	<main class="d-flex align-items-center min-vh-100">
	    <div class="container text-center">
	        Welcome home!
	    </div>
	</main>
	```

=== "home.component.css"
	```css linenums="1"
	main {
	    background-color: grey;
	}
	```

=== "about.component.html"
	```html linenums="1"
	<main class="d-flex align-items-center min-vh-100">
	    <div class="container text-center">
	        Everything about me...
	    </div>
	</main>
	```

=== "about.component.css"
	```css linenums="1"
	main {
	    background-color: rgb(95, 4, 4);
	    color: lightgrey;
	}
	```

=== "login.component.html"
	```html linenums="1"
	<main class="d-flex align-items-center min-vh-100">
	    <fieldset class="container col-4 col-offset-4">
	        <legend>Login</legend>
	        <form>
	            <div class="form-group">
	                <input type="text" class="form-control" id="login1" placeholder="username">
	            </div>
	            <div class="form-group">
	                <input type="password" class="form-control" id="login2" placeholder="password">
	            </div>
	            <button type="submit" class="btn btn-secondary">Login</button>
	        </form>
	    </fieldset>
	</main>
	```

=== "login.component.css"
	```css linenums="1"
	main {
	    background-color: rgb(164, 201, 243);
	}
	```

Die `app.component.html` sieht nun wie folgt aus:

=== "app.component.html"
	```html linenums="1"
	<app-nav></app-nav>
	<router-outlet></router-outlet>
	<app-footer></app-footer>
	```

Diese ist so gestaltet, dass oben die `nav`-Komponente und unten die `footer`-Komponente  eingebunden wird. Dazwischen steht jedoch der Komponentenselektor `<router-outlet></router-outlet>`. An dessen Stelle wird nun jeweils die Komponente eingesetzt, die wir durch das Routing ausgewählt haben. Dies erledigen wir in den folgenden beiden Schritten.

### Routen definieren 

Zunächst definieren wir die Routen und zu jeder Route, welche Komponente dafür eingebunden wird. Die Routendefinitionen erfolgen in der `app-routing.module.ts` und dort im `routes`-Array. Dazu wird das `routes`-Array mit Objekten befüllt, die jeweils einen `path`-Eintrag und einen `component`-Eintrag erhalten. Ein solches Objekt legt fest, für welchen Pfad welche Komponente aufgerufen wird. 

=== "app-routing.module.ts"
	```js linenums="1" hl_lines="1-3 8-19"
	import { HomeComponent } from './home/home.component';
	import { LoginComponent } from './login/login.component';
	import { AboutComponent } from './about/about.component';
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';

	const routes: Routes = [
	  {
	    path: "about",
	    component: AboutComponent
	  },
	  {
	    path: "login",
	    component: LoginComponent
	  },
	  {
	    path: "home",
	    component: HomeComponent
	  }
	];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }
	```

Testen Sie nun die URLs

```bash
http://localhost:4200/about
http://localhost:4200/home
http://localhost:4200/login
```

und Sie sehen jeweils, dass die für die jeweilige Route angegebene Komponente eingebunden wird. Der `<router-outlet></router-outlet>`-Selektor wird also dynamisch befüllt, je nachdem welche Route aufgerufen wird. 

Eine Sache ist jetzt jedoch ncoh nicht optimal. Erstens ist ganz am Anfang, also für `http://localhost:4200` gar keine Komponente eingebunden und zweitens soll unsere `home`-Komponente gar nicht unter einer extra Route (`http://localhost:4200/home`), sondern tatsächlich bereits unter `http://localhost:4200`  aufgerufen werden. Wir passen deshalb das `routes`-Array entsprechend an:

=== "app-routing.module.ts"
	```js linenums="1" hl_lines="17"
	import { HomeComponent } from './home/home.component';
	import { LoginComponent } from './login/login.component';
	import { AboutComponent } from './about/about.component';
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';

	const routes: Routes = [
	  {
	    path: "",
	    component: HomeComponent,
	    pathMatch: 'full'
	  },
	  {
	    path: "about",
	    component: AboutComponent
	  },
	  {
	    path: "login",
	    component: LoginComponent
	  }
	];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }
	```


Die neuhinzugefügte Eigenschaft `pathMatch: 'full'` gibt an, dass diese Route nur aufgerufen wird, wenn danach nichts weiter in der URL folgt. Die Auswahl der Routen erfolgt nach dem *first-match-Prinzip*. Das heißt, dass für die angegebene URL die erste Route ausgewählt wird, die "passt". Mit `pathMatch: 'full'` geben wir an, dass die Route zwar passen muss, aber nicht nur ein Präfix einer längeren Route sein darf. Nun funktionieren die Routen wie gewünscht:

```bash
http://localhost:4200
http://localhost:4200/about
http://localhost:4200/login
```

Für die erste URL wird die `home`-Komponente eingebunden, bei der zweiten die `about`-Komponente und bei der dritten die `login`-Komponente. Nun müssen wir noch organisieren, wie die Routen innerhalb unserer Anwendung aufgerufen werden können (und nicht nur durch Eingabe der jeweiligen URL).

### Routen aufrufen

Wir wollen die Routen durch Mausklick aufrufen. Dafür bietet sich unser Navigationsmenü an. Routen werden **nicht** per `href`-Attribut aufgerufen, sondern per `routerLink`. Wir passen dazu unsere `nav`-Komponente an:


=== "nav.component.html"
	```html linenums="1" hl_lines="3 9-11"
	<nav class="sticky-top navbar navbar-expand-lg navbar-light bg-light">
	    <div class="container-fluid">
	        <a class="navbar-brand" routerLink="">Webtech</a>
	        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
	      <span class="navbar-toggler-icon"></span>
	    </button>
	        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
	            <div class="navbar-nav">
	                <a class="nav-link" routerLink="">Home</a>
	                <a class="nav-link" routerLink="login">Login</a>
	                <a class="nav-link" routerLink="about">About</a>
	            </div>
	        </div>
	    </div>
	</nav>
	```

Wir können das `routerLink`-Attribut auch unter Verwendung von [Property Binding](../angular2/#property-bindings) festlegen (dann kann Routing später sogar über Variablen erfolgen). Wenn Sie beim *Property Binding* den Wert als `String` festlegeen, dann muss dieser `String` in eigenen Hochkomma in den Wert des *Property Binding* geschrieben werden, also z.B. so:

```js
[routerLink]="'login'"
[routerLink]="'about'"
[routerLink]="''"
```

Angenommen, Sie definieren sich noch eine eigene CSS-Klasse, in der sie festlegen, dass die Menüeinträge anders aussehen, wenn sie der aktuellen Route entsprechen, wenn also z.B. `Login` im Menü fett erscheint, sobald `http://localhost:4200/login` ausgewählt wurde. Die CSS-Definition könnte dann so aussehen:

```css
.myactive {
    font-weight: bold;
}
```

Das heißt, Sie haben eine CSS-Klasse `myactive` definiert. Diese Klasse kann aktiviert werden, wenn die Route aktiv ist. Dazu verwenden Sie das Attribut `routerLinkActive` und weisen diesem Attribut den Wert `"myactive"` zu. Das Menü sähe dann so aus:

```html linenums="7"
<div class="collapse navbar-collapse" id="navbarNavAltMarkup">
    <div class="navbar-nav">
        <a class="nav-link" [routerLink]="''" routerLinkActive="myactive">Home</a>
        <a class="nav-link" [routerLink]="'login'" routerLinkActive="myactive">Login</a>
        <a class="nav-link" [routerLink]="'about'" routerLinkActive="myactive">About</a>
    </div>
</div>
```	

Wenn Sie Bootstrap verwenden, dann ist `routerLinkActive` nur für eigene CSS-Klassen notwendig (so wie im Beispiel `myactive`). Die Bootstrap-Klasse `active` wird automatisch aktiviert, wenn die Route aktiv ist. 

### Routenparameter

Häufig sollen aus einer Liste von Objekten ein einzelnes Objekt ausgewählt und dargestellt werden. Angenommen, wir wollen erneut die `staedte.json` aus [JSON und Direktiven](../angular2/#json-und-direktiven) verwenden. Wir einfachen es diesmal ein wenig und verwenden direkt das Array und beschreiben die JavaScript-Objekte nicht in JSON, sondern direkt als Objekte (der Unterschied besteht darin, dass die Schlüssel nicht in Anführungsstrichen stehen).


??? "staedte als Array"
    ```json
    [
    	{
            id: 1,
            jahr: 1237,
            stadt: "Berlin",
            link: "http://de.wikipedia.org/wiki/Berlin",
            bild: "assets/images/berlin.png"
        },
        {
            id: 2,
            jahr: 1624,
            stadt: "New York",
            link: "http://de.wikipedia.org/wiki/New_York_City",
            bild: "assets/images/newyork.png"
        },
        {
            id: 3,
            jahr: 1252,
            stadt: "Stockholm",
            link: "http://de.wikipedia.org/wiki/Stockholm",
            bild: "assets/images/stockholm.png"
        },
        {
            id: 4,
            jahr: 1827,
            stadt: "Bremerhaven",
            link: "http://de.wikipedia.org/wiki/Bremerhaven",
            bild: "assets/images/bremerhaven.png"
        },
        {
            id: 5,
            jahr: 150,
            stadt: "Bremen",
            link: "http://de.wikipedia.org/wiki/Bremen",
            bild: "assets/images/bremen.png"
        },
        {
            id: 6,
            jahr: 1202,
            stadt: "Bernau",
            link: "http://de.wikipedia.org/wiki/Bernau_bei_Berlin",
            bild: "assets/images/bernau.png"
        },
        {
            id: 7,
            jahr: 929,
            stadt: "Brandenburg",
            link: "http://de.wikipedia.org/wiki/Brandenburg_an_der_Havel",
            bild: "assets/images/brandenburg.png"
        },
        {
            id: 8,
            jahr: 805,
            stadt: "Magdeburg",
            link: "http://de.wikipedia.org/wiki/Magdeburg",
            bild: "assets/images/magdeburg.png"
        },
        {
            id: 9,
            jahr: 1222,
            stadt: "Marburg",
            link: "http://de.wikipedia.org/wiki/Marburg",
            bild: "assets/images/marburg.png"
        },
        {
            id: 10,
            jahr: 766,
            stadt: "Mannheim",
            link: "http://de.wikipedia.org/wiki/Mannheim",
            bild: "assets/images/mannheim.png"
        },
        {
            id: 11,
            jahr: 782,
            stadt: "Mainz",
            link: "http://de.wikipedia.org/wiki/Mainz",
            bild: "assets/images/mainz.png"
        }
    ]
    ``` 

sowie den Ordner [images](./files/images_staedte.zip) und greifen über die Route auf ein einzelnes Objekt zu. Wenn wir also z.B. `http://localhost:4200/cities/0` eingeben, soll das `Berlin`-Objekt ausgewählt werden, bei `http://localhost:4200/cities/1` das `New York`-Objekt usw. 

Dazu erstellen wir uns zunächst eine neue Componente `cities` mit `ng g c cities` und folgendem Code:


=== "cities.component.html"
	```html linenums="1"
	<div class="container">
	    <h1>Städte</h1>


	    <table class="table table-striped">
	        <caption>Ausgewählte Städte</caption>
	        <thead>
	            <tr>
	                <th scope="col">Nr</th>
	                <th scope="col">Jahr</th>
	                <th scope="col">Stadt</th>
	                <th scope="col">Bild</th>
	            </tr>
	        </thead>
	        <tbody>
	            <tr *ngFor=" let stadt of staedte; let i=index ">
	                <td>{{ i+1 }} </td>
	                <td>{{ stadt.jahr }}</td>
	                <td>{{ stadt.stadt }}</td>
	                <td>
	                    <a [href]="stadt.link">
	                        <img [src]=" stadt.bild " [alt]="stadt.stadt " />
	                    </a>
	                </td>
	            </tr>
	        </tbody>
	    </table>
	</div>
	```

=== "cities.component.ts"
	```js linenums="1"
	import { Component, OnInit } from '@angular/core';

	@Component({
	  selector: 'app-cities',
	  templateUrl: './cities.component.html',
	  styleUrls: ['./cities.component.css']
	})
	export class CitiesComponent implements OnInit {
	    staedte = [
				    {
				      jahr: 1237,
				      stadt: "Berlin",
				      link: "http://de.wikipedia.org/wiki/Berlin",
				      bild: "assets/images/berlin.png"
				    },
				    {
				      jahr: 1624,
				      stadt: "New York",
				      link: "http://de.wikipedia.org/wiki/New_York_City",
				      bild: "assets/images/newyork.png"
				    },
				    {
				      jahr: 1252,
				      stadt: "Stockholm",
				      link: "http://de.wikipedia.org/wiki/Stockholm",
				      bild: "assets/images/stockholm.png"
				    },
				    {
				      jahr: 1827,
				      stadt: "Bremerhaven",
				      link: "http://de.wikipedia.org/wiki/Bremerhaven",
				      bild: "assets/images/bremerhaven.png"
				    },
				    {
				      jahr: 150,
				      stadt: "Bremen",
				      link: "http://de.wikipedia.org/wiki/Bremen",
				      bild: "assets/images/bremen.png"
				    },
				    {
				      jahr: 1202,
				      stadt: "Bernau",
				      link: "http://de.wikipedia.org/wiki/Bernau_bei_Berlin",
				      bild: "assets/images/bernau.png"
				    },
				    {
				      jahr: 929,
				      stadt: "Brandenburg",
				      link: "http://de.wikipedia.org/wiki/Brandenburg_an_der_Havel",
				      bild: "assets/images/brandenburg.png"
				    },
				    {
				      jahr: 805,
				      stadt: "Magdeburg",
				      link: "http://de.wikipedia.org/wiki/Magdeburg",
				      bild: "assets/images/magdeburg.png"
				    },
				    {
				      jahr: 1222,
				      stadt: "Marburg",
				      link: "http://de.wikipedia.org/wiki/Marburg",
				      bild: "assets/images/marburg.png"
				    },
				    {
				      jahr: 766,
				      stadt: "Mannheim",
				      link: "http://de.wikipedia.org/wiki/Mannheim",
				      bild: "assets/images/mannheim.png"
				    },
				    {
				      jahr: 782,
				      stadt: "Mainz",
				      link: "http://de.wikipedia.org/wiki/Mainz",
				      bild: "assets/images/mainz.png"
				    }
				  ];

	  constructor() { }

	  ngOnInit(): void {
	  }

	}

	```

=== "cities.component.css"
	```css linenums="1"
	td img {
	    width: 10%;
	}
	```

=== "app-routing.module.ts"
	```js linenums="1"
	import { HomeComponent } from './home/home.component';
	import { LoginComponent } from './login/login.component';
	import { AboutComponent } from './about/about.component';
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';
	import { CitiesComponent } from './cities/cities.component';

	const routes: Routes = [
	  {
	    path: "",
	    component: HomeComponent,
	    pathMatch: 'full'
	  },
	  {
	    path: "about",
	    component: AboutComponent
	  },
	  {
	    path: "login",
	    component: LoginComponent
	  },
	  {
	    path: "cities",
	    component: CitiesComponent
	  }
	];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }

	```


Zunächst lagern wir die Daten in einen *Service* aus.

## Services

Ein *Service* ist eine Klasse für einen konkreten Zweck. Services unterscheiden sich von Komponenten dahingehend, dass

- eine Komponente für die Nutzerinteraktion zuständig ist, 
- eine Komponente Eigenschaften (Daten) präsentiert, 
- eine Komponente Methoden zur Datenbindung (*data binding*) zur Verfügung stellt, um
- zwischen *View* und Anwendungslogik zu vermitteln.

Ein Service

- erfüllt eine konkrete Aufgabe, typischerweise mit Daten, 
- ohne sich um die Darstellung der Daten zu kümmern.
- Typische Aufgaben eines Services sind: Daten vom Server holen oder auf den Server laden, Nutzereingaben zu validieren. 
- Ein Service steht typischerweise allen Komponenten zur Verfügung (aber nicht jede Komponente muss einen Service nutzen).

Ein Service ist eine Klasse mit dem Decorator `@Injectable()`. Services enthalten Anwendungslogik, die aus Komponenten ausgelagert werden kann. Ein Service kann mittels CLI so erzeugt werden:

```
ng generate service nameDesServices
```

In dem Decorator `@Injectable()` wird mittels `providedIn: root` angegeben, dass der Service von allen Komponenten innerhalb des Root-Moduls genutzt werden kann. Ist der Service von anderen Services oder Komponenten abhängig, können diese Services oder Komponenten mittels *dependency injection* als Parameter des Service-Konstruktor eingebunden werden. Hier ein allgemeines Beispiel eines Services `MyService`:

=== "my.service.ts"
    ```javascript linenums="1"
    import { Injectable } from '@angular/core';

    @Injectable({
      providedIn: 'root'
    })
    export class MyService {

      constructor(private myDependency: MyDependency) {
      }
    }
    ```

Der Service kann dann mittels *dependency injection* von einer Komponente verwendet werden. Beispiel:

=== "example.component.ts"
    ```javascript
    import {Component, OnInit} from '@angular/core';

    import {MyService} from './shared/my.service';

    @Component({
      selector: 'app-example',
      templateUrl: './example.component.html',
      styleUrls: ['./example.component.css']
    })
    export class ExampleComponent implements OnInit {

      constructor(private myService: MyService) { }

      ngOnInit(): void {
        this.example.methodOfMyService();
      }

    }
    ```

Für weiterführende Informationen siehe [https://angular.io/guide/architecture-services](https://angular.io/guide/architecture-services).

### Service für das Routing-Beispiel

Für unser Routing-Beispiel wollen wir Daten über einen Service allen Komponenten zur Verfügung stellen. Wir erstellen dazu einen Service `data` und dazu auch noch ein *Interface* `data`, das das Datenmodell für eine `Stadt` beschreibt. Beides erstellenb wir in einem `shared`-Ordner.

Mit 

```bash
ng g service shared/data
```

lassen wir die CLI den Service erstellen. Im Ordner `shared` entstehen zwei Dateien:

- `data.service.ts` und 
- `data.service.spec.ts`.

Letztere ist für Testzwecke und interessiert uns (derzeit noch) nicht. In diesen Service binden wir gleich unsere Daten ein und stellen eine Funktion zur Verfügung, die uns alle Daten nach außen zur Verfügung stellt. Zunächst erstellen wir noch, zur Gewährleistung der Typsicherheit, ein *Interface* für das Datenmodell:

```bash
ng g interface shared/data
```

Es entsteht eine Datei `data.ts` mit folgendem Inhalt:

=== "shared/data.ts"
	```js
	export interface Data {
	}
	```

In dieses Interface tragen wir unser Datenmodell ein (wir erweitern unsere Daten um eine `id`, um diese nicht "berechnen" zu müssen):

=== "shared/data.ts"
	```js
	export interface Data {
		id: number;
	  	jahr: number;
	  	stadt: string;
	  	link: string;
	  	bild: string;
	}
	```

Dem `data`-Service fügen wir nun das `staedte`-Array zu und importieren das Interface `Data`:

=== "shared/data.service.ts"
	```js 
	import { Injectable } from '@angular/core';
	import { Data } from './data';

	@Injectable({
	  providedIn: 'root'
	})
	export class DataService {
	  data: Data[];

	  constructor() {
	    this.data = [
	      {
	          id: 1,
	          jahr: 1237,
	          stadt: "Berlin",
	          link: "http://de.wikipedia.org/wiki/Berlin",
	          bild: "assets/images/berlin.png"
	      },
	      {
	          id: 2,
	          jahr: 1624,
	          stadt: "New York",
	          link: "http://de.wikipedia.org/wiki/New_York_City",
	          bild: "assets/images/newyork.png"
	      },
	      {
	          id: 3,
	          jahr: 1252,
	          stadt: "Stockholm",
	          link: "http://de.wikipedia.org/wiki/Stockholm",
	          bild: "assets/images/stockholm.png"
	      },
	      {
	          id: 4,
	          jahr: 1827,
	          stadt: "Bremerhaven",
	          link: "http://de.wikipedia.org/wiki/Bremerhaven",
	          bild: "assets/images/bremerhaven.png"
	      },
	      {
	          id: 5,
	          jahr: 150,
	          stadt: "Bremen",
	          link: "http://de.wikipedia.org/wiki/Bremen",
	          bild: "assets/images/bremen.png"
	      },
	      {
	          id: 6,
	          jahr: 1202,
	          stadt: "Bernau",
	          link: "http://de.wikipedia.org/wiki/Bernau_bei_Berlin",
	          bild: "assets/images/bernau.png"
	      },
	      {
	          id: 7,
	          jahr: 929,
	          stadt: "Brandenburg",
	          link: "http://de.wikipedia.org/wiki/Brandenburg_an_der_Havel",
	          bild: "assets/images/brandenburg.png"
	      },
	      {
	          id: 8,
	          jahr: 805,
	          stadt: "Magdeburg",
	          link: "http://de.wikipedia.org/wiki/Magdeburg",
	          bild: "assets/images/magdeburg.png"
	      },
	      {
	          id: 9,
	          jahr: 1222,
	          stadt: "Marburg",
	          link: "http://de.wikipedia.org/wiki/Marburg",
	          bild: "assets/images/marburg.png"
	      },
	      {
	          id: 10,
	          jahr: 766,
	          stadt: "Mannheim",
	          link: "http://de.wikipedia.org/wiki/Mannheim",
	          bild: "assets/images/mannheim.png"
	      },
	      {
	          id: 11,
	          jahr: 782,
	          stadt: "Mainz",
	          link: "http://de.wikipedia.org/wiki/Mainz",
	          bild: "assets/images/mainz.png"
	      }
	    ];
	   }

	   	getAll(): Data[] {
		    return this.data;
		}
	}

	```


Angenommen, die Datei `staedte.json` liegt im `assets`-Ordner, dann können Sie die Datei auch wie folgt einlesen (anstatt die Daten in den Service zu kopieren):

```js
async getAll(): Promise<Data[]> {
    let response = await fetch('./assets/staedte.json');
    let staedteObj = await response.json();

    return staedteObj.staedte;
  }
```

Beachten Sie, dass Sie dann eine `Promise` zurückgeben, d.h. den Aufruf von `getAll()` können Sie dann wieder `then()`-verketten (oder `await/async` verwenden). 


### Verwendung des Services

Wir zeigen die Verwendung des Services zunächst am Beispiel der `cities`-Komponente. Dort hatten wir bisher die Daten direkt gespeichert. Nun sollen sie dort über den Service eingebunden werden. Dazu ändern wir die `cities.component.ts` wie folgt:

=== "cities.component.ts"
	```js linenums="1" hl_lines="3 11 13-15"
	import { DataService } from './../shared/data.service';
	import { Component, OnInit } from '@angular/core';
	import { Data } from '../shared/data';

	@Component({
	  selector: 'app-cities',
	  templateUrl: './cities.component.html',
	  styleUrls: ['./cities.component.css']
	})
	export class CitiesComponent implements OnInit {
	  staedte: Data[];

	  constructor(private ds: DataService) {
	    this.staedte = this.ds.getAll();
	  }

	  ngOnInit(): void {
	  }

	}
	```

Der Service wird per *Dependency Injection* eingebunden (Zeile `13`). Damit ist `ds` (die Referenz auf den Service) eine weitere Objekteigenschaft der `cities`-Komponent. Wir rufen die `getAll()`-Funktion des Services auf, die alle Daten des `staedte`-Arrays zurückgibt und speichern diese in der `staedte`-Variablen (Zeile `14`). Diese ist vonm Typ `Data[]` (Zeile `11`). Um diesen Typ zu kennen, muss das Interface `Data` in die Komponente importiert werden (Zeile `3`). Unsere Anwendung funktioniert nun wieder exakt wie zuvor. 

## Weiter mit parametrisierten Routen

Denselben Service wollen wir nun auch in der `city`-Komponente verwenden, in der wir eine einzelne Stadt nach ihrer `id` auswählen und darstellen wollen. Dazu erweitern wir zunächst den `data`-Service um eine Funktion, die uns ein einzelnes Stadt-Objekt für eine gegebene `id` zurückgibt:


=== "shared/data.service.ts"
	```js linenums="1" hl_lines="18-20"
	import { Injectable } from '@angular/core';
	import { Data } from './data';

	@Injectable({
	  providedIn: 'root'
	})
	export class DataService {
	  data: Data[];

	  constructor() {
	    this.data = [ /* rausgekuerzt, muss aber bleiben! */  ];
	  }

	  getAll(): Data[] {
	    return this.data;
	  }

	  getOne(id: number): Data {
	    return this.data[id-1];
	  }
	}

	```

Diese Funktion ist sehr einfach gehalten. Angenommen, die `id=1` wird übergeben, dann wird das erste Element (`index=0`) zurückgegeben, also das `Berlin`-Objekt. Problem dieser Funktion ist, dass gar nicht überprüft wird, ob es sich bei `id-1` um einen korrekten Index aus dem Array handelt. Eine Möglichkeit, dieses Problem zu umgehen, wäre z.B. die Verwendung der Modulo-Funktion für die `id` über die Länge des Arrays, z.B. so:

```js
  getOne(id: number): Data {
    let index = id-1;
    index = index % this.data.length;
    return this.data[index];
  }
```

Wir lassen die Funktion aber bewusst so, um zu zeigen, wie wir mit `undefined` Ergebnissen umgehen könnten. 

Die Tabelle, die wir in `cities.somponent.html` erzeugen, erweitern wir um eine Spalte, in der wir die Links auf die Detailseiten der jeweiligen Stadt hinterlegen:

=== "cities.component.html"
	```html linenums="1" hl_lines="12 25-27"
	<div class="container">
	    <h1>Städte</h1>

	    <table class="table table-striped">
	        <caption>Ausgewählte Städte</caption>
	        <thead>
	            <tr>
	                <th scope="col">Nr</th>
	                <th scope="col">Jahr</th>
	                <th scope="col">Stadt</th>
	                <th scope="col">Bild</th>
	                <th scope="col"></th>
	            </tr>
	        </thead>
	        <tbody>
	            <tr *ngFor=" let stadt of staedte; let i=index ">
	                <td>{{ i+1 }} </td>
	                <td>{{ stadt.jahr }}</td>
	                <td>{{ stadt.stadt }}</td>
	                <td>
	                    <a [href]="stadt.link">
	                        <img [src]=" stadt.bild " [alt]="stadt.stadt " />
	                    </a>
	                </td>
	                <td>
	                    <a [routerLink]="['/cities', (i+1)]">Detail</a>
	                </td>
	            </tr>
	        </tbody>
	    </table>
	</div>

	```

Wir sehen darin, dass der Wert für `routerLink` auch ein Array sein kann, dessen erster Eintrag die Route und dessen zweiter Eintrag eine anschließende `/id` sein kann. Der so beschriebene Wert ergibt dann die Routen `/cites/1`, `/cities/2` usw. Es hätte auch funktioniert, wenn wir `<a [routerLink]="'/cities/'+(i+1)">Detail</a>` geschrieben hätten. 

Wenn wir nun in der Tabelle auf `Detail` klicken (z.B. in der `Berlin`-Zeile), dann ist die Route `/cities/1`. In der `city`-Komponente wollen wir diese Zahl auslesen. Dazu erweiteren wir unser `routes`-Array in der `app-routing.module.ts`:

=== "app-routing.module.ts"
	```js linenums="1" hl_lines="1 27-30"
	import { CityComponent } from './cities/city/city.component';
	import { HomeComponent } from './home/home.component';
	import { LoginComponent } from './login/login.component';
	import { AboutComponent } from './about/about.component';
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';
	import { CitiesComponent } from './cities/cities.component';

	const routes: Routes = [
	  {
	    path: "",
	    component: HomeComponent,
	    pathMatch: 'full'
	  },
	  {
	    path: "about",
	    component: AboutComponent
	  },
	  {
	    path: "login",
	    component: LoginComponent
	  },
	  {
	    path: "cities",
	    component: CitiesComponent
	  },
	  {
	    path: "cities/:id",
	    component: CityComponent
	  }
	];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }

	```

Wir definieren darin, dass wir den Zahlenwert an der Route als `id` auslesen werden. Der Doppelpunkt `:` steht für eine parametrisierte Route. Der Name für `id` ist frei wählbar. Wir werden aber gleich sehen, wie dieser Name verwendet wird. Diesen Wert wollen wir nun in der `city`-Komponente auslesen, um zu erkennen, welche Stadt ausgewählt wurde. Dazu erweiteren wir die `city.component.ts`.

=== "city.component.ts"
	```js linenums="1" hl_lines="2-4 12 13 15 18 19"
	import { Component, OnInit } from '@angular/core';
	import { ActivatedRoute } from '@angular/router';
	import { Data } from 'src/app/shared/data';
	import { DataService } from 'src/app/shared/data.service';

	@Component({
	  selector: 'app-city',
	  templateUrl: './city.component.html',
	  styleUrls: ['./city.component.css']
	})
	export class CityComponent implements OnInit {
	  id: number = 0;
	  stadt!: Data;

	  constructor(private route: ActivatedRoute, private ds: DataService) { }

	  ngOnInit(): void {
	    this.id = Number(this.route.snapshot.paramMap.get('id'));
	    this.stadt = this.ds.getOne(this.id);
	  }

	}
	```

Erläuterungen zum Code:

- In den Zeilen `2-4` werden das Modul `ActivatedRoute`, das Interface `Data` und der Service `DataService` importiert. `ActivatedRoute` benötigen wir zum Auslesen der aktiven Route, also insbesondere zum Auslesen der `id`, die an die Route gehängt ist. 
- In Zeile `12` deklarieren wir uns eine Variable `id`, in der wir genau diese `id` der Route speichern wollen. 
- In Zeile `13` deklarieren wir uns eine Variable `stadt`. Diese ist vom Typ `Data` (unserem Interface). Beachten Sie das `!` hinter dem Variablennamen. Hierbei handelt es sich um eine *Assertion*, also Zusicherung. Es handelt sich um den *Non-null assertion operator*. Damit wird dem TypeScript-Compiler mitgeteilt, dass er sich nicht darum kümmern muss, ob der Wert dieser Variable `null` ist oder nicht. Tatsächlich werden wir sogar den Fall berücksichtigen, dass der Wert `null` sein kann.
- In Zeile `14` wird sowohl der `DataService` als auch `ActivatedRoute` per *dependency injection*  eingebunden. Den `DataService` benötigen wir, um das entsprechende `stadt`-Objekt zu erhalten und `ActivatedRoute` wird benötigt, um die Zahl (`id`) zu ermitteln, die bei der aktuellen Route angegeben ist. 
- In Zeile `18` wird genau diese Route ausgelesen. Insbesondere wird hier jetzt der Name verwendet, der in `app-routing.module.ts` für den Routen-Parameter vergeben wurde (also hier `id`). Dieser Wert wird als `string` zurückgegeben. Er wird mit `Number` zu `number` konvertiert. Wichtig ist, dass `snapshot` genau einmal die Route ausliest (beim Initialisieren der Komponente), aber nicht ständig auf Änderungen der Route hört. 
- In Zeile `19` wird die `id` verwendet, um der `getOne()`-Funktion des `DataService` übergeben zu werden. Diese Funktion liefert die entsprechende `stadt` aus dem `staedte`-Array zurück. 

### Verwenden der Daten 

Wie die Werte der Daten nun in der `city.component.html` verwendet werden, bleibt natürlich Ihnen überlassen. Wir zeigen hier die einfache Verwendung mithilfe einer Bootstrap-`card`:

=== "city.component.html"
	```html linenums="1"
	<div class="container">
	    <div *ngIf="stadt" class="mt-5">

	        <div class="card m-4" style="width: 30%">
	            <img class="card-img-top" [src]="stadt.bild" [alt]="stadt.stadt">
	            <div class="card-body">
	                <h4>Willkommen in {{ stadt.stadt }} </h4>
	            </div>
	        </div>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="'/cities'">Zurück zur Liste</a>
	    </div>
	    <div *ngIf="!stadt">
	        <h1>Leider wurde keine Stadt gefunden</h1>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="'/cities'">Zurück zur Liste</a>
	    </div>
	</div>

	```

Zwei Dinge sind zu beachten: 

1. Es wird unterschieden, ob die Variable `stadt` einen Wert hat (also auf ein Stadt-Objekt zeigt) oder nicht (also noch `undefined` ist). Letzteres kann dadurch entstehen, dass die `getOne()`-Funktion des `DataService` kein Objekt zurückgeliefert hat, nämlich dann, wenn die übergebene `id` keinem `index` im Array entsprach (siehe obige Diskussion dieser Funktion). Sollte `stadt` noch `undefined` sein, dann wird `Leider wurde keine Stadt gefunden` angezeigt. 
2. Es wurde ein Anchorelement (`<a>`) eingefügt, um wieder zurück zur Liste zu gelangen. Hierbei ist zu erwähnen, dass es wichtig ist, dass die Route `'/cities'` lautet und nicht nur `'cities'`. Im letzteren Fall würde `cities` einfach an die aktuelle Route angehängt werden, also dann z.B. `/cities/1/cities` lauten. 

### Neuladen bei neuer Route

Angenommen, wir erweitern die `city.component.html` um zwei weitere Navigationsbuttons, um zwischen den einzelnen Städten "zu blättern":


=== "city.component.html"
	```html linenums="1" hl_lines="10 12"
	<div class="container">
	    <div *ngIf="stadt" class="mt-5">

	        <div class="card m-4" style="width: 30%">
	            <img class="card-img-top" [src]="stadt.bild" [alt]="stadt.stadt">
	            <div class="card-body">
	                <h4>Willkommen in {{ stadt.stadt }} </h4>
	            </div>
	        </div>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="['/cities', stadt.id-1]"> &lt; </a>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="'/cities'">Zurück zur Liste</a>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="['/cities', stadt.id+1]"> &gt; </a>
	    </div>
	    <div *ngIf="!stadt">
	        <h1>Leider wurde keine Stadt gefunden</h1>
	        <a class="btn btn-secondary m-4 px-4" [routerLink]="'/cities'">Zurück zur Liste</a>
	    </div>
	</div>

	```

Wenn wir nun auf einen solchen Navigationsbutton klicken, dann sehen wir, dass sich im URL-Fenster die Route ändert. Jedoch erscheint keine neue Stadt. Das liegt daran, dass die Route nicht automatisch neu geladen wird, wenn sich die Route ändert. Das liegt an der `RouteReuseStrategy` (siehe [hier](https://angular.io/api/router/RouteReuseStrategy)). Darin wird festgelegt, ob die aktivierte Route wiederverwendet werden soll (`true`) oder nicht (`false`). Im letzteren Fall wird die Komponente automatisch neu geladen, wenn die aktivierte Route sich ändert. Wir ändern entsprechend die `city.component.ts`:

=== "city.component.ts"
	```js linenums="1" hl_lines="2 16 22"
	import { Component, OnInit } from '@angular/core';
	import { ActivatedRoute, Router } from '@angular/router';
	import { Data } from 'src/app/shared/data';
	import { DataService } from 'src/app/shared/data.service';

	@Component({
	  selector: 'app-city',
	  templateUrl: './city.component.html',
	  styleUrls: ['./city.component.css']
	})
	export class CityComponent implements OnInit {
	  id: number = 0;
	  stadt!: Data;

	  constructor(
	    private route: ActivatedRoute,
	    private ds: DataService,
	    private router: Router
	    ) { }

	  ngOnInit(): void {
	    this.router.routeReuseStrategy.shouldReuseRoute = () => false;
	    this.id = Number(this.route.snapshot.paramMap.get('id'));
	    this.stadt = this.ds.getOne(this.id);
	  }

	}
	```

Die Notation `() => false` ist sicherlich ungewöhnlich. Dabei handelt es sich um eine Funktion in *Arrow-Notation*. 

### Arrow-Funktionen

*Arrow-Funktionen* werden auch als *Lambda-Ausdrücke* bezeichnet. Eine Arrow-Funktion ist eine Kurzschreibweise für eine anonyme Funktion. Anstelle von `function()` schreibt man nur noch einen Pfeil. Enthält die anonyme Funktion sogar nur ein Argument (Parameter), kann man links vom Pfeil sogar die runden Klammern weglassen. Auch die geschweiften Klammern des Funktionskörpers können entfallen. Wenn die geschweiften Klammwern weggelassen werden, dann entspricht die rechte Seite des Pfeils dem Rückgabewert der Funktion, d.h. es kann sogar `return` weggelassen werden. Folgende Funktionsdefinitionen sind äquivalent:

```js
function(foo) = {return foo+1;}
(foo) => {return foo+1;}
foo => {return foo+1;}
foo => foo+1;
```

## Routen absichern mit Guards

*Guards* sind Funktionen, die entscheiden, ob ein Navigationsschritt ausgeführt werden darf oder nicht. Diese Entscheidung wird durch den Rückgabewert der Funktion ausgedrückt. Es gibt drei verschiedene Varainten für den Rückgabewert: 

- `true`: der Navigationsschritt wird ausgeführt, 
- `false`: der Navigationsschritt wird nicht ausgeführt, 
- Rückgabe vom Typ `URLTree`: die Navigation wird abgebrochen und eine Navigation zu einer anderen Route gestartet. 

*Guards* werden immer als Eigenschaft einer Route definiert, also bereits bei der Definition der Route im `routes`-Array in `app-routing.module.ts`. Es gibt vier verschiedene Guard-Typen:

- `CanAvtivate`: entscheidet, ob eine Route aktiviert werden darf,
- `CanAvtivateChild`: entscheidet, ob die Kind-Routen einer Route aktiviert werden dürfen (Kind-Routen haben wir uns bis jetzt noch nicht angeschaut),
- `CanDeaktivate`: entscheidet, ob eine Route deaktiviert werden darf,
- `CanLoad`: entscheidet, ob ein Module (asynchron) geladen werden darf. 

Uns genügt es, `CanActivate` zu betrachten. Damit wollen wir regulieren, dass nur eine bestimmte *Rolle* von Nutzern eine bestimmte Komponente verwenden darf. Wir erstellen uns einen solchen Guard mithilfe des Angular CLI und nennen den Guard `authguard`:

```bash
ng g guard authguard --implements CanActivate
```

Dadurch entsteht eine Datei `authguard.guard.ts` mit folgendem Inhalt:

=== "authguard.guard.ts"
	```js linenums="1"
	import { Injectable } from '@angular/core';
	import { ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, UrlTree } from '@angular/router';
	import { Observable } from 'rxjs';

	@Injectable({
	  providedIn: 'root'
	})
	export class AuthguardGuard implements CanActivate {
	  
	  canActivate(
	    route: ActivatedRouteSnapshot,
	    state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {
	    return true;
	  }
	  
	}

	```

Um dieses Beispiel etwas realistischer zu gestalten, erstellen wir noch einen `auth`-Service, der später unserer Nutzer- und Rollenverwaltung dient. Wir nennen ihn `auth` und erstellen ihn ebenfalls im `shared`-Ordner:

```bash
ng g service shared/auth
```

In diesen Service fügen wir nur eine dummy-Funktion `isAuthenticated()` ein, die ein `true` oder `false` zurückliefert:

=== "shared/auth.service.ts"
	```js linenums="1" hl_lines="10-12"
	import { Injectable } from '@angular/core';

	@Injectable({
	  providedIn: 'root'
	})
	export class AuthService {

	  constructor() { }

	  isAuthenticated(): boolean {
	    return false;
	  }
	}
	```

Diesen Service und davon insbesondere die `isAuthenticated`-Funktion verwenden wir in unserem `auth`-Guard:


=== "authguard.guard.ts"
	```js linenums="1"
	import { Injectable } from '@angular/core';
	import { ActivatedRouteSnapshot, CanActivate, Router, RouterStateSnapshot, UrlTree } from '@angular/router';
	import { AuthService } from './shared/auth.service';

	@Injectable({
	  providedIn: 'root'
	})
	export class AuthguardGuard implements CanActivate {

	  constructor(
	    private as: AuthService,
	    private router: Router
	  ) {}

	  canActivate(
	    route: ActivatedRouteSnapshot,
	    state: RouterStateSnapshot): boolean | UrlTree {
	    return this.as.isAuthenticated()
	      ? true
	      : this.router.parseUrl('/login');
	  }

	}
	```

Erläuterungen der Anpassungen:

- Zunächst haben wir die Rückgabetypen der `canActivate()`-Funktion auf `boolean` und `UrlTree` reduziert. Die anderen möglichen Rückgabetypen `Observable<boolean | UrlTree> | Promise<boolean | UrlTree>` haben wir gelöscht (und somit auch `import { Observable } from 'rxjs';`) - siehe Zeile `17`.
- Dann haben wir den `AuthService` und auch das `Router`-Modul per *dependency injection* in den Konstruktor der `AuthGuard`-Klasse eingefügt, um Beides verwenden zu können (Zeilen `10-13`). 
- Dann haben wir die Berechnung des Rückgabewertes der `canActivate`-Funktion ergänzt. Der Rückgabewert ist abhängig vom Rückgaewert der `isAuthenticated()`-Funktion des `AuthServices`. Liefert diese Funktion ein `true` zurück, dann gibt auch die `canActivate()`-Funktion ein `true` zurück (Zeile `19`). Ist der Rückgabewert jedoch `false`, dann liefert die `canActivate()`-Funktion ein `UrlTree` in der Form zurück, dass die Navigation auf die Route `/login` umgeleitet wird. 

Jetzt können wir diesen Guard verwenden und passen dafür die `app-routing.module.ts` an. Wir wollen hier exemplarisch demonstrieren, dass die `/cities`- und `/cities/:id`-Routen nur dann aktiviert werden können, wenn die `canActivate()`-Funktion des `AuthGuard`s ein `true` zurückliefert. Dazu sind folgende Änderungen in der `app-routing.module.ts` notwendig: 

=== "app-routing.module.ts"
	```js linenums="1" hl_lines="5"
	import { AuthguardGuard } from './authguard.guard';
	import { CityComponent } from './cities/city/city.component';
	import { HomeComponent } from './home/home.component';
	import { LoginComponent } from './login/login.component';
	import { AboutComponent } from './about/about.component';
	import { NgModule } from '@angular/core';
	import { RouterModule, Routes } from '@angular/router';
	import { CitiesComponent } from './cities/cities.component';

	const routes: Routes = [
	  {
	    path: "",
	    component: HomeComponent,
	    pathMatch: 'full'
	  },
	  {
	    path: "about",
	    component: AboutComponent
	  },
	  {
	    path: "login",
	    component: LoginComponent
	  },
	  {
	    path: "cities",
	    component: CitiesComponent,
	    canActivate: [AuthguardGuard]
	  },
	  {
	    path: "cities/:id",
	    component: CityComponent,
	    canActivate: [AuthguardGuard]
	  }
	];

	@NgModule({
	  declarations: [],
	  imports: [
	    RouterModule.forRoot(routes)
	  ],
	  exports: [RouterModule],
	  providers: []
	})
	export class AppRoutingModule { }

	```


Wenn wir nun auf `/cities` navigieren wollen, dann werden wir direkt auf die `/login`-Route umgeleitet. Die `CitiesComponent` und auch die `CityComponent` bleiben gesperrt solange `isAuthenticated()` ein `false` zurückliefert. 

!!! success
	Wir haben die wesentlichsten Konzepte des Routing kennengelernt. Darüber hinaus gibt es noch Themen für Fortgeschrittene, wie z.B. lazy-loading von Modulen (Module erst dann laden, wenn man sie wirklich erst aufruft), Routen für Kindkomponenten, mehrere outlets usw. Aber uns genügen die hier erläuterten wesentlichen Konzepte. 