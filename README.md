# Multi-Sensor Explorer Android App 📱✨

An interactive Android application built with **Kotlin** and **Jetpack Compose** that explores and utilizes multiple hardware sensors across different categories, featuring real-time UI effects and strict lifecycle management.

---

## 🚀 Key Features & Sensor Categories

This application meets and exceeds all requirements by utilizing **3 sensors from 3 distinct sensor categories**:

| Category | Sensor Name | Sensor Type Constant | Direct UI Effect |
| :--- | :--- | :--- | :--- |
| **1. Motion** | Accelerometer | `Sensor.TYPE_ACCELEROMETER` | Controls the real-time physics movement and rolling of a glowing orb inside a bounded arena based on device tilt. |
| **2. Environment** | Ambient Light Sensor | `Sensor.TYPE_LIGHT` | Dynamically adapts the entire app theme, card colors, and background gradient between **Night Mode** (< 15 lux) and **Day Mode** (>= 15 lux), displaying a live lux meter. |
| **3. Position** | Proximity Sensor | `Sensor.TYPE_PROXIMITY` | Detects objects near the screen (e.g., hand covering top of phone), activating an animated **Radar Shield / Warning Overlay** and live status badge. |

---

## 🔄 Sensor Lifecycle Management

To ensure optimal battery life and prevent background resource leaks, sensor listeners are strictly bound to the Android Activity lifecycle using Jetpack Compose `LocalLifecycleOwner` and `DisposableEffect`:

- **`ON_RESUME`**: Registers sensor listeners (`sensorManager.registerListener(...)`) for Accelerometer, Light, and Proximity sensors.
- **`ON_PAUSE`**: Unregisters all listeners (`sensorManager.unregisterListener(...)`) when the app is backgrounded or paused.

---

## 🛠️ Tech Stack
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose & Material 3
- **Android APIs**: `SensorManager`, `SensorEventListener`, `LifecycleEventObserver`

---

## 📱 How to Run & Test

### 1. On a Physical Android Device
1. Install and open the app.
2. **Motion**: Tilt your phone in any direction to roll the glowing ball.
3. **Environment**: Move your phone under a desk (low light) or near a bright light source (high light) to watch the app theme switch between Dark/Night and Light modes automatically.
4. **Position**: Place your hand near the top earpiece (proximity sensor) to trigger the red Shield Active warning overlay.

### 2. On Android Studio Emulator
1. Open the **Extended Controls** panel (`...` button on the emulator toolbar).
2. Go to **Virtual Sensors**:
   - **Accelerometer**: Adjust Roll and Pitch sliders to tilt the ball.
   - **Light**: Adjust lux slider to trigger theme changes.
   - **Proximity**: Change the distance slider to test NEAR/FAR shield states.
