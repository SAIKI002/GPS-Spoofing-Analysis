# Testing and Results

This section documents the practical testing performed on the Cube Orange+
flight controller using ArduPilot, Mission Planner, Here4 GNSS, and the
GPS spoofing test setup.

## Test Objective

The main objective was to verify how the flight controller responds to
spoofed GNSS information and to observe the corresponding GPS and spoofing
status reported through Mission Planner.

## Test Setup

The testing involved:

- Cube Orange+ flight controller
- Here4 GNSS receiver
- ArduPilot firmware
- Mission Planner
- HackRF-based GPS signal simulation
- GPS-SDR-SIM
- SDR++ and related SDR utilities
- DroneCAN communication between the Here4 and Cube Orange+

## Tests Performed

### 1. Normal GPS Operation

The system was first tested under normal GPS conditions to establish the
baseline GPS behavior.

Mission Planner was used to observe:

- GPS position
- Satellite count
- HDOP
- GPS status
- Pre-arm and GPS-related messages

### 2. Spoofed GPS Position

A simulated GPS signal was generated using GPS-SDR-SIM and transmitted
through the SDR setup.

The flight controller accepted the simulated GPS information and the
reported position shifted toward the simulated coordinates.

This confirmed that the spoofed GNSS signal was reaching the GPS data path
and being processed by the flight controller.

### 3. Spoofing Status – Level 0

The first spoofing condition was tested and the corresponding spoofing
status was observed through Mission Planner.

**Result:** Level 0 condition successfully reproduced.

### 4. Spoofing Status – Level 1

The next spoofing condition was tested using the same setup.

**Result:** Level 1 condition successfully reproduced and observed through
the Mission Planner messages/status interface.

### 5. Higher Spoofing Conditions

Higher spoofing conditions require a more complex signal setup.

The planned approach is to use two HackRF devices to generate the required
GNSS signal conditions and investigate the higher spoofing levels.

**Status:** Work in progress.

## Observations

During testing, the following changes were observed when the simulated GPS
signal was introduced:

- GPS coordinates changed toward the simulated location.
- Satellite information changed during the test.
- HDOP values changed.
- Mission Planner displayed the corresponding GPS/spoofing information.
- DroneCAN communication was confirmed as an important part of the GPS
  data path for the Here4 setup.

## Current Status

| Test | Status |
|------|--------|
| Normal GPS operation | Completed |
| Spoofed GPS position | Completed |
| Spoofing Level 0 | Completed |
| Spoofing Level 1 | Completed |
| Higher spoofing levels | In progress |

## Evidence

Screenshots of Mission Planner observations are stored in:

`../screenshots/`

These include GPS position changes, spoofing-level messages,
magnetometer-related messages, and DroneCAN configuration.
