# Datenverarbeitung & Jobs

## Jobs anlegen

Dieses Kapitel beschreibt alle Schritte, die ein:e Datenkurator:in beim Anlegen eines neuen Jobs durchläuft.  

Klicken Sie auf der Seite "Jobs" den Button "Neuen Job anlegen". Es öffnet sich der Job-Wizard, der Sie schrittweise durch die Job-Konfiguration führt. Der Assistent überprüft Ihre Eingaben und zeigt farblich hervorgehobene Hinweise, falls Werte fehlen oder nicht gültig sind.

Wählen Sie hier zunächst den gewünschten Arbeitsbereich aus der Liste und setzen Sie den Konfigurationsprozess mit einem Klick auf "Weiter" fort. 

Wählen Sie anschließend das Template für das Sie einen neuen Archivierungsjob anlegen möchten. Bestätigen Sie mit "Weiter" und starten sie damit den eigentlichen Konfigurationsprozess.

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Arbeitsbereich-Template-Beschreibung.pdf" type="application/pdf" width="100%" height="800px" />

### Beschreibung

In diesem Schritt erfassen Sie die grundlegenden Angaben zu Ihrem Job. Wählen Sie einen Titel, der den Zweck des Jobs möglichst eindeutig beschreibt, damit Sie ihn später in der Job-Übersicht leicht wiederfinden.

Im Feld Beschreibung können Sie zusätzliche Hinweise eintragen, die Ihnen oder Kolleg:innen beim Verständnis des Jobs helfen. 

Mit der Angabe eines Ansprechpartners für das Quellsystem stellen Sie sicher, dass bei Rückfragen zur Datenquelle schnell die richtige Kontaktperson erreicht werden kann. Alle Angaben lassen sich später über die Funktion Bearbeiten erneut anpassen.

### Datenauswahl

In diesem Schritt legen Sie fest, welche Daten der DCM für den Job verarbeiten soll. Je nach Job-Typ (OAI-PMH oder Hotfolder, basierend auf dem entsprechenden Template) wählen Sie entweder eine OAI-PMH-Quelle oder ein Verzeichnis, aus dem extern erzeugte IPs geladen werden sollen, aus. 

#### OAI-PMH-Harvesting

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenauswahl__OAI-PMH_.pdf" type="application/pdf" width="100%" height="800px" />

Wenn das Template auf OAI-PMH basiert, haben Sie die Möglichkeit, die Auswahl der zu archivierenden Daten auf ein oder mehrere Set(s) und/oder zeitlich zu beschränken . 

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenauswahl__fertige_IPs____Verzeichnis_auswahlen.pdf" type="application/pdf" width="100%" height="800px" />

Wenn Sie mit extern erstellten IPs arbeiten, wählen Sie ein bestehendes Verzeichnis aus, das der DCM als Quelle nutzt. Der Assistent zeigt Ihnen alle verfügbaren Verzeichnisse an; bei Bedarf können Sie ein neues Verzeichnis erstellen, aus dem Information Packages geladen werden sollen.

!!! info
    Die hier angzeigten Verzeichnisse befinden sich im vom Administrator für das Template gewählten Hotfolder. Wie Sie Daten in diese Verzeichnisse übertragen, hängt von der Systemkonfiguration ab. Je nach Einrichtung des DCM können dafür unterschiedliche Verfahren genutzt werden, z.B. SFTP, NFS, SMB oder WebDAV. Welche Methode Sie verwenden, richtet sich nach der Konfiguration der Anwendungsumgebung.

#### Hotfolder. Extern erstellte IPs – Verzeichnis hinzufügen

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenauswahl__fertige_IPs____Verzeichnis_hinzufugen.pdf" type="application/pdf" width="100%" height="800px" />

Hier fügen Sie neue Verzeichnisse hinzu, deren Inhalte in den Job einfließen sollen. Die ausgewählten Ordner werden übersichtlich aufgelistet. Einträge lassen sich jederzeit ergänzen, ersetzen oder entfernen.

### Datenaufbereitung

Im Schritt Datenaufbereitung legen Sie fest, wie die Metadaten Ihrer Intellectual Entities während der Verarbeitung angepasst oder angereichert werden sollen. Die Einstellungen gliedern sich in die Bereiche *Rechte*, *Signifikante Eigenschaften* und *Preservation Level*.

Bei OAI-PMH-Jobs muss in diesem Schritt im Tab *Metadaten* zusätzlich ein Mapping-Skript hochgeladen werden. Dieses Skript legt fest, wie die Metadaten aus dem Quellsystem auf die IP-Metadaten des DCM übertragen werden.

#### Metadaten (Nur OAI-PMH)

!!! info
    In Hotfolder-Jobs steht dieser Schritt nicht zur Verfügung.

In diesem Schritt laden Sie ein eigenes Mappingskript (Python oder XSLT) hoch, das der DCM für die Erstellung der Information Packages ausführt. Das Skript wird als Teil des Jobs gespeichert und bei jeder Ausführung automatisch angewendet. Bei Bedarf können Sie es später durch ein neues Skript ersetzen. Siehe hierzu auch den Abschnitt [Einen Job bearbeiten](#einen-job-bearbeiten).

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenaufbereitung___OAI-PMH_mit_Mapping__.pdf" type="application/pdf" width="100%" height="800px" />

**Vom Quellsystem zum IP – so funktioniert das Mapping**

In diesem Abschnitt finden Sie zwei einfache Beispielskripte – eines in XSLT und eines in Python –, die zeigen, wie Sie Metadaten aus Ihrem Quellsystem in die Struktur des Information Packages übertragen können. Beide Skripte übernehmen dabei dieselbe Aufgabe: Sie lesen grundlegende Felder aus den gelieferten Metadaten aus und schreiben sie in die passenden IP-Metadaten hinein.

Die Beispiele sollen Ihnen den Einstieg erleichtern und können als Vorlage für Ihre eigenen Skripte dienen. Sie lassen sich leicht an unterschiedliche Quellen oder Projekterfordernisse anpassen. In beiden Beispielen wird mit Metadaten im Format Dublin Core (DC) gearbeitet.

??? "XSLT-Beispielskript"
    ```xslt
    <xsl:stylesheet xmlns:oai="http://www.openarchives.org/OAI/2.0/"
        xmlns:dc="http://purl.org/dc/elements/1.1/"
        xmlns:oai_dc="http://www.openarchives.org/OAI/2.0/oai_dc/"
        xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        exclude-result-prefixes="oai oai_dc dc"
        version="1.0">
        <xsl:output method="xml" indent="yes" encoding="UTF-8"/>
    
        <xsl:template match="/">
            <metadata>
                <xsl:apply-templates select="//oai_dc:dc"/>
            
                <!-- Static Origin-System-Identifier -->
                <field>
                    <xsl:attribute name="key">Origin-System-Identifier</xsl:attribute>
                    <xsl:text>My-System-Identifier</xsl:text>
                </field>
            
                <!-- Static Source-Organization -->
                <field>
                    <xsl:attribute name="key">Source-Organization</xsl:attribute>
                    <xsl:text>My-Organization</xsl:text>
                </field>
            
                <!-- External-Identifier from OAI Record Identifier -->
                <field>
                    <xsl:attribute name="key">External-Identifier</xsl:attribute>
                    <xsl:value-of select="//oai:record/oai:header/oai:identifier"/>
                </field>
            </metadata>
        </xsl:template>
    
        <!-- Template for mapping descriptive metadata from oai_dc:dc -->
        <xsl:template match="//oai_dc:dc">
            <xsl:for-each select="dc:creator">
                <field>
                    <xsl:attribute name="key">DC-Creator</xsl:attribute>
                    <xsl:value-of select="."/>
                </field>
            </xsl:for-each>
            <xsl:for-each select="dc:title">
                <field>
                    <xsl:attribute name="key">DC-Title</xsl:attribute>
                    <xsl:value-of select="."/>
                </field>
            </xsl:for-each>
            <xsl:for-each select="dc:rights">
                <field>
                    <xsl:attribute name="key">DC-Rights</xsl:attribute>
                    <xsl:value-of select="."/>
                </field>
            </xsl:for-each>
            <!-- DC-Identifier: only URN or DOI -->
            <xsl:for-each select="dc:identifier">
                <xsl:if test="contains(., 'urn:nbn') or starts-with(., '10.')">
                    <field>
                        <xsl:attribute name="key">DC-Terms-Identifier</xsl:attribute>
                        <xsl:value-of select="."/>
                    </field>
                </xsl:if>
            </xsl:for-each>
        </xsl:template>
    </xsl:stylesheet>
    ```

??? "Python-Beispielskript"
    ```python
    import re
    from pathlib import Path

    from dcm_ip_builder.plugins.mapping import GenericMapper
    from dcm_ip_builder.plugins.mapping.util import (
        XMLXPathMappingRule,
        load_xml_tree_from_file,
    )


    class ExternalMapper(GenericMapper):
        """Mapper for Miami-OAI-protocol to BagIt-metadata."""

        NAMESPACES = {
            "": "http://www.openarchives.org/OAI/2.0/",
            "oai_dc": "http://www.openarchives.org/OAI/2.0/oai_dc/",
            "dc": "http://purl.org/dc/elements/1.1/",
        }

        STATIC_METADATA = {
            "Origin-System-Identifier": "My-System-Identifier",
            "Source-Organization": "My-Organization",
        }

        LINEAR_RULES = [
            XMLXPathMappingRule(
                "/GetRecord/record/header/identifier",
                "External-Identifier",
                ns=NAMESPACES,
            ),
            XMLXPathMappingRule(
                "/GetRecord/record/metadata/oai_dc:dc/dc:creator",
                "DC-Creator",
                ns=NAMESPACES,
            ),
            XMLXPathMappingRule(
                "/GetRecord/record/metadata/oai_dc:dc/dc:title",
                "DC-Title",
                ns=NAMESPACES,
            ),
            XMLXPathMappingRule(
                "/GetRecord/record/metadata/oai_dc:dc/dc:rights",
                "DC-Rights",
                ns=NAMESPACES,
            ),
            XMLXPathMappingRule(
                "/GetRecord/record/metadata/oai_dc:dc/dc:identifier",
                "DC-Terms-Identifier",
                post_process=lambda x: (
                    None
                    if not x
                    else [
                        identifier
                        for identifier in x
                        if identifier is not None
                        and re.search(
                            r"10\.\d{4,9}/[-._;()/:A-Z0-9]+|^urn:nbn:[a-zA-Z0-9\-:.]+",
                            identifier,
                            re.IGNORECASE,
                        )
                    ]
                ),
                ns=NAMESPACES,
            ),
        ]

        def get_metadata(self, path, /, **kwargs):
            tree = load_xml_tree_from_file(Path(path))
            metadata = self.STATIC_METADATA.copy()
            for rule in self.LINEAR_RULES:
                try:
                    metadata[rule.dst] = rule.map(tree)
                # pylint: disable=broad-exception-caught
                except Exception:
                    pass
            return metadata
    ```

#### Signifikante Eigenschaften, Rechte und Preservation Level

In diesem Schritt legen Sie fest, wie der DCM die Metadaten Ihrer Intellectual Entities während der Verarbeitung anpassen oder ergänzen soll. Für jede der drei Metadatengruppen *Rechte*, *Signifikante Eigenschaften* und *Preservation Level* stehen Ihnen drei Aktionen zur Verfügung:

- **Ergänzen:** Fügt das angegebene Feld hinzu, wenn es in den Ausgangsmetadaten noch nicht vorhanden ist.  
- **Ersetzen:** Tauscht den vorhandenen Wert eines Feldes durch einen neuen Wert aus.  
- **Überschreiben:** Ersetzt alle vorhandenen Vorkommen eines Feldes und setzt es vollständig auf den angegebenen Wert.  

Mit diesen Einstellungen steuern Sie, wie Metadaten vereinheitlicht oder angereichert werden sollen – etwa um institutionelle Anforderungen oder Policies umzusetzen. Die gewählten Aktionen werden auf alle IEs angewendet, die im Rahmen dieses Jobs verarbeitet werden (Batch-Verarbeitung).

!!! tip "Aktionen gezielt kombinieren"
    Sie können einzelne Aktionen kombinieren.
    
    Ein typisches Beispiel: Ein vorhandener Wert kann **überschrieben** werden, während fehlende Felder gleichzeitig **ergänzt** werden – so stellen Sie sicher, dass IEs mit heterogenen Ausgangsmetadaten normalisiert werden.  

    Ebenso können Sie bestimmte Ausgangswerte gezielt **ersetzen** und bei fehlenden Feldern automatisch einen neuen Standardwert **ergänzen**.  
    
    Beachten Sie: **Überschreiben** und **Ersetzen** schließen sich gegenseitig aus, da Überschreiben immer Vorrang hat!

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenaufbereitung__fertige_IPs_ohne_Mapping_.pdf" type="application/pdf" width="100%" height="800px" />

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenaufbereitung___Rechte__Erganzen__dann_Ersetzen_.pdf" type="application/pdf" width="100%" height="800px" />

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenaufbereitung___Rechte__Erganzen__dann_Uberschreiben_.pdf" type="application/pdf" width="100%" height="800px" />

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Datenaufbereitung___Preservation_Level__Erganzen__dann_Uberschreiben_.pdf" type="application/pdf" width="100%" height="800px" />

### Zeitplan

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Zeitplan.pdf" type="application/pdf" width="100%" height="800px" />

Falls der Job regelmäßig ausgeführt werden soll, definieren Sie hier einen Zeitplan. Wählen Sie Startdatum und Uhrzeit und optional ein Wiederholungsintervall. Ohne Zeitplan kann der Job nur manuell gestartet werden. Die manuelle Ausführung steht auch bei Jobs mit Zeitplan zur Verfügung.

### Zusammenfassung

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Zusammenfassung.pdf" type="application/pdf" width="100%" height="800px" />

Die Zusammenfassung zeigt alle gewählten Einstellungen. Prüfen Sie abschließend Ihre Einstellungen. Mit *Job anlegen* wird der neue Job endgültig angelegt.

#### Job testen

<embed src="../assets/media/pdf/datenkurator-job-anlegen/Neuen_Job_anlegen___Job_testen.pdf" type="application/pdf" width="100%" height="800px" />

Vor dem Anlegen des Jobs kann ein optionaler Testlauf durchgeführt werden. Dieser simuliert sämtliche Verarbeitungsschritte, ohne einen echten Ingest auszuführen. So können Fehlkonfigurationen frühzeitig erkannt werden.

## Jobs verwalten

Die Tabelle auf der Seite *Jobs* zeigt eine Übersicht aller angelegten Jobs in den Arbeitsbereichen, auf die Sie Zugriff haben. Sie enthält grundlegende Informationen wie den aktuellen Status oder den nächsten geplanten Lauf (falls vorhanden). Darüber hinaus können hier – abhängig vom jeweiligen Jobstatus – verschiedene Aktionen direkt ausgeführt werden. Zudem können über Filter und eine Suchfunktion gezielt bestimmte Jobs ein- oder ausgeblendet werden.

### Aktionen in der Job-Übersicht

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

### Einen Job bearbeiten

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Job_bearbeiten.pdf" type="application/pdf" width="100%" height="800px" />

Über das Drei-Punkte-Menü können Sie die Funktion *Bearbeiten* auswählen, um die grundlegenden Einstellungen eines Jobs anzupassen oder ein aktualisiertes Mapping-Skript hochzuladen. Es öffnet sich der aus dem Anlegen des Jobs bekannte Wizard, in dem Sie Änderungen an der Konfiguration vornehmen können. Die Anpassungen werden erst wirksam, wenn der Job erneut gespeichert wird (*Änderungen übernehmen*).

### Zeitplan pausieren

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Zeitplan_pausieren.pdf" type="application/pdf" width="100%" height="800px" />

Jobs mit aktivem Zeitplan können über einen Schalter vorübergehend deaktiviert werden. Der Job wird dadurch nicht gelöscht und kann weiterhin manuell gestartet werden, führt jedoch keine automatisierten Läufe mehr aus. Der Zeitplan kann jederzeit wieder aktiviert werden.

#### Automatisches Pausieren bei Fehlern

<embed src="../assets/media/pdf/datenkurator-job-interaktion/Zeitplan_pausieren.pdf" type="application/pdf" width="100%" height="800px" />

Tritt während der Ausführung ein kritischer Fehler auf, der auf eine grundlegende Problematik in der Job-Konfiguration oder in der Datenstruktur des Quellsystems hinweist, wird die automatische Ausführung gemäß Zeitplan deaktiviert. Dadurch werden wiederholte Fehlversuche verhindert und eine kontrollierte Fehlerbehandlung ermöglicht.

Die Informationen in der Tabelle sowie im verfügbaren Report geben Aufschluss über Art und Ort des Fehlers innerhalb der DCM-Verarbeitungskette, sodass notwendige Korrekturen gezielt vorgenommen werden können.

Nach der Fehlerbehebung kann der Job manuell neu gestartet oder – durch erneutes Aktivieren des Schalters – wieder in den Zeitplan eingebunden werden.

### Einen laufenden Job abbrechen
<embed src="../assets/media/pdf/datenkurator-job-interaktion/Laufenden_Job_abbrechen.pdf" type="application/pdf" width="100%" height="800px" />

Wenn ein Job gerade ausgeführt wird, steht die Aktion *Abbrechen* zur Verfügung. Dadurch wird die laufende Verarbeitung gestoppt, und der Job erhält den Status *Abgebrochen*. Abgebrochene Jobs können anschließend erneut gestartet oder bearbeitet werden. Während des Joblaufs bereits vollständig verarbeitete und erfolgreich archivierte IEs bleiben vom Abbruch unberührt; der Abbruch verhindert lediglich die weitere Bearbeitung der noch ausstehenden IEs.

### Job-Details & Historie

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen.pdf" type="application/pdf" width="100%" height="800px" />

Die Job-Details zeigen alle bisherigen Ausführungen eines Jobs sowie den Status der jeweils verarbeiteten Intellectual Entities (IEs). Im Kopfbereich finden Sie den Gesamtstatus des Jobs und weitere allgemeine Informationen. 

Die darunterliegende Tabelle listet alle IEs der gesamten Job-Historie mit ihren Statuswerten, Validierungsergebnissen und Zeitstempeln. Über Filter und die Suchfunktion können Sie gezielt nach bestimmten IEs oder nach IEs mit Fehlern suchen.

Für jede IE lassen sich zudem Verarbeitungsreports herunterladen. Bei IEs, die nicht erfolgreich verarbeitet wurden, stehen außerdem (zeitlich begrenzt) die einzelnen Verarbeitungsstufen – IE, IP und SIP – als Download zur Verfügung, sodass Sie Fehler auf Ihrem eigenen Rechner analysieren können.

#### Validierung fehlgeschlagen: Aktionen pro IE

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Fehler_ignorieren.pdf" type="application/pdf" width="100%" height="800px" />

Wenn die Objektvalidierung fehlschlägt, markiert die Detailansicht die betroffene IE und stellt im Drei-Punkte-Menü passende Aktionen bereit. Mit *Fehler ignorieren* wird die IE trotz Validierungsfehler übernommen; die weiteren Verarbeitungsschritte laufen regulär weiter.

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Als_Bitstream_einliefern.pdf" type="application/pdf" width="100%" height="800px" />

Über *Als Bitstream einliefern* wird die IE trotz Formatvalidierungsfehlern eingespielt. Das (optionale) Metadatum *Preservation Level* wird automatisch auf *Bitstream* gesetzt.

<embed src="../assets/media/pdf/datenkurator-job-details-ansehen/Job_Details_ansehen___Validierung_fehlgeschlagen___Verwerfen.pdf" type="application/pdf" width="100%" height="800px" />

Die Aktion *Verwerfen* entfernt die fehlerhafte IE vollständig aus der Verarbeitung und merkt diese als nicht archivierungsfähig vor. Sie muss im Quellsystem aktualisiert werden und kann dann erneut vom DCM verarbeitet werden.
