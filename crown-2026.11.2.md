# LineageOS for the Echo Show 8 (1st Gen), Kiosk Satellite Edition 2026.11.2

This release fixes the Wi-Fi problem 2026.11.1 caused near Hotspot 2.0 networks such as `xfinitywifi` and makes the 2.4 GHz check after a boot more reliable.

## Fixes

- Wi-Fi almost stopped working near a Hotspot 2.0 network ([#38](https://github.com/jxlarrea/lineageos-echo-kiosk-satellite/issues/38)). After a scan, Android asked every nearby Hotspot 2.0 network for details, such as `xfinitywifi`, even with no Passpoint profile saved. That query takes the Wi-Fi radio off its channel and the Show's Wi-Fi driver then lost most traffic until Wi-Fi reconnected. The scan after a boot added in 2026.11.1 made this happen on Shows connected at 2.4 GHz. Android now sends the query only when a Passpoint profile is saved. If you locked your network to one access point to work around this, you can forget it and join it again without `-b`.
- The 2.4 GHz check after a boot could miss the 5 GHz radio ([#35](https://github.com/jxlarrea/lineageos-echo-kiosk-satellite/issues/35)). A scan while connected can take more than 8 seconds, which was as long as EchoService waited for it. EchoService then lost the results of that scan and could leave the Show on 2.4 GHz. It now waits up to 15 seconds for each scan.

## Updating

Install it from the Show's **Firmware** entity in Home Assistant or from Kiosk Satellite's remote admin. EchoService downloads it, checks it and restarts the Show into TWRP, which installs it and starts Android again. Kiosk Satellite and its settings stay. If your Show cannot get online yet, install this release by hand from TWRP with the steps in the [Echo Show 8 guide](https://github.com/jxlarrea/lineageos-echo-kiosk-satellite/blob/main/docs/echo-show-8.md#installing), leaving out `twrp wipe data`.

## Requirements

The Show needs amonet 2 with TWRP 3.7.0_9-0. See [Unlocking](https://github.com/jxlarrea/lineageos-echo-kiosk-satellite/blob/main/docs/unlocking.md#echo-show-8-1st-gen). If the Show is on amonet 1, see [Updating from amonet 1](https://github.com/jxlarrea/lineageos-echo-kiosk-satellite/blob/main/docs/unlocking.md#updating-from-amonet-1-1).

Kiosk Satellite needs to be 2026.11.1 or newer. Its echo canceller is built for the raw microphone the image gives it since 2026.10.6, so update Kiosk Satellite on the Show too.

## Download

`lineageos-echo-kiosk-satellite-2026.11.2-crown.zip`, build `64a8c752a6`

**SHA-256:** `0458cd6faf654d3111de6ee68ece8ff046eb65f4ef028a33fa904e2b0509f6c5`

`lineageos-echo-kiosk-satellite-2026.11.2-crown.zip.sig` is the release signature. EchoService checks it before it installs an update. Echo Show 8 releases are tagged `crown-`. EchoService only installs those.
