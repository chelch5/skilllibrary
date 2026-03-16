---
name: react-native-firebase
description: Captures mobile app patterns centered on React Native and Firebase integration for auth, Firestore, and Storage. Trigger when building a React Native mobile app backed by Firebase. Do NOT use for web-only Firebase projects.
source: github.com/invertase/react-native-firebase
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: draft
  risk: low
  tags: [react-native, firebase, mobile]
---

# Purpose
Provides patterns for building React Native mobile applications using the `react-native-firebase` library for auth, Firestore, and Cloud Storage integration.

# When to use this skill
Use when:
- Building a React Native app that uses Firebase for backend services
- Integrating Firebase Auth, Firestore, or Storage into an existing React Native app

Do NOT use when:
- Building a web app (use firebase or firebase-sdk skills)
- Using a different mobile backend than Firebase

# Operating procedure
1. Install and configure `@react-native-firebase/app` and required service modules
2. Implement Firebase Auth with native sign-in flows (Google, Apple, email)
3. Set up Firestore with real-time listeners using `onSnapshot`
4. Handle offline persistence and sync conflicts explicitly
5. Apply Firebase Security Rules to protect data access

# Output defaults
React Native screens with Firebase Auth, Firestore real-time data, and offline support configured.

# Failure handling
If Firebase services are unreachable, use cached data and queue writes for replay when connectivity restores.
