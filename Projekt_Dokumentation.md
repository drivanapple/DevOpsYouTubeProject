
# Dokumentation: Einrichtung des MacBook und Vorbereitung des Python-Entwicklungsprojekts

---

### **1. Zielsetzung**
Einrichten des MacBook als Entwicklungsumgebung für ein automatisiertes YouTube-DevOps-Projekt mit Python.

---

### **2. Schritte zur Einrichtung**

#### **2.1 Terminal verwenden**
- **Öffnen des Terminals:**
  - Mit Spotlight-Suche (`Command + Leertaste`), „Terminal“ eingeben und starten.
  - Alternativ: Im Finder unter **Programme** > **Dienstprogramme** > **Terminal**.

#### **2.2 Homebrew installieren**
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

#### **2.3 Python installieren**
- **Python mit Homebrew installieren:**
  ```bash
  brew install python
  ```
- **Version überprüfen:**
  ```bash
  python3 --version
  pip3 --version
  ```

#### **2.4 Symlinks erstellen**
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

#### **2.5 PATH konfigurieren**
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

#### **2.6 Endprüfung**
- **Python-Version:**
  ```bash
  python3 --version
  ```
- **Pip-Version:**
  ```bash
  pip3 --version
  ```

---

### **3. Verwendung von Pages**
- Pages wurde als vorinstallierte Textverarbeitungssoftware gewählt.
- Dokumentation wird hier erstellt und verwaltet.

---

### **4. Nächster Schritt**

#### **4.1 Installation von FFmpeg mit Homebrew**
- **FFmpeg installieren:**
  ```bash
  brew install ffmpeg
  ```
- **FFmpeg-Version überprüfen:**
  ```bash
  ffmpeg -version
  ```

#### **4.2 GitHub-Repository einrichten**
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

#### **4.3 Erste Dateien hinzufügen und Commit erstellen**
- **Dateien zum Git-Index hinzufügen:**
  ```bash
  git add main.py
  ```
- **Ersten Commit erstellen:**
  ```bash
  git commit -m "Initial commit with main.py"
  ```

#### **4.4 Pushen zum GitHub-Repository**
- **Änderungen zu GitHub pushen:**
  ```bash
  git push -u origin main
  ```

---

### **5. Weitere Schritte**
- Weitere Schritte umfassen das Erstellen von Python-Skripten, das Implementieren von GitHub Actions für CI/CD-Pipelines und das Automatisieren von Prozessen wie das Hochladen von YouTube-Videos und das Verarbeiten von Mediendateien mit FFmpeg.

### **5.1 Hinzufügen der README.md zu GitHub**
Nun kannst du diese README.md-Datei einfach zu deinem Repository hinzufügen und dort einsehen.
