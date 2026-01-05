# Projektname AppleAppCollection

Willkommen in diesem Repository! Diese Anleitung beschreibt, wie du die benötigten Tools und Pakete installieren und exportieren kannst.

## Inhaltsverzeichnis

- [Beschreibung](#beschreibung)
- [Voraussetzungen](#voraussetzungen)
- [Installation](#installation)
- [Exportieren der Brewfile](#exportieren-der-brewfile)

## Beschreibung

Dieses Projekt nutzt Homebrew zur Verwaltung von Softwarepaketen und Applite zur Verwaltung von Anwendungen. Die `Brewfile` wird verwendet, um alle installierten Pakete zu dokumentieren, wobei bestimmte Einträge gefiltert werden. Applite wird als Teil des Homebrew-Bundles installiert und ermöglicht das Importieren von Anwendungen aus einer Exportdatei.

## Voraussetzungen

- macOS
- Homebrew installiert ([Anleitung zur Installation von Homebrew](https://brew.sh/))

## Installation

1. **Installiere das Brew Bundle:**
   
   Führe im Terminal den folgenden Befehl aus, um alle benötigten Pakete und Anwendungen zu installieren:

   ```sh
   brew bundle
    ```
    Dieser Befehl installiert alle in der Brewfile aufgelisteten Pakete, einschließlich Applite.
2. **Importiere Anwendungen mit Applite:**
    Um Anwendungen aus einer Exportdatei zu importieren, öffnet man die Applite-Oberfläche. Im Menü `App Migration` dort auf `Import Apps` klicken und die gewünschte Exportdatei auswählen. Applite wird dann die Anwendungen installieren, die in der Datei aufgelistet sind.

## Exportieren der Brewfile
Um die aktuelle Konfiguration deiner installierten Pakete zu exportieren, kannst du den folgenden Befehl verwenden:

```sh
[ -f Brewfile ] && rm Brewfile && brew bundle dump --file=Brewfile && grep -v '^vscode' Brewfile > Brewfile_filtered && mv Brewfile_filtered Brewfile || brew bundle dump --file=Brewfile && grep -v '^vscode' Brewfile > Brewfile_filtered && mv Brewfile_filtered Brewfile
```
Dieser Befehl entfernt die aktuelle `Brewfile`, erstellt eine neue, und filtert alle Zeilen heraus, die mit `vscode` beginnen. Dadurch wird sichergestellt, dass diese Einträge nicht in der exportierten Datei enthalten sind.
