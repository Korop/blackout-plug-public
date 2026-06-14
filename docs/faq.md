# FAQ

## Is BlackoutPlug hosted locally at home?

No. The Shelly Plug is installed at the monitored location, but BlackoutPlug itself is hosted on a VPS.

The VPS runs the broker, backend service, database, and Telegram bot.

## Does it require Shelly Cloud?

No. The core monitoring path is Shelly MQTT to the VPS broker, not Shelly Cloud.

## Can BlackoutPlug remotely control or manage the plug?

Not in the current public release.

Today, BlackoutPlug focuses on monitoring, outage history, and notifications. Remote plug/device management is a possible future feature for a next release.

## What device is the public setup focused on?

Shelly Plug / Shelly Plug S Gen3 class devices.

Other MQTT-capable devices may be possible, but the public overview uses Shelly resources and screenshots.

## Why Telegram?

Telegram is easy for quick notifications, shared site subscriptions, and mobile-first setup flows. It avoids requiring a custom app before the product value is proven.

Public links:

- Bot: https://t.me/blackout_plug_bot
- Telegram app deep link: `tg://resolve?domain=blackout_plug_bot`
- Official channel: https://t.me/BlackoutPlug

## Why use a VPS?

The VPS keeps the monitoring backend reachable even when the monitored site loses power or the local network disappears.

## Can several people subscribe to one site?

Yes. One person can create a site and share access with family, neighbors, or staff.

BlackoutPlug can also use QR invite cards, Telegram links, and fallback join codes so a place can be shared in person without requiring everyone to know each other already.

## Can one user monitor several sites?

Yes. The product model supports multiple sites per user.

## Can a site have multiple devices?

The product model supports multiple device sources for a site. This can improve confidence and diagnostics.

## Is this a professional utility-grade outage system?

No. It is a practical best-effort monitoring tool using a Shelly device and Internet connectivity.

## How can I request a feature for the next release?

Open a GitHub Issue in this repository and describe the feature you want to see. If you can, include your use case as well.

## Why is the public repository not the full source?

Because this repo is meant to explain the product and engineering approach, not publish private APIs, deployment internals, secrets, or a clone-ready business blueprint.
