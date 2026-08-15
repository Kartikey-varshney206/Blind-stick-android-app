# 👁️ Smart Blind Stick - Next-Gen Android Application

![Smart Blind Stick](https://img.shields.io/badge/Status-Active-brightgreen) ![Android](https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white) ![AI](https://img.shields.io/badge/Powered_by-YOLOv8_%7C_Nvidia_AI-blue)

A revolutionary, AI-powered Android application designed to assist visually impaired individuals. This application transforms a standard smartphone into an incredibly advanced, context-aware navigational and environmental analysis tool.

---

## 🌟 Key Features

*   **🎙️ Intelligent Voice Assistant:** Fully voice-controlled interface for hands-free operation.
*   **🧠 Cloud Vision AI (Nvidia/Llama):** Deep environmental analysis, room layout description (3x3 grid localization), and complex scene understanding.
*   **📷 Real-Time Object Tracking (YOLOv8):** Instantaneous, offline object detection running at high framerates using TensorFlow Lite.
*   **🎧 True 3D Spatial Audio:** Acoustic shadowing, distance attenuation, and continuous panning to create a highly accurate auditory map of the environment.
*   **📍 Dynamic Spatial Memory:** The app remembers the exact global coordinates of objects you walk past using the compass, allowing you to ask "Where is my cup?" even if it's behind you.
*   **🔍 Micro-Navigation (Find Mode):** Ask the app to "Find a door" or "Find a seat", and it will guide you using haptic feedback and spatial audio.
*   **🚨 Fall Detection & Telegram SOS:** Automatically detects free-falls followed by impacts. Triggers an instant SOS message to a predefined Telegram chat.
*   **🔦 Auto-Flashlight:** Intelligently turns on in dark rooms and turns off in bright environments using camera luminance data and hysteresis.
*   **📖 OCR (Optical Character Recognition):** Reads books, signs, and screens out loud.

---

## 🏗️ System Architecture & Flowcharts

The application relies on a dual-tier AI processing system: a **Local Edge AI** (YOLOv8) for zero-latency physical feedback, and a **Cloud LLM AI** (Nvidia Vision) for semantic reasoning.

### 1. High-Level Processing Flow

```mermaid
graph TD
    A[Camera Feed] --> B(VisionProcessor)
    B --> C{Local YOLOv8 Model}
    C -->|High Framerate| D[Spatial Audio Engine]
    C -->|Coordinates| E[Micro-Navigation & Haptics]
    C -->|Object Logs| F[(Spatial Memory Database)]
    
    A -->|On Voice Command| G{Cloud Vision API - Nvidia}
    G -->|Detailed Scene Analysis| H[Text-To-Speech Engine]
    
    I[Sensors - Gyro/Accel/Compass] --> J[Fall Detection]
    I --> F
```

### 2. True 3D Spatial Audio Workflow

The spatial audio engine maps visual objects to a 3D acoustic space.

```mermaid
graph LR
    A[YOLOv8 Detection] --> B(Extract Coordinates)
    B -->|X-Axis| C(Azimuth Panning)
    B -->|Bounding Box Area| D(Depth Attenuation / Volume)
    B -->|Y-Axis| E(Acoustic Shadowing / Pitch)
    C --> F((User Earphones))
    D --> F
    E --> F
```

### 3. Dynamic Spatial Memory

How the app remembers objects that are no longer in the camera frame.

```mermaid
sequenceDiagram
    participant Camera
    participant YOLOv8
    participant Compass
    participant SQLite DB
    participant User
    
    Camera->>YOLOv8: See 'Cup'
    Compass->>SQLite DB: Current Heading (e.g. 90° East)
    YOLOv8->>SQLite DB: Log 'Cup' at 90°
    Note over Camera,User: User turns around 180°
    User->>Camera: "Where is my cup?"
    Camera->>SQLite DB: Query 'Cup'
    SQLite DB-->>Camera: Found at 90°
    Compass-->>Camera: Current Heading is 270° (West)
    Camera->>User: "The cup is behind you."
```

### 4. Fall Detection & SOS

```mermaid
graph TD
    A[Accelerometer Data] --> B{Acceleration < 3.0 m/s²?}
    B -- Yes --> C[Free Fall Detected!]
    C --> D{Impact > 20.0 m/s² within 2s?}
    D -- Yes --> E[Trigger Emergency Protocol]
    E --> F[Speak: 'Fall Detected']
    E --> G[Send Telegram JSON Payload]
    G --> H((Emergency Contact Telegram))
```

---

## 🛠️ Tech Stack
*   **Language:** Kotlin
*   **UI Framework:** Jetpack Compose
*   **Machine Learning:** TensorFlow Lite (YOLOv8), Google ML Kit (OCR/Face Detection)
*   **Cloud AI:** Nvidia / Meta LLaMA Vision APIs
*   **Database:** Room (SQLite)
*   **Hardware Sensors:** CameraX, Accelerometer, Magnetometer (Compass)
*   **Networking:** OkHttp, Coroutines

## 🚀 Setup & Installation
1. Clone this repository.
2. Open the project in **Android Studio**.
3. Let Gradle sync and download dependencies.
4. Replace `<YOUR_API_KEY>` in `NvidiaApiClient.kt` (if applicable).
5. Build and Run on a physical Android device (Sensors and Camera are required).

## 📝 Voice Commands
- *"Describe what you see"* - Triggers Cloud AI for a full room layout.
- *"Find a [object]"* - Triggers Micro-navigation tracking.
- *"Where is my [object]"* - Checks local spatial memory database.
- *"Read"* - Reads text aloud.
- *"Turn off flashlight"* / *"Automatic flashlight"* - Controls the auto-light system.
- *"Switch to spatial"* - Enables 3D audio feedback.

---
*Developed for the betterment of accessibility technology.*
