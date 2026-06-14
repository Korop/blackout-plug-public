# Security and Privacy

BlackoutPlug is designed around a simple rule:

> A device should report status safely in the current release.

## Hosting boundary

BlackoutPlug is **hosted on a VPS**, while the Shelly Plug stays inside the monitored location.

This means the public Internet-facing pieces must be treated carefully:

- MQTT broker access must require authentication.
- TLS should be used for public MQTT listeners.
- Device credentials should be unique per device.
- Runtime secrets belong in private deployment configuration, not in the public repository.

## Vendor cloud boundary

BlackoutPlug does not rely on Shelly Cloud as the core monitoring path.

The intended path is:

```text
Shelly MQTT -> VPS Mosquitto -> blackout-service -> Telegram
```

Shelly Cloud may exist in the Shelly app ecosystem, but BlackoutPlug’s product model is based on MQTT status ingestion to the VPS.

## Device permissions

Recommended device posture:

- publish-only access for device status topics;
- no subscribe permissions for device clients unless explicitly needed;
- no command/RPC/control topic access in the current release;
- separate credentials per physical device;
- easy credential rotation when a device is removed or re-added.

## Future feature note

Remote plug/device management is **not available in the current release**. If it is added in a future release, it should be introduced with stricter permission boundaries and an explicit security review.

## Site privacy

Sites should be private by default.

Privacy-friendly behavior:

- private site labels can be anonymous;
- share codes are preferred for joining;
- public discovery should be optional;
- public docs should never include real addresses, raw credentials, or sensitive IDs.

## What to redact from public material

Before publishing screenshots or docs, remove:

- broker domains if you do not want them public;
- usernames and passwords;
- client IDs if they are tied to a real device;
- device IDs;
- Wi-Fi SSIDs;
- Telegram bot tokens;
