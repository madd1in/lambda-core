# Lambda Core

Ein Half-Life-inspirierter Ego-Shooter, der komplett im Browser läuft — eine einzige
HTML-Datei, three.js vom CDN, alle Texturen, Modelle und Soundeffekte prozedural
im Code erzeugt. Keine Original-Assets von Valve; das hier ist eine eigenständige
Hommage.

**Spielen:** https://madd1in.github.io/lambda-core/

## Worum es geht

Sektor C, Schichtbeginn 08:47. Du fährst die Probe GG-3883 in den Analyseschacht,
das Antimasse-Spektrometer läuft auf 105 % — und dann passiert das, was in solchen
Geschichten immer passiert. Danach willst du nur noch zum Oberflächenzugang.

## Steuerung

| Taste | Funktion |
|---|---|
| `W` `A` `S` `D` | Bewegen |
| Maus / LMT | Umsehen / Feuern |
| `Shift` / `Strg` | Sprinten / Ducken |
| `Leertaste` | Springen |
| `1`–`5` | Waffe wählen |
| `G` | Handgranate werfen |
| `R` / `Q` | Nachladen / letzte Waffe |
| `E` (halten) | Benutzen — Ladestationen, Türen, Wachmann |
| `F` | Helmlampe (eigener Akku) |
| `M` / `V` | Musik / HEV-Sprachausgabe |
| `Esc` | Pause |

## Was drin steckt

- **Level:** 13 verbundene Bereiche, prozedural aus einem Rasterplan gebaut —
  Labor, Silo, Lagerhalle, Wartungskanal, Kriechschacht, Oberflächenzugang
- **Waffen:** Brechstange, 9 mm, MP5, Schrotflinte, Tau-Kanone (aufladbar,
  durchschlägt Gegner und schleudert dich zurück) plus Handgranaten
- **Gegner:** Kopfkrabben, Zombies, Xen-Wächter, Einsatzkommando — mit
  Sichtlinienprüfung, Kopftrefferzone und eigenem Verhalten
- **Verbündeter:** ein Wachmann, den du rekrutieren kannst und der mitkämpft
- **HEV-Anzug:** Panzerung schluckt 80 % Schaden, Lade- und Sanitätsstationen,
  Sprachausgabe über die Web Speech API
- **Grafik:** Phong-Materialien mit prozedural erzeugten Normal-Maps,
  ACES-Tonemapping, Unreal-Bloom, Staubpartikel, Blutlachen, Dampf, Einschusslöcher
- **Ton:** sämtliche Effekte per WebAudio synthetisiert, dazu vier Musikstücke,
  die zwischen Erkundung und Kampf überblenden

## Technik

- three.js r128 (UMD) + `EffectComposer` / `UnrealBloomPass` aus den Legacy-Beispielen
- Kollision über achsenweise AABB-Auflösung mit Zellen-Broadphase
- Beleuchtung über sechs wandernde Punktlichter, die sich den nächsten
  Deckenlampen zuweisen — konstante Lichtzahl, keine Shader-Neukompilierung
- Waffenmodelle in einer zweiten Szene, damit sie nie in Wände schneiden

## Musik

`assets/*.mp3` — vier Stücke, je zwei für Erkundung (*Deep Laboratory Drones*)
und Kampf (*Mechanical Hostility*). Ohne diese Dateien läuft das Spiel
unverändert weiter, nur ohne Musik.

## Lokal starten

Wegen der Audiodateien braucht es einen kleinen Webserver:

```bash
python -m http.server 8000
```

Dann `http://localhost:8000/` öffnen.
