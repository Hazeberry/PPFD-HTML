# PPFD Meter (HTML)

> Kamerabasiertes PPFD-Messwerkzeug als einzelne HTML-Datei — offen, kostenlos, ohne Installation.
> Camera-based PPFD measurement tool in a single HTML file — open, free, no install.

**[🌱 Live-Demo / Live demo](https://hazeberry.github.io/PPFD-HTML/)**

---

## 🇩🇪 Deutsch

### Was ist das?

Ein Werkzeug, das die **Photosynthetisch Aktive Photonenflussdichte (PPFD)** über die Handykamera schätzt — als Alternative zu kommerziellen Apps und teuren Quantensensoren. Läuft komplett im Browser, keine Installation, keine Datenübertragung, keine Werbung.

### ⚠️ Ehrliche Einordnung zuerst

Das ist **kein geeichtes Messgerät**. Es ist ein Schätzwerkzeug, das folgende Eigenschaften ehrlich anzeigt:

- **Reproduzierbar & linear** im gültigen Bereich — zwei Kameras mit unterschiedlicher Optik liefern vergleichbare Werte.
- **Aber ungeeicht** — die Absolutwerte in µmol·m⁻²·s⁻¹ hängen von einer geräteunabhängigen Konstante ab, die *nicht* gegen ein Referenz-PAR-Meter kalibriert ist.
- Solange nicht gegen eine bekannte Referenz kalibriert wurde, sind die Werte für **relative Vergleiche** brauchbar (Standort A heller als B, Änderung nach Umhängen der Lampe), **nicht** als wissenschaftlicher Absolutwert.

Die App zeigt dazu eine **Messzuverlässigkeit** und eine **Clipping-Warnung** an. Ein roter „KRITISCH: Übersteuert!"-Status bedeutet: der Sensor brennt aus, der Wert ist wertlos. Das ist Absicht — ein Messwert ohne Unsicherheitsangabe ist wenig wert.

### Warum ein Diffusor nötig ist

Für belastbare Werte gehört ein **Diffusor** vor die Linse (z. B. ein Blatt 80 g/m² Papier). Er streut und dämpft das Licht so, dass der Sensor im linearen Bereich bleibt und den Kosinus-Einfallswinkel korrekt gewichtet. Ohne Diffusor sind nur grobe relative Vergleiche möglich. (Dasselbe empfehlen auch die kommerziellen Apps.)

### Bedienung

1. Diffusor (Papier) vor die Kamera.
2. Standard ist die **Frontkamera** (für den Aufbau „Display ablesbar, Diffusor auf der Frontlinse"). Umschalter für die Rückkamera vorhanden.
3. „Kamera aktivieren" → Berechtigung erteilen.
4. Auf **Clipping = OK (grün)** und **Zuverlässigkeit möglichst 100 %** achten — nicht auf die große Zahl.
5. Optional: über „Kalibrierung" gegen einen bekannten Referenzwert einmessen (Faktor wird pro Kamera gespeichert).

### 🔬 Mithelfen: Referenzdaten teilen

Der interessanteste Teil eines offenen Projekts: **verteilte Kalibrierung.** Wer dieselbe Kamera *und* ein echtes PAR-Meter besitzt, liefert mit einer einzigen Messung einen Kalibrierpunkt für dieses Gerätemodell — von dem alle anderen mit demselben Gerät profitieren.

Bitte ein Issue mit folgenden Angaben öffnen:

- **Gerät** (z. B. Samsung Galaxy A17)
- **Kamera** (Front / Rück) + Diffusor (Material, g/m²)
- **Referenzgerät** — *entscheidend für die Datenqualität:*
  - 🥇 echtes PAR-/Quantenmeter (herstellerunabhängig)
  - 🥈 digitaler Lux-Sensor (BH1750/VEML7700, werkskalibriert)
  - ❌ andere unkalibrierte Handy-App → bitte **nicht**, verfälscht den Datensatz
- **Referenzwert** und **Rohwert der App** bei gleicher Ausrichtung
- gern mehrere Lichtstärken (für die Linearitätsprüfung)

### Grenzen (bewusst offen)

- **Kein RAW-Zugriff:** Im Browser kommt nur der schon vom ISP verarbeitete Videostream an, nicht die RAW-Sensordaten. Das ist eine harte Plattformgrenze.
- **Spektrale Näherung:** Eine Handykamera ist RGB-gewichtet, nicht auf PAR (400–700 nm gleichgewichtet). Die Lichtquellen-Heuristik ist grob (klassifiziert LEDs teils als „Sonnenlicht").
- **Sichere Umgebung nötig:** `getUserMedia()` braucht HTTPS oder `file://` — über GitHub Pages (HTTPS) läuft es; die Kamera arbeitet danach vollständig lokal.

---

## 🇬🇧 English

### What is it?

A tool that **estimates Photosynthetic Photon Flux Density (PPFD)** using a phone camera — an alternative to commercial apps and expensive quantum sensors. Runs entirely in the browser: no install, no data leaves the device, no ads.

### ⚠️ Honest framing first

This is **not a calibrated instrument.** It is an estimation tool that is honest about its own limits:

- **Reproducible & linear** within the valid range — two cameras with different optics produce comparable readings.
- **But uncalibrated** — absolute µmol·m⁻²·s⁻¹ values depend on a device-independent constant that is *not* calibrated against a reference PAR meter.
- Until calibrated against a known reference, readings are useful for **relative comparisons** (spot A brighter than B, change after moving the lamp), **not** as a scientific absolute value.

The app shows a **measurement reliability** score and a **clipping warning**. A red "CRITICAL: overexposed" status means the sensor is saturating and the value is meaningless. This is intentional — a reading without an uncertainty estimate is worth little.

### Why a diffuser is needed

For meaningful values, place a **diffuser** over the lens (e.g. a sheet of 80 g/m² paper). It scatters and attenuates the light so the sensor stays in its linear range and correctly weights the cosine angle of incidence. Without a diffuser, only rough relative comparisons are possible. (Commercial apps recommend the same.)

### Usage

1. Diffuser (paper) over the camera.
2. Default is the **front camera** (for the "screen readable, diffuser on front lens" setup). A toggle for the rear camera is included.
3. "Activate camera" → grant permission.
4. Watch for **Clipping = OK (green)** and **reliability near 100 %** — not the big number.
5. Optional: calibrate against a known reference via "Calibration" (factor stored per camera).

### 🔬 Contribute: share reference data

The most interesting part of an open project: **distributed calibration.** Anyone who owns the same camera *and* a real PAR meter can provide a calibration point for that device model with a single measurement — benefiting everyone with the same device.

Please open an issue with:

- **Device** (e.g. Samsung Galaxy A17)
- **Camera** (front / rear) + diffuser (material, g/m²)
- **Reference instrument** — *critical for data quality:*
  - 🥇 real PAR/quantum meter (any manufacturer)
  - 🥈 digital lux sensor (BH1750/VEML7700, factory-calibrated)
  - ❌ another uncalibrated phone app → please **don't**, it pollutes the dataset
- **Reference value** and **the app's raw value** at the same orientation
- ideally several light levels (for a linearity check)

### Limitations (deliberately open)

- **No RAW access:** the browser only receives the ISP-processed video stream, not RAW sensor data. A hard platform limit.
- **Spectral approximation:** a phone camera is RGB-weighted, not PAR (400–700 nm equally weighted). The light-source heuristic is coarse (sometimes classifies LEDs as "sunlight").
- **Secure context required:** `getUserMedia()` needs HTTPS or `file://` — it works via GitHub Pages (HTTPS); the camera then runs fully locally.




## Entstehung / Development

Entwickelt von [Hazeberry](https://github.com/Hazeberry), unter Mitarbeit von Claude (Anthropic) — iterativ getestet und verifiziert.
Developed by [Hazeberry](https://github.com/Hazeberry), with assistance from Claude (Anthropic) — iteratively tested and verified.
