# 🥊 Fight the Blize – SpriteKit / Swift

Ein 1-on-1 Fighting Game im Stil von Street Fighter 1, gebaut mit SpriteKit.

## 📁 Projektstruktur

```
StreetFighterClone/
├── GameScenes/
│   └── FightScene.swift          # Hauptszene: Game Loop, Combat Resolution, Effekte
├── Fighters/
│   └── Fighter.swift             # Fighter-Klasse: State Machine, Hitboxen, Animationen
├── Components/
│   ├── TouchInputController.swift # Virtueller Joystick + Attack Buttons
│   ├── HUDOverlay.swift          # Health Bars, Timer, Round Indicators, Announcements
│   └── AIController.swift        # Gegner-KI mit State-basierter Entscheidungslogik
├── GameViewController.swift      # SpriteKit View Setup
└── AppDelegate.swift             # App Entry Point
```

## 🏗️ Architektur

### Game Loop (FightScene)
```
update() → Input lesen → AI berechnen → Fighter updaten → Combat auswerten → HUD updaten → K.O. prüfen
```

### Fighter State Machine
```
idle ↔ walking ↔ jumping
  ↓         ↓
attacking → hit → knockedDown
  ↑
blocking
```

### Combat System
- **Hitbox/Hurtbox-System**: Jeder Fighter hat eine Hurtbox (Körper) und eine Attackbox (aktiv nur während Angriffs-Frames)
- **Active Frames**: Angriffe haben Startup → Active → Recovery Phasen
- **Block-Mechanik**: Reduziert Schaden auf 20%
- **Knockback**: Bei Treffern wird der Gegner zurückgeschoben
- **Push-Collision**: Kämpfer können nicht durcheinander laufen

### Input System
- Virtueller Joystick (links) mit Dead Zone
- 4 Buttons: Punch (P), Kick (K), Special (SP), Block (B)
- Multitouch für gleichzeitiges Bewegen + Angreifen

### AI Controller
- State-basiert: Approaching → Attacking → Retreating → Blocking → Waiting
- Konfigurierbarer Schwierigkeitsgrad (0.0–1.0)
- Reaktionszeit-Simulation
- "Footsies" bei mittlerer Distanz

## 🚀 Xcode Setup

1. Neues Xcode-Projekt: **Game** → SpriteKit → Swift
2. Main.storyboard: View auf `SKView` setzen, Class auf `GameViewController`
3. Die Swift-Dateien aus diesem Ordner ins Projekt kopieren
4. **Device Orientation**: Nur Landscape Left + Landscape Right
5. Build & Run

## 📋 Nächste Schritte

### Sprint 2: Sprite-Assets
- [ ] Pixel-Art Sprite Sheets erstellen (Aseprite empfohlen)
- [ ] Idle, Walk, Jump, Punch, Kick, Special, Hit, Block, KO Animationen
- [ ] `SKTextureAtlas` für performante Sprite-Animationen nutzen
- [ ] Platzhalter-Rechtecke durch echte Sprites ersetzen

### Sprint 3: Game Flow
- [ ] Title Screen Scene
- [ ] Character Select Scene (wenn >1 Charakter)
- [ ] Victory/Defeat Screen
- [ ] Scene-Transitions mit Überblendungen

### Sprint 4: Audio
- [ ] Hintergrundmusik (Stage Theme)
- [ ] Hit/Block/Special Sound-Effekte
- [ ] Announcer-Stimme ("Round 1!", "Fight!", "K.O.!")
- [ ] `SKAudioNode` oder `AVAudioPlayer` nutzen

### Sprint 5: Polish
- [ ] Parallax-Hintergrund für Stages
- [ ] Partikel-Effekte (Staub, Funken, Energie)
- [ ] Screen Shake bei schweren Treffern
- [ ] Combo-System (Punch → Punch → Kick → Special)
- [ ] Zweiten Charakter mit anderen Moves/Stats

### Sprint 6: Multiplayer (Optional)
- [ ] Lokaler 2-Player über Bluetooth/WiFi
- [ ] `MultipeerConnectivity` Framework

## 🎮 Steuerung

| Control | Aktion |
|---------|--------|
| Joystick Links/Rechts | Bewegen |
| Joystick Oben | Springen |
| P-Button | Punch (schnell, kurze Reichweite) |
| K-Button | Kick (mittel, mittlere Reichweite) |
| SP-Button | Special (stark, lange Reichweite, langsam) |
| B-Button | Block (reduziert Schaden auf 20%) |

## ⚠️ Copyright-Hinweis

Dieses Projekt ist ein eigenständiges Fighting Game. Keine Assets, Namen oder geschützten 
Elemente von Capcom oder Street Fighter werden verwendet. Die Mechaniken sind generisch 
und gehören zum allgemeinen Genre der Fighting Games.
