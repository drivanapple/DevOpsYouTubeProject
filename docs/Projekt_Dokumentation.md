# Dokumentation: Einrichtung des MacBook und Vorbereitung des Python-Entwicklungsprojekts

---

### **1. Zielsetzung**
Einrichten des MacBook als Entwicklungsumgebung für ein automatisiertes YouTube-DevOps-Projekt mit Python.

---

### **2. Projektstruktur**
Das Projekt ist modular aufgebaut, um Skalierbarkeit, Wartbarkeit und DevOps-Prinzipien zu gewährleisten. Die Struktur:

- **`app/`**: Enthält die Hauptanwendung und den Python-Code.
  - `main.py`: Einstiegspunkt des Programms.
- **`scripts/`**: Skripte für die Einrichtung und Automatisierung.
  - `setup.sh`: Skript zur Initialisierung des Projekts.
- **`tests/`**: Testmodule für die Anwendung.
- **`docs/`**: Dokumentation des Projekts.
  - `Projekt_Dokumentation.md`: Diese Dokumentation.
- **`configs/`**: Konfigurationsdateien für die Anwendung und Infrastruktur.
- **`ci_cd/`**: Konfigurationen für CI/CD-Pipelines.
- **`logs/`**: Log-Dateien der Anwendung.
- **`docker/`**: Docker-Konfigurationsdateien.
- **`kubernetes/`**: Kubernetes-Konfigurationsdateien.

---

### **3. Schritte zur Einrichtung**

#### **3.1 Terminal verwenden**
- **Öffnen des Terminals:**
  - Mit Spotlight-Suche (`Command + Leertaste`), „Terminal“ eingeben und starten.
  - Alternativ: Im Finder unter **Programme** > **Dienstprogramme** > **Terminal**.

#### **3.2 Homebrew installieren**
- **Befehl ausführen:**
  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  ```
- **Homebrew zu PATH hinzufügen:**
  ```bash
  echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
  eval "$(/opt/homebrew/bin/brew shellenv)"
  ```
- **Funktion prüfen:**
  ```bash
  brew help
  ```

#### **3.3 Python installieren**
- **Python mit Homebrew installieren:**
  ```bash
  brew install python
  ```
- **Version überprüfen:**
  ```bash
  python3 --version
  pip3 --version
  ```

#### **3.4 Symlinks erstellen**
- **/usr/local/bin erstellen:**
  ```bash
  sudo mkdir -p /usr/local/bin
  sudo chown -R $(whoami):admin /usr/local/bin
  chmod u+w /usr/local/bin
  ```
- **Symlinks setzen:**
  ```bash
  ln -sf /opt/homebrew/bin/python3 /usr/local/bin/python3
  ln -sf /opt/homebrew/bin/pip3 /usr/local/bin/pip3
  ```
- **Pfad prüfen:**
  ```bash
  ls -l /usr/local/bin/python3
  ls -l /usr/local/bin/pip3
  ```

#### **3.5 PATH konfigurieren**
- **Pfad in .zshrc setzen:**
  - Datei öffnen:
    ```bash
    nano ~/.zshrc
    ```
  - Hinzufügen:
    ```bash
    export PATH="/usr/local/bin:/opt/homebrew/bin:$PATH"
    ```
  - Datei speichern und neu laden:
    ```bash
    source ~/.zshrc
    ```

#### **3.6 Endprüfung**
- **Python-Version:**
  ```bash
  python3 --version
  ```
- **Pip-Version:**
  ```bash
  pip3 --version
  ```

---

### **4. Verwendung von Pages**
- Pages wurde als vorinstallierte Textverarbeitungssoftware gewählt.
- Dokumentation wird hier erstellt und verwaltet.

---

### **5. Nächster Schritt**

#### **5.1 Installation von FFmpeg mit Homebrew**
- **FFmpeg installieren:**
  ```bash
  brew install ffmpeg
  ```
- **FFmpeg-Version überprüfen:**
  ```bash
  ffmpeg -version
  ```

#### **5.2 GitHub-Repository einrichten**
- **Neues GitHub-Repository erstellen:**
  1. Melde dich bei GitHub an und erstelle ein neues Repository namens „DevOpsYouTubeProject“.
  2. Notiere dir die Repository-URL, z. B. https://github.com/drivanapple/DevOpsYouTubeProject.git.

- **Lokales Git-Repository initialisieren:**
  - Gehe in den Projektordner:
    ```bash
    cd /Pfad/zum/Projekt/DevOpsYouTubeProject
    ```
  - Initialisiere ein Git-Repository:
    ```bash
    git init
    ```

- **Remote-Repository hinzufügen:**
  - Verbinde das lokale Repository mit dem GitHub-Repository:
    ```bash
    git remote add origin https://github.com/drivanapple/DevOpsYouTubeProject.git
    ```

#### **5.3 Erste Dateien hinzufügen und Commit erstellen**
- **Dateien zum Git-Index hinzufügen:**
  ```bash
  git add main.py
  ```
- **Ersten Commit erstellen:**
  ```bash
  git commit -m "Initial commit with main.py"
  ```

#### **5.4 Pushen zum GitHub-Repository**
- **Änderungen zu GitHub pushen:**
  ```bash
  git push -u origin main
  ```

---

### **6. Einrichtung der virtuellen Umgebung**

#### **6.1 Virtuelle Umgebung erstellen**
- **Virtuelle Umgebung mit Python erstellen:**
  ```bash
  python3 -m venv venv
  ```

#### **6.2 Virtuelle Umgebung aktivieren**
- **Aktivieren der virtuellen Umgebung:**
  ```bash
  source venv/bin/activate
  ```
  - Nach der Aktivierung sollte `(venv)` in der Eingabeaufforderung erscheinen.

#### **6.3 Pakete installieren**
- **Abhängigkeiten aus der Datei `requirements.txt` installieren:**
  ```bash
  pip install -r requirements.txt
  ```

#### **6.4 Testen der Installation**
- **Python-Module importieren und testen:**
  ```bash
  python3 -c "import ffmpeg; import requests; import yaml; print('Alle Pakete erfolgreich importiert!')"
  ```

---

### **7. Integration von OpenAI API und Visualisierung**

#### **7.1 OpenAI API einrichten**
- **API-Schlüsseldatei erstellen:**
  Erstelle eine Datei namens `openai_key.txt` im Projektordner und füge deinen OpenAI API-Schlüssel ein.

- **Code anpassen:**
  Der Code lädt automatisch den API-Schlüssel aus der Datei.

#### **7.2 Textgenerierung und Visualisierung**
- **Textgenerierung:**
  Das Programm generiert eine Geschichte basierend auf Benutzereingaben.
- **Visualisierungsvorschläge:**
  Identifiziert visuell geeignete Szenen und bereitet die Beschreibung für DALL-E vor.

#### **7.3 Beispiel**
- **Eingabe:**
  "Charles Manson leben"
- **Ausgabe:**
  - Generierte Geschichte
  - Visualisierungsvorschläge für DALL-E, z. B.:
    1. "Eine düstere Stadt bei Nacht mit bedrohlichen Schatten."
    2. "Ein verlassener Raum mit umgestürzten Möbeln und zerbrochenem Glas."

---

### **8. Weitere Schritte**
- Integration der DALL-E API für die direkte Erstellung von Bildern basierend auf den generierten Szenen.
- Implementierung von CI/CD-Pipelines zur Automatisierung von Tests und Bereitstellung.

---

### **9. Zusätzliche Ressourcen**
- [OpenAI Python Library](https://github.com/openai/openai-python)
- [DALL-E API Dokumentation](https://platform.openai.com/docs/models/dall-e)
