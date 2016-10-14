# Angular 2 für Einsteiger

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

![Angular 2 Grob Architekture](http://imgur.com/1ZFHoBN)

## Quickstart

## Grundlegende Framework Eigenschaften

### Decorators

### Dependency Injection

### Allgemeine Lifecycle Hooks

## Architektur und Hauptbausteine

### Modules (NgModule)

#### Bootstrappen des Root Modules

### Components

#### Lifecycle Hooks

#### Beispiel Component

### Template/View

### Metadata

### Data Binding

### Directives

### Services

## Directives

### Built-in Directives

#### Structural Directives

##### ngFor

##### ngIf

##### ngSwitch

#### Attribute Directives

##### ngStyle

##### ngClass

### Custom Directives

#### Attribute Directives

#### Structural Directives

## Forms

## HTTP

### GET

### POST

### PUT

### DELETE

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





