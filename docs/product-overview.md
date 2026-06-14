# Product Overview

BlackoutPlug is a **VPS-hosted power outage monitoring system** that uses a Shelly Plug as a power-status signal source and Telegram as the main user interface.

The product idea is deliberately small:

```text
monitor a place -> detect power OFF/ON -> notify people who care
```

Just the outage signal, history, and notifications.

## Product promise

BlackoutPlug helps a person or small group answer one question quickly:

> Does this place currently have electricity?

The place can be a home, parents’ apartment, café, office, shop, workshop, or a shared location monitored for neighbors.

## Hosting model

BlackoutPlug is **not hosted locally inside the monitored home network**.

The monitored place contains:

- a Shelly Plug;
- a Wi-Fi router;
- normal Internet access when power is available.

The BlackoutPlug system runs on a VPS:

- Mosquitto MQTT broker;
- `blackout-service` backend;
- PostgreSQL database;
- `blackout-bot` Telegram bot.

This matters because the owner does not need to be inside the same local network to receive notifications or check status.

## Cloud clarification

BlackoutPlug does use a VPS, so it is not a fully local-only system.

The actual claim is narrower and more useful:

> BlackoutPlug does not require Shelly Cloud as the core monitoring path.

The Shelly device publishes MQTT status to your configured broker. BlackoutPlug receives that signal on the VPS and uses Telegram for user communication.

## Key user roles

| Role | Meaning |
|---|---|
| Owner | Creates a site and configures device monitoring. |
| Admin | Helps manage a site and its devices. |
| Subscriber | Receives notifications and can check status/history. |

## Core concepts

| Concept | Meaning |
|---|---|
| Site | A monitored location, such as “Home”, “Café”, or “Parents”. |
| Device source | A Shelly Plug attached to a site. |
| Event | A detected power state change. |
| History | Stored outage/restore timeline for later checks. |
| Share code | A private way to let other users subscribe. |
| QR invite card | A scannable site invite with QR, Telegram link, app link, and fallback code. |

## Main benefits

### 1. Simple outage awareness

Users get a Telegram notification when power is lost and when power is restored.

### 2. Shared monitoring

One device can serve multiple subscribers. This is useful for families, neighbors, and staff. QR invite cards make this practical in places where people do not already know one another.

### 3. Privacy-first onboarding

Sites are private by default. A site can use a simple label instead of a real public address.

### 4. Practical engineering model

A single Shelly Plug and VPS can create a useful monitoring loop without building a giant IoT platform.

## Current release focus

- reliable power-status monitoring;
- outage history;
- Telegram notifications and site sharing;
- QR-based invite sharing for neighborhood and small-business onboarding;
- Shelly-based setup flow.

## Planned future direction

Remote plug/device management is **not available in the current release**. It can be introduced as a future feature after the monitoring workflow is polished.
