# Web-Technologien

Herzlich willkommen zur WebTech-Veranstaltung im Wintersemester 2023/24! 

### Grober Inhalt

In dieser Veranstaltung lernen Sie, was das World Wide Web ist und wie man eigene Webseiten und -anwendungen realisiert. Sie lernen die Protokolle und Sprachen ``http``, ``HTML``, ``CSS``und ``JavaScript`` kennen und machen sich mit ``Angular``, ``Node.js`` und ``REST`` vertraut. Zentrales Thema ist der sogenannte [MEAN](https://www.ibm.com/cloud/learn/mean-stack-explained)-Stack, d.h. Sie lernen die Entwicklung mithilfe von <b>M</b>ongoDB, <b>E</b>xpress.js, <b>A</b>ngular und <b>N</b>ode.js kennen.

Nachfolgend der vorläufige Wochenplan (wird eventuell angepasst). 

| | Woche | Themen (Vorlesung) | Übung | Aufgabe (Stand) | Abgabe Übung bis | 
|-|-------|--------------------|-------|-----------------|------------------|
| 1. | 16.-20.10.2023 | [Einführung](./einfuehrung/#webtechnologien-einfuhrung) und [Organisatorisches](./#organisatorisches) | [Übung 0](./uebungen/#ubung-0) | - | - | 
| 2. | 23.-27.10.2023 | [HTML](./html/) | [Übung 1](./uebungen/#ubung-1) | Idee | 25.10.2022 | 
| 3. | 30.-03.11.2023 | [CSS (Eigenschaften und Selektoren](./css/#css) | [Übung 2](./uebungen/#ubung-2) | - | 01.11.2022 | 
| 4. | 06.-10.11.2023 | [CSS (Grid)](./css/#grid) | [Übung 3](./uebungen/#ubung-3) | Konzept | 08.11.2022 | 
| 5. | 13.-17.11.2023 | [RWD (responsive Webdesign)](./rwd/#responsive-web-design) | [Übung 4](./uebungen/#ubung-4) | - | 15.11.2022 | 
| 6. | 20.-24.11.2023 | [JavaScript (DOM)](./javascript/#javascript) | [Übung 5](./uebungen/#ubung-5) | Datenmodell | 22.11.2022 | 
| 7. | 27.-01.12.2023 | [Angular (Einführung und Komponenten)](./angular/#angular) | [Übung 6](./uebungen/#ubung-6) | Schnittstelle | 29.11.2022 | 
| 8. | 04.-08.12.2023 | [Angular (Bindings und Direktiven) + JSON](./angular2/#json-und-direktiven) | [Übung 7](./uebungen/#ubung-7) | Frontend (c+r)| 06.12.2022 | 
| 9. | 11.-15.12.2023 | [Angular (Routing und Services)](./routing/#routing-und-services) |  | Frontend (u+d)| 13.12.2022 | 
| 10. | 18.-22.12.2023 | [Node.js + Express (REST-Server + MongoDB)](./backend/#rest-api-mongodb) |  | Frontend fertig | 20.12.2021 | 
| | | | | | | |
| 11. | 01.-05.01.2024 | [Angular (Anbindung ans Backend)](./fe-be-anbindung/#frontend-backend-anbindung) |  | Backend ( c ) | 10.01.2023 | 
| 12. | 08.-12.01.2024 | [Nutzerverwaltung und Material](./guards/#subject-observable-observer-und-guards) | - | Backend (r + u) | 17.01.2023 |
| 13. | 15.-19.01.2024 | Wiederholung  | - | Backend (d + fertig)| 24.01.2023 |
| 14. | 22.-26.01.2024 | Wiederholung | - | fertig stellen | 31.01.2023 |
| 15. | 29.-02.02.2024 | - | Fragen | - | - |
| 16. | 05.-09.02.2024 | - | Fragen | Abgabe 1.PZ 13.2.2024, Gespräche 14.2.2024  |
|  |  |  |  |Abgabe 2.PZ 26.3.2024, Gespräche 27.3.2024 | - |

### Organisatorisches 

Zur erfolgreichen Durchführung der Veranstaltung müssen Sie die Übungen lösen und zu den jeweiligen Fristen per Git auf einen Server (GitHub oder GitLab) laden. Am Ende des Semesters ist eine Aufgabe abzugeben. Diese Aufgabe wird bewertet. Die Bewertung entspricht dann der Modulnote. 

[Hier](./uebungen/#ubungen) sind die Übungen beschrieben, die Sie in jeder Woche ausführen sollen. Damit Sie dies erfolgreich erledigen können, ist jeweils angegeben, welche Themen Sie dafür durcharbeiten müssen. Das Durcharbeiten der jeweiligen Themen entspricht jeweils einer Vorlesung. Diese wird also selbständig durchgeführt. 

Für die Kommunikation untereinander verwenden wir [**Slack**](https://slack.com/intl/de-de/). Dort können Sie alle inhaltlichen und organisatorischen Fragen stellen. Ich fände es gut, wenn ich dort möglichst wenig Fragen - zumindest die inhaltlichen - beantworten müsste, sondern eine Art internes Diskussionsforum entsteht. Es ist sehr gewünscht, dort Fragen zu stellen und noch mehr gewünscht, diese von Ihnen dort beantwortet zu sehen. Damit wäre allen geholfen und ich kann besser erkennen, wo noch Nachhol- bzw. Erläuterungsbedarf bei den meisten besteht.  

## Code aus der Vorlesung

??? question "Code Vorlesung 14.11.2023"
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
	            <li><a href="https://www.ecma-international.org/publications-and-standards/standards/ecma-262/">ECMA-262</a>
	            </li>
	            <li><a href="https://dom.spec.whatwg.org/">Document Object Model (DOM)</a></li>
	            <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide">JavaScript Guide</a></li>
	            <li><a href="https://www.w3schools.com/js/default.asp">JavaScript Tutorial</a></li>
	            <li><a href="https://learnjavascript.online/">Learn JavaScript</a></li>
	            <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference">JavaScript Reference</a>
	            </li>
	            <li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType?retiredLocale=de">Objekttypen im DOM</a>
	            </li>
	        </ul>
	        <h4>Ergebnisliste</h4>
	        <ul id="ulresult">
	            <li id="liresult1"></li>
	        </ul>
	        <input onchange="inputToList()" type="text" id="input"  placeholder="Name" />
	        <button type="button">Klick Mich!</button>
	    </main>
	    <script>
	        function helloFIW(name = 'World') {
	            console.log('Hello ' + name)
	        }

	        function inputToList() {
	            let input = document.getElementById('input');
	            let inputValue = input.value;
	            console.log('value :', inputValue)
	            let output = document.querySelector('#liresult1');
	            if(output.innerHTML == "") {
	                output.innerHTML = inputValue;
	                output.style.color = 'red';
	            } else {
	                let newLi = document.createElement('li');
	                let liste = document.querySelector('#ulresult');
	                console.log('ul : ', liste);
	                let newText = document.createTextNode(inputValue);
	                newLi.appendChild(newText);
	                liste.appendChild(newLi);
	            }
	            input.value = "";
	        }
	    </script>
	</body>

	</html>
	```

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

- 1. Prüfungszeitraum: 13.2. Abgabe und 14.2. Gespräch
- 2. Püfungszeitraum: 26.3. Abgabe und 27.3. Gespräch

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

