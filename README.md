# Parabola Lab — Adaptive Quadratic Functions Lab

An individual university assignment for "Web-Based AI Math Differentiator" (Topic 8: AI for Differentiated Learning, Educational Technology & AI). Author: Student Name.

## What this app is
Parabola Lab is a Grade 9 quadratic-functions differentiated-learning app. One core task — the quadratic y = x² − 4x + 3 (vertex (2, −1), axis x = 2, roots 1 and 3, y-intercept 3, range y ≥ −1) — is adapted across three levels. Foundation identifies coefficients, opening and the vertex; Standard finds roots, vertex, axis and sketches; Advanced extends to a projectile model h(t) = −t² + 4t + 5 with physical domain [0, 5], maximum 9 at t = 2, landing at t = 5. All levels share the same core quadratic objective.

## Features
Level tabs, editable core function with a, b, c sliders and an explicit "Apply to task" action, "Generate with AI" (live LLM), "New variant" (deterministic, no AI), progressively revealed hints, level-specific answer fields with deterministic Check, AI Explain for misconceptions, separately revealed step-by-step solution, and an interactive graph showing the equation, axes, roots, vertex and y-intercept. a = 0 is handled honestly as a linear/constant function. The graph and deterministic checks work without AI. Primary language Russian with an English toggle.

## Stack and key files
React Router 8 framework mode (SSR), React 19, TypeScript, Tailwind CSS, Zod, Node 22, PocketBase. apps/web/src/routes/api.math.ts is the signed problem protocol and model endpoint. apps/web/src/constants/ai-assistant.config.ts holds the exact system and level prompts. apps/web/src/lib/quadratic.ts holds the deterministic math (roots, vertex, axis, discriminant, answer validation). apps/web/src/data/content.ts holds bilingual content and the core task. Report: /report.

## Prerequisites and secure configuration
Hostinger Integrated AI is enabled and credentials are platform-managed. No provider key is needed in the browser. Never enter or commit an API key. The server reads INTEGRATED_AI_API_URL and INTEGRATED_AI_API_KEY (platform-managed); do not copy or expose their values. PocketBase configuration (POCKETBASE_URL, PB_SUPERUSER_EMAIL, PB_SUPERUSER_PASSWORD) is also platform-managed. .env.example has placeholders only. .gitignore excludes .env and PocketBase runtime data.

## Local development
Use Node 22.22+ and npm 10. At the repository root: npm install, then npm run dev. The scripts start React Router and PocketBase. The PocketBase binary is supplied by Hostinger; install a matching supported binary for an external local environment. Run npm run typecheck and npm run lint. Credentials and platform model access are not automatically included in a source export.

## Testing
Deterministic math is verified in tests/quadratic.test.ts (run: node --experimental-strip-types tests/quadratic.test.ts from the repo root). Core cases: y = x² − 4x + 3 → roots 1, 3; vertex (2, −1); axis x = 2; y-intercept 3; discriminant 4. Advanced h(t) = −t² + 4t + 5 → maximum 9 at t = 2; landing t = 5; reject t = −1. Also test a missing root (partly correct), an extra root (incorrect), and a = 0 (linear). Live LLM responses require a verified-account review and are not claimed as tested unless you ran them.

## GitHub publication
Download this guide as README.md and place it at the export root. Export source using the editor's supported export option if available. Review it for secrets and runtime data. Create a PUBLIC GitHub repository, then run: git init; git add .; git commit -m "Initial Parabola Lab"; git branch -M main; git remote add origin YOUR_REPOSITORY_URL; git push -u origin main. A repository and its URL must be supplied by you; the app does not create one.

## Live publication
Use Hostinger Publish, open the resulting public URL and verify sign-up, verification email and live generation. Include that URL and your public repository URL in the assignment. An editor preview is not proof of a published submission.

## Important: GitHub Pages cannot host the secure AI backend
GitHub Pages serves only static files. This app's live AI runs through a secure server-side backend (React Router resource route → Hostinger Integrated AI) that holds the model credentials. An exported frontend deployed to GitHub Pages alone CANNOT call the AI: there is no server to hold the secret, and exposing the key in client code is insecure. To run live AI on another host you must provision PocketBase, restore migrations, and replace the managed Integrated AI adapter with a secure server-side provider adapter plus authentication. The deterministic demo (graph, samples, answer checks) works without any backend.

## Portability and limitations
Hostinger source export may not contain credentials, PocketBase records, platform integrations or its managed binary. The React Router backend source is in the project, but the read-only Integrated AI adapter depends on Hostinger. AI prose, hints and explanation assessments remain fallible; deterministic checks verify coefficients, roots, vertex, axis, y-intercept and discriminant, not every natural-language statement. Statistics are intentionally session-only. If AI credentials are unavailable, the app shows a clearly marked Demo mode with deterministic examples; no fake AI responses are generated.
