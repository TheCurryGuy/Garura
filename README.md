
# Garura: The Secure Remote Interview Platform
**A Hack4Bengal 4.0 Submission by TheBotHeads**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![TypeScript](https://img.shields.io/badge/--blue?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-000000?logo=nextdotjs&logoColor=white)](https://nextjs.org/)
[![Electron.js](https://img.shields.io/badge/Electron-47848F?logo=electron&logoColor=white)](https://www.electronjs.org/)

**Garura is a high-integrity, cheat-proof remote interview platform designed to validate a candidate's true skills through a secure, monitored, and feature-rich testing environment.**

**Live Demo:** [https://garuraweb.onrender.com/](https://garuraweb.onrender.com/)

---

## Table of Contents
- [The Problem](#the-problem-restoring-trust-in-remote-hiring)
- [Our Solution](#our-solution-a-fortified-interview-ecosystem)
- [Core Features](#core-features)
  - [For the Interviewer (Web Platform)](#for-the-interviewer-web-platform)
  - [For the Interviewee (Secure Desktop Client)](#for-the-interviewee-secure-desktop-client)
- [The Garuda Security Suite](#the-garuda-security-suite)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [1. Server & Interviewer Platform Setup](#1-server--interviewer-platform-setup)
  - [2. Secure Interviewee Client Setup](#2-secure-interviewee-client-setup)
- [Team](#team)
- [License](#license)

---

## The Problem: Restoring Trust in Remote Hiring
The rise of remote work has made technical interviews more accessible, but it has also created a crisis of integrity. Sophisticated cheating tools can transcribe questions, feed AI-generated answers in real-time, and even allow remote helpers to solve challenges, all while remaining invisible to standard screen-sharing. This erodes trust, devalues merit, and makes it impossible for companies to be sure they are hiring the right person.

## Our Solution: A Fortified Interview Ecosystem
Garuda tackles this problem head-on with an **asymmetric client-server architecture**:
- **Interviewers** operate from a flexible, powerful Next.js web platform.
- **Interviewees** are required to join via a mandatory, locked-down Electron.js desktop application.

This model allows us to enforce system-level security measures that are simply impossible in a browser-based environment, creating a controlled and fair testing ground where a candidate's genuine skills can be accurately assessed.

![Garuda Banner](https://raw.githubusercontent.com/TheCurryGuy/Garura/main/Banner.png) 

## Core Features

### For the Interviewer (Web Platform)
- **Dynamic Session Builder:** Configure each interview on the fly by enabling/disabling modules for a multi-language code editor, a digital whiteboard, or an AI-powered quiz.
- **AI Quiz Generation:** Instantly generate unique, relevant quizzes on any topic using the Google Gemini API, complete with custom time limits.
- **Live Command Center:** A three-pane UI provides complete control, allowing you to push coding questions, launch quizzes, chat in real-time, and receive instant security alerts.
- **Comprehensive Dashboard:** Review a complete history of past interviews and access the detailed process-log security report for each completed session.

### For the Interviewee (Secure Desktop Client)
- **Locked-Down Kiosk Mode:** A borderless, full-screen environment with no OS-level minimize or close buttons, ensuring the candidate's focus remains on the interview.
- **Integrated Tool Suite:**
  - An executable CodeMirror editor supporting Java, C++, Python, and JavaScript, with code execution powered by the Judge0 API.
  - A feature-rich, `tldraw`-powered digital whiteboard for system design and diagramming.
- **Immutable Audio:** The candidate's microphone is programmatically enforced to be "always on," preventing silent communication.

## The Garuda Security Suite
Our Electron client implements a multi-layered security protocol to ensure interview integrity:

| Security Measure              | Description                                                                 | Status |
|-------------------------------|-----------------------------------------------------------------------------|:------:|
| **Pre-Launch App Scan**       | Blocks launch if blacklisted software (Discord, OBS, etc.) is detected.      |   ✅   |
| **Display Affinity Scan**     | Detects and blocks windows using `WDA_EXCLUDEFROMCAPTURE` to hide from screen sharing (Windows-only). |   ✅   |
| **Forced Admin Privileges**   | Installer requires elevated permissions for deep system monitoring.           |   ✅   |
| **Screenshot Termination**    | Instantly terminates the app if the `PrintScreen` key is pressed.         |   ✅   |
| **Ctrl Key Monitoring**       | Alerts the interviewer on each press and terminates the app after 3 presses. |   ✅   |
| **Focus Loss Detection**      | Sends an instant alert to the interviewer if the app window loses focus.   |   ✅   |
| **Clipboard Wiping**          | A background poller clears the system clipboard every 5 seconds.            |   ✅   |
| **Periodic Process Logging**  | Captures a snapshot of all running processes every 10 minutes for the final audit report. |   ✅   |

## Technology Stack
Garuda is built on a modern, robust, and scalable technology stack.

| Component                 | Technologies                                                                 |
|---------------------------|------------------------------------------------------------------------------|
| **Web Platform**          | Next.js, React, TypeScript, Tailwind CSS, shadcn/ui                           |
| **Secure Desktop Client** | Electron.js, Vite, React, TypeScript, PowerShell (for Windows scans)         |
| **Backend & Database**    | Next.js API Routes, PostgreSQL, Prisma ORM                                       |
| **Real-time Services**    | Socket.IO, Stream.io (Video), Google Gemini (AI), Judge0 (Code Execution), Vercel Blob (Storage) |
| **Deployment**            | Vercel (Web App), Render (Server)                                            |

## Project Structure
Our project is a monorepo containing two primary packages: `platform` (the Next.js web app) and `Garura` (the Electron desktop client).

## Getting Started

### 1. Server & Interviewer Platform Setup
Navigate to the `platform` directory:
```bash
cd platform

# Install dependencies
npm install

# Create your .env file from the example
cp .env.example .env  # Add your database, Stream, Gemini, and other API keys

# Initialize and migrate the database
npx prisma migrate dev

# Start the development server
npm run dev
```
The interviewer platform will be accessible at `http://localhost:3000`.

### 2. Secure Interviewee Client Setup
Navigate to the `Garura` directory:
```bash
cd Garura

# Install dependencies
npm install

# Create your .env file from the example
cp .env.example .env  # Add your VITE_STREAM_API_KEY

# Launch the Electron app in development mode
npm run dev
```

## Team
This project was proudly built by **Team TheBotHeads** for the **Hack4Bengal 4.0** hackathon.

- Ishika
- Ayushi
- Satadru
- Bibek Dhara (TheCurryGuy)

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
