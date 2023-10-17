# Web-Technologien

Herzlich willkommen zur WebTech-Veranstaltung im Wintersemester 2022/23! 

### Grober Inhalt

In dieser Veranstaltung lernen Sie, was das World Wide Web ist und wie man eigene Webseiten und -anwendungen realisiert. Sie lernen die Protokolle und Sprachen ``http``, ``HTML``, ``CSS``und ``JavaScript`` kennen und machen sich mit ``Angular``, ``Node.js`` und ``REST`` vertraut. Zentrales Thema ist der sogenannte [MEAN](https://www.ibm.com/cloud/learn/mean-stack-explained)-Stack, d.h. Sie lernen die Entwicklung mithilfe von <b>M</b>ongoDB, <b>E</b>xpress.js, <b>A</b>ngular und <b>N</b>ode.js kennen.

Nachfolgend der vorläufige Wochenplan (wird eventuell angepasst). 

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) | Abgabe Übung bis | 
|-|-------|--------------------|-------|-----------------|------------------|
| 1. | 10.-14.10.2022 | [Einführung](./einfuehrung/#webtechnologien-einfuhrung) und [Organisatorisches](./#organisatorisches) | [Übung 0](./uebungen/#ubung-0) | - | - | 
| 2. | 17.-21.10.2022 | [HTML](./html/) | [Übung 1](./uebungen/#ubung-1) | Idee | 25.10.2022 | 
| 3. | 24.-28.10.2022 | [CSS (Eigenschaften und Selektoren](./css/#css) | [Übung 2](./uebungen/#ubung-2) | - | 01.11.2022 | 
| 4. | 31.-04.11.2022 | [CSS (Grid)](./css/#grid) | [Übung 3](./uebungen/#ubung-3) | Konzept | 08.11.2022 | 
| 5. | 07.-11.11.2022 | [RWD (responsive Webdesign)](./rwd/#responsive-web-design) | [Übung 4](./uebungen/#ubung-4) | - | 15.11.2022 | 
| 6. | 14.-18.11.2022 | [JavaScript (DOM)](./javascript/#javascript) | [Übung 5](./uebungen/#ubung-5) | Datenmodell | 22.11.2022 | 
| 7. | 21.-25.11.2022 | [Angular (Einführung und Komponenten)](./angular/#angular) | [Übung 6](./uebungen/#ubung-6) | Schnittstelle | 29.11.2022 | 
| 8. | 28.-02.12.2022 | [Angular (Bindings und Direktiven) + JSON](./angular2/#json-und-direktiven) | [Übung 7](./uebungen/#ubung-7) | Frontend (c+r)| 06.12.2022 | 
| 9. | 05.-09.12.2022 | [Angular (Routing und Services)](./routing/#routing-und-services) |  | Frontend (u+d)| 13.12.2022 | 
| 10. | 12.-16.12.2022 | [Node.js + Express (REST-Server + MongoDB)](./backend/#rest-api-mongodb) |  | Frontend fertig | 20.12.2021 | 
| 11. | 19.-23.12.2022 | [Angular (Anbindung ans Backend)](./fe-be-anbindung/#frontend-backend-anbindung) |  | Backend ( c ) | 10.01.2023 | 
| | | | | | | |
| 12. | 02.-06.01.2023 | [Nutzerverwaltung und Material](./guards/#subject-observable-observer-und-guards) | - | Backend (r + u) | 17.01.2023 |
| 13. | 09.-13.01.2023 | Wiederholung  | - | Backend (d + fertig)| 24.01.2023 |
| 14. | 16.-20.01.2023 | Wiederholung | - | fertig stellen | 31.01.2023 |
| 15. | 23.-27.01.2023 | - | Fragen | - | - |
| 16. | 30.-02.02.2023 | - | Fragen  | - |
| 17. | 06.-10.02.2023 | - | Fragen | Abgabe 1.PZ 20.2.2023, Gespräche 21.2.2023  |
|  |  |  |  |Abgabe 2.PZ 24.3.2023, Gespräche 27.3.2023 | - |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen Sie die Übungen lösen und zu den jeweiligen Fristen per Git auf einen Server (GitHub oder GitLab) laden. Am Ende des Semesters ist eine Aufgabe abzugeben. Diese Aufgabe wird bewertet. Die Bewertung entspricht dann der Modulnote. 

[Hier](./uebungen/#ubungen) sind die Übungen beschrieben, die Sie in jeder Woche ausführen sollen. Damit Sie dies erfolgreich erledigen können, ist jeweils angegeben, welche Themen Sie dafür durcharbeiten müssen. Das Durcharbeiten der jeweiligen Themen entspricht jeweils einer Vorlesung. Diese wird also selbständig durchgeführt. 

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes Diskussionsforum entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese von Ihnen dort beantwortet zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht.  

## Code aus der Vorlesung

??? note "HTML"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Hello FIW</title>
	</head>

	<body>

	    <h1>Überschrift h1</h1>
	    <p>Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed
	        <br /> diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero
	        eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem
	        ipsum dolor sit amet. Lorem ipsum dolor
	        <img src="./Logos/fiw.jpg" alt="FIW_Logo" />

	        sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam
	        erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no
	        sea takimata sanctus est Lorem ipsum dolor sit amet.
	    </p>
	    <h2>Überschrift h2</h2>
	    <h3>Überschrift h3</h3>
	    <h4>Überschrift h4</h4>
	    <h5>Überschrift h5</h5>
	    <h6>Überschrift h6</h6>

	    <ul>
	        <li>Erster Punkt</li>
	        <li>Zweiter Punkt
	            <ul>
	                <li>Unterpunkt</li>
	                <li>Unterpunkt</li>
	                <li>Unterpunkt</li>
	            </ul>
	        </li>
	        <li>Dritter Punkt</li>
	    </ul>

	    <table>
	        <thead>
	            <tr>
	                <th>Spalte 1</th>
	                <th>Spalte 2</th>
	                <th>Spalte 2</th>
	            </tr>
	        </thead>
	        <tbody>
	            <tr>
	                <td>1</td>
	                <td>2</td>
	                <td>3</td>
	            </tr>
	            <tr>
	                <td>4</td>
	                <td>5</td>
	                <td>6</td>
	            </tr>
	            <tr>
	                <td>7</td>
	                <td>8</td>
	                <td>9</td>
	            </tr>
	        </tbody>
	    </table>

	    <a href="./test.html">Test</a>

	    <header>
	        vielleicht
	        <nav>Menüpunkte weiß nicht</nav>
	        lieber testen
	    </header>
	    <main>lieber testen
	        <section>
	            <article>
	                besser testen
	            </article>
	        </section>
	    </main>
	    <footer>

	    </footer>

	    <input action="/submit">
	    <label for="name">Name</label>
	    <input type="text" id="name" name="name" placeholder="Name">
	    <br />
	    <label for="email">E-Mail</label>
	    <input type="email" id="email" name="email" placeholder="E-Mail">
	    <label for="message">Nachricht</label>
	    <textarea id="message" name="message" placeholder="Nachricht"></textarea>
	    <input type="submit" value="Absenden">
	    <input type="datetime-local" name="" id="">
	    <input type="button" value="OK">
	    </form>
	</body>

	</html>
	```


??? note "CSS Cascading"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Cascading</title>
	    <style>
	        body {
	            background-color: lightgoldenrodyellow;
	            font-family: verdana;
	        }

	        section h2 {
	            color: pink;
	            text-align: center;
	            text-transform: uppercase;
	        }

	        header, footer {
	            background-color: aqua;
	        }
	        main {
	            color: red;
	        }

	        section>p {
	            color: blue;
	        }

	        ol>li {
	            background-color: yellowgreen;
	        }

	        .bgYellow {
	            background-color: yellow;
	        }

	        .fgBrown {
	            color: brown;
	        }

	        #firstH2 {
	            font-weight: 400;
	        }

	        a {
	            text-decoration: none;
	        }

	        a:hover {
	            font-weight: 800;
	        }

	        a:visited {
	            font-weight: 800;
	            color:red;
	        }
	    </style>
	</head>
	<body>
	    <header>
	        <h1 style="padding: 30px; margin-bottom: 100px;">Cascading</h1>
	    </header>
	    <main>
	        <section>
	            <h2 id="firstH2">Section 1</h2>
	            <article>
	                <p class="bgYellow fgBrown">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	                <p class="bgYellow fgBrown">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	            </article>
	            <article>
	                <p class="bgYellow">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	                <p  class="fgBrown">Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	            </article>
	            <p>direktes Kind einer section</p>
	        </section>
	        <section>
	            <h2>Section 2</h2>
	            <article>
	                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	                hallo ballo
	                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	            </article>
	            <article>
	                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	            </article>
	        </section>
	        <ol>
	            <li>item 1
	                <ul>
	                    <li>subitem</li>
	                    <li>subitem</li>
	                    <li>subitem</li>
	                </ul>
	            </li>
	            <li>item 2</li>
	            <li>item 3</li>
	            <li>item 4</li>
	            <li>item 5</li>
	        </ol>
	    </main>
	    <aside>
	        <h2>Aside</h2>
	        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, quae.</p>
	    </aside>
	    <footer>
	        <p><a href="./index.html">Zurück</a></p>
	    </footer>

	</body>
	</html>
	```


??? note "CSS Boxmodel"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Box-Model</title>
	    <style>
	        div {
	            width: 320px;
	            padding: 10px;
	            border: 5px solid gray;
	            margin: 0;
	        }
	    </style>
	</head>
	<body>
	    <header>
	        <h1>Box-Model</h1>
	    </header>
	    <main>
	        <img src="./Logos/fiw.jpg" alt="fiw logo" style="width:350px"/>
	        <div>Das FIW-Logo hat eine Breite von 350px (width:350px).
	            Der Inhalt dieser Box hat eine Breite von 320px.
	            Dazu kommt padding von 10px (auf beiden Seiten)
	            und ein Rahmen mit der Breite von 5px. Macht zusammen
	            350px.
	        </div>
	    </main>
	    <footer>
	        <p><a href="./index.html">Zurück</a></p>
	    </footer>

	</body>
	</html>
	```


??? note "CSS Rangfolge"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Reihenfolge Selektoren</title>
	    <style>
	        a:link {
	        color: blue; 
	        }
	        
	        .link {
	            
	        color: green;
	        }
	        
	        #navigation a.link {
	        color: red;
	        }

	        li a {
	        color: magenta; 
	        }
	        
	        #navigation li a {
	            color: black;
	        }
	    </style>
	</head>
	<body>
	    <header>
	        <h1>Reihenfolge Wirkung Selektoren</h1>
	    </header>
	    <main>
	          <ul id="navigation">
	            <li><a href="./index.html" class="link">Startseite</a></li>
	            <li><a href="./grid.html" class="link">Grid</a></li>
	        </ul>
	  <h2>Prinzip</h2>
	  <dl>
		<dt>Kategorie A</dt>
		<dd>erhält den Wert 1, wenn CSS-Definitionen direkt im style-Attribut eines HTML-Elementes notiert sind</dd>
		<dt>Kategorie B</dt>
		<dd>erhält den Wert 1 bei Selektoren für Elemente mit id-Attributen</dd>
	    	<dt>Kategorie C</dt>
		<dd>Anzahl der von einem Selektor betroffenen Klassen und Pseudoklassen</dd>
	    	<dt>Kategorie D</dt>
		<dd>Anzahl der von einem Selektor betroffenen Elementnamen und Pseudo-Elemente</dd>
	</dl>
	<ol>
	    <li>Bei der Reihenfolge der Sortierung gilt: A > B > C > D, also z.B. 1 0 0 0 vor (größer als) 0 1 2 2.</li>
	    <li>Bei Gleichheit gilt die letzte Definition</li>
	</ol>
	    </main>
	    <footer>
	        <p><a href="./index.html">Zurück</a></p>
	    </footer>

	</body>
	</html>
	```


??? note "display"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>display</title>
	    <style>
	        p {
	            color: red;
	        }

	        p.ex1 {
	            display: none;
	        }
	        p.ex2 {
	            display: inline;
	        }
	        p.ex3 {
	            display: block;
	        }
	        p.ex4 {
	            display: inline-block;
	        }
	        nav {
	            background-color: darkgray;
	            color: white;
	            
	  text-align: center; 
	        }
	        nav li {
	            display: inline-block;
	            padding: 3%;
	        }
	        nav ul li a {
	            color:white;
	            text-decoration: none;
	        }
	    </style>
	</head>
	<body>
	<header>
	    <nav>
	<ul>
	    <li><a href="./boxmodel.html">Boxmodel</a></li>
	    <li><a href="./cascading.html">Cascading</a></li>
	    <li><a href="#">Display</a></li>
	    <li><a href="./grid">Grid</a></li>
	</ul>
	    </nav>
	</header>
	<main>
	<h1>The display Property</h1>

	<h2>display: none:</h2>
	<div>
	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. <p class="ex1">none!</p> Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut.
	</div>

	<h2>display: inline:</h2>
	<div>
	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. <p class="ex2">inline!</p> Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut.
	</div>

	<h2>display: block:</h2>
	<div>
	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. <p class="ex3">block!</p> Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut.
	</div>

	<h2>display: inline-block:</h2>
	<div>
	Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam semper diam at erat pulvinar, at pulvinar felis blandit. <p class="ex4">neue Zeile und dann inline!</p> Vestibulum volutpat tellus diam, consequat gravida libero rhoncus ut.
	</div>   

	<ul>
	    <li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/display?retiredLocale=de">Gibt noch sehr viele andere</a></li>
	    <li><a href="./index.html">Zurück</a></li>
	</ul>
	</main>
	    <footer>
	    
	    </footer>
	</body>
	</html>
	```


??? note "grid"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>CSS-Grid</title>
	    <style>

	        .orange {
	            background-color: orange;
	            opacity: 0.5;
	            border: 2px solid gray;
	            border-radius: 5px;
	            padding: 30px;
	        }

	        .wrapper {
	            display: grid;
	            grid-template-columns: repeat(3, 1fr);
	            grid-gap: 10px;
	            grid-auto-rows: minmax(100px, auto);
	        }

	        .one {
	            grid-column: 1 / 3;
	            grid-row: 1;
	        }

	        .two {
	            grid-column: 2 / 4;
	            grid-row: 1 / 3;
	        }

	        .three {
	            grid-column: 1;
	            grid-row: 2 / 5;
	        }

	        .four {
	            grid-column: 3;
	            grid-row: 3;
	        }
	    </style>
	</head>
	<body>
	    <header>
	        <h1>CSS-Grid</h1>
	    </header>
	    <main class="wrapper">
	        <div class="one orange">One</div>
	        <div class="two orange">Two</div>
	        <div class="three orange">Three</div>
	        <div class="four orange">Four</div>
	        <div class="five orange">Five</div>
	        <div class="six orange">Six</div>
	    </main>
	    <footer>
	        <p><a href="https://www.w3schools.com/cssref/pr_grid.php">grid</a></p>
	        <p><a href="https://www.w3schools.com/cssref/pr_grid-template-columns.php">grid-template-columns</a></p>
	        <p><a href="https://css-tricks.com/introduction-fr-css-unit/">fr - fraction</a></p>
	        <p><a href="./index.html">Zurück</a></p>
	    </footer>

	</body>
	</html>
	```


??? note "rwd - 1"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Document</title>
	    <style>
	        div {
	            margin: auto;
	            width: 100%;
	            height: 100%;
	            text-align: center;
	            background-color: red;
	            padding-top: 20%;
	            padding-bottom: 20%;
	            font-size: medium;
	        }

	        @media screen and (min-width: 800px) {
	            div {
	                background-color: blue;
	                color: white;
	                font-size: large;
	            }
	        }

	        @media (min-width: 1200px) {
	            div {
	                background-color: darkgreen;
	                color: white;
	                font-size: xx-large;
	            }
	        }

	        @media (orientation: portrait) {
	            div {
	                background-color: yellow;
	                color: brown;
	                writing-mode: vertical-rl;
	            }
	        }
	    </style>
	</head>

	<body>
	    <div>Ändern Sie die Breite des Browsers, um den Effekt zu sehen.</div>
	</body>
	</body>

	</html>
	```

??? note "rwd - 2"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1">
	    <title>Responsive Webdesign</title>
	    <style>
	        .small {
	            float: left;
	            width: 98%;
	            padding: 1%;
	        }

	        @media screen and (min-width: 800px) {
	            .medium {
	                float: left;
	                width: 48%;
	                padding: 1%;
	            }
	        }

	        @media screen and (min-width: 1200px) {
	            .large {
	                float: left;
	                width: 23%;
	                padding: 1%;
	            }
	        }
	    </style>
	</head>

	<body>
	    <p class="small medium large">
	        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata
	        sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et
	        ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
	        At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
	        eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet,
	    </p>
	    <p class="small medium large">
	        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata
	        sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et
	        ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
	        At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
	        eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet,
	    </p>
	    <p class="small medium large">
	        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata
	        sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et
	        ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
	        At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
	        eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet,
	    </p>
	    <p class="small medium large">
	        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata
	        sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et
	        ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
	        At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore
	        eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum dolor sit amet,
	    </p>
	</body>

	</html>
	```


??? note "bootstrap"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
	    <!-- <link href="../bootstrap.min.css" rel="stylesheet"> -->
	    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet"
	        integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">
	    <title>Bootstrap</title>
	</head>

	<body>
	    <main role="main">
	        <div class="p-5 mb-4 bg-warning rounded-3">
	            <div class="container-fluid py-5">
	                <h1 class="display-5 fw-bold">Jetzt mit Bootstrap!</h1>
	                <p class="col-md-8 fs-4">Wir verwenden jetzt Bootstrap und schauen uns mal die Anwendung ein wenig genauer an. Das Grundprinzip besteht darin, HTML-Elementen Klassen zuzuordnen. </p>
	                <p><a class="btn btn-primary btn-lg" href="https://getbootstrap.com/docs/5.1/examples/" role="button">Bootstrap Beispiele &raquo;</a></p>
	            </div>
	        </div>

	        <div class="container">
	            <h2>Formular mit Validierung, ob Eingabe erfolgte (nur mit CSS - kein JavaScript!)</h2>
	            <p>Hier wird z.B. die Klasse <code>.was-validated</code> verwendet, um zu überprüfen, ob in den Textfeldern und der Checkbox eine Eingabe erfolgt ist.</p>
	            <form class="was-validated">
	                <div class="form-group">
	                    <label for="uname">Username:</label>
	                    <input type="text" class="form-control" id="uname" placeholder="Enter username" name="uname" required>
	                    <div class="valid-feedback">Korrekt</div>
	                    <div class="invalid-feedback">Feld bitte ausfüllen!</div>
	                </div>
	                <div class="form-group">
	                    <label for="pwd">Password:</label>
	                    <input type="password" class="form-control" id="pwd" placeholder="Enter password" name="pswd" required>
	                    <div class="valid-feedback">Korrekt</div>
	                    <div class="invalid-feedback">Feld bitte ausfüllen!</div>
	                </div>
	                <div class="form-group form-check">
	                    <label class="form-check-label">
	                    <input class="form-check-input" type="checkbox" name="remember" required> Ich habe die Datenschutzerklärung gelesen und stimme ihr zu.
	                    <div class="valid-feedback">Korrekt</div>
	                    <div class="invalid-feedback">Hier bitte bestätigen!</div>
	                </label>
	                </div>
	                <button type="submit" class="btn btn-primary">Login</button>
	            </form>
	        </div>
	    </main>
	</body>

	</html>
	```


??? note "bootstrap grid"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
	    <link rel="stylesheet" href="./css/bootstrap.min.css">
	    <title>Grid</title>
	    <style>
	        div div {
	            padding: 10px;
	        }
	    </style>
	</head>

	<body>
	    <main class="container pt-5 ">
	        <h2>Wichtig ist, dass die Spaltenanzahl in einer Zeile 12 ergibt</h2>
	        <div class="row">
	            <div class="col-3" style="background-color: lightgrey;">
	                <h3>col-3</h3>
	                <p>Diesem &lt;div&gt; wurde die Klasse <code>col-3</code> zugewiesen</p>
	            </div>
	            <div class="col-4" style="background-color: darkgrey;">
	                <h3>col-4</h3>
	                <p>Diesem &lt;div&gt; wurde die Klasse <code>col-4</code> zugewiesen</p>
	            </div>
	            <div class="col-5" style="background-color: grey;">
	                <h3>col-5</h3>
	                <p>Diesem &lt;div&gt; wurde die Klasse <code>col-5</code> zugewiesen</p>
	            </div>
	        </div>
	    </main>
	</body>

	</html>
	```

??? note "bootstrap responsive"
	```html
	<!DOCTYPE html>
	<html lang="en">

	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
	    <link rel="stylesheet" href="./css/bootstrap.min.css">
	    <title>Grid</title>
	    <style>
	        div div {
	            padding: 10px;
	            margin-top: 5px;
	            margin-bottom: 5px;
	        }
	        
	        .row div:nth-child(odd) {
	            background-color: lightgrey;
	            color: black;
	        }
	        
	        .row div:nth-child(even) {
	            background-color: grey;
	            color: white;
	        }
	    </style>
	</head>

	<body>
	    <main class="container pt-5 ">
	        <h2>Jetzt resonsiv - ändern Sie die Monitorbreite</h2>
	        <div class="row">
	            <div class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 1/2</li>
	                    <li>md: <code>col-md-4</code> 1/3</li>
	                    <li>lg: <code>col-lg-3</code> 1/4</li>
	                    <li>xl: <code>col-xl-2</code> 1/6</li>
	                </ul>
	            </div>
	            <div class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 2/2</li>
	                    <li>md: <code>col-md-4</code> 2/3</li>
	                    <li>lg: <code>col-lg-3</code> 2/4</li>
	                    <li>xl: <code>col-xl-2</code> 2/6</li>
	                </ul>
	            </div>
	            <div class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 1/2</li>
	                    <li>md: <code>col-md-4</code> 3/3</li>
	                    <li>lg: <code>col-lg-3</code> 3/4</li>
	                    <li>xl: <code>col-xl-2</code> 3/6</li>
	                </ul>
	            </div>
	            <div class="col-12 col-sm-6 col-md-4 col-lg-3 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 2/2</li>
	                    <li>md: <code>col-md-4</code> 1/3</li>
	                    <li>lg: <code>col-lg-3</code> 4/4</li>
	                    <li>xl: <code>col-xl-2</code> 4/6</li>
	                </ul>
	            </div>
	            <div class="col-12 col-sm-6 col-md-4 col-lg-6 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 1/2</li>
	                    <li>md: <code>col-md-4</code> 2/3</li>
	                    <li>lg: <code>col-lg-6</code> 1/2</li>
	                    <li>xl: <code>col-xl-2</code> 5/6</li>
	                </ul>
	            </div>
	            <div class="col-12 col-sm-6 col-md-4 col-lg-6 col-xl-2">
	                <ul>
	                    <li>xs: <code>col-12</code> 1/1</li>
	                    <li>sm: <code>col-sm-6</code> 2/2</li>
	                    <li>md: <code>col-md-4</code> 3/3</li>
	                    <li>lg: <code>col-lg-6</code> 2/2</li>
	                    <li>xl: <code>col-xl-2</code> 6/6</li>
	                </ul>
	            </div>
	        </div>
	    </main>
	</body>

	</html>
	```


??? note "javascript"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>JavaScript</title>

	</head>
	<body>
	    <h1>JavaScript</h1>
	    <main>
	        <h4>Eigenschaften</h4>
	        <ul>
	            <li>Skriptsprache (aus Performanzgründen aber compiliert - z.B. V8 in Chrome, SpiderMonkey in Firefox)</li>
	            <li>dynamische Typisierung</li>
	            <li>keine unterschiedlichen Referenztypen</li>
	            <li>Vererbung durch <code>prototype</code></li>
	            <li>Objekteigenschaften und -funktionen können einfach dem Objekt hinzugefügt werden</li>
	        </ul>
	        <h4>Nützliche Links</h4>
	        <ul>
	            <li><a href="https://www.ecma-international.org/publications-and-standards/standards/ecma-262/">ECMA-262</a></li>
	            <li><a href="https://dom.spec.whatwg.org/">Document Object Model (DOM)</a></li>
	            <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide">JavaScript Guide</a></li>
	            <li><a href="https://www.w3schools.com/js/default.asp">JavaScript Tutorial</a></li>
	            <li><a href="https://learnjavascript.online/">Learn JavaScript</a></li>
	            <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference">JavaScript Reference</a></li>
	        </ul>
	        <h4>Ergebnisliste</h4>
	        <ul id="ulresult">
	            <li id="liresult1"></li>
	        </ul>
	        <input type="text" onchange="addContentText()" id="input" onfocus="changeColor()" onblur="changeColor()" placeholder="Name"/>
	        <button type="button" onclick="helloFIW()">Klick Mich!</button>
	    </main>
	    <script>

	        function helloFIW(name = 'FIW') {
	            /*
	            let name = 12;
	            let number = 2;
	            let test = name - number;
	            */
	            //console.log('Hello ' + test );
	            console.log('Hello ' + name);
	        }

	        let result = (a, b) => a+b;

	        console.log(result(3,4));

	        function addContentText() {
	            let input = document.getElementById('input');
	            //console.log(input);
	            let inputValue = input.value;
	            console.log(inputValue);
	            let liresult = document.querySelector('#liresult1');
	            liresult.textContent = "<span style='color: red;'>" +inputValue+ '</span>';
	        }

	        function changeColor() {
	            let input = document.getElementById('input');
	            if(input.style.backgroundColor === "yellow")
	            {
	                input.style.backgroundColor = "white"
	            }
	            else {
	                input.style.backgroundColor = "yellow";
	            }

	        }



	    </script>
	</body>
	</html>
	```

??? "Links zu Bootstrap"
	
	[CDN](https://getbootstrap.com/docs/5.2/getting-started/introduction/#cdn-links)</a> <br/>
	[Download](https://getbootstrap.com/docs/5.2/getting-started/download/#compiled-css-and-js)<br/>

??? note "javascript - create"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
	        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
	    <title>Javascript</title>
	    <style>
	        div#output {
	            height: 300px;
	        }
	    </style>
	</head>
	<body class="container">
	    <h1>Formular auslesen</h1>
	    <h4>Kommentare</h4>

	    <form id="form" onsubmit="return false;"> 
	        <div class="form-floating mb-3">
	            <input type="text" class="form-control" id="input1" placeholder="Kommentar 1" onchange="fixeInput()" />
	            <label for="input1">Kommentar 1</label>
	        </div>
	    </form> 
	    <script>
	        let nr = 1;

	        function fixeInput() {
	            let curInputId = "input" + nr;
	            let curInputElement = document.getElementById(curInputId);
	            console.log(curInputElement.value);
	            curInputElement.disabled = "true";

	            let newDiv = document.createElement('div');
	            newDiv.classList.add("form-floating", "mb-3");
	            nr++;
	            let newInputId = "input"+nr;
	            let newInput = document.createElement('input');
	            newInput.classList.add("form-control");
	            newInput.placeholder = "Kommentar " + nr;
	            newInput.id = newInputId;
	            newInput.addEventListener("change", fixeInput);
	            let newLabel = document.createElement('label');
	            newLabel.for = newInputId;
	            newLabel.textContent = "Kommentar " + nr;
	            newDiv.appendChild(newInput);
	            newDiv.appendChild(newLabel);
	            let form = document.getElementById('form');
	            form.appendChild(newDiv);

	            newInput.focus();
	        }
	    </script>

	</body>
	</html>
	```


??? note "javascript - object"
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet"
	        integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">
	    <title>Javascript</title>
	    <style>
	        div#output {
	            height: 300px;
	        }
	    </style>
	</head>
	<body class="container" onload="setBackgroundColorDiv()">
	    
	    <h1>JavaScript-Objekte</h1>
	    <div id="output">

	    </div>
	    <div class="my-3">
	        <div class="row">
	            <div class="col-2">
	                <label for="hueIP" class="form-label">Hue (Farbton)</label>
	            </div>
	            <div class="col-2">
	                <input type="text" class="form-range" id="hueOP" value="50">
	            </div>
	            <div class="col-8">
	                <input type="range" class="form-range" min="0" max="360" id="hueIP" oninput="newHue()" value="50">
	            </div>
	        </div>
	        <div class="row">
	            <div class="col-2">
	                <label for="satIP" class="form-label">Saturation (Sättigung)</label>
	            </div>
	            <div class="col-2">
	                <input type="text" class="form-range" id="satOP" value="50">
	            </div>
	            <div class="col-8">
	                <input type="range" class="form-range" min="0" max="100" id="satIP" oninput="newSat()" value="50">
	            </div>
	        </div>
	        <div class="row">
	            <div class="col-2">
	                <label for="lightIP" class="form-label">Lightness (Helligkeit)</label>
	            </div>
	            <div class="col-2">
	                <input type="text" class="form-range" id="lightOP" value="50">
	            </div>
	            <div class="col-8">
	                <input type="range" class="form-range" min="0" max="100" id="lightIP" oninput="newLight()" value="50">
	            </div>
	        </div>
	    </div>
	   <script>
	    function setBackgroundColorDiv() {
	        let colorHSL = {
	            hue: 50,
	            saturation: 50,
	            lightness: 50,
	            getColor: () => `hsl(${colorHSL.hue}, ${colorHSL.saturation}%, ${colorHSL.lightness}%)`
	        }

	        let div = document.getElementById('output');

	        let cHSLJSON = JSON.stringify(colorHSL) ;
	        console.log(cHSLJSON);

	        let cHSLObj = JSON.parse(cHSLJSON);
	        console.log(cHSLObj);
	        
	        div.style.backgroundColor = colorHSL.getColor();
	    }

	    function asyncBehaviour() {

	        let a = 1;
	        let b = 1;

	        setTimeout( function () {
	            console.log("timeout a = " + a);
	        }, 100)

	        fetch('./index.html')
	        .then( () => console.log('fetch hat geklappt'))

	        
	        console.log("a = ", a);
	        console.log("b = ", b);

	        a = 10 
	        

	    }

	    asyncBehaviour();
	   </script>
	</body>
	</html>
	```


??? note "Angular-Projekt first"

	- [Donload zip-Datei first.zip](./files/first.zip)
	- entpacken
	- in den projektordner wechseln und zunächst `npm i` ausführen
	- dann `ng serve`


??? note "Angular-Projekt part2"

	- [Donload zip-Datei part2.zip](./files/part2.zip)
	- entpacken
	- in den projektordner wechseln und zunächst `npm i` ausführen
	- dann `ng serve`

??? note "Video zur Vorlesung Backend(MongoDB)"
	<iframe src="https://mediathek.htw-berlin.de/media/embed?key=0aa0f30ec91e4254db1e4a33d0eaff89&width=720&height=540&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true&thumb=true" data-src="https://mediathek.htw-berlin.de/media/embed?key=0aa0f30ec91e4254db1e4a33d0eaff89&width=720&height=540&autoplay=false&controls=true&autolightsoff=false&loop=false&chapters=false&playlist=false&related=false&responsive=false&t=0&loadonclick=true" class="" width="720" height="540" frameborder="0" allowfullscreen="allowfullscreen" allowtransparency="true" scrolling="no" aria-label="media embed code" style=""></iframe>

## Semesteraufgabe

Am Ende des Kurses geben Sie eine Webanwendung ab. Diese wird bewertet und bildet die Modulnote für "WebTech" (es gibt also keine Klausur o.ä.). Überlegen Sie sich früh, was Sie implementieren wollen. Ihrer Kreativität sind keine Grenzen gesetzt. Es können 2 Studentinnen gemeinsam ein Projekt durchführen und abgeben. Sie erhalten dann (höchstwahrscheinlich) die gleiche Note. Es muss an den Commits erkennbar sein, welchen Anteil am Ergebnis jede der beiden Studentinnen hatte.

??? question "Mindestanforderungen"
	Folgende Anforderungen werden an Ihr Projekt gestellt:

	* das Frontend soll mit Angular entwickelt werden,
	* das Backend mit Node.js,
	* es soll eine Datenbank (MongoDB, kann aber auch MySQL oder PostgreSQL oder MariaDB - aber **nicht** Firebase) verwendet werden,
	* es soll CRUD implementiert sein, d.h. Sie benötigen 
	    * eine Komponente zur Erstellung und Speicherung eines Datenbankeintrages (<b>C</b>reate),
	    * eine Komponente zur Änderung eines Datenbankeintrages (<b>U</b>pdate),
	    * eine Komponente zur Anzeige *aller* Datenbankeinträge (<b>R</b>ead),
	    * eine Komponente zum Löschen eines Datenbankeintrages (<b>D</b>elete).
    * wenn Sie die Anwendung alleine umsetzen, dann genügen 3 der 4 CRUD-Funktionalitäten
    * wenn Sie die Anwendung zu zweit entwickeln, dann
    	* sollen alle 4 CRUD-Funktionalitäten umgesetzt werden und
    	* Login (Username + Passwort) und
    	* ich schaue mir die Commit-Hiostorie im Git genauer an, um sicherzugehen, dass beide Studentinnen gleich viel an der Anwendung mitentwickelt haben

	Datenbankeinträge können Bücher, CDs, ToDos, Einkaufslisten, Vorlesungen, Kühlschrankinhalte usw. sein - wie gesagt, Ihrer Kreativität sind keine Grenzen gesetzt. 

	Die Anwendung soll in einem Git-Dienst (GitHub, GitLab, ...) verfügbar sein. 

	Verwenden Sie ein CSS-Framework, wie z.B. Materialize, Bootstrap o.ä.! Ihre Anwendung soll "modern" aussehen und responsive sein. 

	Erstellen Sie eine **informative (ausführliche) README**-Datei (`README.md`). Diese Datei sollte beinhalten:

	 - Eine Beschreibung Ihrer Anwendung. Am besten mit Screenshots, so dass sie Ihren Kommilitoninnen aus den nächsten Jahren hilft, ein Verständnis dafür zu entwickeln, was mögliche Semesteraufgaben sein können.
	 - Eine Anleitung zur Installation Ihrer Anwendung. 

	Super wäre es, wenn Sie die Datenbank, die Sie verwenden, per Skript vorausfüllen, d.h. es wäre schön, wenn zum Testen der Anwendung nur das Frontend und das Backend gestartet werden müssten und alles andere automatisch passieren würde. Super wäre es auch, wenn Sie Ihre Anwendung deployen würden. 
	
	Nach Abgabe vereinbaren wir ein Online-Meeting, in dem Sie mir Ihre Anwendung nochmal zeigen können und ich Ihnen Fragen zu Ihrem Code stellen werde. Ist keine Prüfung, sondern eher ein fachliches Gespräch. 

## Abgabe- und Gesprächstermine

Die Lösung für die Semesteraufgabe pushen Sie in Ihr Respository. In einem Gespräch führen Sie die Lösung vor und wir unterhalten uns über Ihre Lösung. Dafür stehen verschiedene Termine zur Verfügung. 

- 1. Prüfungszeitraum: 20.2. Abgabe und 21.2. Gespräch
- 2. Püfungszeitraum: 27.3. Abgabe und 28.3. Gespräch

Bitte tragen Sie sich in [Moodle](https://moodle.htw-berlin.de/course/view.php?id=38845) in den von Ihnen gewünschten Gesprächstermin ein! Wenn Sie im 1.PZ abgeben, tragen Sie sich im LSF zum ersten PZ zur Prüfung ein, ansonsten im 2.PZ. 

### Einige Beispiele

#### Mieter- und Zahlungsinformationen verwalten

- ![projekte](./files/224_projekte1.png)
- ![projekte](./files/225_projekte1.png)
	

#### ToDo-Liste

- ![projekte](./files/226_projekte2.png)
- ![projekte](./files/227_projekte2.png)
- ![projekte](./files/228_projekte2.png)	

- ![projekte](./files/229_projekte2.png)
- ![projekte](./files/230_projekte2.png)


#### Dog-O-Mat

- ![projekte](./files/231_projekte3.png)


#### Reiseplaner

- ![projekte](./files/232_projekte3.png)
- ![projekte](./files/233_projekte3.png)

