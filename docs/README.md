# HomeITAM

**Enterprise IT Asset Management (ITAM) for your Smart Home.**

HomeITAM is a self-hosted platform designed to solve the physical reality of managing a complex smart home. While dashboards like Home Assistant show you the *digital* state of your home, HomeITAM tracks the *physical* state: where devices are installed, how they are wired, when their batteries die, and what happens when the primary host fails.

## Features

- **The "Behind the Drywall" Problem:** Track exactly which junction box a relay is installed in, and upload pre-drywall framing photos so you never lose a wire again.
- **The "Dead Host" Problem:** Maintain a disaster recovery manual. If your primary server dies, HomeITAM stores the switch ports, VLAN tags, and Docker Compose snippets needed to rebuild from scratch.
- **Lifecycle Management:** Track battery levels, replacement dates, and warranty expirations across all your hardware.
- **Handover Protocol:** Generate a beautiful PDF export of your entire smart home infrastructure to hand over to a new buyer when you sell your house.
- **Secure by Design:** Built with AES-256-GCM encryption for sensitive data, JWT authentication, and runs locally.

## Licensing Model (Freemium)

HomeITAM operates on a freemium model:
- **Free Tier:** Manage up to 10 physical devices for free forever. Perfect for small setups or testing.
- **Pro Tier ($15 One-Time):** Unlock unlimited devices. No subscriptions, no recurring fees.

*License keys are managed securely via Lemon Squeezy.*

## Installation

1. Ensure you have Docker and Docker Compose installed.
2. Download the `docker-compose.yml` file.
3. Run the following command in the same directory:

> ```bash
> docker-compose up -d
> ```

4. Access the dashboard at `http://localhost:3000`.
5. The default password is `changeme123`. Please change this in the `docker-compose.yml` file!

## Documentation

For detailed guides, please refer to the `docs/` folder:
- [Installation Guide](docs/INSTALLATION.md)
- [User Guide](docs/USER_GUIDE.md)
- [Data Dictionary & Security](docs/DATA_DICTIONARY.md)

## Licensing
HomeITAM is free for up to 10 devices. To unlock unlimited devices, purchase a Pro license at [Lemon Squeezy](https://myhomeitam.lemonsqueezy.com/checkout/buy/eefca3f6-1f8b-4304-bfda-2224ac911ac3).

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
