---
layout: base
title: homework planner
permalink: /tri2finalblog/
---
# Media Literacy Chatbox
## College Board Create PT - Skill B Documentation

An AI-powered chatbox that helps students analyze news sources through interactive Q&A.

---

## INPUT: What the User Provides

The chatbox collects information from three input fields:

### 1. News Source Field
- User types the name of a news outlet (e.g., "CNN", "Fox News", "BBC")
- Optional field - chatbox works with or without it

### 2. Question   
- User writes their question about media bias or source credibility
- Required field - must have a question to get AI response

### 3. Voice Input
- User says what they want

### 4. Mode Selector (Dropdown)
- **"Hint" mode** - AI gives subtle guidance without direct answers
- **"Information" mode** - AI provides factual details about the source


**Code Example:**
```html
<textarea id="news-source" placeholder="Type a news source..."></textarea>
<textarea id="ai-message" placeholder="Ask a question..." required></textarea>
<select id="ai-mode">
    <option value="hint">Hint</option>
    <option value="information">Information</option>
</select>
```

---

## OUTPUT: What the User Sees

After clicking "Send", the chatbox displays three types of responses:

### 1. Chat Bubbles (Conversational Display)
- **User bubble** - Shows your question in a blue chat bubble
- **AI bubble** - Displays the AI's answer in a different colored bubble
- Auto-scrolls to newest message

### 2. Status Messages (Real-time Feedback)
- **"Processing..."** - While waiting for AI response
- **"Response received!"** - When answer arrives successfully  
- **Error messages** - If something goes wrong (red text)

### 3. Smart Prompt Buttons (Suggestions)
- Popular questions appear as clickable buttons
- Show live click counts (e.g., "42 clicks")
- Sorted by popularity - most clicked questions appear first

**Code Example:**
```javascript
// Create user's message bubble
const userBubble = document.createElement('div');
userBubble.textContent = `You: ${message}`;

// Create AI's response bubble
const aiBubble = document.createElement('div');
aiBubble.innerHTML = `<strong>Hint:</strong> ${data.answer}`;

// Add both to chat log
aiChatLog.appendChild(userBubble);
aiChatLog.appendChild(aiBubble);
```

---

## PROCEDURES: The 4 Main Functions

These functions handle different parts of the chatbox system.

---

### Function 1: `loadPromptClicks()`

**Purpose:** Gets click data from the server

**What it does:** Fetches how many times each prompt button has been clicked, then updates the local list

**Why it matters:** Keeps track of which questions are most popular with students

**Code:**
```javascript
async function loadPromptClicks() {
    const response = await fetch('/api/prompts/clicks');
    const data = await response.json();
    
    // Update each prompt with its click count
    promptsWithClicks = PROMPT_TEMPLATES.map(prompt => ({
        ...prompt,
        clicks: data[prompt.id] || 0
    }));
}
```

---

### Function 2: `renderSmartPrompts()`

**Purpose:** Displays the suggestion buttons

**What it does:** Sorts prompts by popularity (most clicked first), then creates clickable buttons with live counts

**Why it matters:** Shows students what questions other people are asking

**Code:**
```javascript
function renderSmartPrompts(source) {
    // Sort by popularity (highest clicks first)
    const sorted = prompts.sort((a, b) => b.clicks - a.clicks);
    
    // Create a button for each prompt
    sorted.forEach(prompt => {
        const btn = document.createElement('button');
        btn.innerHTML = `${prompt.text} <span>${prompt.clicks}</span>`;
        btn.addEventListener('click', () => handlePromptClick(prompt));
        grid.appendChild(btn);
    });
}
```

---

### Function 3: `handlePromptClick()`

**Purpose:** Handles when user clicks a suggestion button

**What it does:** 
1. Auto-fills the question into the textarea
2. Sends +1 click to the server
3. Updates the button's count

**Why it matters:** Tracks engagement and makes it easier for students to ask common questions

**Code:**
```javascript
async function handlePromptClick(prompt, source) {
    // Fill textarea with selected question
    aiMessageInput.value = prompt.text.replace('{source}', source);

    // Tell server this prompt was clicked
    const response = await fetch(`/api/prompts/${prompt.id}/click`, {
        method: 'POST'
    });
    
    // Update local click count
    const data = await response.json();
    prompt.clicks = data.clicks;
    renderSmartPrompts(source);
}
```

---

### Function 4: `showAIStatus()`

**Purpose:** Shows status messages to the user

**What it does:** Displays colored feedback messages (blue for info, red for errors)

**Why it matters:** Keeps students informed about what's happening

**Code:**
```javascript
function showAIStatus(message, isError = false) {
    aiStatusEl.textContent = message;
    
    // Color code: red for errors, blue for info
    if (isError) {
        aiStatusEl.style.color = '#fca5a5';  // Red
    } else {
        aiStatusEl.style.color = '#7ad2f9';  // Blue
    }
}
```

---

## LOGIC: Selection & Iteration

### Selection (Conditional Logic)

The code makes decisions based on conditions using IF statements.

**Examples:**

```javascript
// Check if user entered a message
if (!message) {
    showAIStatus('Please enter a message', true);
    return;
}

// Choose prompt based on mode
if (mode === 'hint') {
    // Send hint-style prompt
} else {
    // Send info-style prompt
}

// Handle errors
if (!response.ok) {
    throw new Error('Server error');
}
```

---

### Iteration (Loops)

The code uses loops to process multiple items.

**Creating Buttons:**
```javascript
// Go through each prompt and make a button
prompts.forEach(prompt => {
    const btn = document.createElement('button');
    btn.textContent = prompt.text;
    grid.appendChild(btn);
});
```

**Live Updates:**
```javascript
// Refresh click counts every 5 seconds
setInterval(refreshPromptsFromServer, 5000);
```

---

## DATA STRUCTURE: The Prompts List

### What It Is
An array (list) that stores prompt objects with their click counts.

### The Structure

**Template Definition:**
```javascript
const PROMPT_TEMPLATES = [
    { id: 1, text: "What is the political bias of {source}?" },
    { id: 2, text: "Show me recent top stories from {source}" },
    { id: 3, text: "How does {source} compare to other news outlets?" },
    // ... more prompts
];

let promptsWithClicks = [];  // Starts empty, filled by API
```

**What It Looks Like After Loading:**
```json
[
  { "id": 1, "text": "What is the political bias of {source}?", "clicks": 11 },
  { "id": 2, "text": "Show me recent top stories from {source}", "clicks": 34 },
  { "id": 3, "text": "How does {source} compare...", "clicks": 42 }
]
```

### Operations on the List

**SORT - Reorder by popularity**
```javascript
const sorted = prompts.sort((a, b) => b.clicks - a.clicks);
// Result: Highest clicks appear first
```

**FIND - Locate a specific prompt**
```javascript
const prompt = prompts.find(p => p.id === 3);
// Result: Gets the prompt with id 3
```

**MAP - Transform data**
```javascript
const updated = prompts.map(prompt => ({
    ...prompt,
    clicks: data[prompt.id] || 0
}));
// Result: Updates all click counts from API data
```

---

## BACKEND: 3rd Party APIs

### API 1: Google Gemini AI

**What it does:** Generates educational responses about news sources

**Why we use it:** Creates smart hints without revealing bias directly

**Backend Code:**
```python
# Generates AI responses based on mode
if msg_type == 'hint':
    prompt = "Provide a helpful hint (don't reveal bias)"
else:
    prompt = "Provide factual information (don't classify bias)"

model = genai.GenerativeModel('gemini-2.5-flash-lite')
response = model.generate_content(prompt)
```

---

### API 2: Prompt Analytics  

**What it does:** Tracks how many times each question is clicked

**Why we use it:** Shows students which questions are most popular

**Backend Code:**
```python
# Increment click count by 1
for prompt in prompts:
    if prompt['id'] == id:
        prompt['clicks'] += 1
        break
```

---

## College Board Requirements Checklist

| Requirement | Status | Implementation |
|-------------|--------|----------------|
| **INPUT** | ✓ | 3 input fields: source, question, mode selector |
| **OUTPUT** | ✓ | Chat bubbles, status messages, prompt buttons |
| **PROCEDURES** | ✓ | 4 functions: loadPromptClicks, renderSmartPrompts, handlePromptClick, showAIStatus |
| **SELECTION** | ✓ | IF statements for validation, mode selection, error handling |
| **ITERATION** | ✓ | forEach loops for buttons, setInterval for live updates |
| **LIST** | ✓ | promptsWithClicks array with .sort(), .find(), .map() |
| **3rd PARTY API** | ✓ | Google Gemini AI + custom analytics backend |

---

## Why This Matters

This chatbox helps students:
- Learn media literacy without getting direct answers
- See popular questions others are asking
- Get AI-powered guidance tailored to their interests
- Understand source credibility through hints and facts

The code demonstrates full-stack development with:
- Real-time API integration
- Dynamic data management
- User engagement tracking
- Educational AI application

---

**Code Location:** `mainmodule.md` (Lines 990-1220)  
**Backend Files:** `chat_api.py`, `prompt.py`