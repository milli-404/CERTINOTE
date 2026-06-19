# CERTINOTE
An ambient clinical scribe prototype that converts doctor-patient conversations into structured SOAP notes with a built-in safety layer.

The project goal is not just to generate a note, it verifies generated clinical claims against the original transcript, flags unsupported or missing details, assigns confidence levels, and suggests billing codes for human review. It focuses on trustworthy healthcare AI by making every note traceable, auditable, and uncertainty-aware.

## Core Workflow

Ingest a doctor-patient transcript or live text conversation.
Clean and normalize the conversation.
Extract patient-reported symptoms.
Match symptoms against transparent condition rules.
Return "insufficient evidence" when no full rule matches.
Generate a structured SOAP note.
Cross-check the note against the transcript.
Suggest demo billing concepts only when evidence exists.
Show confidence and uncertainty per section.

## Why This Matters
Most student healthcare AI demos stop at:
(Transcript -> AI-generated clinical note)

This project adds the production-minded layer:
(Transcript -> SOAP note -> evidence verification -> uncertainty flags -> human review)
That directly addresses trust, governance, and safety concerns in healthcare AI.

## MVP Features
Run a guided live patient intake from the terminal.
Generate a SOAP note with Subjective, Objective, Assessment, and Plan sections.
Verify each SOAP claim against transcript evidence.
Mark claims as supported, unsupported, contradicted, or uncertain.
Detect important transcript details missing from the generated note.
Suggest possible billing codes for review, never final billing decisions.
Display confidence labels for each SOAP section.
Capture a live text conversation from the terminal.
Match only patient or caregiver-reported symptoms, not clinician prompts.
## Safety Positioning
This is a portfolio and research prototype. It is not intended for clinical use.
No real patient data should be used.
Use synthetic, public, or properly de-identified transcripts only.
All generated medical content requires clinician review.
Billing suggestions are informational and require certified coder review.
The system should prefer "insufficient evidence" over guessing.
## Suggested Stack
Backend: Python, FastAPI, Pydantic
LLM orchestration: simple function pipeline first, LangGraph later if needed
Frontend: React or Next.js
Storage: SQLite for MVP
Evaluation: pytest plus JSON evaluation reports
Optional later: audio transcription with Whisper or a hosted ASR API

## Repository Structure

<img width="311" height="515" alt="Screenshot 2026-06-19 at 3 05 57 PM" src="https://github.com/user-attachments/assets/e34f8cf8-9b6a-45dc-b32c-1c6e8368867c" />

## Run The Web App
Start the local CERTINOTE web demo:
python3 scripts/serve_web.py --port 8000

Then open:
http://127.0.0.1:8000
