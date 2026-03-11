# Turtelbot-Py
Pyton 
Turtelbot 
Code 
import sys
import turtle
Der code ist nicht fertig 
verbesserungs Vorschläge dürfen gerne gemacht werden  
# Eingabe entweder per Kommandozeile (z. B. "python zeit-3.py vorwärts 50")
# oder per stdin (z. B. "echo vorwärts\n50 | python zeit-3.py")
if len(sys.argv) >= 3:
    richtung = sys.argv[1].strip().lower()
    distanz_str = sys.argv[2]
else:
    # Wenn stdin kein Terminal ist (Pipes, Redirects), lese die ersten zwei Zeilen.
    if not sys.stdin.isatty():
        lines = [line.strip() for line in sys.stdin.readlines() if line.strip()]
        if len(lines) >= 2:
            richtung = lines[0].lower()
            distanz_str = lines[1]
        else:
            # Fallback auf interaktive Eingabe
            richtung = input("Richtung angeben (vorwärts, rückwärts, links, rechts): ").strip().lower()
            distanz_str = input("Geben Sie die Geschwindigkeit/Distanz (Zahl) ein: ")
    else:
        # Interaktive Eingabe
        richtung = input("Richtung angeben (vorwärts, rückwärts, links, rechts): ").strip().lower()
        distanz_str = input("Geben Sie die Geschwindigkeit/Distanz (Zahl) ein: ")

try:
    distanz = float(distanz_str.replace(",", "."))
except ValueError:
    print("Ungültige Eingabe. Bitte eine Zahl eingeben.")
    raise SystemExit(1)

# Turtle initialisieren
bot = turtle.Turtle()
bot.speed(5)  # mittlere Geschwindigkeit

if richtung == "vorwärts":
    bot.forward(distanz)
elif richtung == "rückwärts":
    bot.backward(distanz)
elif richtung == "links":
    bot.left(90)
    bot.forward(distanz)
elif richtung == "rechts":
    bot.right(90)
    bot.forward(distanz)
else:
    print("Ungültige Richtung. Bitte 'vorwärts', 'rückwärts', 'links' oder 'rechts' eingeben.")
    raise SystemExit(1)

# Fenster offen halten (schließt nach ~2 Sekunden automatisch)
screen = turtle.Screen()
screen.ontimer(screen.bye, 2000)
# `mainloop` läuft bis das Fenster geschlossen wird
screen.mainloop()
