# 🦷 Smile Care Dental Clinic – AI Appointment Booking

## n8n Workflow with AI Voice Agent
An end-to-end AI-powered appointment booking system built using n8n, Retell AI Voice Agent, Google Gemini, Google Sheets, and Gmail.
This workflow automatically converts phone calls into confirmed appointments with zero manual intervention.

## 📘 Technical Documentation

Workflow File:smile care dental clinic 1.json

## 🔍 Overview
This workflow automates the appointment booking process for Smile Care Dental Clinic using an AI Voice Agent. It listens to patient calls, processes call transcripts, extracts structured appointment details, stores patient data in Google Sheets, and sends confirmation emails via Gmail.

## ⚡ Workflow Trigger
### Webhook – Smile Care Dental Clinic
• Node Type: n8n-nodes-base.webhook
• HTTP Method: POST
#### Purpose:
The webhook receives call event data from Retell once the AI voice call is completed.
#### Payload Includes:
•  Call transcript
•  Caller responses
•  Call metadata 
•  Retell signature

### 🤖 AI Processing Layer

### Google Gemini Chat Model

•  Node Type: lmChatGoogleGemini
•  Input: $json.body.call.transcript

#### Function:
Analyzes the full call transcript and provides reasoning support for accurate data extraction.


