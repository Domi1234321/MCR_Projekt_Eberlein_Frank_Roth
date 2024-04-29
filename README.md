[Schaltplan_MCR_Frank_Eberlein_Roth.pdf](https://github.com/Domi1234321/MCR_Projekt_Eberlein_Frank_Roth/files/15147337/Schaltplan_MCR_Frank_Eberlein_Roth.pdf)


Tasterbeschreibung
Der Master-STM32-Mikrocontroller ist mit fünf Tastern ausgestattet, die verschiedene Funktionen in der Kommunikation mit den beiden Slave-STM32-Mikrocontrollern (STM32 Nucleo-F401RE) über das I2C-Protokoll auslösen. Die Taster ermöglichen es dem Master, LEDs an den Slaves zu steuern und alle LEDs gleichzeitig einzuschalten.
Tasterfunktionen
Taster 1 (PA1):
Funktion: Umschalten von LED 1 an Slave 1.
Beschreibung: Beim Drücken von Taster 1 sendet der Master den Befehl 0x01 an Slave 1, um LED 1 zu toggeln (ein-/ausschalten).
Taster 2 (PA4):
Funktion: Umschalten von LED 2 an Slave 1.
Beschreibung: Beim Drücken von Taster 2 sendet der Master den Befehl 0x02 an Slave 1, um LED 2 zu toggeln (ein-/ausschalten).
Taster 3 (PB0):
Funktion: Umschalten von LED 1 an Slave 2.
Beschreibung: Beim Drücken von Taster 3 sendet der Master den Befehl 0x01 an Slave 2, um LED 1 zu toggeln (ein-/ausschalten).
Taster 4 (PC1):
Funktion: Umschalten von LED 2 an Slave 2.
Beschreibung: Beim Drücken von Taster 4 sendet der Master den Befehl 0x02 an Slave 2, um LED 2 zu toggeln (ein-/ausschalten).
Taster 5 (PC0):
Funktion: Einschalten aller LEDs an beiden Slaves.
Beschreibung: Beim Drücken von Taster 5 sendet der Master den Befehl 0x03 an beide Slaves, um alle LEDs gleichzeitig einzuschalten.
Zusammenfassung der Tasterfunktionen
Die Taster ermöglichen es dem Benutzer, die LEDs an den Slaves gezielt zu steuern:
Taster 1 und Taster 2 steuern die LEDs an Slave 1.
Taster 3 und Taster 4 steuern die LEDs an Slave 2.
Taster 5 schaltet alle LEDs an beiden Slaves gleichzeitig ein.
Diese einfache Tastersteuerung ermöglicht eine intuitive Kontrolle der LEDs an den Slaves und bietet eine praktische Möglichkeit, die Zustände der LEDs auf Knopfdruck zu ändern.



Master-Funktionen
Umschalten einer LED: Der Master kann eine LED an einem der Slaves ein- oder ausschalten. Dazu sendet er eine I2C-Nachricht an den entsprechenden Slave mit dem Befehl, die LED zu toggeln.
Einschalten aller LEDs: Der Master kann alle LEDs an einem der Slaves gleichzeitig einschalten. Dazu sendet er eine I2C-Nachricht an den entsprechenden Slave mit dem Befehl, alle LEDs einzuschalten.
Abfrage des LED-Status: Der Master kann den Status der LEDs (ein/aus) an einem der Slaves abfragen. Dazu sendet er eine I2C-Leseanforderung an den Slave, um den aktuellen Status der LEDs zu erhalten.
Slave-Funktionen
Empfang von I2C-Nachrichten: Die Slaves empfangen I2C-Nachrichten vom Master und verarbeiten die Befehle, um LEDs ein- oder auszuschalten oder alle LEDs gleichzeitig einzuschalten.
Bereitstellung des LED-Status: Die Slaves stellen den aktuellen Status der LEDs auf Anfrage des Masters bereit. Der Status wird über eine I2C-Leseoperation an den Master gesendet.
I2C-Kommunikation
Adressen: Der Master verwendet die I2C-Adressen 0x10 und 0x11 für die beiden Slaves.
Befehle:
LED 1 umschalten: Der Befehl 0x01 toggelt LED 1 an einem Slave.
LED 2 umschalten: Der Befehl 0x02 toggelt LED 2 an einem Slave.
Alle LEDs einschalten: Der Befehl 0x03 schaltet alle LEDs an einem Slave ein.
Abfrage des Status: Der Master sendet eine Leseanforderung an den Slave und erwartet zwei Bytes zurück. Das erste Byte enthält den Status der LED 1 (1 = ein, 0 = aus), und das zweite Byte enthält den Status der LED 2 (1 = ein, 0 = aus).
Kommunikation im Detail
Der Master startet die Kommunikation mit einem Startsignal.
Der Master sendet die I2C-Adresse des Slaves gefolgt von einem Schreib-/Lesebefehl (Schreibbefehl für LED-Steuerung, Lesebefehl für Statusabfrage).
Der Master sendet den Befehl (0x01 für LED 1 toggeln, 0x02 für LED 2 toggeln, 0x03 für alle LEDs einschalten) oder startet eine Leseoperation für den LED-Status.
Der Slave empfängt den Befehl und führt ihn aus (z. B. LED ein/aus) oder antwortet auf eine Leseanforderung mit dem aktuellen LED-Status.
Der Master beendet die Kommunikation mit einem Stop-Signal.
Das Protokoll ermöglicht eine einfache und zuverlässige Steuerung der LEDs an den Slaves und die Abfrage ihres Zustands vom Master aus.



Zur Abfrage des LED-Status der Slaves Taste A auf der Tastatur betätigen.
