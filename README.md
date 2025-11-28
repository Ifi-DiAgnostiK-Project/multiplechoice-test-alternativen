<!--

author: Volker Göhler
email: volker.goehler@informatik.tu-freiberg.de
version: 0.0.1
date: 2025-11-28
edit: true
title: Testbed für Multiple Choice Tests in LiaScript
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
- **Jetzt** nur vollständig korrekte Antworten zählen als korrekt.

