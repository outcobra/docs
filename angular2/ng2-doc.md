# Angular 2 für Einsteiger

[TOC]

## Einleitung

### Ziel und Zweck

Dieses Dokument ist dafür da nicht erfahrene Entwickler einen Einblick in das JavaScript Framework Angular 2 zu geben.
Es werden die grundlegendsten Funktionen des Frameworks erläutert und es wird auch auf fortgeschrittene Funktionen aufmerksam zu machen.

### Zielgruppe

Das Dokument richtet sich an Entwickler, welche noch keinerlei Erfahrung mit Angular 2 haben soll aber auch als Nachschlagwerk dienen.

### Bemerkungen

Die Code Snippets, welche im folgenden Dokument werden, wurden entweder der Seite [angular.io](angular.io) entnommen oder vom Autor selber geschrieben.

Die englischen Namen, welche von Angular vorgegeben werden, werden in diesem Dokument nicht auf Deutsch übersetzt.

## Was ist Angular?

Angular ist ein JavaScript Framework, welches von Google Entwickelt wird. Die erste Version kam im Jahr 2009 heraus und trug den Namen AngularJS.
AngularJS wird bis heute noch weiterentwickelt und die aktuellste Version ist die 1.5.8 (Stand 20.09.2016).
Im Jahr 2014 hat Google damit begonnen Angular 2.0 zu entwickeln. Das Entwicklerteam hat sich entschieden das neue Framework in TypeScript zu schreiben. Mehr dazu im Kapitel Ty-peScript.
Am 15. September 2016 wurde die erste finale Version von Angular 2 released, diese Version trägt die volle Versionsnummer Angular 2.0.0.
Im Vergleich zu AngularJS soll es mit Angular 2 möglich sein Native und Desktop Apps zu programmieren. Diese Apps sollen, dann mit dem gleichen Code ausgeführt werden wie die WebApps, jedoch aber Zugriff auf die OS APIs Zugriff haben und so noch mehr Möglichkeiten zu erhalten.

In diesem Dokument werde ich mich grundsätzlich nur mit Angular 2 befassen.

### TypeScript

TypeScript ist eine Programmiersprache, welche in JavaScript kompiliert wird und bietet Fea-tures wie die statische Typisierung (im Gegensatz zu JavaScript), komplette Objektorientiert-heit

### Grob Architektur

Das untenstehende Diagramm zeigt die Grob-Architektur einer Angular 2 Komponente und ih-rer Abhängigkeiten.

Was alle diese einzelnen Komponenten bedeuten wird weiter unten erklärt.

![Angular 2 Grob Architektur](http://imgur.com/1ZFHoBN.png)

## Quickstart

Um einen kleinen Einblick in die einfachste Funktionsweise von Angular zu erhalten wird mit einem einfachen Fallbeispiel begonnen.
Es geht darum, dass man ein Array von Heroes auf der View anzeigt.

Bevor man mit dem programmieren beginnt muss man ein Angular 2 Projekt erstellen. Am besten geht das in dem man den [angular2-seed](https://github.com/angular/quickstart/blob/master/README.md) über git klont oder dem [quickstart guide](https://angular.io/docs/ts/latest/quickstart.html) auf angular.io folgt.

Nachdem man jetzt ein Starter Projekt hat empfiehlt es sich den Quellcode in einer IDE zu öff-nen. Es wird empfohlen [IntelliJ IDEA](https://www.jetbrains.com/idea/) oder [WebStorm](https://www.jetbrains.com/webstorm/) zu gebrauchen.

Im Repository des Quickstarts ist schon eine Komponente mit dem Namen `app.component.ts` vorhanden.
Der Inhalt dieser Datei kann jetzt mit dem folgenden Code Snippet ersetzt werden.

```typescript
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `
        <h1>{{title}}</h1>
        <ul>
            <li *ngFor="let hero in heroes">
                {{ hero }}
            </li>
        </ul>
    `
})
export class AppComponent {
    title = 'My Heroes';
    heroes = ['Windstorm', 'Bombasto', 'Magneta', 'Tornado'];
}
```

Jetzt kann man den Entwicklungsserver mit `npm start` starten und der Browser sollte sich automatisch und eine Seite anzeigen, welche so aussieht wie das untenstehende Bild. 

![heroes-list](http://imgur.com/LpPLYU6.png)

Wie man sieht ist das Starten mit Angular 2 sehr einfach und vorallem ist die ganze Syntax mit TypeScript sehr einfach zu verstehen und nach zu vollziehen.

## Grundlegende Framework Eigenschaften

In Angular 2 gibt es Dinge die immer wieder auftauchen und über das ganze Framework im-mer wieder die gleiche Funktion bzw. Funktionsweise haben. Diese Teile werden in diesem Kapitel beschrieben.

### Decorators

Decorators (dt. Dekorierer) sind zu Vergleichen mit Annotations in Java oder anderen Spra-chen. Die Decorators sind dafür da Angular zu sagen, dass eine TypeScript Klasse zu Angular gehört bzw. eine bestimmte Funktion in Angular erfüllt. Sie werden auch benötigt um bestimm-te Metadaten an Angular zu liefern. Was für Metadaten das sind, wird dort erklärt wo die De-corator explizit verwendet werden.

Beispiel:

```typescript
@Directive({
    selector: 'hero-directive'
})
```

Ein Decorator ist eigentlich eine Funktion, welche ein Objekt als Parameter nimmt. Das Objekt hat dann (je nach de Decorator) vorbestimmte Eigenschaften.
Bei einer Component oder einer Directive ist das zum Beispiel der Selektor, wie im obigen Bei-spiel.
Die Directive könnte jetzt, bei richtiger Importierung, in einem Template File einer Component mit `<hero-directive></hero-directive>` angesprochen werden.
Die wichtigsten Parameter eines Decorators werden an der Entsprechenden Stelle im Doku-ment erläutert.

Ein Decorator erkennt genau wie eine Annotation am @-prefix.

Eine Liste aller Decorator findet man [hier](https://angular.io/docs/ts/latest/api/#!?apiType=Decorator).

### Dependency Injection

Wie viele moderne Frameworks benutzt auch Angular 2 Dependency Injection.

Bei der Dependency Injection erstellt eine Klasse die Instanzen der Abhängigkeiten nicht selbst, sondern bekommt diese mithilfe des Konstruktors mitgegeben. In Angular werden meis-tens die Services in den Components injiziert.

Damit ein Service injiziert werden kann muss er zuerst als Provider registriert werden. Die Re-gistrierung erfolgt in der Komponente oder im Modul.

Wie genau die Registrierung funktioniert wird in den unten verlinkten Kapitel erklärt.
TODO LINK

### Allgemeine Lifecycle Hooks

Die Components und Directives von Angular haben verschiedene Lifecycle Hooks, welche von Angular gemanagt werden.
Die untenstehenden Hooks gelten für Components, wie auch für Directives.

| Name        | Beschreibung                             |
| :---------- | :--------------------------------------- |
| ngOnChanges | Wenn die Werte von Input Properties geändert werden |
| ngOnInit    | Nach dem Initialisieren der Component direkt nach dem Konstruktor |
| ngDoCeck    | Wird bei jeder Änderung an einer Component getriggered, umfasst sehr viel Änderung, welche durch Angular gemacht werden. Wird sehr häufig aufgerufen. |
| ngOnDestroy | Wird aufgerufen bevor Angular die Component definitiv zerstört. |

Um die Lifecycle Hooks in einer Component bzw. Directive zu aktivieren muss man ein ent-sprechendes Interface implementieren. Der Name des Interfaces ist immer der Name des Hooks ohne den Prefix „ng“.

```typescript
export class PeekABoo implements OnInit {
  constructor(private logger: LoggerService) { }

  // implement OnInit's `ngOnInit` method
  ngOnInit() { this.logIt(`OnInit`); }

  protected logIt(msg: string) {
    this.logger.log(`#${nextId++} ${msg}`);
  }
}
```

Die Components haben noch eigene Hooks, welche im Kapitel zu den Components gefunden werden kann.

Genauere und bessere Dokumentation zu den Lifecycle Hooks kann [hier](https://angular.io/docs/ts/latest/guide/lifecycle-hooks.html) gefunden werden.

## Architektur und Hauptbausteine

![NgModule Overview](http://imgur.com/V6NzPf5.png)

Auf dem Diagramm sieht man die acht Hauptbestandteile von Angular 2.

•	Modules
•	Components
•	Template/View
•	Metadata
•	Data Binding
•	Directives
•	Services
•	Dependency Injection

Logischerweise besteht das ganze Framework nicht nur aus diesen acht Komponenten.
Jedoch sind diese acht Bestandteile die Grundbausteine und man sollte alle kennen und wis-sen für was sie da sind.

Die Code Snippets beziehen sich meistens auf den Code im angular/quickstart Repository.

### Modules (NgModule)

Eine Angular App ist in verschiedene Module aufgebaut, jedes Modul ist in den meisten Fällen ein Teilsystem.
Ein Modul muss immer vorhanden sein, denn man muss beim Start der Applikation ein Modul „bootstrapen“.

Ein Modul ist eine TypeScript-Klasse, welche mit einem NgModule Decorator ausgestattet ist. Die wichtigsten Eigenschaften für das Objekt im NgModule Decorator werden im folgenden Teil aufgelistet und kurz beschrieben.

| Name           | Typ   | Beschreibung                             |
| -------------- | ----- | ---------------------------------------- |
| `declarations` | Array | Beinhaltet alle im Modul definierten „view classes“ (Components, Directives, und Pipes). |
| `exports`      | Array | Beinhaltet alle „view classes“, welche in anderen Modulen sichtbar sein sollen. |
| `imports`      | Array | Beinhaltet andere Module, welche in den „view classes“ dieses Moduls importierbar sein sollen. |
| `providers`    | Array | Alle Services, welche in diesem Modul definiert werden. Sind danach in der ganzen Applikation verfügbar. |
| `bootstrap`    | Array | Die Hauptview einer Applikation, welche beim Start der Applika-tion gebootstrapped werden soll. |

#### Bootstrappen des Root Modules

Der Code unten beschreibt unser Root Modul. Das Root Modul wird die Component AppCom-ponent starten und anzeigen, wie die AppComponent aussieht spielt für dieses Beispiel keine Rolle.

```typescript
import { NgModule }      from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
@NgModule({
    imports:      [ BrowserModule ],
    providers:    [ Logger ],
    declarations: [ AppComponent ],
    exports:      [ AppComponent ],
    bootstrap:    [ AppComponent ]
})
export class AppModule { }
```

```typescript
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app.module';

platformBrowserDynamic().bootstrapModule(AppModule);
```

Um das AppModul zu bootstrappen muss man in der main.ts Datei die obenstehenden Module importieren und dann kann das Modul mit der letzten Zeile gebootstrapped werden.

Mehr und genauere Informationen zu NgModule findet man [hier](https://angular.io/docs/ts/latest/guide/ngmodule.html).

### Components

Eine Component ist eine Klasse, welche eine View kontrolliert.
In der Klasse wird die ganze Logik für die View programmiert. Dazu gehört das „handeln“ von Events oder das Kommunizieren mit Services.

Jedes Attribut einer Component-Klasse ist von der View aus ansprechbar. Mehr dazu im Kapi-tel Templates.

#### Lifecycle Hooks

Eine Component hat einen bestimmten Lifecycle, welcher von Angular gemanagt wird.
Zusätzlich zu den im Kapitel **Allgemeine Lifecycle Hooks** beschriebenen Hooks umfassen die Components noch die folgenden Hooks.

#### Beispiel Component

Diese Component holt sich eine Liste von Helden von dem HeroService, welcher im Konstruk-tor direkt als Attribut der Klasse injiziert wird.
Mit der Methode selectHero kann noch ein Held ausgewählt werden.

```typescript
export class HeroListComponent implements OnInit {
  heroes: Hero[];
  selectedHero: Hero;

  constructor(private service: HeroService) { }

  ngOnInit() {
    this.heroes = this.service.getHeroes();
  }

  selectHero(hero: Hero) { this.selectedHero = hero; }
}
```

### Template/View

In Angular wird die HTML-Struktur mittels Templates bestimmt. Eigentlich sieht eine Template Datei auch aus wie eine HTML-Datei und wird auch mit der Dateiendung .html gespeichert, je-doch hat ein Template in Angular noch Angular spezifische Unterschiede.

Als Beispiel ein passendes Template für die HeroListComponent von oben.

```html
<h2>Hero List</h2>
<p><i>Pick a hero from the list</i></p>
<ul>
  <li *ngFor="let hero of heroes" (click)="selectHero(hero)">
    {{hero.name}}
  </li>
</ul>
<hero-detail *ngIf="selectedHero" [hero]="selectedHero"></hero-detail>
```

Wie man sieht hat es normale HTML-Elemente, wie auch neue Tags wie das hero-detail-Tag. Dieses Tag repräsentiert wieder eine Component mit dem Selektor „hero-detail“.
Für diese ChildComponent ist auch wieder ein ähnliches Template definiert, welches vielleicht auch wieder eine andere Component als Child hat.

Daraus folgt, dass man in den Templates beliebig viele ChildComponents haben kann.

### Metadata

Wenn man die obige Component genau anschaut, sieht man, dass es nichts gibt woran man erkennen würde, dass es eine Component ist. Um eine Klasse für Angular als Component sichtbar zu machen braucht es einen @Component-Decorator.
Dieser nimmt wie schon im Kapitel **Decorators** erklärt ein Objekt als Funktionsparameter.

Die wichtigsten Eigenschaften dieses Objekts sind nachfolgend aufgelistet.

| Name          | Typ    | Beschreibung                             |
| ------------- | ------ | ---------------------------------------- |
| ` selector `  | String | HTML-Selektor, welcher verwendet wird um diese Component in den Templates zu verwenden. |
| `templateUrl` | String | Pfad zur Template-Datei                  |
| `template`    | String | Template als String oder als [Template-String](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/template_strings) |
| `directives`  | Array  | Alle in dieser Component verwendeten Directives. |
| `providers`   | Array  | Alle in dieser Component verwendeten Services. |

Eigentlich bilden die Component-Klasse die Template-Datei und die Metadaten eine Component. Wenn ein Teil fehlt funktioniert es nicht.

### Data Binding

Da die Component-Klasse die View mit Daten abfüllen soll und die View die Klasse über Events informieren soll muss eine Verbindung dazwischen bestehen.

Es gibt drei Verbindungsarten.

```typescript
<li>{{hero.name}}</li>
<hero-detail [hero]="selectedHero"></hero-detail>
<li (click)="selectHero(hero)"></li>
```

•	Interpolation – `{{ hero.name }}` zeigt den Wert name vom hero Objekt in der Component an.
•	Property Binding – setzt die die Eigenschaft vom Element auf den Wert von dem `selectedHero` Attribut
•	Event Binding – führt die Methode `selectHero` mit dem Funktionsparameter `hero` aus

Zudem gibt es noch das Prinzip des Two-Way-Data Binding. Das wird meistens bei Inputfeldern verwendet.
Da diese Art des Bindens das Property Binding und das Event Binding kombiniert wird es wie folgt verwendet.

```html
<input [(ngModel)]="hero.name">
```

 In diesem Beispiel hat das Attribut hero.name in der Component und das Input-Feld immer den gleichen Wert.
Wenn jetzt neben dem Inputfeld noch `hero.name` mit Hilfe von Interpolation angezeigt wird, wird auch das immer den gleichen Wert haben wie das Input-Feld.

### Directives

In Angular ist eine Component eigentlich eine Directive mit einem Template. Das sieht man auch daran, dass der `@Component` Decorator vom `@Directive` Decorator erbt und diesen nur noch mit Templateorientierten Attributen erweitert (templateUrl etc.).

Directives werden häufig dafür gebraucht einen bestimmten Style zu einem Element hinzuzufügen. Zum Beispiel kann man ein Input Feld ganz einfach grösser werden lassen sobald man in das Feld klickt, in dem man eine eigene Directive erstellt und diese dem Input-Feld hinzu-fügt.
Mehr Informationen findet man im Kapitel **Directives**.

### Services

Ein Service ist eine ganz einfache TypeScript-Klasse, welche verschiedene Funktionen in sich hat und einem bestimmten Fachgebiet zugeordnet ist. Jeder Service kann allen in Modulen durch die Dependecy Injection injiziert werden, dabei ist aber zu achten, dass der Service in einem Modul als Provider registriert wurde.

Man kann fast alles in einer Angular 2 Applikation in einen Service packen. 
Beispiele: 
•	Kommunikation mit einer API (z.B. REST)
•	Logger
•	Zins-Rechner

## Directives

In Angular 2 gibt es drei verschiede Arten von Directives.
•	Components
•	Attribute Directives
•	Structural Directives

Components
Eine Component ist eigentlich eine Directive mit Template und ist die meist verwendete Art ei-ner Directive. Aus Components besteht der grösste einer Angular 2 App.

Attribute Directives
Eine Attribute Directive kann das Verhalten und das Aussehen eines DOM-Elementes ändern. Ein Beispiel dafür ist die **NgStyle** Directive.

Structural Directives
Eine Structural Directive ändert die Struktur des DOMs. Es können Elemente hinzugefügt und gelöscht werden. Angular 2 bringt unter anderem **ngFor** und **ngIf** als Structural Directives mit sich.

### Built-in Directives

#### Structural Directives

##### ngFor

Die NgFor Directive ist wie eine foreach-Schleife in einer anderen Programmiersprache. Der einzige Unterschied ist, dass ngFor explizit auf das DOM ausgerichtet ist.

Es erstellt für jedes Element anhand eines Template ein neues DOM-Element.
Im untenstehenden Beispiel wird für jedes item ein neues listitem erstellt.

```html
<ul>
    <li *ngFor="let item of items">{{ item.itemName }}</li>
</ul>
```

In der zugehörigen Component-Klasse muss natürlich eine Eigenschaft `items` vom Typ Array bestehen, welcher `item`-Objekte mit einer `itemName`-Eigenschaft enthalten.

Neben der ganz trivialen Verwendung nach obigem Beispiel gibt es auch noch diverse Variablen, welche die **NgFor** Directive exportiert und die wir als lokale Template Variablen entgegen-nehmen können.

```html
<ul>
    <li *ngFor="let item of items; let i = index; let odd = odd">
        {{ item.itemName }}
    </li>
</ul>
```

Wichtig ist auch noch, dass man weiss, das sobald man die iterierte Eigenschaft der Component-Klasse ändert automatisch auch das ngFor neu durchlaufen wird. Genau das gleiche trifft auch auf die zwei folgenden Directives zu.

##### ngIf

Die NgIf Directive ist ganz einfach zu verstehen und macht genau das, was man erwartet. Es wird ein Wahrheitswert überprüft, welcher darüber entscheidet ob ein Element im DOM existieren soll oder nicht.

```html
<p *ngIf="foo">
    foo is true
</p>
<p *ngIf="!foo">
    foo is false
</p>
```

Wenn der der Wahrheitswert falsch ergibt wird das Element komplett entfernt und ist nicht mehr im DOM vorhanden. Das verhindert unerwartetes Verhalten von DOM-Elementen, welche eigentlich gar nicht mehr gebraucht werden dürften.

##### ngSwitch

Auch NgSwitch funktioniert wie in anderen Sprachen und erfüllt eine ähnliche Aufgabe wie NgIf.

```html
<div [ngSwitch]="foo">
    <span *ngSwitchCase="'case1'">It's case 1</span>
    <span *ngSwitchCase="'case2'">It's case 2</span>
    <span *ngSwitchDefault>It's neither case 1 nor case 2</span>
</div>
```

Genau gleich wie bei NgIf werden auch hier die DOM-Elemente komplett entfernt, um die oben angesprochene Problematik zu umgehen.

#### Attribute Directives

##### ngStyle

Mit der NgStyle Directive kann man dynamisch den Style eines DOM-Elements ändern. Vielmals wird dies über einen Wert in der Component-Klasse gesteuert.

```html
<p [style.font-size]="isBig ? '24px' : '12px'">
    Is it big?
</p>
```

Das obige Beispiel ist die Kurzversion zum Setzen von bestimmten Styles über eine Eigenschaft bzw. einer Methode. Das gezeigte ist das einfache Style Binding, welches zu der Grup-pe der Property Bindings gehört.

Mit der NgStyle Directive lassen sich im Gegensatz zum Style Binding einfacher mehrere Styles gleichzeitig auf das gleiche Element anwenden.

Dafür eignet sich die folgende Methode in der Component.

```typescript
setStyles() {
    let styles = {
        // CSS property names
        'font-style':  this.canSave      ? 'italic' : 'normal',  // italic
        'font-weight': !this.isUnchanged ? 'bold'   : 'normal',  // normal
        'font-size':   this.isSpecial    ? '24px'   : '8px',     // 24px
    };
    return styles;
}
```

Im Template sieht es dann so aus.

```html
<div [ngStyle]="setStyles()">
    This div is italic, normal weight, and extra large (24px).
</div>
```

Die NgStyle Directive erwartet ein Objekt mit Key-Value Pairs, wo der Key die CSS-Eigenschaft ist und der Value den Wert dieser Eigenschaft ist.

Das Verwenden von NgStyle macht es zwar einfach die Styles eines Elementes dynamisch zu ändern, jedoch kann es sehr schnell unübersichtlich werden sobald viele verschieden CSS-Eigenschaften gleichzeitig geändert werden sollen. Dafür gibt es im folgenden Kapitel den be-schrieb der NgClass Directive.

##### ngClass

NgClass funktioniert ähnlich wie NgStyle, jedoch bietet es eine klarere Trennung zwischen Layout und Style der Webseite. Die Definierung der Styles bleibt in den CSS-Dateien und das Layout wird immer noch in den HTML-Dateien definiert.

Auch wie das Style Binding gibt es auch eine vereinfachte Art von NgClass. Das nennt man Class Binding und funktioniert wie folgt.

```html
<div [class.fancy]="isItFancy()">
    Sometimes I am fancy.
</div>
```

Der Wert, welcher beim Class Binding übergeben wird muss ein Boolean sein, jedoch ist es egal wie dieser Boolean ermittelt wird.

```typescript
setClasses() {
    let classes =  {
        saveable: this.canSave,      // true
        modified: !this.isUnchanged, // false
        special: this.isSpecial,     // true
   };
   return classes;
}
```

Genau gleich wie bei NgStyle wird auch hier den Rückgabewert der setClasses Funktion der NgClass Directive übergeben.

```html
<div [ngClass]="setClasses()">This div is saveable and special</div>
```

### Custom Directives

#### Attribute Directives

Wie im Kapitel **Directives** beschrieben ist eine Directive eine TypeScript Klasse mit dem `@Directive` Decorator und wird häufig für das anwenden bestimmter Styles auf einem Ele-ment gebraucht.

Alternativ kann eine Directive erstellt werden, welche beim Klick auf ein Element fragt ob man eine Aktion wirklich durchführen will. Dies wird häufig gebraucht, wenn es darum geht ein Da-tensatz zu löschen.

**Beispiel:**

```typescript
@Component({
  selector: 'visit-on-github',
  template: `
    <button type="button" (click)="visitOnGithub()" confirm>Visit OutCobra on GitHub</button>
  `
})
export class VisitOnGithubComponent {
  visitRangle() {
    location.href = 'https://github.com/outcobra';
  }
}
```

```typescript
@Directive({
  selector: `[confirm]`
})
export class ConfirmDirective {

  @HostListener('click', ['$event'])
  confirmFirst(event: Event) {
    return window.confirm('Are you sure you want to do this?');
  }
}
```

Im Beispiel wird der User jetzt gefragt ob er wirklich auf die andere Wechseln möchte.

Mit dem `@HostListener ` Decorator kann man in einer Attribute Directive Events vom Host bzw. dem Holder der Directive entgegennehmen und bearbeiten.

Beim `@HostListener` Decorator sind alle Events möglich, welche auch als Event Binding verfügbar sind.

Es ist auch möglich mit dem `@Input` Decorator Inputvariablen festzulegen. Diese funktionieren genau gleich wie bei den Components. Genaueres findet man im Kapitel **Advanced Components > Input**.

#### Structural Directives

## Forms

## HTTP

Um echte Daten in Angular 2 zu brauchen, muss man früher oder später sich mit einem Server verbinden und mit diesem die erforderlichen Daten austauschen.

In den meisten Fällen hat man eine REST-API als Backend, mit welcher man kommuniziert. Wie das Backend genau gebaut ist spielt für Angular keine Rolle, man muss nur wissen welche Endpoints, also Ansprechstellen, in der API existieren und was sie für Daten liefern bzw. erfordern.

Da die Kommunikation über HTTP/S läuft hat man alle die bekannten HTTP-Methoden wie **GET**, **POST**, **PUT**, **PATCH** und **DELETE** zur Verfügung.

Um die oben genannten Methoden zu nutzen gibt es die `Http` Klasse in `@angular/http`.
Diese Klasse bietet für alle Methoden eine eigene gleichnamige Funktion, welche immer eine `url` als Parameter braucht und teilweise noch einen `RequestBody` (nur bei post, put und patch). Es besteht auch immer die Möglichkeit `RequestOptions` hinzuzufügen, dies ist immer der letzte Parameter der jeweiligen Funktion.

Alle Funktionen geben ein Observable vom Typ `Response` (`Observable<Response>`) zurück, welches dann an beliebigen Orten weiterverarbeitet werden kann.
Das verwendete Observable ist eine leicht angepasste Version von dem RxJS Observable.

Mehr zu RxJS gibt es am Ende dieses Kapitels. In den Beispielen werden schon RxJS spezifische Dinge gebraucht daher empfiehlt es sich sich zuerst das **RxJS** Kapitel anzuschauen.

Alle Zugriffe auf einen Server werden in Services abgehandlet.

In den unteren Beispiel wird ein HeroService verwendet, welcher in einer Component des gleichen Moduls injiziert werden kann. Natürlich muss der Service als Provider im NgModule registriert werden.

### GET

Mit GET werden Daten vom Server geholt.

```typescript
  private heroesUrl = '/heroes';  // URL to web api

  constructor(private http: Http) { }

  getHeroes(): Observable<Hero[]> {
    return this.http.get(this.heroesUrl)
               .map(response => response.json().data as Hero[]);
  }
```

In der Methode `getHeroes` wird ein Observable vom Type Hero[] zurückgegeben, wir können danach in einer beliebigen Component diesem Observable "subscriben" und somit die Daten, welche in im `data` Objekt der Response sind, entgegennehmen.

```typescript
@Component({
  selector: 'heroes'
  template `
		<div *ngFor="let hero of heroes">
			{{ hero.name }}
		<div>
	`
})
export class HeroComponent implements OnInit {
  private heroes: Hero[];
  
  constructor(private heroService: HeroService) {}
  	
  ngOnInit() {
    this.heroes = this.heroService.getHeroes()
    	.subscribe(data => this.heroes = data);
  }
}
```

Sobald das Observable die Daten vom Server bekommen hat werden die Heroes in die Component lokale Variable gespeichert und die  Daten in der View werden automatisch aktualisiert.

### POST, PUT, PATCH

POST und PUT wird dafür gebraucht auf dem Server neue Ressourcen anzulegen oder bereits bestehende zu verändern. Hingegen wird mit PATCH nur ein Teil einer Ressource aktualisiert.

Jedoch sind alle drei Methoden in Angular 2 sehr ähnlich und werden hier zusammengefasst.

```typescript
private heroesUrl = '/hero';  // URL to web api

  constructor(private http: Http) { }

  updateHero(hero: Hero): Observable<Hero[]> {
    let body = JSON.stringify(hero);
    let headers = new Headers({ 'Content-Type': 'application/json' });
	let options = new RequestOptions({ headers: headers }):

    return this.http.post(this.heroesUrl, body, options)
               .map(response => response.json());
  }
```

Jetzt kann genau gleich wie bei GET in der Component dem Observable subscribed werden und die Rückgabe des Servers entsprechend bearbeitet werden.

Der Rückgabewert des Servers unterscheidet sich natürlicherweise je nach Implementation der REST-API und kann hier nicht generalisiert werden, jedoch ändert sich das Prinzip nicht.

Wie man sieht gibt es jetzt einen zweiten und dritten Parameter, welche zum ersten der Request Body und zum zweiten die Request Headers sind.
Der Body muss momentan noch mit `JSON.stringify` serialisiert werden, jedoch sollte dies mit einer zukünftigen Version von Angular überspringbar sein (aktuelle Version 2.1.0).
Die Headers sind ein RequestOptions Objekt, welches als Konstruktor Parameter unter anderem ein Objekt mit dem Key `headers` entgegennimmt. Für mehr Informationen zu [Headers](https://angular.io/docs/ts/latest/api/http/index/RequestOptions-class.html) und [RequestOptions](https://angular.io/docs/ts/latest/api/http/index/Headers-class.html) einfach auf ihre Namen klicken.

### DELETE



### Error Handling

### Promise oder Observable

### RxJS

## Routing

## Advanced Components

### Input

### Events

## Pipes

### Built-in Pipes

## Custom Pipes

## Security

## Glossar

| ID   | Bezeichnung  | Beschreibung                             |
| ---- | ------------ | ---------------------------------------- |
| 1    | Komponente   | Bestandteil eines Systems                |
| 2    | Component    | Angular 2 Component (`@Component({})`)   |
| 3    | view classes | Übername für Components, Directives und Pipes |
| 4    | View         | Synonym für Template oder einfach das für den User sichtbare |
| 5    | RxJS         | Reactive Extensions for JavaScript ([RxJS](https://github.com/Reactive-Extensions/RxJS)) |





