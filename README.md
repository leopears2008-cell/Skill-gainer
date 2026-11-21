# MASTERYLOOP AI

A hackathon prototype for concept-level adaptive learning. The demo shows how answer evidence can update a learner model, surface a possible reasoning misconception, choose a next question, schedule a review, and make class-wide patterns visible to teachers.

## Run locally

Requirements: Node.js 20 or later and npm.

```bash
cd .
npm install
npm run dev
```

Vite prints the local URL, usually `http://localhost:5173`.

## Three-minute judge demo

1. Open the landing page and choose **Start learning → Student demo**.
2. Point out that the dashboard identifies Ohm’s law as a low-evidence concept and labels its sample learner data.
3. Open **Adaptive practice**. On the first question, choose a wrong answer and enter reasoning such as “the resistor uses up some current.” Submit with a confidence level.
4. Show the bounded mastery change, rationale, and the deterministic “possible misconception” signal. Explain it is a demo pattern match, not a model diagnosis.
5. Choose **Next question** and point out the “Why this question?” panel. The selector ranks the weakest supported concept and deprioritizes recent question IDs.
6. Open **Revision** to show the earlier review created by the incorrect response.
7. Select **Classroom analytics** in the sidebar to show the fictional classroom heatmap and teaching priority.
8. Use the profile menu to reset local demo progress before the next run.

## What is implemented

- Student and teacher demo modes with no signup.
- LocalStorage persistence and reset for the demo learner.
- Twelve concept nodes across selected Class 10 Physics topics and an interactive prerequisite map.
- Eight-question diagnostic flow that updates concept estimates.
- Adaptive practice with question difficulty, confidence, written reasoning, hints, feedback, and a selected-next-question explanation.
- Explainable bounded mastery update based on correctness, difficulty, confidence, reasoning detail, and repeated evidence.
- Conservative deterministic misconception signals with response evidence and uncertainty wording.
- Review timing heuristic (1 day after a miss; 3, 7, or 14 days based on mastery after a correct answer).
- Learner progress views and simulated teacher analytics.
- Responsive layout, keyboard-operable concept nodes, visible focus, and reduced-motion support.

## AI and data status

This build does **not** call Gemini or any other hosted AI. The question selector and misconception matcher are deterministic demo logic. No provider key is used in the browser, and no backend exists in this prototype. ` .env.example` documents the intended server-side Gemini variables; add a backend proxy, validation, timeouts, and rate limiting before enabling a provider. The demo questions and classroom learners are sample/fictitious data. Syllabus coverage is illustrative and should be checked against the current board syllabus before classroom use.

Demo learning state lives only in the current browser's localStorage. There is no account system, server storage, multi-user sync, formal student privacy workflow, or validated assessment model.

## Deploy

Build with `npm run build`; publish the generated `dist/` directory on Vercel or another static host. A Vercel project can use the repository root `work/` as its root directory, with build command `npm run build` and output directory `dist`. No environment variables are required for the demo. Never add provider credentials to `VITE_*` frontend variables.

## Honest prototype limits

- Static question bank; no generated question authoring or answer validation service.
- Mastery and review timing are transparent heuristics, not scientifically validated measurements.
- Misconception matching is narrow phrase matching and must not be used as a diagnosis.
- Teacher roster and heatmap are seeded simulation, not real classroom evidence.
- Google Gemini status: not integrated. A secure server proxy is a future task.
- No automated test suite was requested or added; production and syllabus validation remain outstanding.

