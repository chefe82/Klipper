# Nevermore Aktivkohle nach Nutzungszeit (Tagen)

Die Aktivkohle im Nevermore Filter sollte idealerweise 50 Druckstunden bzw. 30 Tagen nach herausnahme aus der Vakuumverpackung getaucht werden.
Hiermit stellen wir eine Möglichkeit bereit die entsprechende Werte in Klipper speichern und Auswerten zu können.

ACHTUNG: Wir übernehmen keine Haftung bei Schäden die durch die Nutzung entstehen könnten.

Voraussetzung ist das ihr folgende Configuration schon erfolgreich durchgeführt habt:
https://github.com/cryd-s/Vyper_extended/tree/main/Betriebsstunden


## **Anleitung:**
 
 Es werden folgende Dateien benötigt:

 - [ ] gcode_shell_command.py
 - [ ] get_filter_time.sh
 - [ ] reset_filter_time.sh
 - [ ] filter_used_time.cfg
 - [ ] printtime.cfg
 - [ ] user_variable.cfg (angepasst)
 - [ ] .ftime.stb (optional wird automatisch erstellt

Erstellt in Mainsail einen neuen Ordner z.B. 

     Nevermore_Scripts

 in diesen Ordner kopiert ihr folgende Dateien
 `get_filter_time.sh, reset_filter_time.sh und die .ftime.stb`.

Die Datei `filter_used_time.cfg` in einen Ordner eurer Wahl einfügen und in der `printer.cfg` mit [Include filter_used_time.cfg] einbinden (danach Nur speichern kein Neustart).

Die schon vorhandene `user_variable.cfg` durch die neue ersetzen.

Die Datei `gcode_shell_command.py` könnt ihr in das Homeverzeichnis z.B. `/home/pi/` kopieren.

Damit Klipper dies Funktionen aus dem Python Script aufrufen kann muss diese über ein Symlink in Klipper eingebunden werden. Dazu per SSH folgenden Befehl ausführen

    ln -s /home/pi/gcode_shell_command.py /home/pi/klipper/klippy/extras/gcode_shell_command.py

danach Klipper Service Neustarten.
Nach dem Neustart von Klipper sollte keine Fehlermeldung erscheinen!!

Folgendes Macro ausführen `ResetFilterDate` somit wird das aktuelle Datumgespeichert ud nahend diesem die vergangene Tagen berechnet.
Das Datum kann man in der .`ftime.stb` manuell ändern wenn man weiß wann das letzte mal die Aktivkohle getauscht wurde. 

    Format: YYYYMMDD

Mit dem Ausführen des Macros `get_FilterStatusDate` kann man sich die Auswertung anzeigen lassen.
Dies sollte dan so aussehen

![enter image description here](https://github.com/chefe82/Klipper/blob/main/Nevermore/Used_Time/Pictures/nevermore_status.png?raw=true)
		
Mit dem Aufruf des Macros `get_FilterStatusAll` wird die komplette Statistik angezeigt (Druckzeit und Used Days)
![enter image description here](https://github.com/chefe82/Klipper/raw/main/Nevermore/Used_Time/Pictures/nevermore_status_all.png)


    



 


