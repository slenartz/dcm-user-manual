# Grundlagen

## Arbeitsbereiche, Templates, Jobs – das Grundkonzept 

Das grundlegende Anwendungskonzept besteht aus drei Elementen:

- **Arbeitsbereich**  
    Ein Arbeitsbereich fasst zusammengehörige Projekte, Datenquellen oder organisatorische Einheiten einer Institution zusammen und legt fest, welche Nutzer:innen auf die darin enthaltenen Templates und Jobs zugreifen dürfen.
- **Template**  
    Templates legen fest, welche Art von Job in einem Arbeitsbereich erstellt werden kann (z.B. OAI-PMH-Harvesting oder die Verarbeitung extern erstellter Information Packages in einem Hotfolder). Sie definieren die zentralen Parameter für die Anbindung der jeweiligen Quellsysteme und nehmen Datenkuratoren die Eingabe von technischen Konfigurationsparametern ab.
- **Job**  
    Ein Job ist eine konkrete Ausführung auf Basis eines Templates. Er umfasst die vom Datenkurator:in erfassten zusätzlichen Konfigurationen zur Datenauswahl, zu Metadaten-Mappings sowie optional einen Zeitplan für wiederkehrende Ausführungen. Alle Ausführungen eines Jobs werden protokolliert; Ergebnisse der Verarbeitung einzelner Intellectual Entities lassen sich jederzeit über die entsprechenden Job-Detail-Seiten einsehen.

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
