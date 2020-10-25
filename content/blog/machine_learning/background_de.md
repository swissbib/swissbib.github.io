---
title: "Warum maschinelles Lernen im swissbib Projekt"
description: "Warum maschinelles Lernen"
date: 2020-07-18T15:50:09+02:00
draft: false

tags: [project information, deutsch, 2020]
categories: [Machine Learning]

---



Seit gefühlt zwei, drei Jahren lassen sich kaum mehr Artikel zum Thema Daten und Informationen finden, in denen nicht mindestens einmal  Begriffe wie "Maschinelles Lernen", "Künstliche Intelligenz" (KI) oder "Neuronale Netze" erwähnt und als das Erfolgsrezept für die Zukunft beschrieben werden. Sollte damit das, was wir in den letzten 12 Jahren gemacht haben, veraltet und nicht mehr relevant sein? Das swissbib Team ist ja nicht dafür bekannt, sich vor neuen Softwaretechnologien zu scheuen. Wir schauen schon seit je her regelmässig über den Tellerrand um mitzubekommen, ob sich neue Methoden nicht mit unseren klassischen Methoden verbinden lassen. Das Problem dabei: Bevor man aus der Menge des Möglichen etwas Vielversprechendes wählen, ausprobieren und dann vielleicht produktiv einsetzen kann, muss man sich erstmal durch die Grundlagen und Begrifflichkeiten des neuen Themengebiets kämpfen. Nicht so einfach für ein swissbib Team, dass mit Personen nicht üppig ausgestattet ist und den Laden (sprich die "grünen, orangenen oder wie auch immer farbigen Services") am Laufen halten muss.


Helfen kann in so einer Situation manchmal Begeisterung für die Sache, Offenheit (auch von Software) und ein Netz von Personen von ausserhalb unseres Bibliothekskuchens, die man neugierig auf coole Projekte mit unseren Daten machen kann. So geschehen mit [Andreas Jud](https://www.linkedin.com/in/andreas-jud-2a39a770/), ein swissbib-Freund, der sich in einer Weiterbildung an der [EPF Lausanne](https://www.extensionschool.ch/applied-data-science-machine-learning) mit Methoden des maschinellen Lernens beschäftigt hat. Im Rahmen seines Abschlussprojekts hat er untersucht, welche der zahlreichen Methoden sich für das Clustern von bibliographischen Metadaten einsetzen lassen. In dieser Blog-Serie wird er in die ausgewählten Methoden und Ergebnisse einführen. Die komplette Projektarbeit ist als eine Serie von [Jupyter Notebooks](https://github.com/swissbib/clustering_metadata) frei verfügbar.


Im swissbib Projekt ist die Essenz all unserer Aktivitäten der Umgang mit und die Aufbereitung von (Meta-) Daten. Normalisieren, Anreichern, Zusammenführen  (Clustern) sowie Verknüpfen von Informationen und dies alles auf maschineller Basis ist die Grundlage dafür, dass wir Services wie verschiedene Discoveries, unterschiedliche Schnittstellen oder Dienstleistungen für Dritte anbieten können. Vor allem für das maschinelle Clustern von Daten nutzen wir die (kommerzielle) Software eines Partners, die es uns flexibel ermöglicht, Daten so aufzubereiten, dass man sie für die unterschiedlichen Services einsetzen kann. Dies war über die Jahre kein einmaliger Vorgang mit einem statischen Resultat sondern ein iterativer Prozess, in denen sowohl wir (in den letzten Jahren vor allem unsere Kollegin Silvia Witzig) von der Nutzerinnenseite als auch unser Partner gegenseitig Wissen in den Prozess zur Verbesserung der Datenaufbereitung einbrachten. Die Aktivitäten zur Datenaufbereitung bleiben zentral für die Qualität der Dienstleistungen, die swissbib erbringt.


Maschinelles Lernen basiert auf Daten. Daten von swissbib sind daher die Basis der Abschlussarbeit von Andreas an der EPFL. Mit den Daten, die Andreas in ihrer Rohform vom swissbib Team erhalten hat, lassen sich Ergebniscluster von überzeugender Qualität ermitteln. Dies sei an dieser Stelle bereits vorweggenommen. Nach Abschluss der Arbeit bleiben aber Bereiche, an denen gearbeitet werden muss, um die Resultate in einen produktiven Betrieb zu überführen.

- Die Projektarbeit von Andreas hatte ihren Schwerpunkt im Gegenüberstellen unterschiedlicher Methoden des maschinellen Lernens. Fragen zur Skalierung der Datenmengen (wie wir sie im swissbib Projekt mit 45 Millionen Aufnahmen bewältigen müssen) konnten nicht berücksichtigt werden. Dieser offene Punkt muss noch angegangen werden. Die Bildung von sogenannten pre-cluster auf der inhaltlichen sowie der Einsatz von Frameworks zur verteilten Verarbeitung wie Apache Flink auf der technischen Ebene sind hier vielversprechende Ansätze.
- Auch wenn die Ergebnisse der Abschlussarbeit vielversprechend und die Möglichkeiten moderner offener Software noch so cool sind, bleibt der alte Spruch "garbage in, garbage out". Modelle des maschinellen Lernens müssen trainiert werden und die in die Modelle einfliessenden Daten von möglichst guter Qualität sein.  Für diesen Prozess braucht es sowohl Menschen, die sich mit Daten, deren Formaten aber auch deren Inhalten auskennen, wie auch Personen auf der Softwareseite. Mit unseren swissbib Erfahrungen bringen wir Know-How auf beiden Seiten ein und werden auch versuchen, in den anstehenden Monaten unsere Expertise, die wir mit unserer produktiven Komponente gesammelt haben und die uns nach wie vor hervorragende Ergebnisse liefert, noch besser zu dokumentieren. Damit erhoffen wir uns, Wissen zu erhalten als auch weiterzugeben. Zudem möchten wir dieses Wissen natürlich in verschiedenen Verfahren, wie zum Beispiel Maschinelles Lernen, einsetzen können und dadurch auch die Chance für Bibliotheken zur Weiterentwicklung nutzen.
- Die Rohdaten, welche für das Trainieren von Maschinen verwendet wurden, haben noch nicht die Ausprägung und Qualität, wie wir sie in Jahren auf unserer produktiven Maschine aufbauen konnten. Ein nächster Schritt muss darin bestehen, auf unseren Swissbib-Datenstandard aufzusetzen.
- Als Freizeitprojekt gestartet, bieten die erarbeiteten Resultate Einstiegsmöglichkeiten für Personen mit unterschiedlichem Hintergrund. Es war erfreulich zu beobachten, wie Andreas als promovierter Physiker mit Interesse und Ausdauer die MARC-Regeln der LOC studiert und den Input aus unserem swissbib Team für sein Arbeit aufgenommen hat. Das nun vorliegende Ergebnis, wie maschinelles Lernen auf den Bereich der Aggregation von bibliographischen Metadaten (Clustern) angewendet werden kann, bietet die Möglichkeit, die Magie besser zu fassen, die mit maschinellem Lernen und KI einhergeht. Dies auch für Menschen mit einem informationswissenschaftlichen und weniger technischen Hintergrund.

Wir freuen uns, wenn Sie unsere Blogserie zum Thema Deduplizierung von bibliographischen Daten mit Methoden des Maschinellen Lernens mitverfolgen. Noch mehr freut uns die aktive Teilnahme am Themengebiet und der Diskussion darüber.
Unter diesen links erhalten Sie den Zugriff auf die einzelnen Teile der dreiteilgen Blogserie, in der die verschiedenen Methoden sowie ihre Ergebnisse bewertet und gegenübergestellt werden.

[Introductory article: why do we deal with methods of machine learning](/blog/machine_learning/background_en)  
[Part1: ensemblemethods](/blog/machine_learning/ensemblemethods)  
[Part 2: support vector machine](/blog/machine_learning/support_vector_machine)  
[Part3: Neuronale Netzwerke](/blog/machine_learning/neural_networks)


Eine Anekdote zum Abschluss. Bei der Verteidigung des Projekts an der EPFL sass Andreas Prüfern gegenüber, die äusserten, dass er mit einem "grossartigen Datensatz" gearbeitet hat. Das hat selbstverständlich auch uns gefreut. Vielleicht ist dies aber auch ein Satz, der zum Nachdenken darüber anregt, ob unsere Daten nicht mehr verdient haben, als nur in ein Bibliothekssystem mit relationalem Datenbanksystem gesteckt zu werden.
