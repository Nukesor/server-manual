# File Permissions

Unter Linux gibt es sogenannte File permissions, diese werden gerne in oktaler Schreibweise dargestellt. z.B. 0770
Wenn du in einem Directory `ls -l` ausführst, siehst du links z.B. ein Zeichenkette `- rw- r-- r--`. Diese symbolisieren die Permission bits, jeder Bindestrich steht für eine 0, jeder Buchstabe für eine 1.
Normale permissions sind aufgeteilt in den ersten Bit, der besagt ob es sich um ein directory handelt oder nicht, und drei aufeinanderfolgende 3-bit Sequenzen.
Folgendes Beispiel: `- rw- r-- r--` ist equivalent zu `0 110 100 100`, was in oktaler Schreibweise folgendes wäre 0644.
Die 3-bit Sequenzen stehen in folgender Reihenfolge für: Owner, Group, Everybody.
Die bits in jeder 3-bit Sequenz stehen in folgender Reihenfolge für: read, write, execute

Der Owner ist der absolute Besitzer einer Datei/ eines Directories.
Einen Group ist lediglich eine Gruppe, der beliebig viele User zugewiesen werden können. Dies ist praktisch um Zugriffsrechte mit mehreren Leuten zu koordinieren
Everybody ist für absolut JEDEN user auf dem system einsehbar. Daher sollten hier eigentlich maximal leserechte zugewiesen werden. 

Es wird also für jede der Parteien (Owner, Group, Everybody) festgelegt, ob die Partei lesen, schreiben oder ausführen darf.
Im Falle eines Directories, bedeutet das executable-bit, dass die Partei in den Ordner hereinschauen darf.
Bei einer normalen Datei, bedeutet das executable-bit, dass die Partei die Datei wie ein Programm oder Script behandeln und ausführen darf.

Dementsprechend sind Standard File Permissions für Dateien `0644`, was equivalent ist zu `- rw- r-- r--`, was bedeutet, dass alle Lesen dürfen, aber nur der Owner schreiben darf.
Das equivalent für directories ist `- rwx r-x r-x`,  was bedeutet, dass alle lesen und hineinschauen dürfen, aber nur der Owner schreiben darf.

In deinem Fall, willst du nun, dass mehrere User auf ein Directory lesen und schreiben dürfen, nämlich christian und syncthing und wahrscheinlich noch mehr Programme.
Was du also nun tun willst ist folgendes:

- Eine Gruppe files erstellen (welche glaube ich bereits existiert), zu der du die User hinzufügst, die Schreibrechte erhalten sollen
- Die Besitzer des Directories, welches du teilen willst sollte geändert werden: `sudo chown root:files -R hier_ordner_pfad`.
    chown ändert den owner und die Group nach folgender Syntax chown user:group. Das -R steht für recursive und ändert dadurch auch alle Dateien innerhalb des Directories und nicht nur des Directories selbst.
- Ändere die Zugriffsrechte aller Dateien innerhalb des Ordners, sodass die Gruppe lesen UND schreiben kann. Das machst du mit:
`sudo chmod g+w -R /path/to/dir`.
`chmod` funktioniert genauso wie `chown` nur für Zugriffsrechte. `g+w` steh hier für `gruppe+write`, um zu signalisieren, dass alle Dateien der Gruppe erlauben sollen zu schreiben.
- zuletzt noch eine letzte Änderung: Damit neu geschriebene Dateien ebenfalls automatisch diese Permissions bekommen, muss noch das groupset bit gesetzt werden. Das machst du mit:
`sudo chmod g+s -R /path/to/dir`

# Fix Wrong File Permissions

Falls man mal die File Permissions für ein Directory verhauen hat, muss man sie wieder auf Normalzustand stellen.
Das heißt für alle Files den Befehl `chmod 664` ausführen und für alle directories den Befehl `chmod 02775`.
Das kannst du mit dem schönen Tool `find` machen.
Find sucht in einem spezifischen Directory nach Dateien und erlaubt es einem auf die Dateien bestimmte Befehle auszuführen.

Dazu gibt es hier einen guten [Stackoverflow post](https://stackoverflow.com/questions/3740152/how-do-i-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files).

Zusammengefasst benutzt du diese Commands:
`find path/to/directory -type d -exec chmod 02775 {} \;`
`find path/to/directory -type f -exec chmod 644 {} \;`
`find -type d` steht für: Finde alle Typen vom Typ Directory
`find -type f` steht für: Finde alle Typen vom Typ File

Mit `-exec` spezifizierst du, welches command ausgeführt werden soll und das `{}` in dem command wird durch die jeweiligen gefundenen Datei Pfade ersetzt.
Du kannst ja gerne mal die commands ohne den hinteren teil ausführen.
Also lediglich `find path/to/directory -type d` und `find path/to/directory -type f`. Dann siehst du genau, was `find` macht.
