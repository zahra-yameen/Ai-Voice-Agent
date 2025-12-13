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

## 🤖 AI Processing Layer

### Google Gemini Chat Model

•  Node Type: lmChatGoogleGemini
•  Input: $json.body.call.transcript

#### Function:
Analyzes the full call transcript and provides reasoning support for accurate data extraction.

## AI Agent – Virtual Receptionist

•  Node Type: n8n-nodes-langchain.agent

### Responsibilities:

•  Extract patient details (name, phone, email, city, concern)

•  Confirm appointment date and time

•  Validate unclear inputs (email spelling, phone numbers)

•  Maintain a professional receptionist tone

### System Prompt Capabilities:

•  Structured data collection

•  Input validation

•  Appointment confirmation

•  Clean JSON-only output

## 🧩 Output Parsing

### Structured Output Parser

•  Node Type: outputParserStructured

### Schema Fields:

•  name

•  phone

•  email

•  city

•  concern

•  appointmentTime

•  confirmationMessage

This ensures the AI output is reliable, strictly structured, and ready for downstream automation.

## 📊 Data Storage Layer
### Google Sheets – Append Row

•  Operation: Append

•  Sheet Name: Dental Receptionist Log

### Captured Fields:

•  Full Name

•  Phone Number

•  City

•  Email Address

•  Appointment Time

•  Patient Concern

### Purpose:
Maintains a centralized appointment log for administrative and record-keeping use.

## 📧 Communication Layer
### Gmail – Send Confirmation Email

•  Node Type: n8n-nodes-base.gmail

### Email Includes:

•  Personalized greeting

•  Thank-you message

•  Appointment confirmation details

## 🔄 End-to-End Workflow Summary

1. Patient calls the AI receptionist

2. Retell sends the call transcript to n8n

3. Google Gemini analyzes the transcript

4. AI Agent extracts structured appointment data

5. Data is parsed into clean JSON

6. Appointment details are saved in Google Sheets

7. Confirmation email is sent to the patient

## 🧠 Workflow Diagram

      Retell AI Voice Agent  

              │
              ▼
           Webhook 
     
              │
              ▼
        Google Gemini
 
              │ 
              ▼
          AI Agent
   
              │
              ▼
      Structured Parser

              │
              │
              │
         ┌────┴─────┐
         ▼          ▼

Google Sheets      Gmail


## 🚀 Features

•  AI-powered voice receptionist

•  Automatic appointment extraction

•  Google Sheets integration

•  Gmail confirmation emails

•  Fully automated backend workflow

•  Real-time execution

## 📂 Included Files

•  smile care dental clinic 1.json – Complete n8n workflow

•  AI receptionist system prompt

•  Google Sheets mapping logic

•  Automated email template

## ⚙️ Requirements
### Accounts

•  n8n (Cloud or Self-hosted)

•  Retell AI

•  Google Cloud Project

•  Gmail

•  Google Sheets

### n8n Credentials

•  Google Gemini API Key

•  Google Sheets OAuth2

•  Gmail OAuth2

## 🛠 Setup Instructions

1. Import the workflow JSON into n8n

2. Configure the webhook URL in Retell

3. Add Google Sheets and Gmail credentials

4. Update Sheet ID and email template if required

5. Test the workflow using a phone call

## 📌 Use Cases

•  Dental Clinics

•  Medical Offices

•  Beauty & Wellness Clinics

•  Restaurants & Reservations

•  Service-Based Businesses

## 📜 License

This project is provided for educational and demonstration purposes.
You are free to modify and adapt it for personal or commercial use.

## 🙌 Contributing

Contributions and improvements are welcome.
Feel free to submit pull requests or open issues.

## 👩‍💻 Author

Zahra yameen

AI Automation Strategist

Designing intelligent AI-driven workflows to automate real-world business operations.


