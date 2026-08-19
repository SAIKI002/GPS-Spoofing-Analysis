# GPS Spoofing Detection — Technical Documentation

## Scope

This document records the investigation into GPS spoofing detection using Cube Orange+, Here4, ArduPilot, Mission Planner, GPS-SDR-SIM, and HackRF.

## Main Investigation

The spoofing experiment successfully changed the GPS position reported by the system. Satellite count and HDOP also changed.

The key debugging question was why the spoofing status itself was not appearing in Mission Planner.

The investigation traced the path from the u-blox receiver through the Here4 firmware and DroneCAN to the Cube Orange+.

## Documented Finding

The u-blox receiver generated spoofing state information, but that state was not initially included in the DroneCAN message transmitted by the Here4 module.

This resulted in the spoofing state being unavailable to the Cube Orange+ / Mission Planner path.

## Firmware Files

- `20003.Status.uavcan`
- `Tools/AP_Periph/gps.cpp`
- `AP_GPS_DroneCAN.cpp`
- `AP_GPS_UBLOX.cpp`

## Spoofing Levels

- Level 0: No Fix
- Level 1: No Spoofing
- Level 2: Suspicious
- Level 3: Spoofing Detected

## Verification

Level 0 and Level 1 were verified.

Level 2 and Level 3 remained pending and required conflicting GPS-signal conditions for further testing.
