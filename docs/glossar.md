# Glossar

**Arbeitsbereich**: Logischer Bereich innerhalb der DCM-Webanwendung, in dem Daten, Templates und Jobs organisiert werden. Er definiert auch die Zugriffsrechte für Nutzer:innen und gruppiert zusammenhängende Inhalte oder Projekte.

**BagIt**: Ein standardisiertes Verpackungsformat für die zuverlässige Speicherung und Übertragung digitaler Inhalte. Ein „Bag“ besteht aus einer klar definierten, hierarchischen Verzeichnisstruktur, die aus einem Payload (den eigentlichen Dateien) und Tags (beschreibende Metadaten) besteht. Das Format macht dabei keinerlei Annahmen über die inhaltliche Bedeutung oder interne Struktur der Dateien im Payload. Durch seine einfache, aber robuste Struktur ist das BagIt-Format besonders geeignet für die verlässliche Speicherung und den sicheren Transfer digitaler Objekte.

**Datenkurator**: Nutzer_in mit der Aufgabe, Jobs anzulegen, zu konfigurieren und auszuführen. Ist für die Kuratierung, die Validierung und Qualitätssicherung der Inhalte im Pre-Ingest verantwortlich.

**Hotfolder**: Überwachtes Verzeichnis auf dem Anwendungsserver, in das externe Systeme fertige Information Packages (IPs) ablegen können. Der DCM erkennt neue Pakete automatisch und übernimmt sie gemäß konfigurierter Jobs in die interne Verarbeitung.

**Information Package (IP)**: Zentrales internes Verarbeitungsformat des DCM. Es wird entweder extern erzeugt (Hotfolder) oder intern generiert (z. B. bei OAI-Harvester-Jobs). IPs folgen einer veröffentlichten Spezifikation, damit sie von allen Microservices verarbeitet werden können. Je nach Zielsystem (aktuell wird nur Rosetta unterstützt), wird aus dem IP ein entsprechendes SIP erzeugt.

**Intellectual Entity (IE)**: Logisch zusammengehörige Einheit von Inhalten, die im Kontext der digitalen Langzeitverfügbarkeit als ein „Werk“ oder eine „geistige Einheit“ betrachtet wird. Eine Intellectual Entity kann aus mehreren Dateien oder Repräsentationen bestehen, wird jedoch als ein zusammenhängender, konzeptionell einheitlicher Inhalt behandelt. Im Kontext des DCM entspricht eine Intellectual Entity dem logischen Objekt, das in einem Information Package (IP) verarbeitet und später in ein SIP überführt wird. Sie auch 'Payload'.

**Job**: Konkrete Konfiguration und Verarbeitungseinheit innerhalb des DCM. Ein Job definiert Datenquellen, Metadaten-Mappings und ggf. Ausführungszeitpunkte. Er kann manuell gestartet oder zeitgesteuert ausgeführt werden.

**Objektvalidierung**: Prüfung der im Payload enthaltenen Dateien (für unterstützte Formate) auf formale Korrektheit. Zur Validierung kommt der spezialisierte Dateiformat-Validator JHOVE zum Einsatz.

**Payload**: Der Payload bezeichnet den eigentlichen Dateinhalt eines Information Packages im Verzeichnis '/data'. Er umfasst alle digitalen Objekte, die archiviert werden sollen — unabhängig von deren interner Struktur oder semantischer Bedeutung. Der Payload ist somit der Kernbestandteil eines Bags und Gegenstand der Objekt- bzw. Dateiformatvalidierung.

**OAI-PMH (Open Archives Initiative Protocol for Metadata Harvesting)**: Standardprotokoll zum Einsammeln von Metadaten aus Repositorien. Im DCM wird OAI-PMH verwendet, um Metadaten abzurufen und als Grundlage für die Erstellung von Information Packages (IPs) zu nutzen. Der eigentliche Payload wird dabei nicht über OAI-PMH übertragen, sondern anhand der in den Records enthaltenen Links vom DCM automatisch nachgeladen.

**SIP (Submission Information Package)**: Paket, das an das Langzeitarchivsystem übergeben wird.

**Template**: Vordefinierte Konfiguration, die bestimmt, welche Art von Job angelegt wird. Enthält Angaben zu technischen Parametern, die vom Anwendungsadministrator gepflegt werden.

**Zeitplan**: Option zur regelmäßigen automatischen Ausführung eines Jobs. Kann in definierten Intervallen oder zu bestimmten Zeitpunkten erfolgen.
