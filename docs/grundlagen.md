# Grundlagen

## Arbeitsbereiche, Templates und Jobs

Der DCM strukturiert die Arbeitsabläufe in drei zentrale Bausteine.

**Arbeitsbereich**<br>
Arbeitsbereiche bündeln zusammengehörige Projekte oder Datenquellen und sorgen für eine klare organisatorische Struktur. Administrator:innen verwalten die Arbeitsbereiche und legen fest, welche Templates und Nutzer:innen ihnen zugeordnet sind. Für Datenkurator:innen ergibt sich daraus, welche Möglichkeiten sie im jeweiligen Bereich zum Anlegen und Bearbeiten von Jobs haben.

**Template**<br>
Templates werden von Administrator:innen erstellt. Sie enthalten die zentralen Einstellungen für die jeweilige Datenquelle und stellen sicher, dass technische Parameter bereits vorkonfiguriert sind. Für Datenkurator:innen bedeutet das, dass sie Jobs auf Grundlage einheitlicher und geprüfter Einstellungen anlegen können, ohne selbst technische Details anpassen zu müssen.

**Job**<br>
Jobs sind von Datenkurator:innen auf Basis eines Templates angelegte Konfigurationen, die beliebig oft ausgeführt werden können. Sie legen die für den jeweiligen Verarbeitungsvorgang notwendigen Einstellungen fest – etwa zur Datenauswahl, zu Metadaten-Mappings oder zu einem Zeitplan für wiederkehrende Läufe. Jobs bündeln die zugehörigen Archivierungsprozesse und erleichtern deren Statusnachverfolgung und Verwaltung.

## Rollen- und Berechtingungskonzept

Im DCM gibt es zwei Rollen, die verschiedene Aufgaben abdecken:

- **Administrator**  
    Verwaltet Arbeitsbereiche, Nutzer, Rollen und Templates.

- **Datenkurator**  
    Verantwortlich für das Anlegen, Konfigurieren und Ausführen von Jobs in Arbeitsbereichen. 
  
Diese Dokumentation führt beide Rollen durch die wichtigsten Funktionalitäten des DCM und bietet einen strukturierten Überblick über alle Schritte, die für einen reibungslosen Pre-Ingest-Prozess notwendig sind.

## Informationsmodell

Der DCM arbeitet mit *Information Packages* (IPs). Ein IP ist ein sich selbst beschreibender, konsistenter Container für alle Daten (Payload und Metadaten) einer Intellectual Entity. Es basiert auf dem BagIt-Standard.

Link zur aktuellen LZV.nrw Information Package Spezifikation: [https://github.com/lzv-nrw/spec-information-package](https://github.com/lzv-nrw/spec-information-package)

Es gibt zwei Wege, wie Information Packages vom DCM importiert werden:

- **Extern erstellte IPs (Hotfolder-Jobs)**  
Externe Systeme oder Workflows können IPs selbst erzeugen und über einen überwachten Hotfolder in den DCM einliefern. Diese IPs müssen der öffentlich dokumentierten IP-Spezifikation entsprechen, damit sie vom System validiert und weiterverarbeitet werdenx.

- **Vom DCM erzeugte IPs (OAI-PMH-Jobs)**  
Alternativ werden IPs vom DCM selbst generiert, wenn Daten über OAI-PMH-Jobs importiert werden.

!!! info
     Extern erstellte Information Packages werden anhand der in der Anwendung hinterlegten Profile auf Konformität geprüft. Das jeweils verwendete Profil wird im Metadatum BagIt-Profile-Identifier angegeben. Es ist auch möglich, eigene Profile zu verwenden, ohne sie im DCM zu hinterlegen – vorausgesetzt, sie sind vollständig kompatibel mit den Anforderungen des DCM. Eine Prüfung erfolgt bei der Verarbeitung des entsprechenden Information Packages.

Unabhängig vom Ursprung gelten für alle Information Packages dieselben Regeln und Formatvorgaben. Dies stellt sicher, dass die angebundenen Microservices – etwa für Objekt-Validierung, Metadatenmapping oder SIP-Generierung – zuverlässig und reproduzierbar arbeiten können. Durch das einheitliche Format sind sowohl externe Zulieferungen als auch intern erzeugte Information Packages voll kompatibel.
