# Firmware Analysis

This section documents the firmware-level analysis carried out to understand how
GPS spoofing and jamming status is generated, propagated, and exposed through
the ArduPilot GPS and DroneCAN software stack.

## Analysis Scope

The investigation focused on tracing the spoofing-status data flow from the
GPS/DroneCAN peripheral to the flight controller and finally to the ground
station interface.

The main areas investigated were:

- GNSS spoofing and jamming status generation
- DroneCAN GNSS status transmission
- DroneCAN GPS status reception in ArduPilot
- Integration of spoofing information with the GPS subsystem
- Propagation of spoofing status to Mission Planner
- Differences between the u-blox and DroneCAN GPS processing paths

## Firmware Data Flow

```text
GNSS / GPS Peripheral
        │
        │ GNSS Status
        ▼
Tools/AP_Periph/gps.cpp
        │
        │ DroneCAN message
        ▼
ardupilot_gnss_Status
        │
        ▼
AP_GPS_DroneCAN.cpp
        │
        │ Spoofing / Jamming State
        ▼
AP_GPS / EKF GPS Data Path
        │
        ▼
MAVLink / GCS Telemetry
        │
        ▼
Mission Planner
