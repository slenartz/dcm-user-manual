# Jobs managen und überwachen

Die Tabelle auf der Seite *Jobs* zeigt eine Übersicht aller angelegten Jobs in den Arbeitsbereichen, auf die Sie Zugriff haben. Sie enthält grundlegende Informationen wie den aktuellen Status oder den nächsten geplanten Lauf (falls vorhanden). Darüber hinaus können hier – abhängig vom jeweiligen Jobstatus – verschiedene Aktionen direkt ausgeführt werden. Zudem können über Filter und eine Suchfunktion gezielt bestimmte Jobs ein- oder ausgeblendet werden.

## Aktionen in der Job-Übersicht

In der Job-Übersicht stehen Ihnen je nach Jobstatus verschiedene Aktionen zur Verfügung:

- **Zeitplan aktivieren/deaktivieren (Schalter)**  
  Über den Schalter kann der Zeitplan eines Jobs jederzeit pausiert oder wieder aktiviert werden. Beim Deaktivieren werden keine automatisierten Ausführungen mehr gestartet; manuelle Starts bleiben weiterhin möglich.
- **Job starten**  
  Führt den Job manuell aus, unabhängig davon, ob ein Zeitplan definiert ist.
- **Job-Details öffnen**  
  Öffnet die Detailseite eines Jobs mit Informationen zu verarbeiteten Intellectual Entities (IEs), Fehlermeldungen und Reports.
- **Report herunterladen** (über das Drei-Punkte-Menü)  
  Ermöglicht den Download des ausführlichen Ergebnis- und Fehlerreports des gesamten Jobs, inklusive aller bisherigen Ausführungen.
- **Bearbeiten** (über das Drei-Punkte-Menü)  
  Öffnet den bekannten Wizard, um die Konfiguration des Jobs anzupassen. Änderungen werden erst nach dem Speichern wirksam.
- **Löschen** (über das Drei-Punkte-Menü)  
  Entfernt den Job dauerhaft. *Achtung*: Dadurch geht die vollständige Ausführungs- und Verarbeitungshistorie des Jobs unwiderruflich verloren.

## Einen Job bearbeiten

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Job_bearbeiten.pdf" type="application/pdf" width="100%" height="800px" />

Über das Drei-Punkte-Menü können Sie die Funktion *Bearbeiten* auswählen, um die grundlegenden Einstellungen eines Jobs anzupassen oder ein aktualisiertes Mapping-Skript hochzuladen. Es öffnet sich der aus dem Anlegen des Jobs bekannte Wizard, in dem Sie Änderungen an der Konfiguration vornehmen können. Die Anpassungen werden erst wirksam, wenn der Job erneut gespeichert wird (*Änderungen übernehmen*).

## Zeitplan pausieren

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Zeitplan_pausieren.pdf" type="application/pdf" width="100%" height="800px" />

Jobs mit aktivem Zeitplan können über einen Schalter vorübergehend deaktiviert werden. Der Job wird dadurch nicht gelöscht und kann weiterhin manuell gestartet werden, führt jedoch keine automatisierten Läufe mehr aus. Der Zeitplan kann jederzeit wieder aktiviert werden.

### Automatisches Pausieren bei Fehlern

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Zeitplan_pausieren.pdf" type="application/pdf" width="100%" height="800px" />

Tritt während der Ausführung ein kritischer Fehler auf, der auf eine grundlegende Problematik in der Job-Konfiguration oder in der Datenstruktur des Quellsystems hinweist, wird die automatische Ausführung gemäß Zeitplan deaktiviert. Dadurch werden wiederholte Fehlversuche verhindert und eine kontrollierte Fehlerbehandlung ermöglicht.

Die Informationen in der Tabelle sowie im verfügbaren Report geben Aufschluss über Art und Ort des Fehlers innerhalb der DCM-Verarbeitungskette, sodass notwendige Korrekturen gezielt vorgenommen werden können.

Nach der Fehlerbehebung kann der Job manuell neu gestartet oder – durch erneutes Aktivieren des Schalters – wieder in den Zeitplan eingebunden werden.

## Einen laufenden Job abbrechen
<embed src="../assets/media/pdf/datenkurator-job-interaktion/Laufenden_Job_abbrechen.pdf" type="application/pdf" width="100%" height="800px" />

Wenn ein Job gerade ausgeführt wird, steht die Aktion *Abbrechen* zur Verfügung. Dadurch wird die laufende Verarbeitung gestoppt, und der Job erhält den Status *Abgebrochen*. Abgebrochene Jobs können anschließend erneut gestartet oder bearbeitet werden. Während des Joblaufs bereits vollständig verarbeitete und erfolgreich archivierte IEs bleiben vom Abbruch unberührt; der Abbruch verhindert lediglich die weitere Bearbeitung der noch ausstehenden IEs.

## Job-Details & Historie

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen.pdf" type="application/pdf" width="100%" height="800px" />

Die Job-Details zeigen alle bisherigen Ausführungen eines Jobs sowie den Status der jeweils verarbeiteten Intellectual Entities (IEs). Im Kopfbereich finden Sie den Gesamtstatus des Jobs und weitere allgemeine Informationen. 

Die darunterliegende Tabelle listet alle IEs der gesamten Job-Historie mit ihren Statuswerten, Validierungsergebnissen und Zeitstempeln. Über Filter und die Suchfunktion können Sie gezielt nach bestimmten IEs oder nach IEs mit Fehlern suchen.

Für jede IE lassen sich zudem Verarbeitungsreports herunterladen. Bei IEs, die nicht erfolgreich verarbeitet wurden, stehen außerdem (zeitlich begrenzt) die einzelnen Verarbeitungsstufen – IE, IP und SIP – als Download zur Verfügung, sodass Sie Fehler auf Ihrem eigenen Rechner analysieren können.

### Validierung fehlgeschlagen: Aktionen pro IE

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Fehler_ignorieren.pdf" type="application/pdf" width="100%" height="800px" />

Wenn die Objektvalidierung fehlschlägt, markiert die Detailansicht die betroffene IE und stellt im Drei-Punkte-Menü passende Aktionen bereit. Mit *Fehler ignorieren* wird die IE trotz Validierungsfehler übernommen; die weiteren Verarbeitungsschritte laufen regulär weiter.

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Als_Bitstream_einliefern.pdf" type="application/pdf" width="100%" height="800px" />

Über *Als Bitstream einliefern* wird die IE trotz Formatvalidierungsfehlern eingespielt. Das (optionale) Metadatum *Preservation Level* wird automatisch auf *Bitstream* gesetzt.

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Verwerfen.pdf" type="application/pdf" width="100%" height="800px" />

Die Aktion *Verwerfen* entfernt die fehlerhafte IE vollständig aus der Verarbeitung und merkt diese als nicht archivierungsfähig vor. Sie muss im Quellsystem aktualisiert werden und kann dann erneut vom DCM verarbeitet werden.
