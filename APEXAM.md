---
layout: base
title: AP Computer Science
permalink: /APCSP
---

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Verse Engine</title>

<!-- PyScript -->
<link rel="stylesheet" href="https://pyscript.net/releases/2024.1.1/core.css">
<script type="module" src="https://pyscript.net/releases/2024.1.1/core.js"></script>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=EB+Garamond:ital,wght@0,400;0,500;1,400&family=Courier+Prime:ital@0;1&display=swap" rel="stylesheet">

<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --ink:      #14100c;
    --leather:  #2c1f14;
    --mahogany: #3a2516;
    --gold:     #c9a84c;
    --gold-dim: #8a6f35;
    --cream:    #ede0cc;
    --parchment:#f5ede0;
    --ash:      #7a6a5a;
  }

  html, body {
    background: var(--ink);
    color: var(--cream);
    font-family: 'EB Garamond', Georgia, serif;
    min-height: 100vh;
    background-image:
      radial-gradient(ellipse 80% 60% at 15% 10%, rgba(44,31,20,0.9) 0%, transparent 70%),
      radial-gradient(ellipse 60% 80% at 85% 90%, rgba(61,43,31,0.7) 0%, transparent 65%),
      url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
  }

  .page { max-width: 820px; margin: 0 auto; padding: 60px 28px 80px; }

  /* ── HEADER ── */
  .masthead { text-align: center; margin-bottom: 48px; }
  .masthead-candle {
    font-size: 22px; margin-bottom: 18px; display: block; opacity: 0.85;
    animation: flicker 3s ease-in-out infinite;
  }
  @keyframes flicker {
    0%,100%{opacity:.85} 45%{opacity:.65} 55%{opacity:.92} 75%{opacity:.72}
  }
  .masthead-eyebrow {
    font-family: 'Courier Prime', monospace; font-size: 10px;
    letter-spacing: 0.4em; color: var(--gold-dim);
    text-transform: uppercase; margin-bottom: 16px;
  }
  .masthead h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.2rem, 5.5vw, 3.8rem);
    font-weight: 400; color: var(--parchment);
    line-height: 1.1; margin-bottom: 10px;
  }
  .masthead h1 em { font-style: italic; color: var(--gold); }
  .masthead-sub { font-size: 1.05rem; color: var(--ash); font-style: italic; }

  /* ── ORNAMENT ── */
  .ornament { display: flex; align-items: center; gap: 14px; margin: 36px 0; }
  .ornament::before, .ornament::after {
    content: ''; flex: 1; height: 0.5px;
    background: linear-gradient(to right, transparent, var(--gold-dim), transparent);
  }
  .ornament span { color: var(--gold); font-size: 11px; letter-spacing: 0.15em; }

  /* ── PANEL ── */
  .panel {
    background: var(--leather);
    border: 0.5px solid rgba(201,168,76,0.22); border-radius: 2px;
    padding: 36px 40px 32px; margin-bottom: 28px;
    box-shadow: 0 12px 56px rgba(0,0,0,0.55), inset 0 1px 0 rgba(201,168,76,0.08);
    position: relative;
  }
  .panel-cap {
    position: absolute; top: -10px; left: 50%; transform: translateX(-50%);
    background: var(--leather); color: var(--gold); font-size: 16px; padding: 0 12px;
  }
  .grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 20px; margin-bottom: 24px; }
  @media(max-width:580px) {
    .grid-3 { grid-template-columns: 1fr 1fr; }
    .panel  { padding: 28px 18px 24px; }
  }

  .field label {
    display: block; font-family: 'Courier Prime', monospace; font-size: 9.5px;
    letter-spacing: 0.32em; text-transform: uppercase; color: var(--gold-dim); margin-bottom: 7px;
  }
  select {
    width: 100%; background: var(--mahogany);
    border: 0.5px solid rgba(201,168,76,0.28); border-radius: 1px;
    color: var(--cream); font-family: 'EB Garamond', serif;
    font-size: 0.95rem; padding: 9px 32px 9px 11px;
    appearance: none; cursor: pointer;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='6'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%238a6f35'/%3E%3C/svg%3E");
    background-repeat: no-repeat; background-position: right 10px center;
    transition: border-color .2s;
  }
  select:focus { outline: none; border-color: var(--gold); }

  .lines-wrap { grid-column: 1 / -1; display: flex; align-items: center; gap: 16px; }
  .lines-label {
    font-family: 'Courier Prime', monospace; font-size: 9.5px;
    letter-spacing: 0.32em; text-transform: uppercase; color: var(--gold-dim); white-space: nowrap;
  }
  input[type=range] {
    flex: 1; appearance: none; height: 1.5px;
    background: rgba(201,168,76,0.18); border-radius: 1px; cursor: pointer;
  }
  input[type=range]::-webkit-slider-thumb {
    appearance: none; width: 13px; height: 13px; border-radius: 50%;
    background: var(--gold); border: 2px solid var(--leather);
    cursor: pointer; transition: transform .15s;
  }
  input[type=range]::-webkit-slider-thumb:hover { transform: scale(1.2); }
  .lines-num {
    font-family: 'Playfair Display', serif; font-size: 1.5rem;
    color: var(--gold); min-width: 24px; text-align: center;
  }

  /* ── BUTTON ── */
  .btn-wrap { text-align: center; margin-top: 6px; }
  #btn-compose {
    font-family: 'Playfair Display', serif; font-size: 1rem;
    letter-spacing: 0.09em; color: #1a1208;
    background: linear-gradient(160deg, #e0c060 0%, var(--gold) 40%, #b8903a 100%);
    border: none; padding: 13px 52px; border-radius: 1px; cursor: pointer;
    box-shadow: 0 2px 24px rgba(201,168,76,0.28);
    transition: box-shadow .2s, transform .15s; position: relative;
  }
  #btn-compose::after {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(to bottom, rgba(255,255,255,0.12), transparent);
    border-radius: 1px; pointer-events: none;
  }
  #btn-compose:hover:not(:disabled) { box-shadow: 0 4px 36px rgba(201,168,76,0.48); transform: translateY(-1px); }
  #btn-compose:active:not(:disabled) { transform: translateY(0); }
  #btn-compose:disabled { opacity: 0.45; cursor: not-allowed; }

  /* ── BOOT / LOADING ── */
  #boot-msg {
    text-align: center; padding: 10px;
    font-family: 'Courier Prime', monospace; font-size: 10px;
    letter-spacing: 0.22em; color: rgba(138,111,53,0.55); text-transform: uppercase;
    animation: pulse 1.8s ease-in-out infinite;
  }
  #boot-msg.hidden { display: none; }
  @keyframes pulse { 0%,100%{opacity:.4} 50%{opacity:1} }

  /* ── OUTPUT ── */
  .output-shell {
    background: var(--mahogany); border: 0.5px solid rgba(201,168,76,0.18);
    border-radius: 2px; padding: 52px 60px; min-height: 200px;
    display: flex; flex-direction: column; justify-content: center;
    box-shadow: inset 0 2px 40px rgba(0,0,0,0.45);
    position: relative; overflow: hidden;
  }
  @media(max-width:580px) { .output-shell { padding: 36px 24px; } }
  .output-shell::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(to right, transparent, rgba(201,168,76,0.35), transparent);
  }
  .corner { position: absolute; width: 16px; height: 16px; border-color: rgba(201,168,76,0.3); border-style: solid; }
  .tl { top:10px; left:10px;   border-width: 1px 0 0 1px; }
  .tr { top:10px; right:10px;  border-width: 1px 1px 0 0; }
  .bl { bottom:10px; left:10px;  border-width: 0 0 1px 1px; }
  .br { bottom:10px; right:10px; border-width: 0 1px 1px 0; }

  #poem-placeholder {
    font-family: 'EB Garamond', serif; font-style: italic;
    font-size: 1.05rem; color: rgba(122,106,90,0.5);
    text-align: center; line-height: 1.9;
  }
  #poem-output {
    font-family: 'EB Garamond', serif; font-size: 1.28rem;
    line-height: 2.05; color: var(--parchment);
    white-space: pre-wrap; display: none;
  }
  #poem-output.show { display: block; animation: reveal .65s ease; }
  @keyframes reveal {
    from { opacity: 0; transform: translateY(8px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── FOOTER ── */
  .output-foot {
    display: flex; justify-content: space-between;
    align-items: center; margin-top: 12px; padding: 0 2px;
  }
  #poem-meta {
    font-family: 'Courier Prime', monospace; font-size: 9.5px;
    color: rgba(122,106,90,0.5); letter-spacing: 0.2em; text-transform: uppercase;
  }
  #btn-copy {
    font-family: 'Courier Prime', monospace; font-size: 9.5px;
    letter-spacing: 0.2em; text-transform: uppercase;
    color: var(--gold-dim); background: none;
    border: 0.5px solid rgba(201,168,76,0.22);
    padding: 5px 14px; border-radius: 1px; cursor: pointer;
    display: none; transition: color .2s, border-color .2s;
  }
  #btn-copy:hover { color: var(--gold); border-color: var(--gold); }

  .colophon {
    text-align: center; margin-top: 52px;
    padding-top: 28px; border-top: 0.5px solid rgba(201,168,76,0.12);
  }
  .colophon p {
    font-family: 'Courier Prime', monospace; font-size: 9px;
    letter-spacing: 0.28em; color: rgba(122,106,90,0.38); text-transform: uppercase;
  }

  py-terminal { display: none !important; }
</style>
</head>
<body>

<div class="page">

  <header class="masthead">
    <span class="masthead-candle">🕯</span>
    <p class="masthead-eyebrow">AP CSP · Performance Task</p>
    <h1>The <em>Verse</em> Engine</h1>
    <p class="masthead-sub">A poem generator for the wandering mind</p>
  </header>

  <div class="ornament"><span>❧ ❧ ❧</span></div>

  <div class="panel">
    <span class="panel-cap">✦</span>
    <div class="grid-3">

      <div class="field">
        <label for="theme">Theme</label>
        <select id="theme">
          <option value="nature">Nature</option>
          <option value="city">City</option>
          <option value="space">Space</option>
          <option value="ocean">Ocean</option>
          <option value="time">Time</option>
        </select>
      </div>

      <div class="field">
        <label for="mood">Mood</label>
        <select id="mood">
          <option value="melancholy">Melancholy</option>
          <option value="joyful">Joyful</option>
          <option value="tense">Tense</option>
          <option value="dreamy">Dreamy</option>
          <option value="angry">Angry</option>
        </select>
      </div>

      <div class="field">
        <label for="structure">Structure</label>
        <select id="structure">
          <option value="freeverse">Free Verse</option>
          <option value="haiku">Haiku</option>
          <option value="couplets">Couplets</option>
          <option value="anaphora">Anaphora</option>
        </select>
      </div>

      <div class="lines-wrap" id="lines-wrap">
        <span class="lines-label">Lines</span>
        <input type="range" id="lines" min="3" max="12" value="6">
        <span class="lines-num" id="lines-num">6</span>
      </div>

    </div>
    <div class="btn-wrap">
      <button id="btn-compose" disabled>Loading Python…</button>
    </div>
  </div>

  <p id="boot-msg">Initialising Python runtime…</p>

  <div class="output-shell">
    <span class="corner tl"></span><span class="corner tr"></span>
    <span class="corner bl"></span><span class="corner br"></span>
    <p id="poem-placeholder">Select your theme and mood above,<br>then let the engine speak.</p>
    <div id="poem-output"></div>
  </div>

  <div class="output-foot">
    <span id="poem-meta"></span>
    <button id="btn-copy">Copy verse</button>
  </div>

  <div class="colophon">
    <p>Powered by PyScript · Python running natively in your browser · Every verse is unique</p>
  </div>

</div>

<script type="py">
# =============================================================================
# THE VERSE ENGINE — AP CSP Create Performance Task
# Student-developed program code
# =============================================================================
# PROGRAM PURPOSE:
#   This program generates original poems based on user-selected theme, mood,
#   structure, and line count. The user interacts through dropdown menus and
#   a slider (USER INPUT), and the finished poem is displayed on screen (OUTPUT).
# =============================================================================

import random
from pyscript import document
from pyodide.ffi import create_proxy


# =============================================================================
# SECTION 1 — DATA (Lists used as collections to manage program complexity)
# =============================================================================
# WORD_BANKS is a dictionary whose values are LISTS of strings.
# Using lists here manages complexity: instead of hundreds of individual
# variables, one organised structure holds all vocabulary for every theme.
# The program indexes into these lists throughout poem generation.
# =============================================================================

WORD_BANKS = {
    # Each theme maps to a dict of three lists: nouns, verbs, adjectives.
    "nature": {
        "nouns":      ["forest", "petal", "root", "branch", "fog",
                       "dusk", "thorn", "seed", "ash", "bloom"],
        "verbs":      ["withers", "breathes", "falls", "rises", "fades",
                       "clings", "sways", "grows", "sleeps", "drifts"],
        "adjectives": ["hollow", "silent", "brittle", "wild", "pale",
                       "deep", "bare", "soft", "dim", "alive"]
    },
    "city": {
        "nouns":      ["neon", "alley", "rooftop", "window", "concrete",
                       "wire", "shadow", "crowd", "signal", "smoke"],
        "verbs":      ["flickers", "rushes", "echoes", "breaks", "burns",
                       "hums", "bleeds", "scatters", "presses", "lingers"],
        "adjectives": ["loud", "grey", "sharp", "crowded", "cold",
                       "rusted", "bright", "faceless", "urgent", "worn"]
    },
    "space": {
        "nouns":      ["nebula", "void", "orbit", "dust", "signal",
                       "horizon", "gravity", "star", "silence", "pulse"],
        "verbs":      ["collapses", "expands", "drifts", "ignites", "fades",
                       "bends", "reaches", "fractures", "spins", "vanishes"],
        "adjectives": ["infinite", "cold", "ancient", "burning", "dark",
                       "luminous", "vast", "hollow", "suspended", "quiet"]
    },
    "ocean": {
        "nouns":      ["current", "tide", "wreck", "depth", "salt",
                       "shore", "wave", "kelp", "abyss", "pearl"],
        "verbs":      ["pulls", "crashes", "rises", "sinks", "swells",
                       "erodes", "surrenders", "churns", "whispers", "carries"],
        "adjectives": ["restless", "deep", "grey", "boundless", "cold",
                       "soft", "heavy", "dark", "foaming", "still"]
    },
    "time": {
        "nouns":      ["clock", "dust", "echo", "moment", "scar",
                       "thread", "memory", "hour", "ghost", "rust"],
        "verbs":      ["passes", "returns", "unravels", "settles", "forgets",
                       "remains", "breaks", "repeats", "lingers", "dissolves"],
        "adjectives": ["fleeting", "old", "faded", "endless", "brittle",
                       "quiet", "lost", "worn", "bitter", "slow"]
    }
}

# MOOD_ADVERBS — list of adverbs matched to each mood.
# Stored as a list so the program can randomly select from them,
# giving each generated poem a different emotional texture.
MOOD_ADVERBS = {
    "melancholy": ["quietly", "slowly", "gently", "softly", "barely"],
    "joyful":     ["brightly", "freely", "warmly", "lightly", "easily"],
    "tense":      ["sharply", "suddenly", "tightly", "quickly", "fiercely"],
    "dreamy":     ["distantly", "softly", "hazily", "slowly", "endlessly"],
    "angry":      ["fiercely", "harshly", "blindly", "deeply", "heavily"]
}

# MOOD_OPENERS — list of opening phrases per mood.
# The first line of every poem is chosen from this list,
# ensuring the poem opens with the correct emotional register.
MOOD_OPENERS = {
    "melancholy": ["Even now,", "Somewhere,", "In the end,", "Once,", "Still,", "Perhaps,"],
    "joyful":     ["Look —", "Here,", "Yes,", "Today,", "Now,", "Again,"],
    "tense":      ["Wait —", "Not yet.", "Listen:", "Careful —", "Already,", "Too late,"],
    "dreamy":     ["Maybe", "Somewhere between", "If only", "As if", "Like a", "Half-remembered,"],
    "angry":      ["No more —", "Tell me:", "How long", "Still —", "Even now", "Don't say"]
}

# ANAPHORA_ANCHORS — list of repeating anchor phrases for the anaphora structure.
# Each line in an anaphora poem starts with the next item from this list,
# cycling through it with the modulo operator inside the loop.
ANAPHORA_ANCHORS = ["I remember", "There is", "We carry", "It was", "You left", "I find"]


# =============================================================================
# SECTION 2 — STUDENT-DEVELOPED PROCEDURE
# =============================================================================
# PROCEDURE NAME : generate_poem
# PARAMETERS     : theme     (str) — which word bank to draw from
#                  mood      (str) — which adverbs/openers to use
#                  num_lines (int) — how many lines to produce
# RETURN VALUE   : a single string containing the finished poem
#
# This procedure contains the three required algorithmic components:
#   • SEQUENCING  — statements execute top-to-bottom in a defined order
#   • SELECTION   — if/elif/else decides which line template to apply
#   • ITERATION   — for-loop repeats the line-building process num_lines times
# =============================================================================

def generate_poem(theme, mood, num_lines):
    """
    Build and return a free-verse poem as a multi-line string.

    Parameters
    ----------
    theme     : str  — one of "nature", "city", "space", "ocean", "time"
    mood      : str  — one of "melancholy", "joyful", "tense", "dreamy", "angry"
    num_lines : int  — number of lines to generate (3–12, chosen by user slider)

    Returns
    -------
    str  — the complete poem with lines joined by newline characters
    """

    # ------------------------------------------------------------------
    # SEQUENCING (step 1 of 4): Look up the correct word lists.
    # These two statements must run before the loop — they set up the
    # data that every iteration will pull words from.
    # ------------------------------------------------------------------
    bank    = WORD_BANKS[theme]      # dict containing three lists: nouns, verbs, adjectives
    adverbs = MOOD_ADVERBS[mood]     # list of adverbs that match the selected mood

    # ------------------------------------------------------------------
    # SEQUENCING (step 2 of 4): Choose one opening phrase for line 0.
    # random.choice picks one element at random from the list.
    # ------------------------------------------------------------------
    opener = random.choice(MOOD_OPENERS[mood])

    # ------------------------------------------------------------------
    # SEQUENCING (step 3 of 4): Initialise the output list.
    # 'poem_lines' is a LIST that stores each generated line (string).
    # Using a list manages program complexity: rather than building a
    # single giant string by concatenation, we collect lines individually
    # and join them at the end. This also lets us inspect or modify any
    # individual line by index if needed.
    # ------------------------------------------------------------------
    poem_lines = []    # LIST — will hold one string per poem line

    # ------------------------------------------------------------------
    # ITERATION: Repeat the line-building block num_lines times.
    # 'i' tracks which line we are currently writing (0-indexed).
    # Without this loop the procedure could only ever produce one line,
    # so iteration is essential to the program's purpose.
    # ------------------------------------------------------------------
    for i in range(num_lines):

        # Randomly sample one word from each vocabulary list.
        # These four statements are SEQUENCED — each must complete
        # before the next assignment can use its own random draw.
        noun  = random.choice(bank["nouns"])        # one noun  from the theme's noun  list
        verb  = random.choice(bank["verbs"])        # one verb  from the theme's verb  list
        adj   = random.choice(bank["adjectives"])   # one adj   from the theme's adj   list
        adv   = random.choice(adverbs)              # one adverb from the mood's adverb list
        noun2 = random.choice(bank["nouns"])        # second noun for variety in mid-line templates

        # --------------------------------------------------------------
        # SELECTION: Choose the correct line template based on position.
        #
        #   Branch 1 (if)   — first line  (i == 0)
        #                     Uses the mood opener so the poem begins
        #                     with the right emotional register.
        #
        #   Branch 2 (elif) — last line   (i == num_lines - 1)
        #                     Ends with a period to close the poem.
        #
        #   Branch 3 (else) — every middle line
        #                     Picks randomly from five templates so the
        #                     interior of the poem stays varied.
        #
        # Only one branch executes per iteration — that is what makes
        # this a selection (decision) rather than sequencing.
        # --------------------------------------------------------------

        if i == 0:
            # SELECTION — Branch 1: opening line with mood-specific opener
            line = f"{opener} the {adj} {noun} {verb} {adv}"

        elif i == num_lines - 1:
            # SELECTION — Branch 2: closing line ends the poem with a full stop
            line = f"and the {adj} {noun} {verb}."

        else:
            # SELECTION — Branch 3: middle lines vary across five templates
            middle_templates = [
                f"the {adj} {noun} {verb} {adv}",
                f"{adv}, the {noun} {verb}",
                f"a {adj} {noun} and a {noun2}",
                f"{noun} {verb} like {adj} {noun2}",
                f"the {noun} that {verb} {adv}"
            ]
            line = random.choice(middle_templates)   # randomly pick one template

        # --------------------------------------------------------------
        # SEQUENCING (step 4 of 4, inside loop):
        # Append the finished line to the output list.
        # This must come after the selection block so that 'line' is
        # fully built before it is stored.
        # --------------------------------------------------------------
        poem_lines.append(line)    # add this line to the LIST

    # After all iterations: join every element of the list with newlines
    # and return the complete poem string to the caller.
    return "\n".join(poem_lines)


# =============================================================================
# SECTION 3 — SUPPORTING PROCEDURES
# (also student-developed; each calls the same list-based word banks above)
# =============================================================================

def generate_haiku(theme, mood):
    """
    Return a three-line haiku string.
    Parameters: theme (str), mood (str)
    Returns   : str
    """
    bank    = WORD_BANKS[theme]           # SELECTION — pick correct word bank list
    adverbs = MOOD_ADVERBS[mood]          # SELECTION — pick correct mood adverb list

    # Build exactly three lines as a list, then join — same list pattern as above
    haiku_lines = [
        f"{random.choice(bank['adjectives'])} {random.choice(bank['nouns'])} drifts",
        f"{random.choice(adverbs)}, the {random.choice(bank['nouns'])} {random.choice(bank['verbs'])}",
        f"only {random.choice(bank['nouns'])} remains"
    ]
    return "\n".join(haiku_lines)    # return the joined string


def generate_couplets(theme, mood, num_lines):
    """
    Return a poem arranged in rhyming-style couplets (blank line every two lines).
    Parameters: theme (str), mood (str), num_lines (int)
    Returns   : str
    """
    bank    = WORD_BANKS[theme]
    adverbs = MOOD_ADVERBS[mood]
    couplet_lines = []    # LIST — collects each line and blank-line separator

    # ITERATION — build num_lines lines, inserting a blank line after every pair
    for i in range(num_lines):
        noun = random.choice(bank["nouns"])
        verb = random.choice(bank["verbs"])
        adj  = random.choice(bank["adjectives"])
        adv  = random.choice(adverbs)
        couplet_lines.append(f"the {adj} {noun} {verb} {adv}")

        # SELECTION — insert blank line after even-indexed lines (every couplet)
        # but not after the very last line
        if i % 2 == 1 and i != num_lines - 1:
            couplet_lines.append("")    # blank line separates couplet pairs

    return "\n".join(couplet_lines)


def generate_anaphora(theme, mood, num_lines):
    """
    Return a poem where each line starts with a repeating anchor phrase.
    Parameters: theme (str), mood (str), num_lines (int)
    Returns   : str
    """
    bank           = WORD_BANKS[theme]
    anaphora_lines = []    # LIST — stores each anaphora line

    # ITERATION — build num_lines lines, cycling through ANAPHORA_ANCHORS list
    for i in range(num_lines):
        # SELECTION — cycle through the ANAPHORA_ANCHORS list using modulo
        # so we never go out of bounds, regardless of num_lines
        anchor = ANAPHORA_ANCHORS[i % len(ANAPHORA_ANCHORS)]
        adj    = random.choice(bank["adjectives"])
        noun   = random.choice(bank["nouns"])
        anaphora_lines.append(f"{anchor} the {adj} {noun}")

    return "\n".join(anaphora_lines)


# =============================================================================
# SECTION 4 — USER INPUT & OUTPUT
# =============================================================================
# INPUT  : The user clicks "Compose a Verse" after choosing theme, mood,
#          structure, and line count from the HTML controls. The on_compose
#          function reads those selections with getElementById().
#
# OUTPUT : The finished poem string is written to the #poem-output element,
#          making it visible on the page (visual output to the user).
# =============================================================================

def on_compose(event):
    """
    Event handler — called when the user clicks the Compose button (USER INPUT).
    Reads all four user selections, calls the appropriate student-developed
    procedure, then writes the result to the page (OUTPUT).
    """

    # ── READ USER INPUT ──────────────────────────────────────────────
    # Each getElementById call reads a value the user chose from a
    # dropdown or slider — this is the program's primary input source.
    theme     = document.getElementById("theme").value       # user-selected theme
    mood      = document.getElementById("mood").value        # user-selected mood
    structure = document.getElementById("structure").value   # user-selected structure
    num_lines = int(document.getElementById("lines").value)  # user-selected line count (slider)

    # ── SELECTION: call the right procedure based on structure choice ─
    # Each branch calls a different student-developed procedure and
    # stores the returned poem string in the local variable 'poem'.
    if structure == "haiku":
        poem      = generate_haiku(theme, mood)    # CALL to student-developed procedure
        num_lines = 3                              # haiku is always exactly 3 lines

    elif structure == "couplets":
        poem = generate_couplets(theme, mood, num_lines)    # CALL to student-developed procedure

    elif structure == "anaphora":
        poem = generate_anaphora(theme, mood, num_lines)    # CALL to student-developed procedure

    else:
        # Default: free verse — CALL to the primary student-developed procedure
        poem = generate_poem(theme, mood, num_lines)        # CALL to student-developed procedure

    # ── WRITE OUTPUT ─────────────────────────────────────────────────
    # Display the generated poem string to the user (VISUAL OUTPUT).
    # The poem variable — returned by generate_poem — is placed directly
    # into the DOM so the user can read it on screen.
    out = document.getElementById("poem-output")
    out.textContent = poem          # OUTPUT: write poem text to the page
    out.className   = ""
    out.className   = "show"        # trigger CSS reveal animation

    # Hide the placeholder and show the metadata + copy button
    document.getElementById("poem-placeholder").style.display = "none"
    document.getElementById("poem-meta").textContent = (
        f"{theme}  ·  {mood}  ·  {structure}  ·  {num_lines} lines"
    )
    document.getElementById("btn-copy").style.display = "inline-block"


# =============================================================================
# SECTION 5 — RUNTIME SETUP
# Bind the button click to on_compose and signal that Python is ready.
# =============================================================================

btn = document.getElementById("btn-compose")
btn.addEventListener("click", create_proxy(on_compose))   # wire button → handler
btn.disabled    = False
btn.textContent = "Compose a Verse"
document.getElementById("boot-msg").className = "hidden"
</script>

<!-- JS — UI-only helpers, no Python logic -->
<script>
  // Update the displayed line count as the slider moves
  document.getElementById("lines").addEventListener("input", function () {
    document.getElementById("lines-num").textContent = this.value;
  });

  // Disable the lines slider when haiku is selected (haiku is always 3 lines)
  document.getElementById("structure").addEventListener("change", function () {
    const wrap    = document.getElementById("lines-wrap");
    const isHaiku = this.value === "haiku";
    wrap.style.opacity       = isHaiku ? "0.3" : "1";
    wrap.style.pointerEvents = isHaiku ? "none" : "auto";
  });

  // Copy the poem text to the clipboard
  document.getElementById("btn-copy").addEventListener("click", function () {
    const text = document.getElementById("poem-output").textContent;
    navigator.clipboard.writeText(text).then(() => {
      this.textContent = "Copied ✓";
      this.style.color = "var(--gold)";
      setTimeout(() => { this.textContent = "Copy verse"; this.style.color = ""; }, 1800);
    });
  });
</script>

</body>
</html>