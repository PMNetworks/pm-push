# Änderungen

Versionen nach dem Schema JJJJ.MM.N, Releases als Tag `vJJJJ.MM.N`.

## 2026.11.2 – 2026-11-14

CallKit nur noch für echte Anrufe (Haustür). Alarm, Rauch, Gas und Wasser kommen als Mitteilung.

- `interruption-level: critical` geht als kritische Mitteilung an Apple, mit kritischem Ton
  (`sound: {"critical": 1, "name": "default", "volume": 1.0}`; Name und Lautstärke aus `push.sound` werden übernommen).
  Es folgt kein Anruf „Alarmanlage“ mehr.
- Ohne Berechtigung von Apple für kritische Mitteilungen stellt iOS sie als gewöhnliche Mitteilung zu; PM HomeControl
  macht sie dann zeitkritisch, damit sie den Fokus durchbricht.
- Option „Kritische Mitteilungen zusätzlich als Anruf“ entfällt. Ein gespeicherter Wert früherer Versionen wird beim
  Start still entfernt.
- `pm_push.anruf` ist für die Haustür. Die Anlässe `alarm` und `gefahr` werden weiter angenommen, damit bestehende
  Automationen nicht scheitern, senden aber eine kritische Mitteilung statt eines Anrufs (mit Hinweis im Protokoll).

## 2026.11.1 – 2026-11-13

Erste Version von PM Push (hervorgegangen aus PM Mobil).

- Einrichtung ohne Eingaben: Push läuft über den Dienst PM Push von PM Networks. Kein Konto bei Apple, kein eigener
  Schlüssel; die App weist sich per DeviceCheck aus und bekommt je Token eine Kennung.
- Mitteilungen: `notify.pm_push` und `notify.pm_push_<gerät>` mit den Feldern der Companion-App.
- Anrufe per VoIP: `pm_push.anruf` (Haustür nur an Personen unterwegs), `pm_push.anruf_beenden`.
- Live Activities der Automationen: `pm_push.live_activity` und `pm_push.live_activity_beenden` mit den Feldern von
  `script.live_activity`; die geöffnete App zeigt sie direkt, per Push auch bei geschlossener App.
- Optionen: Zonen, die als zu Hause gelten; kritische Mitteilungen als Anruf. Felder für Schlüssel gibt es nicht, wie bei
  der Companion-App; zugestellt wird immer über das Relay.
- Eigenes Symbol und Logo in Home Assistant, Installation und Updates über HACS aus `PMNetworks/pm-push`.
