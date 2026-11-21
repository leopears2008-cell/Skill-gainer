<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>MasteryLoop AI — README</title>
<meta name="description" content="A frontend-only prototype for concept-level adaptive learning.">
<style>
:root{
  --bg:#f7f8fa; --surface:#ffffff; --ink:#14213d; --muted:#5b6478; --line:#dde2ea;
  --accent:#1f5eff; --accent-soft:#e8efff; --warn-bg:#fff6e0; --warn-line:#f0c050; --code:#0f1a33; --code-ink:#e6ecff;
}
@media (prefers-color-scheme:dark){
  :root{--bg:#0e1424; --surface:#151c30; --ink:#e8ecf6; --muted:#9aa5bd; --line:#27304a;
    --accent:#6c93ff; --accent-soft:#1c2748; --warn-bg:#2a2412; --warn-line:#8a6c1d; --code:#0a1020; --code-ink:#dfe7ff;}
}
*{box-sizing:border-box}
html{scroll-behavior:smooth;scroll-padding-top:72px}
@media (prefers-reduced-motion:reduce){html{scroll-behavior:auto}}
body{margin:0;background:var(--bg);color:var(--ink);font:16px/1.65 Georgia,"Iowan Old Style","Times New Roman",serif}
h1,h2,h3,nav,.badge,table,code,pre,button,.meta{font-family:system-ui,-apple-system,"Segoe UI",Roboto,Helvetica,Arial,sans-serif}
a{color:var(--accent)}
a:focus-visible,button:focus-visible{outline:3px solid var(--accent);outline-offset:2px;border-radius:4px}
header{background:var(--code);color:var(--code-ink);padding:64px 24px 56px}
.wrap{max-width:1040px;margin:0 auto}
header h1{margin:0 0 12px;font-size:clamp(2rem,6vw,3.25rem);letter-spacing:-.02em;line-height:1.1}
header p{margin:0;max-width:60ch;font-size:1.15rem;color:#b9c6e6}
.badges{display:flex;flex-wrap:wrap;gap:8px;margin-top:24px}
.badge{font-size:.8rem;padding:4px 10px;border:1px solid #3a4a74;border-radius:999px;color:#cdd8f5}
nav{position:sticky;top:0;z-index:5;background:var(--surface);border-bottom:1px solid var(--line)}
nav .wrap{display:flex;gap:4px;overflow-x:auto;padding:0 12px}
nav a{padding:14px 12px;font-size:.9rem;text-decoration:none;color:var(--muted);white-space:nowrap}
nav a:hover{color:var(--accent)}
main{padding:16px 24px 64px}
section{padding:36px 0;border-bottom:1px solid var(--line)}
section:last-child{border-bottom:0}
h2{font-size:1.6rem;margin:0 0 16px;letter-spacing:-.01em}
h3{font-size:1.05rem;margin:24px 0 8px}
p{margin:0 0 14px;max-width:72ch}
pre{background:var(--code);color:var(--code-ink);padding:16px 18px;border-radius:8px;overflow-x:auto;font-size:.9rem;line-height:1.5;margin:12px 0 16px}
code{font-size:.9em;background:var(--accent-soft);padding:1px 6px;border-radius:4px}
pre code{background:none;padding:0}
.callout{background:var(--warn-bg);border-left:4px solid var(--warn-line);padding:14px 18px;border-radius:0 8px 8px 0;margin:16px 0;max-width:80ch}
.callout strong{font-family:system-ui,sans-serif}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:16px;margin-top:8px}
.item{background:var(--surface);border:1px solid var(--line);border-radius:8px;padding:16px 18px}
.item h3{margin-top:0}
.item p{margin:0;font-size:.95rem;color:var(--muted)}
.scroll{overflow-x:auto}
table{border-collapse:collapse;width:100%;min-width:560px;background:var(--surface);font-size:.92rem}
th,td{text-align:left;padding:10px 14px;border:1px solid var(--line);vertical-align:top}
th{background:var(--accent-soft)}
ol.steps{padding-left:22px;max-width:80ch}
ol.steps li{margin-bottom:10px}
footer{padding:28px 24px;text-align:center;color:var(--muted);font:.85rem system-ui,sans-serif}
</style>
</head>
<body>
<header>
  <div class="wrap">
    <h1>MasteryLoop AI</h1>
    <p>A frontend-only prototype for concept-level adaptive learning. Every answer updates a local learner model, informs reasoning feedback, and helps choose the next practice question and review.</p>
    <div class="badges">
      <span class="badge">Hackathon prototype</span>
      <span class="badge">Frontend only</span>
      <span class="badge">Node.js 20+</span>
      <span class="badge">Vite</span>
      <span class="badge">No backend or API keys</span>
    </div>
  </div>
</header>

<nav aria-label="Sections">
  <div class="wrap">
    <a href="#run">Run locally</a>
    <a href="#demo">Demo</a>
    <a href="#features">Features</a>
    <a href="#status">AI and data</a>
    <a href="#limits">Limitations</a>
    <a href="#deploy">Deploy</a>
  </div>
</nav>

<main class="wrap">
  <section id="run">
    <h2>Run locally</h2>
    <p>Requires Node.js 20 or later and npm.</p>
<pre><code>npm install
npm run dev</code></pre>
    <p>Vite prints the local URL, usually <code>http://localhost:5173</code>. The app runs entirely in the browser on the frontend development server. There is no backend, API proxy, database server, or authentication service.</p>
  </section>

  <section id="demo">
    <h2>Three-minute demo</h2>
    <ol class="steps">
      <li>Open the landing page and choose <strong>Start learning → Student demo</strong>.</li>
      <li>Point out that the dashboard identifies Ohm’s law as a low-evidence concept and labels the sample learner data.</li>
      <li>Open <strong>Adaptive practice</strong>. Choose a wrong answer and enter reasoning such as “the resistor uses up some current.” Submit with a confidence level.</li>
      <li>Show the mastery update and the possible misconception signal. This is deterministic, rule-based analysis, not an LLM diagnosis.</li>
      <li>Choose <strong>Next question</strong> and explain the learner-model selection panel.</li>
      <li>Open <strong>Revision</strong> to show the review scheduled after the incorrect response.</li>
      <li>Select <strong>Classroom analytics</strong> to show the fictional classroom heatmap and teaching priority.</li>
      <li>Use the profile menu to reset local demo progress.</li>
    </ol>
  </section>

  <section id="features">
    <h2>Features</h2>
    <div class="grid">
      <div class="item"><h3>Instant demos</h3><p>Student and teacher demos with no signup.</p></div>
      <div class="item"><h3>Local persistence</h3><p>Demo learner data is saved in LocalStorage and can be reset at any time.</p></div>
      <div class="item"><h3>Concept map</h3><p>Twelve concept nodes across selected Class 10 Physics topics, with an interactive prerequisite map.</p></div>
      <div class="item"><h3>Diagnostic flow</h3><p>An eight-question diagnostic that updates concept estimates.</p></div>
      <div class="item"><h3>Adaptive practice</h3><p>Difficulty, confidence, written reasoning, hints, feedback, and an explanation of why the next question was chosen.</p></div>
      <div class="item"><h3>Bounded mastery update</h3><p>Weighs correctness, difficulty, confidence, reasoning detail, and repeated evidence.</p></div>
      <div class="item"><h3>Misconception signals</h3><p>Rule-based matching with response evidence and uncertainty wording.</p></div>
      <div class="item"><h3>Review and analytics</h3><p>Local review scheduling, progress views, and simulated teacher analytics.</p></div>
      <div class="item"><h3>Accessible by design</h3><p>Responsive layout, keyboard-operable concept map nodes, visible focus, and reduced-motion support.</p></div>
    </div>
  </section>

  <section id="status">
    <h2>AI and data status</h2>
    <div class="scroll">
    <table>
      <thead><tr><th>Area</th><th>Status</th></tr></thead>
      <tbody>
        <tr><td>Hosted AI (Gemini and others)</td><td>Not integrated. No API key is needed or accepted.</td></tr>
        <tr><td>Core logic</td><td>Deterministic and local to the browser.</td></tr>
        <tr><td>Student progress</td><td>Stored in this browser’s LocalStorage.</td></tr>
        <tr><td>Classroom data</td><td>Fictional, simulated names and scores.</td></tr>
        <tr><td>Syllabus coverage</td><td>Illustrative. Check it against the current board syllabus before classroom use.</td></tr>
      </tbody>
    </table>
    </div>
  </section>

  <section id="limits">
    <h2>Limitations</h2>
    <div class="callout">
      <strong>Prototype notice.</strong> Mastery scores and review timing are transparent heuristics, not scientifically validated measurements.
    </div>
    <p>This prototype has no account system, server storage, multi-user sync, or validated assessment model. Misconception matching is a narrow rules engine and should not be treated as a diagnosis.</p>
  </section>

  <section id="deploy">
    <h2>Deploy</h2>
<pre><code>npm run build</code></pre>
    <p>Publish the generated <code>dist/</code> directory on Vercel or another static host. No environment variables are required.</p>
  </section>
</main>

<footer>MasteryLoop AI · Frontend-only hackathon prototype</footer>
</body>
</html>
