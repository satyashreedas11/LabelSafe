#  LabelSafe AI

> **Scan. Understand. Decide.** — Your AI-powered food safety companion.

[![Flutter](https://img.shields.io/badge/Flutter-3.1+-02569B?logo=flutter)](https://flutter.dev)
[![Gemini AI](https://img.shields.io/badge/Powered%20by-Gemini%20AI-4285F4?logo=google)](https://ai.google.dev)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

##  Problem Statement

**70% of consumers don't understand food labels.** Complex ingredient names, hidden additives, and misleading marketing make it nearly impossible for people to make informed food choices. This leads to:

- Unknowingly consuming harmful additives
- Allergic reactions from hidden ingredients
- Poor dietary decisions affecting long-term health
- Difficulty managing conditions like diabetes or hypertension

---

##  Our Solution

**LabelSafe AI** uses Google's Gemini AI to instantly analyze product labels and provide clear, actionable health insights. Simply scan any food, cosmetic, or medicine label and get:

-  **Safety Score (0-100)** — Instant health rating
-  **Color-Coded Badges** — Safe (Green), Caution (Yellow), Avoid (Red)
-  **Ingredient Breakdown** — What each ingredient does and its health impact
-  **Composition Analysis** — Sugar, fat, and additive percentages
-  **Smart Recommendations** — Personalized consume/avoid advice

---

##  Key Features

###  Smart Label Scanning
- Real-time camera scanning with auto-detection
- Gallery upload support for existing images
- Works with food, cosmetics, and medicine labels

###  AI-Powered Analysis
- Powered by **Google Gemini 1.5 Flash**
- Analyzes ingredients against EU/WHO safety standards
- Detects harmful additives, artificial colors, excessive sugar
- Provides health impact explanations for each ingredient

###  Visual Health Dashboard
- Circular gauge showing safety score
- Composition breakdown (Risk, Processed, Sugar, Fats)
- Quick stats for safe/caution/avoid ingredients count

### Detailed Ingredient View
- Each ingredient rated individually
- Technical names (E-numbers) displayed
- Health impact explanation in plain language
- Function category (Preservative, Sweetener, Color, etc.)

###  Scan History
- All previous scans saved locally
- Quick access to past analyses
- Track your food safety journey

###  Modern UI/UX
- Beautiful glassmorphic design
- Smooth animations throughout
- Dark/Light mode support
- Premium feel with attention to detail

---

##  Tech Stack

| Technology | Purpose |
|------------|---------|
| **Flutter 3.1+** | Cross-platform mobile framework |
| **Dart** | Programming language |
| **Google Gemini AI** | Vision AI for label analysis |
| **Riverpod** | State management |
| **GoRouter** | Navigation |
| **SharedPreferences** | Local data persistence |
| **Camera** | Real-time scanning |
| **Flutter Animate** | Smooth animations |

---

##  Getting Started

### Prerequisites
- Flutter SDK 3.1+
- Dart SDK
- Android Studio / VS Code
- Google Gemini API Key

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/vivekvsingh19/labelsafe_ai.git
   cd labelsafe_ai
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure API Key**

   Create a `.env` file in the root directory:
   ```env
   GEMINI_API_KEY=your_gemini_api_key_here
   GEMINI_MODEL=gemini-1.5-flash
   ```

4. **Run the app**
   ```bash
   flutter run
   ```

### Build APK
```bash
flutter build apk --release
```

---

##  Architecture

```
lib/
├── main.dart                 # App entry point
├── core/
│   ├── models/              # Data models (ProductAnalysis, etc.)
│   ├── providers/           # Riverpod providers
│   ├── routing/             # GoRouter configuration
│   ├── services/            # Gemini AI service
│   ├── theme/               # App theming
│   └── widgets/             # Reusable widgets
└── features/
    ├── home/                # Home dashboard
    ├── scan/                # Camera scanning
    ├── result/              # Analysis results
    ├── history/             # Scan history
    ├── profile/             # User profile
    ├── onboarding/          # Onboarding flow
    └── splash/              # Splash screen
```

---

## How It Works

1. **Capture** — User scans a product label using camera or uploads from gallery

2. **Process** — Image is sent to Gemini AI with specialized prompts for ingredient analysis

3. **Analyze** — AI evaluates each ingredient against health databases:
   - Checks for harmful additives (artificial colors, HFCS, BHA/BHT)
   - Calculates sugar and fat percentages
   - Rates each ingredient (Safe/Caution/Avoid)
   - Generates overall safety score

4. **Present** — Results displayed with:
   - Visual safety gauge
   - Color-coded recommendations
   - Detailed ingredient breakdown
   - Actionable health advice

---

##  Scoring Algorithm

| Factor | Weight | Criteria |
|--------|--------|----------|
| Ingredient Safety | 60% | Harmful additives = major penalty |
| Sugar Content | 25% | >20g/100g = Avoid rating |
| Fat & Overall | 15% | Balanced assessment |

**Automatic Downgrades:**
- Any "avoid" ingredient → Max score 50
- 2+ "caution" ingredients → Max score 65
- Artificial colors → Always "avoid"

---

##  Design Philosophy

- **Clarity First** — Complex data simplified into visual indicators
- **Trust Through Transparency** — Show exactly why each rating is given
- **Accessibility** — Color-coded + text labels for all ratings
- **Delight** — Smooth animations and premium feel

---

## Future Roadmap

- [ ] Barcode scanning for instant product lookup
- [ ] Personalized health profiles (allergies, dietary restrictions)
- [ ] Product comparison feature
- [ ] Community reviews and ratings
- [ ] Offline mode with cached data
- [ ] Multi-language support
- [ ] Wear OS companion app

---


##  Acknowledgments

- Google Gemini AI for powering our analysis
- Flutter team for the amazing framework
- Open source community for inspiration

---

<p align="center">
  <b>Making food transparency accessible to everyone.</b>
  <br><br>
  ⭐ Star this repo if you find it helpful!
</p>
