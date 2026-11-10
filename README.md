# Drone Training Simulator

**by AeroMaverick Technologies**

Offline PC simulator for multirotor pilot training. Each drone flies with its own ArduPilot parameter file, either on the built-in ArduPilot-compatible flight controller or on the real ArduPilot firmware (SITL).

![FPV view with ArduPilot-style OSD](screenshots/fpv-gates.png)

## Download

**[Download for Windows (64-bit)](https://github.com/UnknownEng/drone-training-simulator/releases/latest)**: open the latest release and download the `.zip` under **Assets**. No installation, works fully offline.

1. Download the zip and extract it (right-click → **Extract All**).
2. Open the extracted folder and run **DroneTrainingSimulator.exe**.
3. If Windows shows "Windows protected your PC", click **More info → Run anyway**. The app is not code-signed yet.

**Requirements:** Windows 10 or 11 (64-bit), a graphics card with DirectX 11 / WebGL 2, about 300 MB of disk space. A gamepad or an RC transmitter in USB joystick mode is optional; the keyboard works too.

The demo video is attached to the [latest release](https://github.com/UnknownEng/drone-training-simulator/releases/latest).

## Features

- **Flight physics:** 6-DOF model with motor spin-up lag, thrust curves, battery voltage sag, ground effect, vortex-ring state, rotor drag, and wind with gusts and turbulence. Landing-gear contact and collisions with trees, buildings and wires.
- **ArduPilot flight controller:** a built-in ArduCopter-compatible controller that reads real `.param` files: rate/angle PIDs with input shaping, altitude and position control, flight modes (STABILIZE, ALT_HOLD, LOITER, POSHOLD, RTL, LAND, GUIDED and more) and failsafes.
- **Real ArduPilot firmware:** connect ArduCopter SITL as the flight controller (lock-step at 1,200 Hz, MAVLink ground-station link).
- **Your own drones:** load a drone's `.param` file and edit its physical model (mass, motors and propellers, battery, drag, camera).
- **Training:** 12 missions from first hover to advanced drills (gate course, wind and gusts, GPS failure, low battery, motor failure), with scoring, debriefs and training records.
- **Views:** chase camera, FPV with an ArduPilot-style OSD and analog video effects, line of sight from the pilot box, and a ground-station panel.
- **Live tuning:** change PID gains in flight and see the effect in the tuning graph and the step-response test.

## Controls

| Key | Action |
|---|---|
| W / S | throttle up / down (Space = 50 %) |
| Arrow keys | pitch and roll |
| A / D | yaw |
| Enter | arm / disarm |
| 1–6 | flight-mode switch |
| H | return to launch |
| C | camera: chase / FPV / line of sight |
| Tab | ground-station panel |
| G | tuning graph |
| F1 | all controls |
| Esc | pause / menu |

Gamepads and RC transmitters work as on the real aircraft; calibrate them under **Controller setup**.

## Screenshots

| | |
|---|---|
| ![Main menu](screenshots/main-menu.png) | ![Chase view and ground-station panel](screenshots/chase-gcs.png) |
| ![Real ArduPilot SITL as the flight controller](screenshots/sitl.png) | ![Tuning graph and step test](screenshots/tuning.png) |
| ![ArduPilot parameters](screenshots/parameters.png) | ![Line-of-sight view](screenshots/line-of-sight.png) |

## Using the real ArduPilot firmware (optional)

Run ArduCopter SITL (on Linux or in WSL) with its JSON physics model pointed at this PC, for example:

```
arducopter -w --model JSON:<this PC's IP> --defaults Tools/autotest/default_params/copter.parm,<your_drone>.param
```

Then in the app choose **Flight controller → Use ArduPilot SITL** and start a flight. Wait for "EKF3 IMU0 is using GPS" in the ground-station messages before flying.

---

© 2026 AeroMaverick Technologies. All rights reserved. The source code is not public.
