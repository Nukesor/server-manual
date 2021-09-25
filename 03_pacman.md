# Pacman

In den meisten Linux distributionen (distro), gibt es offizielle Repositories, in denen Programme von den Maintainern der jeweiligen distro zur Verfügung gestellt werden.

Du benutzt immer **s**pacman, aber das ist im Endeffekt nur ein alias (Eine Abkürzung für `sudo pacman`)
`sudo` ist ein Befehl, welcher den nachfolgenden Aufruf mit `root` Rechten ausführt, also praktisch als Admin.

`pacman -Syu`  -- Updated dein System komplett.  
`-S` steht für `install`  
`-y` Aktualisiert die Datenbank mit den Paketen, damit er mitbekommt, dass es neue Pakete gibt  
`-u` Steht für `Update` von existierenden Paketen  

`pacman -S $package` --  Installiert dir ein bestimtes Programm

`Pacman -Rns $package` -- Deinstalliert dir ein bestimmtes Programm  
`-R` steht für `Remove`  
`-s` `Recursive` heißt es wird nicht nur das Paket entfernt, sondern auch alle Dependencies, die es hatte  


## Inoffizielle Programme

Es gibt neben den offiziellen Repositories auch das Arch User Repository (AUR), welches jedem User erlaubt eigene Pakete hochzuladen.

Bei diesen Paketen ist es nicht offiziell garantiert, dass diese laufen dort sidn auch mal outdated oder nicht funktionierende Programme.


Um Sachen aus dem AUR runterzuladen, benutzt man inzwischen das Programm `yay`.

Yay funktioniert im Endeffekt genau so wie Pacman, es gibt jedoch ein paar Features on-top, welche die Interaktion mit dem AUR erleichtern.

- `yay -Syu` updated zum Beispiel alle offiziellen Programme + Programme aus dem AUR.
- `yay -Syu --devel` updated auch experimentelle Programme, also den neusten momentanen Stand der noch nicht offiziell in einer neue Version released wurde
- `--noconfirm` ist eine Flag, die ihr hinter jedes Command von `yay` schreiben könnt. Dadurch werdet ihr nicht mehr gefragt, ob ihr euch den ganzen Kram anschauen wollt, stattdessen wird alles direkt installiert.
