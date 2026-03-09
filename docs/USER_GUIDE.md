# HomeITAM User Guide

HomeITAM is a centralized ledger for managing the physical and network infrastructure of a smart home. It complements Home Assistant by documenting the "Behind the Drywall" and "Dead Host" problems that operational dashboards ignore.

## Core Features

### 1. The Infrastructure Asset Register

The **Asset Register** is a relational database linking digital Home Assistant entities to physical reality.

- **Physical Mapping**: Track the exact location of smart relays or Cat6 runs before the drywall goes up. If a switch fails in three years, you know exactly which junction box to open.
- **Network & Stack Topology**: A centralized ledger for static IP allocations, MAC addresses, VLAN tagging (separating IoT hardware from the main network), and Docker container port mappings on the host server (like an N100 mini-PC).
- **Dependency Mapping**: Visually map what breaks if a specific component goes down (e.g., if the main PoE switch dies, the APs and the cameras go down with it).

### 2. The "Behind the Drywall" Problem

Home Assistant knows a smart relay exists, but it doesn't know where it is.

For a new build, HomeITAM allows you to upload photos of open framing, link them to a specific room's floor plan, and map exactly where the neutral wires, relays, and Cat6 drops are located before the plaster goes up. If a physical switch fails five years later, you aren't guessing which junction box to open.

**How to use:**
1. Navigate to the **Asset Register**.
2. Click on an asset (e.g., "Kitchen Lights Relay" or "Cat6 Drop").
3. A slide-out panel will appear.
4. Upload and view pre-drywall framing photos in the **Physical Location** section.

### 3. The "Dead Host" Problem

If the mini PC running the smart home dies, the Home Assistant dashboard dies with it.

HomeITAM acts as the off-grid disaster recovery manual. It holds the documentation for the Docker stack, the static IP allocations, and the VLAN topology, so you know exactly how to rebuild the environment from scratch on a new piece of hardware.

**How to use:**
1. Navigate to the **Disaster Recovery** page via the sidebar.
2. View the core infrastructure status and automated backup health.
3. Access the **Host Configuration (Docker Stack)** snippet needed to rebuild the Home Assistant server.
4. Review the **VLAN & Subnet Topology** table.

### 4. Non-Digital Asset Storage

HomeITAM allows you to attach, view, and manage non-digital assets directly linked to the physical device.

**How to use:**
1. Navigate to the **Asset Register**.
2. Click on an asset.
3. In the slide-out panel, access the **Documentation** section.
4. Upload and view PDF hardware manuals and photographs of purchase receipts.

### 5. Lifecycle & Maintenance Management

Smart homes require physical maintenance. HomeITAM tracks the lifecycle of your hardware.

- **Battery Tracking**: A unified view of every battery-powered sensor (Zigbee/Z-Wave), predicting when they will die based on historical drain rates, rather than just showing a current percentage.
- **Warranty & Lifespan**: Tracking purchase dates and warranty expirations for expensive hardware (like a $400 Unifi router or a NAS drive).

**How to use:**
1. Navigate to the **Maintenance** page via the sidebar.
2. View devices requiring battery replacements and upcoming warranty expirations.

### 6. The Property Handover Protocol

When selling a house with a complex smart home setup, the buyer needs to know how to operate it.

HomeITAM generates a "Handover Pack"—a clean, user-friendly PDF export that strips out the complex networking details and provides the new owner with exactly what they need: where the main hub is, how to reset the Wi-Fi, and a list of all the smart switches in the walls.

**How to use:**
1. Navigate to the **Handover** page via the sidebar.
2. Click **Generate PDF Manual**.
3. Download the generated PDF, which includes the asset register and basic troubleshooting information.
