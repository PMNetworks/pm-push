# Änderungen

Versionen nach dem Schema JJJJ.MM.N, Releases als Tag `vJJJJ.MM.N`.

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
