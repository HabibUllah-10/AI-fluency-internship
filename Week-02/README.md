### Voice Card

When helping me write portfolio content, use a simple, conversational, friendly, and confident tone. Avoid buzzwords and keep the writing sounding like me.

---

### Case Study 1:(Kisan AI)

# Kisan AI — A Farming Assistant Built to Actually Help Farmers

**🏆 1st Place, Kirothon (Regional Hackathon) — Solo Project**

---

## The Problem

Farmers often don't have quick, easy access to plant disease diagnosis or reliable, localized farming advice. If a crop starts showing signs of disease, a farmer usually has to rely on guesswork, word of mouth, or wait to reach an expert — and by then, the damage is already spreading.

I wanted to build something a farmer could actually use in the field: take a photo, get an answer, get a remedy, and get advice — all in their own language.

## What I Did

I built Kisan AI as a solo project with three connected features:

**1. Plant Disease Detection from Photos**
A farmer uploads a photo of their plant, and I send that image to a vision-capable model through Groq's API to identify the likely disease. Once the disease is identified, I match it against my own remedy database to return a clear treatment recommendation — rather than letting the model freely generate treatment advice, which keeps the guidance consistent and controlled.

**2. Kisan Madadgar — A Farming Chatbot (Urdu, Punjabi, Sindhi, and Pashto)**
This is the part I'm most proud of. Farmers can ask questions in their own language — for example in Urdu, "گندم میں زنگ کا علاج بتائیں" (tell me the cure for wheat rust) — and get a real, useful answer. I built it to support four regional languages (Urdu, Punjabi, Sindhi, and Pashto), because a farming assistant only helps if farmers can actually talk to it comfortably. Instead of letting the model answer from general knowledge, I inject actual farming data directly into the prompt — fertilizer prices, disease treatments, dosages — so the model's answer is grounded in real, local information rather than something it's guessing at.

I want to be upfront about this: I initially thought of this as RAG (Retrieval-Augmented Generation), but when I looked closer at what I'd actually built, it wasn't. There's no embedding step and no vector database — the knowledge is added straight into the prompt, which is closer to prompt engineering / context injection. It's a smaller technical claim than RAG, but it's honest, and it works well for the size of my knowledge base.

**3. City-Level Disease Heatmap**
Every time a farmer uploads a photo and a disease is detected, I log it against their city. Using Leaflet (a JS mapping library), I built a live heatmap showing where a disease is spreading — strong, medium, or weak — based on how many reports have come in from each city. It gives a visual, real-time picture of outbreaks instead of a single farmer's isolated result.

*(One known limitation I'm upfront about: right now, "strong" just means more reports came from that city — it doesn't yet account for how many farmers are actually using the app there. A city with more active users will naturally show more reports. Normalizing by active users per city is the next improvement I'd make.)*

**4. Farm Health Score**
Beyond just diagnosing a single disease, I wanted to give farmers a broader picture of their plant's overall health. So alongside the photo, I ask the farmer a few quick questions — has the plant had disease before, what soil type they're using, what water source they rely on (well, canal, rainwater, etc.). I combine the photo diagnosis with these answers using a weighted formula I designed myself, and generate a score out of 100.

Alongside the score, I send the same inputs to the LLM to generate advice specifically around likely nutrient deficiencies — so the farmer doesn't just get a number, they get a reason and a next step. I deliberately used two different approaches here: the remedy lookup earlier uses a fixed database for consistency, while the nutrient advice uses the LLM because it needs to reason across multiple inputs rather than just match a single label.

## What Came Of It

I built and demoed the full working product — photo-based diagnosis, the Urdu,Punjabi,Sindhi and Pashto chatbot, and the live heatmap — solo, at Kirothon, a regional hackathon, and **won 1st place.**


---

### Case Study 2:(Code Mentor AI)

# Code Mentor AI — Building a Coding Assistant to Apply What I Was Learning

**Solo Project — Built while learning the Gemini API**

## The Problem

While learning generative AI and working through a Gemini API course, I didn't just want to follow along with tutorials — I wanted real hands-on experience actually building something with what I was learning. I picked a coding mentor/assistant because it's something I'd genuinely use myself: a tool that can explain coding concepts, write code, and catch errors in code you paste in, all through a simple chat.

## What I Did

I built Code Mentor AI as a chat-based assistant using the Gemini API, with three core capabilities:

**1. Explaining Coding Concepts**
The user can ask about any coding concept in free-text — like "explain recursion" — and the app sends the question to Gemini with a system prompt instructing it to act as a code mentor. It's a simple, open chat interface rather than a fixed set of topics or difficulty levels, which keeps it flexible for whatever the user wants to learn.

**2. Writing Code**
Same underlying setup — the user asks for code, and Gemini generates it directly in the chat.

**3. Error Checking with Real Code Execution**
This is the part I made sure to get technically right, rather than oversell: when a user pastes in code to check for errors, I use Gemini's built-in code execution capability to actually *run* the code — not just have the model read it and guess. This means the errors it flags come from actual execution, across many supported languages, not just the model's text-based reasoning.

I built the whole app using JavaScript.

## What Came Of It

This was a solo, self-directed project — built specifically to apply my Gen AI learning to something real rather than just following tutorial exercises. It's fully built and working: a chat-based mentor that explains concepts, writes code, and checks errors using real code execution through the Gemini API.

---

## About Me

I'm a 3rd-year Computer Science student, and I like building AI-powered tools that actually solve a real problem for real people — not just tech for the sake of tech. I built Code Mentor AI while learning the Gemini API, as a way to turn what I was studying into something genuinely useful. I'm currently looking for AI/ML Engineer opportunities where I can keep building practical, useful applications.

---

## Let's Talk

📧 Email: habiballamgir@gmail.com
💼 LinkedIn:https://www.linkedin.com/in/habibullah-ai
💻 GitHub: https://github.com/HabibUllah-10

---

## Before / After: Writing in My Own Voice

**Before (generic AI-sounding):**
"Kisan AI is an innovative, AI-powered farming assistant designed to revolutionize agricultural practices by leveraging cutting-edge machine learning and natural language processing to empower farmers with data-driven insights."

**After (edited, my voice):**
"Farmers often don't have quick, easy access to plant disease diagnosis or reliable, localized advice. With Kisan AI, a farmer can upload a photo to diagnose their plant's disease and get a remedy. A heatmap shows where a disease is strong, medium, or weak across different cities. There's also a health score card for the field, a Kisan Madadgar chatbot that answers the farmer's personal questions, and a farming advisor that gives next steps."

