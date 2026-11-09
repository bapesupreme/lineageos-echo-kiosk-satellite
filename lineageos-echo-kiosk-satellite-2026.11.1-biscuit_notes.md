# LineageOS for the Echo Dot (2nd Gen), Kiosk Satellite Edition 2026.11.1

This release makes `biscuit_service bt on` turn Bluetooth on without pairing mode, so it can turn Bluetooth back on for Kiosk Satellite's Bluetooth proxy.

## Changes

`biscuit_service bt on` turns Bluetooth on without pairing mode. It was another name for `bt pair`, which also set the Dot up to take audio from phones and made it discoverable for five minutes. It now turns Bluetooth back on with the Dot set up as it was, such as for Kiosk Satellite's Bluetooth proxy for Home Assistant. The Echo Dot guide now shows how to turn Bluetooth off and back on.

## Updating

Install it from the Dot's **Firmware** entity in Home Assistant or from Kiosk Satellite's remote admin. BiscuitService installs it into both slots and restarts the Dot twice. Kiosk Satellite and its settings stay. Keep the Dot on its own power adapter, not a USB hub, or TWRP may not start. If your Dot cannot get online yet, install this release by hand from TWRP with the steps in the Echo Dot guide, leaving out `twrp wipe data`.

## Requirements

The Dot needs amonet v2.0.0 or v2.0.1 with TWRP 3.7.0_9-0. See [Unlocking](#).

Kiosk Satellite needs to be 2026.11.1 or newer. Its echo canceller is built for the raw microphone the image gives it since 2026.10.18, so update Kiosk Satellite on the Dot too.

## Download

`lineageos-echo-kiosk-satellite-2026.11.1-biscuit.zip`, build `0d9ba6a402`

**SHA-256:** `2115175683c36d170135741c2f3e2c05928b1e69b9c392543082176423c00773`

`lineageos-echo-kiosk-satellite-2026.11.1-biscuit.zip.sig` is the release signature. BiscuitService checks it before it installs an update. Echo Dot releases are tagged `biscuit-`. BiscuitService only installs those.
