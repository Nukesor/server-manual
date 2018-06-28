## Commandline/Shell

Auf der Commandline navigieren ist verdammt wichtig.
Um mit dem Operating System zu interagieren benutzt man in der Regel eine Shell.
Die verbreitetste Shell ist `bash`, gefolgt von `zsh` (mein Favorit) und anderen wie z.B. `fish`.
Im Grunde verhalten sich Shells meistens sehr ähnlich, einige haben jedoch mehr features und eventuell eine leicht andere Syntax.
Im Folgenden gehe ich einfach von `bash` oder `zsh` aus, die praktisch die selbe Syntax haben.

Fangen wir mit einfachen Grundlagen und simplen Commands an.

### Das Filesystem

Sobald man ein Terminal öffnet, befindet man sich in einer bestimmten Stelle im Filesystem z.B. `/home/Christian`.
`/home/Christian` wäre z.B. der Home Ordner des Nutzers `Christian`.
Die Slashes stehen dafür, dass man in einen Ordner gegangen ist.
Die Spitze des Dateisystems ist der sogenannte `root` und ist durch den Pfad `/` gekennzeichnet.

### Aufrufen von Programmen
Wenn man ein Programm von der Commandline starten/aufrufen will, tippt man lediglich den Namen des Programms ein.
So könnte man z.B. einen Browser von der Commandline öffnen, indem man `firefox` eintippt und `Enter` drückt.
Viele Commands können weitere Optionen übergeben bekommen, häufig in Form von Flags oder normalen Parametern.
So würde `firefox --headless -P test@user.de` Firefox starten, jedoch ohne jegliches Interface (`--headless`) und eingeloggt mit dem User account von `test@user.de`.
Falls man wissen will, welche Optionen oder Parameter ein Programm annimmt, kann man dies entweder mit der Flag `-h` oder `--help` erfahren oder für sehr detailierte Anweisunge gibt es manpages.
Manpages bieten ein ausführliches manual für ein jeweiliges Programm. Um eine Manpage zu lesen, muss man lediglich `man` und darauf den namen des Programmes tippen, also z.B. `man test`. Es ist jedoch anzumerken, dass nicht jedes Programm eine Manpage zur Verfügung stellt, wie z.B. Firefox.

### Navigieren des Filesystems

Zum Navigieren des Filesystems nehmen wir in erster Linie die Commands `cd` und `ls`.
`ls` zeigt einem die Inhalte des Ordners an, in dem man sich momentan befindet.
Wenn man einige sogenannte Flags hinzufügt, kann man mehr Informationen über die Dateien erfahren.
Z.B. zeigt einem `ls -a -l` oder kurz `ls -al` die Zugriffsrechte, die Größe und sonstige Informationen (`-l` für `list`), sowie alle Dateien an, also auch versteckte Dateien (`-a` für `all`)

`cd` wird benutzt um sich durch Ordner zu navigieren. Hierzu kann entweder ein zum root absoluter Pfad angegeben werden z.B. `cd /home/Christian`, oder ein Pfad relativ zum momentanen Ordner z.B. `cd ..`.
Es gibt hierbei einige Zeichen oder Zeichenfolgen, die eine bestimmte Bedeutung haben:
- `~` symbolisiert das Home directory des momentanen Nutzers.
- `..` ist der übergeordnete Ordner.
- `.` ist der momentane Ordner.

