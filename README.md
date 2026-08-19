## 👥 Team

| | |
|---|---|
| **Team Name** | Clover Dynamics |
| **Team Member** | Kartikey Varshney, Kamakhya Anupam Sharma|
| **City** | Bengaluru |

---

## 🎯 App

| | |
|---|---|
| **App name** | VSense — An Assistive App for the Visually Impaired |
| **Theme** | Utility app |
| **One-liner** | It's an assistive technology app that helps visually impaired users sense their environment through the camera of their phones |

### What we built
A comprehensive assistive Android application designed to give visually impaired users independence. The app uses offline on-device computer vision (YOLOv8) combined with a custom 3D spatial audio engine to give users a real-time "acoustic map" of their surroundings. It features a Voice Assistant that leverages powerful Cloud Vision AI to describe environments, read text (OCR), and provide micro-navigation (e.g., finding a door). Additionally, the app includes an automatic Fall Detection system that sends a Telegram SOS message with the user's GPS location, a persistent Spatial Memory database, and an offline Facial Recognition engine to identify friends.

### How the AI is used
- **Model:** `meta/llama-3.2-90b-vision-instruct` (via Nvidia NIM API)
- **What the AI does:** Acts as the cognitive brain of the app. It takes an image of the user's surroundings along with a voice prompt (e.g., "Describe what you see" or "Find a door") and provides a detailed 3x3 grid spatial description to the user via Text-To-Speech.
- **AI pattern:** Vision · Chat · Extract

---

## ▶️ How to run it

```bash
# 1. Clone the repository
git clone https://github.com/k-anupam-sharma/TechQuest.git
cd TechQuest

# 2. Open the project in Android Studio
#    (let Gradle finish syncing before you Run)
```

**API Setup**
- The Cloud Vision features require an API key. 
- Open `app/src/main/java/com/example/smartblindstick/NvidiaApiClient.kt`
- Replace the `apiKey` variable with your Nvidia NIM API key.

**Build the APK**
- Android Studio → `Build → Build Bundle(s)/APK(s) → Build APK(s)`
- Output: `app/build/outputs/apk/debug/app-debug.apk`

---

## 📱 Demo

- **APK:** Navigate to the `app/build/outputs/apk/debug/app-debug.apk` path after building to install the app on your device.
- **Screen recording:** *(Add your video link here)*
- **Screenshots:** *(Add your screenshots here)*

---

## 🧰 Tech stack
- Android (Kotlin) · Android Studio
- Nvidia NIM API (Meta LLaMA Vision)
- TensorFlow Lite (YOLOv8 Object Detection, MobileFaceNet)
- Google ML Kit (Face Detection & Text Recognition OCR)
- Android CameraX & SensorManager
- Room Database (SQLite)
- OkHttp (Networking & Telegram API)

---

## ✅ Submission checklist
- [x] This README is filled in (team, theme, how to run)
- [x] The API key is **NOT** in the repo (see `.gitignore` below)
- [x] Final code pushed to **your fork**
- [ ] APK and/or a screen recording added or linked
- [ ] **Pull Request opened** from your fork → `Reskilll/TechQuest` **before the deadline**
- [x] PR title = your **team name**

---

<!-- 🔒 Keep your key out of the repo. Add these lines to a .gitignore file:

local.properties
*.apk
.env
*.keystore

-->

<sub>Built at **TechQuest · AI Tech Workshop** — iQOO Connect × Reskilll.</sub>
