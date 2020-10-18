# workflow Publizieren von (Blog) webpages mit dem Werkzeug Hugo

0. [Hugo](https://gohugo.io/) ist ein Framework zum Erstellen und Publizieren von statischen websites
1. Hugo lokal [installieren](https://gohugo.io/getting-started/installing/)
2. dadurch können Bloginhalte lokal neu erstellt oder editiert werden (mit Hilfe eines lokalen webservers werden die Inhalte sofort lokal publiziert 
```bash
hugo server -D
```
3. die Seiten werden über den github pages Mechanismus publiziert. Dieser Mechnismus nut den branch 'publish', der auch als default branch für dieses Repository eingestellt ist.
4. im ersten Schritt muss das repository 'ge-cloned' werden
```bash
git clone --recursive git@github.com:swissbib/swissbib.github.io.git
#damit ist auch das template zur Darstellung der Inhalte lokal verfügbar. Dieses ist unter einer anderen Adresse verfügbar. Mehr Hintergrund dazu später.
```
5. Bitte nie auf dem branch publish direkt Inhalte neue erstellen oder editieren. Immer zuerst einen neuen branch erstellen
```bash
git checkout -b [mein neuer branch]
#der neue branch kann natürlich auch nach Github 'ge-pushed' werden
```
6. wenn man mit dem Ergebnis zufrieden ist und die neuen Inhalte publizieren möchte, den neuen branch nach publish mergen 
```bash
git checkout publish
git merge [mein neuer branch]
```

7. damit der Inhalt auf swissbib.github.io auf Basis des branch publish dargestellt werden kann, müssen zuerst die komplette domain mit den neuen Inhalten als statische webistes mit Hilfe von Hugo generiert werden
```bash
#im branch publish
hugo -D
#Option -D damit auch als draft gekennzeichnete webpages übernommen werden. Falls das icht gewünscht ist, diese Option weglassen
#Dieses Kommando ändert natürlich die Inhalte des directories publish stark. Die geänderten Inhalte müssen nach Git übernommen werden
git add .
git commit -m 'was habe ich gemacht'
git push origin publish

#die temporären branches zum Erstellen der Inhalte können nun gelöscht werden
```
8. Hinweis: wenn die neuen Inhalte auf swissbib.github.io nach dem push nicht gleich angezeigt werdem: Einfach den cache des browsers löschen. Da es sich um statische Inhalte handelt, kommt das caching stark zum Einsatz 



### Version 0.01 (18.10.2020)


