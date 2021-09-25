# Commandline (Shell)

Auf der Commandline navigieren ist verdammt wichtig, wenn man ein bisschen tiefer in Linux einsteigen will.
Die verbreitetste Shell ist `bash`, gefolgt von `zsh` (mein Favorit) und anderen wie z.B. `fish`.
Im Grunde verhalten sich alle Shells generell sehr ähnlich, einige haben eventuell mehr/andere Features und eventuell eine leicht andere Syntax.
Im Folgenden gehe ich einfach von `bash` oder `zsh` aus, die praktisch die selbe Syntax haben.

Allgemein gilt:
Wenn man ein Programm von der Commandline starten/aufrufen will, tippt man lediglich den Namen des Programms und die dazugehörigen Paramter ein.
- Zuerst das auszuführende Programm **ls** `-al /path/to/file`
- Dann die Parameter `ls` **-al /path/to/file**


So könnte man z.B. einen Browser von der Commandline öffnen, indem man `firefox` eintippt und `Enter` drückt.

Viele Commands können weitere Optionen übergeben bekommen, häufig in Form von Flags oder normalen Parametern.
Flags sind Optionen, welche angegeben werden können, jedoch meist optional sind.
Dargestellt werden Flags als z.B. `-a` oder `--all`.

Als Beispiel kann man `ls` einfach so ausführen oder `ls --all`, um auch versteckte Dateien anzuzeigen. `--all` ist hier komplett optional.

In der Regel gilt:
    - Abgekürzte Flags sind mit einem Bindstrich `-a`
    - Ausgeschrieben mit zwei Bindestrichen `--all`

Abgekürzte Flags können häufig aneinander gereiht werden. Also anstatt `ls -a -l -R -h` zu schreiben, kannst du auch einfach `ls -ahlR` schreiben.  
Das verwirrt am Anfang immer gerne, aber achte einfach darauf, ob du hier einen Bindestricht hast oder zwei.

`ls /path/to/directory` -- Zeigt die Inhalte des Ordners. Steht für `list`
`cd /path/to/directory` -- Gehe in dieses Directory. Steht für `change directory`
`rm  /path/to/directory` -- Löscht dateien. Steht für `remove`
`rm -r /path/to/directory  /path/to/file` -- Löscht auch Ordner


**Help und Man Pages**

Falls man wissen will, welche Optionen oder Parameter ein Programm annimmt, kann man dies entweder mit der Flag `-h` oder `--help` erfahren. Dort wird meist ausreichend Information über die Bedienung gut zusammengefasst zur Verfügung gestellt.

Falls man ausführliche Informationen zum Programm braucht, gibt es die `man page`.
Beinahe jedes Programm hat eine sogenannte _man page_, welche an sich nur ein Manual ist, welches dir genau erklärt, wie das Programm benutzt werden soll und welche _Flags_ und _Parameter_ existieren.
Man kann aus dem Manual jederzeit mit `q` raus und mit den Pfeiltasten navigieren.  
Mit `/` kann man nach bestimmten Begriffen suchen.  

Ein Beispiel für eine _man page_ wäre z.B. `man ls`, welches dir ausführlichst alle Möglichkeiten `ls` zu benutzen auflistet.


**Das Filesystem**

Sobald man ein Terminal öffnet, befindet man sich in einer bestimmten Stelle im Filesystem z.B. `/home/nuke`.
`/home/nuke` wäre z.B. der Home Ordner des Nutzers `nuke`.
Die Slashes stehen dafür, dass man in einen Ordner gegangen ist.
Die Spitze des Dateisystems ist der sogenannte `root` und ist durch den Pfad `/` gekennzeichnet.

Zum Navigieren des Filesystems nehmen wir in erster Linie die Commands `cd` und `ls`.
`ls` zeigt einem die Inhalte des Ordners an, in dem man sich momentan befindet.
Wenn man einige sogenannte Flags hinzufügt, kann man mehr Informationen über die Dateien erfahren.
Z.B. zeigt einem `ls -a -l` oder kurz `ls -al` die Zugriffsrechte, die Größe und sonstige Informationen (`-l` für `list`), sowie alle Dateien an, also auch versteckte Dateien (`-a` für `all`)

`cd` wird benutzt um sich durch Ordner zu navigieren. Hierzu kann entweder ein zum root absoluter Pfad angegeben werden z.B. `cd /home/Christian`, oder ein Pfad relativ zum momentanen Ordner z.B. `cd ..`.
Es gibt hierbei einige Zeichen oder Zeichenfolgen, die eine bestimmte Bedeutung haben:
- `~` symbolisiert das Home directory des momentanen Nutzers.
- `..` ist der übergeordnete Ordner.
- `.` ist der momentane Ordner.


**Symbole auf der Shell**  

Es gibt nen Haufen Symbole, die eine besondere Bedeutung auf der Shell haben, hier ein paar der wichtigsten: 

- `.` Der Punkt steht immer für das momentane Directory, in dem du dich befindest. `ls .` zeigt also den Inhalt des momentenen directories an.
- `..` Der doppelte Punkt steht immer für das überliegende (_parent_) Directory. `cd /home/nuke && cd ..` würde dich erst in `/home/nuke` bewegen und anschließend aus dem Ordner heraus in den überliegenden `/home`.
- `~` Die Raute steht für deinen `Home`-Directory. Also für das Directory, dass deinem User zugewiesen ist. Bei dir wäre das der merlon ordner. Genauer `/home/merlon`. Bei mir ist das `/home/nuke`.
- `*` Alle Dateien im momentanen Ordner. `rm *` würde also alle Dateien löschen, die sich im Ordner befinden
- Dateien, die mit einem Punkt beginnen, sind versteckte Dateien. Z.b. das `.config` Ordner in deinem _Home_, welches Konfigurationsdateien für viele deiner persönlichen Programme enthält.
- `&&` Damit kannst du auf der commandline Programme aneinanderreihen. z.B. `touch test && rm test` erstellt eine Datei und löscht sie direkt danach wieder.

# Ein paar wichtige Programme mit den wichtigsten Flags

**ls**
- `-a` zeigt alle Dateien an. Auch versteckte
- `-l` zeigt Dateien in Listenansicht an, mit mehr Details und informationen
- `-h` zeigt Zahlen in menschlich besser lesbarem Format an
- `-R` zeigt die Ordner Inhalte rekursiv an


**rm**

- `-r` löscht rekursiv. Ist also benötigt zum löschen von Ordnern
