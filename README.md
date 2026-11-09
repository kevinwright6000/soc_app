# SOC Threat Map

Single-file, fully offline cyber attack map for a SOC wall display. Open `index.html` in a browser.

- Animated attack arcs, impact ripples (white breach ring = traffic allowed), origins/targets/type panels, live feed table, priority alerts
- Dot-matrix / vector map toggle, rate slider, pause (Space), fullscreen (F), click an attack type to filter
- **Default data is simulated** (badge in header says so). Edit `CFG.home` in the script to set your protected site.

## Feeding real data
- `index.html?ws=wss://host/path` or `?sse=https://host/stream` — messages are JSON events (or arrays)
- Or from the console / your own script: `SOC.ingest(event)`

```json
{"src":{"lat":55.75,"lon":37.6,"city":"Moscow","cc":"RU","country":"Russia","ip":"198.51.100.7","org":"Example ISP"},
 "dst":{"lat":33.54,"lon":-112.19,"city":"Glendale","cc":"US","country":"United States"},
 "svc":"ssh","port":22,"cat":"brute","sev":"high","blocked":true,"ts":1760000000000}
```
`cat`: brute, exploit, malware, ddos, scan, phish, ransom · `sev`: crit, high, med, low
Geolocate source IPs upstream (e.g. MaxMind) before sending. Firewall/IDS/SIEM feeds need a small adapter to this shape.
