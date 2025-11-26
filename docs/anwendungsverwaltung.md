# Anwendungsverwaltung

## Nutzer & Rollen verwalten

Die Nutzerverwaltung deckt das komplette Lifecycle-Management ab – vom erstmaligen Anlegen bis zur Anpassung bestehender Konten.

### Nutzer anlegen

<embed src="../assets/media/pdf/admin-nutzer/Nutzer_anlegen.pdf" type="application/pdf" width="100%" height="800px" />

Im Formular *Neuen Nutzer erstellen* erfassen Sie Stammdaten und weisen die passenden Rollen bzw. Arbeitsbereiche zu.

Aktivierung von Nutzerkonten via Link beschreiben. **#TODO**

### Nutzer bearbeiten und löschen

<embed src="../assets/media/pdf/admin-nutzer/Nutzer_bearbeiten.pdf" type="application/pdf" width="100%" height="800px" />

Bestehende Konten lassen sich über das Stift-Symbol jederzeit bearbeiten, um Rollen zu ändern und neue Arbeitsbereiche freizuschalten. Zudem lassen sich Nutzer über das Mülleimer-Symbol löschen.

## Arbeitsbereiche verwalten

Arbeitsbereiche strukturieren Zugriffe und sorgen für getrennte Konfigurationen je Mandant oder Projekt. Die folgenden Ansichten zeigen typische Administratoraktionen.

### Arbeitsbereiche anlegen

<embed src="../assets/media/pdf/admin-arbeitsbereiche/Arbeitsbereich_erstellen.pdf" type="application/pdf" width="100%" height="800px" />

Beim Anlegen vergeben Sie einen Namen für den Arbeitsbereich.

### Arbeitsbereich umbenennen oder entfernen

<embed src="../assets/media/pdf/admin-arbeitsbereiche/Arbeitsbereich_umbenennen.pdf" type="application/pdf" width="100%" height="800px" />

über das Drei-Punkte-Menü können Sie Sie Arbeitsbereiche umbenennen, wenn sich etwa Projekttitel oder Organisationsstrukturen ändern, oder den Arbeitsbereich entfernen. <br><br> **Vorsicht**: Beim entfernen eines Arbeitsbereichs gehen sämtliche verküpfte Templates und Jobs verloren.

### Arbeitsbereich Templates zuweisen

<embed src="../assets/media/pdf/admin-arbeitsbereiche/Arbeitsbereich___Template_hinzufugen.pdf" type="application/pdf" width="100%" height="800px" />

Templates (siehe [Templates verwalten](#templates-verwalten)) können einem Arbeitsbereich direkt zugewiesen werden, damit Datenkurator:innen die passenden Workflow-Typen bereitgestellt bekommen.

### Arbeitsbereich Nutzer zuweisen

<embed src="../assets/media/pdf/admin-arbeitsbereiche/Arbeitsbereich___Nutzer_mit_Rolle_hinzufugen.pdf" type="application/pdf" width="100%" height="800px" />

Hier legen Sie fest, welche Nutzer:innen mit welchen Rollen Zugriff auf einen Arbeitsbereich haben. Die einzige relevante Rolle innerhalb von Arbeitsbereichen ist zur Zeit *Datenkurator*.

### Arbeitsbereich löschen
<embed src="../assets/media/pdf/admin-arbeitsbereiche/Arbeitsbereich_loschen.pdf" type="application/pdf" width="100%" height="800px" />

Nicht mehr benötigte Arbeitsbereiche können gelöscht werden; alle abhängigen Ressourcen werden dabei entfernt.

## Templates verwalten

Templates enthalten die grundlegenden technischen Konfigurationen zur Anbindung von Quellsystemen und bilden die Basis für alle Jobs. In der Templateverwaltung werden Templates erstellt, angepasst und Arbeitsbereichen zugewiesen, wodurch gesteuert wird, welche Nutzer:innen sie zum Anlegen neuer Jobs verwenden können. Der DCM unterscheidet hierbei zwei Template-Typen: OAI-PMH für automatisierte Harvesting-Prozesse und Hotfolder für die Verarbeitung extern erstellter Information Packages.

### Templates erstellen 

#### OAI-PMH

<embed src="../assets/media/pdf/admin-templates/Template_erstellen__OAI-PMH_.pdf" type="application/pdf" width="100%" height="800px" />

#### Hotfolder

<embed src="../assets/media/pdf/admin-templates/Template_erstellen__Hotfolder_.pdf" type="application/pdf" width="100%" height="800px" />

Die Masken zum Erstellen decken sowohl OAI-PMH-Quellen als auch Hotfolder-basierte Ingests ab.

### Templates bearbeiten

<embed src="../assets/media/pdf/admin-templates/Template_bearbeiten.pdf" type="application/pdf" width="100%" height="800px" />

Über die Bearbeitungsmaske passen Sie bestehende Templates an, ohne dass laufende Jobs verloren gehen.

### Templates löschen

<embed src="../assets/media/pdf/admin-templates/Template_loschen__mit_verknupften_Jobs_.pdf" type="application/pdf" width="100%" height="800px" />

Beim Löschen warnt das System vor verknüpften Jobs, damit Sie Abhängigkeiten bewusst auflösen können.
