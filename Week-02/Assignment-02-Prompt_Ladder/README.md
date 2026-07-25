# Prompt Ladder Assignment

## Introduction

### Prompt Engineering
Prompt engineering is the skill of designing, testing, and refining prompts to help an AI produce more accurate, relevant, and useful responses for a specific task. It involves improving prompts by adding clear goals, context, audience, constraints, examples, or formatting instructions.

### Prompt Ladder
A prompt ladder is a step-by-step method for improving a prompt by making one intentional change at a time. After each change, the AI's output is compared with the previous version to understand which prompt engineering technique improved the response and why.

---

# Objective

The objective of this assignment is to improve a weak prompt through five iterations by adding one prompt engineering layer at a time. After each iteration, I compared the output with the previous version to understand how each prompt change  affected the AI's response.

---

# Baseline

## Prompt

```text
Write a case study for my portfolio.
```

## Representative Output

> Paste a representative excerpt from Claude's response.
I'd love to help. A few quick things will help me write something that actually fits your work:

OR

```md
![Baseline Output](images/baseline.png)
```

---

# Version 1

### Layer Added
**Real Context (Project Name)**

## Prompt

```text
My project is kisan AI
```

## Representative Output

There are several different "Kisan AI" projects out there, so I can't tell which one is yours — and a case study needs specifics (problem, your role, approach, and results) to feel real rather than generic. Could you fill me in on a few things?
1. **What does your Kisan AI actually do?** (e.g., crop disease detection, weather-based alerts, market price info, chatbot for farmers, irrigation monitoring, etc.)
2. **What was your role?** (designer, developer, PM, solo builder?)
3. **What problem were you solving**, and for what tech stack / platform (mobile app, web app, hackathon project)?
4. **Any results or outcomes** — users, accuracy numbers, awards, feedback — even rough estimates?
If you give me even a short paragraph or bullet points on these, I'll turn it into a polished case study.

OR

```md
![Version 1](images/version1.png)
```

### Comparison with Baseline

#### What changed in the prompt?

I told Claude the name of my project (Kisan AI).

#### What actually improved in the output?

Claude started asking questions specific to my project instead of asking only general questions.

#### What still failed?

Claude still did not understand what my project actually does.

#### What would you try next?

I would explain what the project is and what features it has.

---

# Version 2

### Layer Added
**Project Context**

## Prompt

```text
I build kisan AI that helps farmer to diagnose disease of plants,field advice,kisan chatbot
```

## Representative Output

A few more quick details and I can write a strong case study:

OR

```md
![Version 2](images/version2.png)
```

### Comparison with Version 1

#### What changed in the prompt?

I explained what my project is and described its main features.

#### What actually improved in the output?

Claude understood my project better and started asking more relevant questions to build a stronger case study.

#### What still failed?

Claude still did not know the project's outcome or whether I built it solo or with a team.

#### What would you try next?

I would tell Claude that I built the project solo and that it won first place in a regional hackathon.

---

# Version 3

### Layer Added
**Project Outcome & Role**

## Prompt

```text
i made it solo and it won the first position at hackathon  regional level
```

## Representative Output

> Paste a representative excerpt.
>
# Kisan AI: Helping Farmers Diagnose Crop Disease with AI

**Role:** Solo Builder (Design + Development)
**Type:** Hackathon Project — 🥇 1st Place, Regional Round
**Timeline:** [add duration, e.g. "48-hour hackathon" or "3 weeks"]

## Overview

Kisan AI is an AI-powered assistant built to help farmers identify plant diseases early, get personalized field advice, and get quick answers to their farming questions through a chatbot — all in one tool. I designed and built the entire product solo, and it went on to win first place at the regional hackathon.

*[Add a screenshot or GIF of the app here once you have visuals ready]*

## The Problem

Smallholder farmers often lose a significant share of their crop yield to diseases that go undetected until it's too late — usually because:

- Agricultural experts aren't accessible or affordable for most farmers, especially in rural areas
- Diagnosing plant disease by eye requires expertise most farmers don't have
- Generic farming advice online isn't localized to their specific crop, soil, or season
- Existing tools are either too complex, too expensive, or not built for low-connectivity, low-literacy users

I wanted to build something a farmer could point a phone camera at a sick plant and get a real, useful answer back — in minutes, not days.

---


OR

```md
![Version 3](images/version3.png)
```

### Comparison with Version 2

#### What changed in the prompt?

I added that I built the project solo and that it won first place in the regional hackathon.

#### What actually improved in the output?

Claude stopped asking questions about my project and started writing the actual case study.

#### What still failed?

The Tech Stack section was incomplete because I had not provided that information.

#### What would you try next?

I would provide the technologies and APIs used to build the project.

---

# Version 4

### Layer Added
**Technical Context**

## Prompt

```text
i  used html,css,js and MERN and grok api  for LLM acessss
```

## Representative Output


## My Process

**1. Research & Problem Framing**

**2. Design**
I designed the interface to be simple and visual-first, since many users would be more comfortable with images and voice/chat than dense text — minimizing steps between "problem" and "answer."

**3. Building the AI Pipeline**
I integrated the Grok API to power the intelligence layer of the app — from interpreting plant/leaf images for disease diagnosis, to generating tailored field advice, to driving natural, conversational responses in the Kisan chatbot. Using a single LLM API across all three features let me move fast as a solo builder while keeping the experience consistent.

**4. Iteration Under Time Pressure**
Building solo for a hackathon meant prioritizing ruthlessly — I focused on making the three core flows (diagnose → advise → chat) work reliably end-to-end rather than spreading effort across extra features.

---

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript
- **Backend / Stack:** MERN (MongoDB, Express, React, Node.js)
- **AI / LLM:** Grok API — powering disease diagnosis reasoning, field advice generation, and the Kisan chatbot


OR

```md
![Version 4](images/version4.png)
```

### Comparison with Version 3

#### What changed in the prompt?

I added the tech stack and the API used in the project.

#### What actually improved in the output?

Claude included the technologies in the case study, making it more complete and informative.

#### What still failed?

The case study was still not written for a specific audience.

#### What would you try next?

I would specify that the target audience is recruiters.

---

# Version 5

### Layer Added
**Defined Audience**

## Prompt

```text
the target audience for my portfolio is recruiters
```

## Representative Output

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript
- **Backend / Stack:** MERN (MongoDB, Express, React, Node.js)
- **AI / LLM:** Grok API — powering disease diagnosis reasoning, field advice generation, and the Kisan chatbot

## Outcome

- 🏆 **Won 1st place at the regional hackathon**, competing against [add number of teams if known]
- Built and shipped a working end-to-end prototype solo within the competition timeframe

## What I Learned

- Building solo forced me to make fast, decisive tradeoffs between scope and polish
- Supporting Urdu, Punjabi, Sindhi, and Pashto taught me how much accessibility matters for real adoption — a technically correct diagnosis is useless if the farmer can't understand the answer

---

### Comparison with Version 4

#### What changed in the prompt?

I specified that the target audience for my portfolio is recruiters.

#### What actually improved in the output?

Claude produced a case study that was more suitable for a recruiter reviewing my portfolio.

#### What still failed?

Although the output became more recruiter-focused, I still needed to review and verify some details before using it. The AI also left placeholders where information was missing.

#### What would you try next?

If I continued improving the prompt, I would add verification instructions so the AI clearly marks assumptions or missing information instead of making them.

---

# Final Best Prompt

```text
Write a case study for my portfolio,my project name is kisan AI-it helps the farmer to diagnose their plants disease,field advice and also has Kisan Madgar chatbot which ans the farmers questions.I built that project solo and that it won first place in the regional hackathon.The tech i used to build this project is HTML,CSS,JAVASCRIPT,MERN and Groq API key.The my target audience for my portfolio are Recruiters-that are hiring AI/ML Engineers.It should include these step in my project case study like what was the problem?and what decisions i take or what i did? and what outcomes from this project?.The case study should be professional,recruiter-focused highly. If any information missing use placeholder.
```

This final prompt combines the successful improvements from all previous versions and can be reused by someone else with similar project information.

---

# Reflection

### What I Learned

- Improving one prompt element at a time made it easy to identify which change had the biggest impact on the AI's response.
- Adding project context helped the AI understand the task and produce a complete case study.
- Specifying the audience made the content more suitable for recruiters.
- Providing technical details made the case study more complete.
- I also learned that AI responses should always be reviewed because the model can make assumptions or leave placeholders when information is missing.

---

