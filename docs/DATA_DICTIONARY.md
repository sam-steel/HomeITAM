# HomeITAM Data Dictionary

HomeITAM uses a local SQLite database (\`homeitam.db\`) to store all infrastructure data. This ensures your smart home topology never leaves your local network.

## Table: \`assets\`

The \`assets\` table is the core ledger linking digital entities to physical reality.

| Column | Type | Description |
| :--- | :--- | :--- |
| \`id\` | TEXT (PK) | Unique identifier for the asset (e.g., A001). |
| \`name\` | TEXT | Human-readable name (e.g., "Main Router (UDM Pro)"). |
| \`type\` | TEXT | Category (Network, Server, Relay, Sensor, Hub, Infrastructure). |
| \`location\` | TEXT | Physical location in the property (e.g., "Basement Rack"). |
| \`junctionBox\` | TEXT | Specific junction box or enclosure (e.g., "JB-K1 (Behind Switch)"). |
| \`ipAddress\` | TEXT | Static IP allocation (e.g., "192.168.1.10"). |
| \`macAddress\` | TEXT | Hardware MAC address. |
| \`vlan\` | INTEGER | VLAN tag for network isolation (e.g., 10 for Servers, 20 for IoT). |
| \`installDate\` | TEXT | ISO date of installation. |
| \`warrantyExpiry\` | TEXT | ISO date of warranty expiration. |
| \`batteryLevel\` | INTEGER | Current battery percentage (0-100). |
| \`batteryReplaced\` | TEXT | ISO date of last battery replacement. |
| \`status\` | TEXT | Operational status (Online, Offline, Warning). |
| \`dependencies\` | TEXT (JSON) | Array of asset IDs this device depends on (e.g., \`["A001"]\`). |
| \`notes\` | TEXT | Additional context (e.g., "Run goes through central HVAC chase"). |
| \`drywallPhoto\` | TEXT | URL/Path to pre-drywall framing photo. |
| \`manualUrl\` | TEXT | URL/Path to PDF hardware manual. |
| \`receiptUrl\` | TEXT | URL/Path to purchase receipt. |
| \`dockerConfig\` | TEXT | \`docker-compose.yml\` snippet for rebuilding the host server. |
| \`switchPort\` | TEXT | Physical switch port connection (e.g., "Port 4"). |

## Table: \`integrations\`

The \`integrations\` table stores connections to external systems like Home Assistant or Unifi.

| Column | Type | Description |
| :--- | :--- | :--- |
| \`id\` | TEXT (PK) | Unique identifier for the integration (e.g., I001). |
| \`name\` | TEXT | Name of the integration (e.g., "Home Assistant"). |
| \`url\` | TEXT | Base URL of the integration (e.g., "http://homeassistant.local:8123"). |
| \`encryptedToken\` | TEXT | **Encrypted** API token or credentials. |

## Security Architecture

### AES-256-GCM Encryption at Rest

Sensitive data, such as Long-Lived Access Tokens for Home Assistant, are **never** stored in plain text.

When an integration is saved, the backend uses the \`ENCRYPTION_KEY\` environment variable to encrypt the token using AES-256-GCM before writing it to the SQLite database.

The format stored in the \`encryptedToken\` column is:
\`[Initialization Vector (Hex)]:[Authentication Tag (Hex)]:[Encrypted Payload (Hex)]\`

Even if the host machine is compromised and the \`homeitam.db\` file is stolen, the tokens remain securely encrypted.
