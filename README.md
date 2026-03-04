# HomeITAM

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-1.0.0-green.svg)

**Enterprise IT Asset Management (ITAM) for your Smart Home.**

HomeITAM is a self-hosted platform designed to solve the physical reality of managing a complex smart home. While dashboards like Home Assistant show you the *digital* state of your home, HomeITAM tracks the *physical* state: where devices are installed, how they are wired, when their batteries die, and what happens when the primary host fails.

Most importantly, the data is all stored locally and there are no ongoing subscription costs.

## Features

- 📍 **The "Behind the Drywall" Problem:** Track exactly which junction box a relay is installed in, and upload pre-drywall framing photos so you never lose a wire again.
- 💀 **The "Dead Host" Problem:** Maintain a disaster recovery manual. If your primary server dies, HomeITAM stores the switch ports, VLAN tags, and Docker Compose snippets needed to rebuild from scratch.
- 🔋 **Lifecycle Management:** Track battery levels, replacement dates, and warranty expirations across all your hardware.
- 📄 **Handover Protocol:** Generate a beautiful PDF export of your entire smart home infrastructure to hand over to a new buyer when you sell your house.
- 🔒 **Secure by Design:** Built with AES-256-GCM encryption for sensitive data, JWT authentication, and a heavily obfuscated backend.

## Licensing Model (Freemium)

HomeITAM operates on a freemium model:
- **Free Tier:** Manage up to 10 physical devices for free forever. Perfect for small setups or testing.
- **Pro Tier ($15 One-Time):** Unlock unlimited devices. No subscriptions, no recurring fees.

*License keys are managed securely via Lemon Squeezy.*

## Installation

HomeITAM is designed to be run as a Docker container.

### Option 1: Home Assistant Add-on (Recommended)
Add our public repository URL to your Home Assistant Add-on store:
`https://github.com/yourusername/homeitam-addon`

### Option 2: Docker Compose (Standalone)
Create a `docker-compose.yml` file:

```yaml
version: '3.8'
services:
  homeitam:
    image: ghcr.io/yourusername/homeitam-core:latest
    container_name: homeitam
    ports:
      - "3000:3000"
    volumes:
      - ./data:/app/data
    environment:
      - ADMIN_PASSWORD=your_secure_password
      - JWT_SECRET=your_random_jwt_secret
      - ENCRYPTION_KEY=your_32_character_encryption_key
    restart: unless-stopped
```

Run the container:
```bash
docker-compose up -d
```

## Documentation

For detailed guides, please refer to the `docs/` folder:
- [Installation Guide](docs/INSTALLATION.md)
- [User Guide](docs/USER_GUIDE.md)
- [Data Dictionary & Security](docs/DATA_DICTIONARY.md)

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License

[MIT](https://choosealicense.com/licenses/mit/)

