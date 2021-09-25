# Git:

Ein paar Grundbegriffe:
- `repository` oder kurz `repo` ist praktisch ein Projekt, das von Git verwaltet ist. Der redditbot liegt z.B. in einem git repository.
- `clone` bedeuted sich ein existierendes Repository herunterzuladen
- `stage` Dateien, die zu einem Commit hinzugefügt werden.
- `dirty` Dateien, die geändert wurden, aber noch nicht in den Commit übernommen werden.

**Repository clonen.**

Ein existierendes Projekt herunterzuladen geht ganz einfach.
Um ein repo zu clonen, muss man lediglich folgendes ausführen:

`git clone $url`

Die URL eines Repositories findet bei Github z.B. immer rechts in der Repository Übersicht bei `Clone or download`.  
Da du ja schon einen SSH key hast, kannst du einfach immer die SSH URL nehmen. Das sieht dann z.B. so aus:

`git clone git@github.com:Nukesor/beginner-cheatsheet.git`


**Basics:**  
Damit git funktioniert, musst du dich erstmal im Ordner des Respositories befinden.

_Wie es im groben funktioniert:_  
Bevor man in Git einen neuen Commit erstellt, fügt man erst einmal alle Dateien hinzu, welche man im Commit haben will.
Das nennt man `stagen` und werde ich ab jetzt auch so weiterhin verwenden.  
Änderungen, die noch nicht gestaged wurden, nennt man `dirty`.

`git add .`  
Staged alles im momenten Directory. Der Punkt `.` steht auf der Commandline immer für den Directory, in dem du dich gerade befindest.

`git add /path/to/file`  
Staged nur diese spezifische/n Datei/en

`git status`  
Zeigt dir an, was sich so alles geändert hat. I.e. welche Dateien _staged_ sind, welche Dateien hinzugefügt/entfernt wurden und welche Dateien _dirty_ sind.

`git commit`  
Erstellt einen neuen Commit mit allen Änderungen, die _staged_ sind. Wenn jetzt z.B. noch eine Datei geändert wurde und du danach nicht nochmal `git add /path/to/file` ausgeführt hast, wird diese Änderung nicht in den Commit übernommen.

`git commit -m "Commit message"`  
Das selbe wie oben drüber, nur dass du die Commit message nicht extra in nem Editor aufmachst.

`git push`  
Schiebt alle neuen Commit von dir auf einen Server, wie z.B. in unserem Falle zu Github.


**Praktische tools für Git**  
Du kannst dir die tatsächlichen Änderungen an den Dateien auf der Commandline anschauen, um z.B. nochmal einen Überblick zu bekommen, was du alles getan hast, bevor du etwas committest.

Dafür gibt es den `git diff` Befehl. `diff` für differences.

`git diff` zeigt dir alle Änderungen an Dateien, die momentan _dirty_ sind.  
`git diff --staged` zeigt dir alle Änderungen an, die momentan _staged_ sind, also die zum Commit hinzugefügt werden würden, wenn du gerade jetzt `git commit` ausführen würdest.  
