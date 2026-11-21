# MASTERYLOOP AI

A frontend-only hackathon prototype for concept-level adaptive learning. Every answer updates a local learner model, informs reasoning feedback, and helps choose a next practice question and review.

## Run locally

Requirements: Node.js 20 or later and npm.

```bash
npm install
npm run dev
```

Vite prints the local URL, usually `http://localhost:5173`. The app runs entirely in the browser with the frontend development server. There is no backend, API proxy, database server, or authentication service.

## Three-minute demo

1. Open the landing page and choose **Start learning → Student demo**.
2. Point out that the dashboard identifies Ohm’s law as a low-evidence concept and labels sample learner data.
3. Open **Adaptive practice**. Choose a wrong answer and enter reasoning such as “the resistor uses up some current.” Submit with a confidence level.
4. Show the mastery update and possible misconception signal. This is deterministic, rule-based analysis, not an LLM diagnosis.
5. Choose **Next question** and explain the learner-model selection panel.
6. Open **Revision** to show the review scheduled after the incorrect response.
7. Select **Classroom analytics** to show the fictional classroom heatmap and teaching priority.
8. Use the profile menu to reset local demo progress.

## Features

- Instant student and teacher demos with no signup.
- LocalStorage persistence and reset for demo learner data.
- Twelve concept nodes across selected Class 10 Physics topics with an interactive prerequisite map.
- Eight-question diagnostic flow that updates concept estimates.
- Adaptive practice with difficulty, confidence, written reasoning, hints, feedback, and a next-question explanation.
- Bounded mastery update that weighs correctness, difficulty, confidence, reasoning detail, and repeated evidence.
- Rule-based misconception signals with response evidence and uncertainty wording.
- Local review scheduling, progress views, and simulated teacher analytics.
- Responsive layout, keyboard-operable concept map nodes, visible focus, and reduced-motion support.

## AI and data status

Gemini and other hosted AI services are **not integrated**. All core demo logic is deterministic and runs locally in the browser. No API key is needed or accepted. Student progress is stored in this browser's LocalStorage; classroom names and scores are fictional simulated data. Syllabus coverage is illustrative and should be checked against the current board syllabus before classroom use.

This prototype has no account system, server storage, multi-user sync, or validated assessment model. Mastery and review timing are transparent heuristics, not scientifically validated measurements. Misconception matching is a narrow rules engine and should not be treated as a diagnosis.

## Deploy

Run `npm run build` and publish the generated `dist/` directory on Vercel or another static host. No environment variables are required.
