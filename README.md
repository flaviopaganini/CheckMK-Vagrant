# Vagarnt-CheckMK
© By Flavio Paganini ST16E
## Einleitung
Dies ist die Dokumenation für das Vagrant File für einen CheckMK Server samt einem CheckMK Test Client. Der CheckMK Server ist sobal das Vagrantfile durchgelaufen ist über `http://localhost:8080/TBZSide/check_mk/login.py` ereichbar. Mit den Default einstellungen von dem Vagrantfile wird dem Benutzer `cmkadmin` das Passwort `Admin1234` gesetzt. Es werden zwei Boxen gestartet mit je 512MB Ram. Die beiden Boxen sind über ein Boxen internes Netzwerk verbunden. Der Server hat die IP `192.168.55.100` und der Client hat `192.168.55.101`. Der Client ist vom Host aus nur via SSH ereichbar, sonst ist er hinter der NAT Firewall von VirtualBox geschützt. Der CheckMK Server ist nur via Port 8080 und dem SSH Port ereichbar.

Die Idee für dieses Projekt habe ich gefunden weil bei uns in der Firma auch CheckMK benutzt wird und ich wollte schon immer einmal einen eigen CheckMK aufsetzten. Vagrant ist nicht Optimal für das aber so kann ich schon einmal testen wie CheckMK funktioniert um es danach als richtige VM zu Instalieren.
___
