# InclusiAi

### Empowering Independence Through AI

InclusiAi is an **AI-powered accessibility platform** designed to make everyday digital and real-world interactions more accessible for people with different accessibility needs.

Instead of functioning as a generic AI chatbot, InclusiAi organizes AI capabilities around accessibility-focused workflows such as **vision assistance, hearing support, cognitive assistance, speech/AAC communication, motor assistance, voice interaction, and emergency support**.

The platform combines multimodal AI with accessible interfaces to help users understand, communicate, navigate, and interact more independently.

---

## ✨ Key Features

### 👁️ Vision Assistance

AI-powered tools designed to help users understand visual information.

Features include:

* Image description
* OCR / text extraction
* Object recognition
* Object finding
* People awareness
* Color identification
* Barcode scanning
* Money reading
* Form assistance
* Card assistance
* Continuous text reading
* Camera-based assistance
* Vision history

---

### 👂 Hearing Assistance

Tools that convert audio information into accessible visual information.

Features include:

* Live captions
* Speech-to-text
* Real-time captioning
* Sound awareness
* Announcement detection
* Call captioning
* Conversation bridge
* Hearing assistant

---

### 🖐️ Motor Assistance

Designed to reduce the need for precise physical interaction.

Features include:

* Voice commands
* Hands-free interaction
* Motor assistance workflows
* Adaptive interaction support

---

### 🧠 Cognitive Assistance

AI tools designed to make complex information easier to understand and act upon.

Features include:

* Text simplification
* Summarization
* Question answering
* Task breakdown
* AI-assisted text processing

---

### 🗣️ Speech & AAC Assistance

Alternative and augmentative communication tools for users who need different ways to communicate.

Features include:

* AAC assistant
* Communication board
* Quick phrases
* Type-to-speak
* Voice banking
* Communication routines
* Care team support
* Communication bridge
* AAC settings

---

### 🎙️ Voice Assistant

A voice-first interaction layer designed to provide hands-free access to accessibility features and AI assistance.

The architecture is designed so additional voice workflows can be integrated as the platform evolves.

---

### 🚨 Emergency Assistance

Emergency-oriented features provide quick access to important assistance workflows.

Features include:

* Emergency button
* Emergency contacts
* Trusted people
* Danger detection
* Emergency feature hub

> **Important:** Emergency functionality should be treated as an assistive system. Production deployments should provide reliable deterministic emergency pathways and should not depend exclusively on AI-generated decisions.

---

## 👤 Accessibility Profiles

InclusiAi supports accessibility-oriented user profiles so the interface can adapt to different user requirements.

Supported profile concepts include:

* Visual
* Hearing
* Motor
* Cognitive
* Speech
* Elderly
* Multiple Disabilities
* General
* Admin

Profile-based feature access is handled through the application's feature guard architecture.

---

# 🧠 AI Architecture

InclusiAi uses a provider-based AI architecture.

Instead of connecting every feature directly to a specific AI service, the application uses a common AI provider interface.

```text
Accessibility Feature
        ↓
       AI API
        ↓
  Provider Factory
        ↓
 ┌───────────────┐
 │ Gemini        │
 │ OpenAI        │
 │ Claude        │
 └───────────────┘
        ↓
   AI Response
        ↓
Accessible UI
```

This architecture makes it possible to change or add AI providers without rewriting every accessibility feature.

---

## 🤖 Current AI Provider

### Google Gemini

Gemini is currently configured as the primary/default AI provider.

The AI layer supports capabilities such as:

* Image description
* OCR
* Object recognition
* Audio transcription
* Text simplification
* Summarization
* Question answering
* Task breakdown
* Speech-related capabilities

The AI provider implementation is located under:

```text
lib/ai/
```

Important files include:

```text
lib/ai/base.ts
lib/ai/gemini.ts
lib/ai/openai.ts
lib/ai/claude.ts
lib/ai/factory.ts
lib/ai/utils.ts
```

OpenAI and Claude provider structures are included for extensibility/future integrations.

---

# 🔌 AI API

The application exposes a centralized AI endpoint:

```text
POST /api/ai
```

The API handles different request types such as:

```text
vision
text
simplify
summarize
question
audio
```

The API:

1. Receives the request.
2. Determines the requested operation.
3. Selects the AI provider.
4. Validates the input.
5. Sends the request to the provider.
6. Processes the response.
7. Returns the result to the frontend.

---

# 🛠️ Technology Stack

## Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS
* Radix UI
* Lucide React
* Framer Motion

## State Management

* Zustand
* TanStack React Query

## AI

* Google Gemini
* Provider abstraction for additional AI services

## Web Platform

* Next.js App Router
* Progressive Web App (PWA)

## Desktop

* Electron
* electron-builder

---

# 📁 Project Structure

```text
InclusiAI-main/
│
├── app/
│   ├── (auth)/
│   │   ├── login/
│   │   └── signup/
│   │
│   ├── (dashboard)/
│   │   ├── dashboard/
│   │   ├── vision/
│   │   ├── hearing/
│   │   ├── motor/
│   │   ├── cognitive/
│   │   ├── speech/
│   │   ├── voice-assistant/
│   │   ├── emergency/
│   │   ├── settings/
│   │   └── admin/
│   │
│   ├── (onboarding)/
│   │   └── profile-selection/
│   │
│   ├── api/
│   │   └── ai/
│   │
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
│
├── components/
│   ├── accessibility/
│   ├── admin/
│   ├── branding/
│   ├── dashboard/
│   ├── features/
│   ├── layout/
│   ├── navigation/
│   ├── onboarding/
│   └── providers.tsx
│
├── config/
│   ├── accessibility.ts
│   ├── ai-providers.ts
│   └── branding.ts
│
├── lib/
│   ├── ai/
│   ├── constants/
│   ├── hooks/
│   ├── store/
│   ├── types/
│   └── utils/
│
├── electron/
│   ├── main.js
│   ├── preload.js
│   └── entitlements.mac.plist
│
├── public/
│   ├── manifest.json
│   ├── sw.js
│   └── icons/
│
├── scripts/
│
├── package.json
├── next.config.ts
├── tsconfig.json
└── README.md
```

---

# ♿ Accessibility First

Accessibility is a core architectural principle of InclusiAi.

The application includes dedicated accessibility components and configuration for:

* Keyboard navigation
* Screen readers
* Text-to-speech
* Voice interaction
* High contrast
* Font-size customization
* Reduced motion
* Accessible focus states
* Camera-based assistance
* Hands-free interaction
* PWA installation

Important accessibility components include:

```text
AccessibilityWrapper
TextToSpeech
CameraStabilizer
PWAInstallPrompt
ServiceWorkerRegistration
```

The project targets **WCAG 2.1 AA** principles.

However, actual accessibility compliance should be verified through both automated testing and manual testing with real assistive technologies.

---

# 📱 Progressive Web App

InclusiAi includes PWA functionality so that the application can behave more like an installable application.

PWA-related files include:

```text
public/manifest.json
public/sw.js
```

The application manifest provides:

* Application metadata
* Icons
* Installation configuration
* Application shortcuts

---

# 🖥️ Desktop Application

InclusiAi also includes Electron support.

Electron files:

```text
electron/main.js
electron/preload.js
electron/entitlements.mac.plist
```

The project can be packaged for:

* Windows
* macOS
* Linux

The Next.js configuration uses standalone output to support desktop packaging.

---

# 🎨 Branding System

Branding is centralized rather than being scattered across individual components.

Main configuration:

```text
config/branding.ts
```

Current branding:

**Name:** InclusiAi

**Tagline:** Empowering Independence Through AI

Centralizing branding makes future rebranding significantly easier and reduces the possibility of stale product names remaining throughout the application.

---

# ⚙️ Installation

## Prerequisites

Make sure the following are installed:

* Node.js
* npm

Recommended modern Node.js version:

```text
Node.js 20+
```

---

## Clone the Repository

```bash
git clone <your-repository-url>
```

Enter the project directory:

```bash
cd InclusiAI-main
```

---

## Install Dependencies

```bash
npm install
```

---

# 🔐 Environment Variables

Create a `.env.local` file in the project root.

Example:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

Never commit real API keys to Git.

Make sure environment files containing secrets are included in `.gitignore`.

---

# 🚀 Running the Application

Start the development server:

```bash
npm run dev
```

The application will normally be available at:

```text
http://localhost:3000
```

---

# 🧪 Development Checks

Before submitting changes, run:

```bash
npm run lint
```

Then:

```bash
npm run build
```

Both should complete successfully before considering a major change complete.

---

# 🖥️ Electron Development

To run the desktop version during development:

```bash
npm run electron:dev
```

Electron packaging commands are defined in:

```text
package.json
```

---

# 📦 Electron Build

For macOS:

```bash
npm run electron:build:mac
```

Additional Windows and Linux build commands are available through the Electron-builder configuration in `package.json`.

---

# 🔄 Application Flow

The overall architecture can be represented as:

```text
                 ┌────────────────────┐
                 │      User          │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Authentication     │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Profile Selection  │
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │ Accessibility      │
                 │ Dashboard          │
                 └─────────┬──────────┘
                           │
       ┌───────────┬───────┼────────┬───────────┐
       ▼           ▼       ▼        ▼           ▼
    Vision      Hearing   Motor  Cognitive    Speech
       │           │       │        │           │
       └───────────┴───────┴────────┴───────────┘
                           │
                           ▼
                    ┌─────────────┐
                    │   AI API    │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │ AI Provider │
                    │   Gemini    │
                    └──────┬──────┘
                           │
                           ▼
                    ┌─────────────┐
                    │ Accessible  │
                    │   Result    │
                    └─────────────┘
```

---

# 🗃️ State Management

InclusiAi uses Zustand to separate state by functional domain.

Examples include:

```text
Authentication
User Profile
User Preferences
API Keys
Vision History
Captions
AAC
Voice Banking
Emergency Contacts
Trusted People
Object Memory
Sound Awareness
Forms
Products
Tags
Admin
```

This allows individual feature modules to manage their own state while keeping the application maintainable.

---

# 🔒 Security Considerations

Because InclusiAi can process potentially sensitive information such as images, audio, communication data and emergency contacts, security should be treated as a core requirement.

Production deployments should verify:

* API keys are never committed.
* API keys are not unnecessarily exposed to the browser.
* Authentication is enforced server-side.
* Authorization is enforced server-side.
* Admin access cannot be bypassed through client-side state.
* AI requests have appropriate limits.
* Uploaded files are validated.
* Camera/microphone permissions are handled securely.
* Sensitive information is not unnecessarily logged.
* AI provider errors do not expose secrets.

---

# 🛡️ AI Safety

AI responses should be treated as assistive output.

The platform should not assume that an AI-generated response is always correct, especially for:

* Emergency situations
* Safety decisions
* Medical information
* Identity-related information
* Financial information
* Critical accessibility instructions

For safety-critical functionality, deterministic fallback mechanisms should always be available.

---

# 🔏 Privacy

InclusiAi may process information such as:

* Images
* Camera input
* Audio
* Text
* Accessibility preferences
* Emergency contacts
* Communication information

A production privacy policy should clearly explain:

1. What information is collected.
2. What information is processed locally.
3. What information is sent to AI providers.
4. What information is stored.
5. How long information is retained.
6. How users can delete their information.
7. How provider APIs process submitted data.

---

# 🧩 Future Development

The architecture allows the platform to be extended with additional capabilities.

Potential future directions include:

* More AI providers
* Advanced voice assistant
* Offline AI capabilities
* Improved object recognition
* Real-time environmental awareness
* Wearable-device integration
* Smart-home accessibility controls
* Advanced AAC personalization
* Caregiver dashboards
* Accessibility analytics
* More sophisticated emergency workflows
* Additional desktop/mobile integrations

---

# 🧪 Testing Checklist

Before releasing a new version, verify:

### Authentication

* [ ] Signup works
* [ ] Login works
* [ ] Logout works
* [ ] Invalid credentials are handled
* [ ] Sessions are secure

### Dashboard

* [ ] Dashboard loads
* [ ] Profile selection works
* [ ] Feature cards open correctly
* [ ] Navigation works

### Vision

* [ ] Camera permissions work
* [ ] Image upload works
* [ ] Image description works
* [ ] OCR works
* [ ] Object-related workflows work

### Hearing

* [ ] Microphone permissions work
* [ ] Captions work
* [ ] Speech-to-text works
* [ ] Sound awareness works

### Motor

* [ ] Voice commands work
* [ ] Hands-free interactions work

### Cognitive

* [ ] Simplification works
* [ ] Summarization works
* [ ] Question answering works
* [ ] Task breakdown works

### Speech

* [ ] AAC works
* [ ] Quick phrases work
* [ ] Type-to-speak works
* [ ] Voice banking workflows work

### Emergency

* [ ] Emergency interface loads
* [ ] Emergency contacts work
* [ ] Trusted people work
* [ ] Fallback behavior is tested

### Accessibility

* [ ] Keyboard navigation
* [ ] Screen reader navigation
* [ ] Focus indicators
* [ ] Color contrast
* [ ] Text scaling
* [ ] Reduced motion
* [ ] High contrast
* [ ] Accessible labels

### Build

```bash
npm run lint
npm run build
```

---

# 🤝 Contributing

Contributions are welcome.

When contributing:

1. Understand the existing architecture.
2. Keep accessibility as a first-class requirement.
3. Avoid unnecessary rewrites.
4. Follow the existing component structure.
5. Keep AI integrations behind the provider abstraction.
6. Do not commit secrets.
7. Run lint before submitting changes.
8. Run the production build before submitting major changes.
9. Test keyboard and screen-reader behavior when modifying accessibility components.

---

# 📄 License

Add the project's chosen open-source or proprietary license here.

Example:

```text
MIT License
```

Do not claim a license unless a corresponding license file has been added to the repository.

---

# 🌍 Vision

InclusiAi aims to make artificial intelligence more accessible by placing AI capabilities inside interfaces designed around people's accessibility needs.

The goal is simple:

> **Use AI to remove barriers, increase independence, and make technology more accessible to everyone.**

---

## Project Status

**Development / Prototype**

The project contains a broad accessibility architecture with multiple AI-powered feature areas, PWA functionality and Electron support. Individual features should be validated against their actual implementation and production requirements before being represented as fully production-ready.

---

**InclusiAi — Empowering Independence Through AI**
