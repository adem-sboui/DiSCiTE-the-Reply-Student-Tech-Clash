<p align="center">
  <img src="assets/discite-logo.jpeg" alt="Discite logo" width="420">
</p>

# DiSCiTE

An AI-study-planner prototype for the **Reply Student Tech Clash**, a
hackathon on using AI to reshape education, at Politecnico di Torino
([MONTH YEAR]). [RESULT, ONLY IF TRUE, e.g. "Participant"].

> **Demo data:** all reviews, grades and notes in this prototype are
> synthetic (generated or invented). It does not contain real student data.

## The idea
Students prepare for exams without knowing what actually worked for others.
DiSCiTE collects anonymous experiences from students who already passed a
course and turns them into guidance for the next student.


## Features
- **Course insights:** average grade by weekly study time and by start date,
  hardest topics, and grade gain from each resource (slides, past exams,
  study groups...)
- **Get your approach:** enter weekly hours, target grade and weeks until
  the exam, and get a week-by-week plan built from students who reached that
  grade
- **Add a review:** share your own experience and earn tokens
- **Notes library:** upload notes to earn tokens, unlock other students'
  notes with tokens
- **Best notes:** merges notes from top-grade students, ranking points that
  several of them wrote

## The AI part
Two features use a language model (Claude):
- **Rewrite with AI (plan):** the app first builds a rule-based plan from the
  aggregated data. The model then writes it as a personal plan, using only
  those numbers. It is told not to invent statistics.
- **Rewrite as one study guide with AI (notes):** merges top-grade notes into
  one guide, using only points that appear in the notes.

The API key lives on a small Python server (`server.py`), never in the
browser. Student notes are treated as data, and the model is told to ignore
any instructions written inside them. Without a key, the app still works with
its rule-based output.

## How it works
Front end: plain HTML, CSS and JavaScript. Data is stored in the browser
(`localStorage`). The plan and combined notes are first built by
**rule-based logic on aggregated data**; the AI step rewrites them.

## Not implemented
User accounts, a database, real data, checking the model's output
automatically, and AI features on the public GitHub Pages demo (they need
the server).

## Run it
Without AI: open `index.html` in a browser.

With AI:

    pip install -r requirements.txt
    export ANTHROPIC_API_KEY=your-key     # Windows: set ANTHROPIC_API_KEY=your-key
    python server.py

Then open http://localhost:5000.

## Files
- `index.html`: the front end
- `server.py`: small Flask server for the AI calls
- `requirements.txt`
- `assets/discite-logo.jpeg`: logo
