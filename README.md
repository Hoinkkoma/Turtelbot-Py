# Turtelbot-Py

Python-basierte Implementierung eines Turtle-Robot-Steuersystems.

## Projekt-Beschreibung

Turtelbot ist ein Roboter-Steuersystem basierend auf Python's `turtle` Modul. Das System ermöglicht die Steuerung eines virtuellen Roboters durch Kommandozeilen-Eingaben oder stdin.

Der Code ist noch nicht fertig - Verbesserungsvorschläge sind willkommen!

## Systemarchitektur

```
┌─────────────────────────────────────────────────────────────┐
│                     Assoziation zu Raum                     │
└─────────────────────────────────────────────────────────────┘
         │                                           │
         ▼                                           ▼
    ┌─────────────┐                          ┌──────────────┐
    │ Controller  │◄────────────────────────►│  Sensoren    │
    │Befehl zur   │  Assoziation             │ Position im  │
    │Sicherung    │                          │ Raum         │
    └─────────────┘                          │ Geschwindigkeit
         │                                   └──────────────┘
         │                                           ▲
         ▼                                           │
    ┌─────────────────────┐                         │
    │      Motor          │                         │
    │ Bewegung im Raum    │◄────────┐              │
    │ Umdreh-Geschwindigkeit        │              │
    └─────────────────────┘         │              │
                                    │              │
                            ┌───────┴──────┐      │
                            │  Aggregator  │──────┘
                            └───────┬──────┘
                                    │
                                    ▼
                            ┌──────────────────┐
                            │    Roboter       │
                            │ @ name : Turebot │
                            └──────────────────┘
```

### Komponenten:

- **Controller**: Zentrale Steuereinheit für Befehle und Sicherheit
- **Motor**: Verwaltet Bewegungen und Rotationsgeschwindigkeit im Raum
- **Sensoren**: Erfasst Position und Geschwindigkeit des Roboters
- **Aggregator**: Koordiniert Datenfluss zwischen Komponenten
- **Roboter (Turebot)**: Der virtuelle Roboter, der die Befehle ausführt

## Verwendung

Die Eingabe kann entweder per **Kommandozeile** oder **stdin** erfolgen:

### Kommandozeile-Beispiel:
```bash
python main.py vorwärts 50
```

### Stdin-Beispiel:
```bash
echo -e "vorwärts\n50" | python main.py
```

### Interaktive Eingabe:
```bash
python main.py
```
(Dann werden Sie aufgefordert, Richtung und Distanz einzugeben)

## Befehle

- **vorwärts**: Roboter bewegt sich vorwärts
- **rückwärts**: Roboter bewegt sich rückwärts
- **links**: Roboter dreht nach links und bewegt sich
- **rechts**: Roboter dreht nach rechts und bewegt sich

## Parameter

- **Distanz/Geschwindigkeit**: Eine numerische Zahl (Komma oder Punkt als Dezimaltrennzeichen möglich)

## Code-Beispiel

```python
import sys
import turtle

# Eingabe entweder per Kommandozeile oder stdin
if len(sys.argv) >= 3:
    richtung = sys.argv[1].strip().lower()
    distanz_str = sys.argv[2]
else:
    richtung = input("Richtung angeben (vorwärts, rückwärts, links, rechts): ").strip().lower()
    distanz_str = input("Geben Sie die Geschwindigkeit/Distanz (Zahl) ein: ")

# Turtle initialisieren
bot = turtle.Turtle()
bot.speed(5)

# Befehle ausführen
if richtung == "vorwärts":
    bot.forward(float(distanz_str))
# ... weitere Richtungen
```

## Status

⚠️ **Der Code ist noch nicht vollständig implementiert**

Geplante Verbesserungen:
- [ ] Vollständige Architektur-Implementierung
- [ ] Fehlerbehandlung erweitern
- [ ] Unit-Tests hinzufügen
- [ ] Dokumentation erweitern

## Beitragen

Verbesserungsvorschläge und Contributions sind willkommen! 🙌
