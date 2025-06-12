# Sesame CSM Voice Assistant

A fully local voice assistant that combines real-time speech-to-text, on-device LLM reasoning, and expressive speech synthesis using the latest NLP and TTS advancements. Runs fully offline, with GPU acceleration and modular Docker-based architecture.

---

## Team Name: FitnessGram

**Members:**  
- Lwazi Mabota  
- Resis Cook  
- Zafar Ahmad  
- Jian Zhou

---

## Introduction

**Use Case:** An offline voice assistant for personal desktop use, enabling private, low-latency conversation using voice.

**Purpose:** Replace cloud-based voice assistants with a high-performance, fully local solution that supports real-time transcription, smart reasoning, and expressive speech feedback.

**Target Users:**  
- Privacy-focused users  
- Developers and engineers  
- AI voice UI researchers  

---

## Problem Statement & Objective

Existing voice assistants like Siri, Alexa, and Google Assistant rely on cloud APIs, posing privacy and latency risks. Our goal was to build a local-first assistant that:  
- Works without internet  
- Uses on-device LLMs for intelligent responses  
- Sounds human and emotionally expressive  
- Runs fast on modern consumer GPUs  

---

## Model Selection & Justification

### LLM: Llama 3.2 1B (Meta)
- Chosen for its speed, low VRAM use, and Hugging Face GGUF compatibility.
- Suitable for general-purpose conversations.

### ASR: distil-whisper large-v3.5
- Provides fast and accurate real-time transcription.
- Works well with conversational speech.

### TTS: Sesame CSM (senstella/csm-expressiva-1b)
- Emotionally expressive, context-aware speech synthesis.
- Turn-level prosody and expressive voice output.

---

## System Architecture

![System Architecture](docs/architecture_diagram.png)

### Components
- **Frontend (Tauri/React):** Desktop GUI with voice animations, history, and controls.
- **Backend (FastAPI):** Hosts the model pipeline.
- **Pipeline:**  
  - Mic Input → distil-whisper → Transcribed Text  
  - Transcribed Text → Llama 3.2 → Assistant Response  
  - Response → Sesame CSM → Audio Output  

---

## Live Demo

### Run Locally

#### Prerequisites
```bash
- Docker Desktop
- Rust & Cargo
- Node.js (v18+)
- NVIDIA GPU (CUDA 12.1+)
- Hugging Face token (for Llama 3.2 access)
