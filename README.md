# AI-Powered Discovery Engine 🔍🤖

An automated product analytics pipeline built using **n8n**, **Google Sheets**, and **Google Gemini (Gemini Flash/Lite)**. This workflow transforms unstructured user feedback regarding search and retrieval failures into structured, actionable telemetry for product development.

---

## 🚀 Overview
Modern search systems often fail due to nuance gaps (e.g., human memory vs. file metadata mismatches, compositional errors, or OCR degradation). This repository provides a fully automated **Discovery Engine** that ingests raw user friction logs, processes them via large language models using strict JSON schema enforcement, and logs categorized root causes directly into a tracking spreadsheet.

---

## 🛠️ Architecture & Data Flow
The workflow operates as a continuous, end-to-end pipeline:
1. **Trigger:** Manual execution or scheduled polling.
2. **Ingestion (`Google Sheets`):** Pulls raw, open-ended user feedback from live survey responses.
3. **AI Analysis (`Google Gemini`):** Parses the natural language text and extracts structured metadata.
4. **Export (`Google Sheets`):** Appends the categorized output back into a structured analysis sheet.

---

## 📋 Extracted JSON Schema
The LLM node enforces a strict JSON output containing the following keys:
* `intended_target`: What exact asset or photo the user was trying to retrieve.
* `memory_anchors`: The specific human memory cues or context available to the user.
* `system_failure_reason`: The underlying technical reason the retrieval failed.
* `root_cause_category`: Categorized into standardized failure modes (*Metadata/Episodic Mismatch*, *Compositional Query Failure*, *OCR/Text Degradation*, *Translation/Trust Deficit*).

---

## ⚙️ Setup & Installation
1. Import the provided workflow JSON file (`ai-discovery-engine.json`) into your local or cloud-hosted **n8n** instance.
2. Configure your **Google Sheets** credential (OAuth2) to connect your source survey and destination report sheets.
3. Configure your **Google Gemini** API credential.
4. Execute the workflow to begin automated analysis.
