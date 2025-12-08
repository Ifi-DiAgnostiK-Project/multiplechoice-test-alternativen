<!--

author: Volker Göhler
email: volker.goehler@informatik.tu-freiberg.de
version: 0.0.2
date: 2025-11-28
edit: true
title: Testbed für Multiple Choice Tests in LiaScript
language: de
comment: UI mocks and design questions for DiAgnostiK LiaScript Courses

import: https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/LiaScript_DragAndDrop_Template/refs/heads/main/README.md
        https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/LiaScript_ImageQuiz/refs/heads/main/README.md

link: https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/LiaScript-Courses/refs/heads/main/courses/style.css

-->

# Testbed für Multiple Choice Tests in LiaScript

[![LiaScript Course](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://github.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/blob/main/README.md?raw=true)

Verschiedene Stimmen in der Benutzung unserer Multiple Choice Tests in LiaScript haben uns auf einige Probleme und Wünsche hingewiesen. Dieses Testbed soll helfen, diese Probleme zu analysieren und mögliche Lösungen zu testen.

## Probleme und Wünsche

Hauptproblem ist eine falsche Auffassung des Multiple Choice Tests Tools.
Entweder wir betrachten es in einem "Leistungskontrolle" Modus, oder in einem "Selbstlern" Modus.
- Bei einer Leistungskontrolle, hat der Delinquent nur einen Versuch, und die Bewerung seiner Leistung kann für Weiteres genutzt werden.
- In einer Selbstlernsituation soll der Lernende so oft üben können, wie er möchte, und idealerweise auch sofort Feedback bekommen.

Auf dieser Basis betrachtet können wir den Feedback einordnen:

- *Richtige* sollen markiert werden bei **check**, Bei zB 3 Versuchen werden jedesmal alle Richtigen markiert. Nur Sinnvoll für Selbstlernmodus.
- Wir verwalten einen Counter der Richtige pro Versuch zählt, und zeigen diesen am Ende an. Sinnvoll für beide Modi.
- **Jetztstand:** nur vollständig korrekte Antworten zählen als korrekt.

## Multiple Choice

Der in LiaScript integrierte MCQ.

### Kritikpunkte der Öffentlichkeit

Hier die Liste aus der Umfrage:

- 

### Jetzstand

- Antworten 2,3 und 4 sind richtig
- Antworten randomiziert
- Lösungsbutton ist aus
- drei maximale versuche

<!-- 
data-randomize
data-max-trials="3"
data-solution-button="off" 
-->
- [[ ]] Option 1
- [[x]] Option 2
- [[x]] Option 3
- [[x]] Option 4
- [[ ]] Option 5

Nur wenn alle Optionen korrekt sind, wird die Aufgabe als Korrekt gewertet.

Es gibt zwar `data-show-partial-solution` aber das funktioniert nicht mit MCQ.

### Idee 1 "markiert Lösungen"

Bei den Durchgängen wird die richtige Unterlösung entsprechend markiert. Nur Sinnvoll bei Selbstlernsituationen um kein "ich klick mich einfach durch" zu provozieren. Optional mit einem Counter.

![Version 1](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/version1.png)

### Idee 2 "Richtige Lösungen Zähler"

Wir nutzen als zusätzliches "Hint" Element einen Zähler, der richtige vs. total Verwaltet.

![Version 2](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/version2.png)

## Drag and Drop

Die "Drag and Drop"-funktionalität kommt aus: [unserem Repository](https://github.com/Ifi-DiAgnostiK-Project/LiaScript_DragAndDrop_Template)

Challenges
==========

- Ein `Compile` im LiveEditor reseted das Quiz nicht
- unklar welche parameter den beeinflussen


### Jetztstand

Try to order these items correctly by dragging and dropping them (hint: should be a sentence)!

<!-- 
data-randomize
data-max-trials="3"
data-solution-button="off" 
-->
@dragdroporder(@uid,solution|is|this|the,this|is|the|solution)

### Kritikpunkte der Öffentlichkeit

Hier die Liste aus der Umfrage:

- 

### Vorschlag 1

markiert wenn Reihenfolge stimmt

![einfaches Beispiel](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/DD_Text_1_marked.png)

ABER
=======

- Was machen wir wenn subreihenfolgen übereinstimmen!?

z.B. [Hamlet](https://en.wikipedia.org/wiki/To_be%2C_or_not_to_be)

<section class="flex-container border">
<div class="flex-child" style="width:300px;">
<!-- 
data-randomize
data-max-trials="2"
data-solution-button="off" 
-->
@dragdroporder(@uid,To|be|or|not|to|that|is|the|question|be,To|be|or|not|to|be|that|is|the|question)

</div>
<div class="flex-child">
![to be or not to be example](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/big_example.png)<!--style="max-width:350px;"-->
</div>
</section>

- hier haben wir 2 *richtige* Segmente "To be or not to" und "that is the question". Es muss nur noch "be" gesetzt werden.
- Die Darstellung mit richtige Reihenfolge markieren suggeriert aber das beide Segmente ein Segment sind. Das ist irreführend!
- Alternativ könnte man nur das größte Segment markieren, läuft dort aber ebenso in Probleme. Da nicht markierte Segmente ja auch richtig sein können.

## Multiple Choice Drag and Drop


Die Funktion kann Texte und Bilder verschieben!

Sie lebt im selben [Repository](https://github.com/Ifi-DiAgnostiK-Project/LiaScript_DragAndDrop_Template).

Challenges
==========

- unklar ob und welche parameter beachtete werden.

    - `data-max-trials`wird nicht beachtet!
    - 

- beim D&D resizen die boxen dynamisch, das ist etwas annoying
- doppelklick zum moven?
- Bildvariante ist auch sehr buggy!
- Drop targets Auswahl und Antwort sollten gleich gross sein

### Jetztstand

Die Komponente kann Texte und Bilder bearbeiten. Bei Bildern den vollen Pfad zur Datei angeben!

#### D&D mit Texten

Wähle gerade Zahlen:

<!-- 
data-randomize
data-max-trials="3"
data-solution-button="off" 
-->
@dragdropmultiple(@uid,2|4|6,1|3|5)


#### D&D mit Bildern
<!--
@house1: https://upload.wikimedia.org/wikipedia/commons/0/01/%22Short_Off%2C%22_Burke_County_School%2C_Built_of_Native_Stone_%286811940793%29.jpg
@house2: https://upload.wikimedia.org/wikipedia/commons/d/d2/Apex_School%2C_North_Carolina_%286811927511%29.jpg
@basket: https://upload.wikimedia.org/wikipedia/commons/5/5d/Baskets_on_display_at_the_Qualla_Arts_and_Crafts_Mutual_%288635531782%29.jpg
@cloths: https://upload.wikimedia.org/wikipedia/commons/c/c2/Clothing_exhibit_at_the_Reynolda_House_Museum_of_American_Art_%288635531538%29.jpg
@wood: https://upload.wikimedia.org/wikipedia/commons/e/ed/Ranger_Larry_Andrews_and_a_cross_section_of_a_175_year_old_Water_Oak_taken_from_the_Cape_Fear_River_basin_%288634423731%29.jpg

-->

Die Lösung sind die **Häuser** !!!

<!-- 
data-randomize
data-max-trials="3"
data-solution-button="off" 
-->
@dragdropmultiple(@uid, @house1|@house2, @basket|@cloths|@wood)

### Kritikpunkte der Öffentlichkeit

Hier die Liste aus der Umfrage:

- 

### Vorschlag 1 "Richtige vs. Geforderte"

Analog zu MCQ. gibt an wieviele choices gefordert sind.

![Version 1](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/DD_MPQ_1.png)


### Vorschlag 2 "Markiert Richtige"

Analog zu MCQ. Nicht nur Angabe wieviele Richtig sind, sondern auch welche richtige Picks sind.

![Version 2](https://raw.githubusercontent.com/Ifi-DiAgnostiK-Project/multiplechoice-test-alternativen/main/img/DD_MPQ_2.png)

## Drag and Drop Alternativen

- wir können die LiaScript selection Komponente nutzen um ein Drag and Drop durchzuführen
- das kann mit `->` in der Komponenten gemacht werden
- `[->[eins | zwei | (drei) ]]`

[->[eins | zwei | (drei) ]]

- das geht auch im Text!
- `dieser [->[Pferd | (Text)]] nutzt [->[Drops | (Drag)]] and [->[Trüffel | (Drop)]] Komponenten.`
- dieser [->[Pferd | (Text)]] nutzt [->[Drops | (Drag)]] and [->[Trüffel | (Drop)]] Komponenten.

### D&D mit Texten Alternative

`[->[eins | (zwei)]] [->[drei | (vier)]] [->[fünf | (sechs)]]`

Wählen Sie alle geraden Zahlen:

[->[eins | (zwei)]] [->[drei | (vier)]] [->[fünf | (sechs)]]

- Sortierung ist hierbei Wichtig!
- `[->[(Äpfel)]] [->[(Birnen)]] [->[(Bananen)]]`

[->[(Äpfel)]] [->[(Birnen)]] [->[(Bananen)]]

- gleiche Werte werden nicht gefiltert
- Die erste `5` ist die Lösung die zweite **Nicht**
- `[->[(3)|2]] + [->[(2)|3]] = [->[(5)|5]]`

> [->[(3)|2]] + [->[(2)|3]] = [->[(5)|5]]

## FAQ

- `Check`statt `Prüfen`: da fehlt `language: de` in der Preamble!
