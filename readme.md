# Technischer Plan der Netzwerk-Infrastruktur für yihaaaaa.biz

## Netzwerkaufbau

### 1. Subnetzkonfiguration

| **Abteilung**           | **Subnetzbereich**   | **CIDR** | **Max Hosts** | **Reserve** |
|--------------------------|----------------------|----------|---------------|-------------|
| Geschäft/Finanzen/Recht  | 172.16.0.0 - 172.16.0.31  | /27      | 30            | 5           |
| Marketing/Verkauf        | 172.16.0.32 - 172.16.0.63 | /27      | 30            | 5           |
| Produktion/Vertrieb      | 172.16.0.64 - 172.16.0.127 | /26     | 62            | 10          |
| IT/Operations            | 172.16.0.128 - 172.16.0.159 | /27    | 30            | 5           |
| **Gesamtnetz**           | 172.16.0.0/24       |          |               |             |

### 2. Netzwerkgeräte

#### **Benötigte Geräte**

| **Gerät**                    | **Menge** | **Einsatzort** |
|-------------------------------|-----------|-----------------|
| Ubiquiti EdgeRouter X         | 4         | Je Abteilung    |
| OPNSense Firewall             | 4         | Je Abteilung    |
| Netgear GS108T Network Switch | 4         | Je Abteilung    |
| Netgear AccessPoint           | 6         | WLAN-Bereitstellung |
| Linux Abteilungsserver        | 4         | Je Abteilung    |
| Drucker                       | 4         | Je Abteilung    |
| Core-Firewall                 | 1         | Zentrale        |
| ISP-Router                    | 1         | Zentrale        |

### 3. Geräte-Namenskonvention

- **Router:** `ROUTER-[Abteilung]`
- **Firewall:** `FW-[Abteilung]`
- **Switch:** `SW-[Abteilung]`
- **AccessPoint:** `AP-[Abteilung]-[Nummer]`
- **Server:** `SRV-[Abteilung]`
- **Drucker:** `PRN-[Abteilung]`
- **Mitarbeitergeräte:** `LPT-[Abteilung]-[Nummer]`
- **Mobile Geräte:** `MOB-[Abteilung]-[Nummer]`

### 4. Übersicht der IP-Adressierung

#### Beispiel für Geschäft/Finanzen/Recht (172.16.0.0/27):

| **Gerät**        | **IP-Adresse**      |
|-------------------|---------------------|
| Router           | 172.16.0.1         |
| Firewall         | 172.16.0.2         |
| Switch           | 172.16.0.3         |
| Access Point 1   | 172.16.0.4         |
| Server           | 172.16.0.5         |
| Drucker          | 172.16.0.6         |
| Mitarbeitergeräte| 172.16.0.7-172.16.0.20 |
| Mobile Geräte    | 172.16.0.21-172.16.0.30 |

### 5. Topologie (Diagramm)

Das Netzwerkdiagramm zeigt:

- **Core-Komponenten:**
  - ISP-Router → Core-Firewall → Verteilung auf die Abteilungsrouter

- **Pro Abteilung:**
  - Router → Firewall → Switch → Access Points/Endgeräte
  - Server und Drucker direkt am Switch angeschlossen

### 6. Sicherheit

- **Abteilungs-Firewalls:** Trennung der Subnetze
- **Core-Firewall:** Zentraler Schutz vor externen Bedrohungen
- **WLAN-Segmentierung:** Gäste- und Mitarbeitergeräte getrennt

---

Ein visuelles Diagramm kann auf Basis dieser Spezifikation erstellt werden, um die Netzwerkstruktur grafisch darzustellen.
