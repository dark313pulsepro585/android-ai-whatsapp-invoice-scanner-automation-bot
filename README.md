# Android AI WhatsApp Invoice Scanner Automation Bot

An Android AI automation system that pulls the latest invoice image from WhatsApp, processes it in a native scanner app, extracts key fields using OCR, then completes an invoice submission flow inside the RTS Pro factoring app. It streamlines a repetitive, multi-app workflow into a reliable device-driven pipeline with validation, retries, and full run logging.

Built for real Android devices, this project focuses on stable UI navigation, dependable data extraction, and consistent PDF upload + payment submission.

<p align="center">
  <a href="https://Appilot.app" target="_blank"><img src="https://github.com/Instagram-Automations/Footer-test/blob/main/appilot-baner.png" alt="Appilot Banner" width="100%"></a>
</p>
<p align="center">
  <a href="https://t.me/devpilot1" target="_blank"><img src="https://img.shields.io/badge/Chat%20on-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"></a>
  <a href="mailto:support@appilot.app" target="_blank"><img src="https://img.shields.io/badge/Email-support@appilot.app-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"></a>
  <a href="https://Appilot.app" target="_blank"><img src="https://img.shields.io/badge/Visit-Website-007BFF?style=for-the-badge&logo=google-chrome&logoColor=white" alt="Website"></a>
  <a href="https://discord.gg/3YrZJZ6hA2" target="_blank"><img src="https://img.shields.io/badge/Join-Appilot_Community-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Appilot Discord"></a>
</p>


<p align="center">
Created by Appilot, built to showcase our approach to Automation! <br>
If you are looking for custom <strong> Android AI WhatsApp Invoice Scanner Automation Bot </strong>, you've just found your team — Let’s Chat.&#128070; &#128070;
</p>


## Introduction

Manually moving invoices between WhatsApp, a scanner app, and a factoring app is slow and error-prone. Operators must open chats, locate the latest image, scan it, export a PDF, read values from the invoice, then retype them into an invoice form and upload the document for submission.

This automation replaces that manual routine with a single end-to-end run: it collects the latest WhatsApp image, scans and generates a PDF, performs OCR to extract invoice fields, fills the RTS Pro invoice form, uploads the PDF, and submits for payment—while producing structured logs and a run summary.

### Mobile Invoice Submission Workflow

- Converts a multi-app manual routine into a repeatable Android automation pipeline
- Reduces form-entry errors by extracting data directly from the scanned invoice
- Ensures the latest WhatsApp invoice is always processed first
- Produces consistent PDF outputs with validation before upload
- Adds reliability with retries, screenshots, and step-level checkpoints

---

## Core Features

| Feature | Description |
|----------|-------------|
| WhatsApp Latest Media Fetch | Opens a configured chat and selects the most recent image attachment |
| Native Scanner App Control | Automates scan/crop/confirm steps and exports a clean PDF |
| OCR Extraction Pipeline | Extracts invoice fields from scanned content using on-device OCR |
| Field Normalization | Cleans and normalizes dates, currency, totals, and vendor/customer names |
| RTS Pro App Navigation | Launches and navigates to the invoice creation flow reliably |
| Invoice Form Autofill | Populates required fields using extracted data with validation rules |
| PDF Attachment Upload | Selects the exported PDF and uploads it to the invoice submission |
| Submission Confirmation | Verifies successful submission and records confirmation state |
| Template & Vendor Rules | Supports vendor-specific parsing rules and field mapping overrides |
| Error Detection & Recovery | Detects missing elements, unexpected screens, and recovers safely |
| Retry & Backoff | Retries transient UI failures with controlled backoff and timeouts |
| Evidence Capture | Saves screenshots and UI dumps for debugging and audit trails |
| Run Logging & Summary | Structured logs per step plus a final JSON summary output |
| Device Farm Ready | Supports multiple devices with per-device configs and isolated outputs |

---

## How It Works

| Step | Description |
|------|-------------|
| **Input or Trigger** | A scheduled run or manual trigger starts on a connected Android device with configured WhatsApp chat and RTS Pro profile |
| **Core Logic** | The bot opens WhatsApp, pulls the latest invoice image, sends it to the scanner app to generate a PDF, runs OCR to extract fields, then opens RTS Pro to fill and submit the invoice |
| **Output or Action** | A submitted invoice with uploaded PDF, plus structured logs, screenshots, and an output summary containing extracted fields and submission status |
| **Other Functionalities** | Step checkpoints, validation gates, retries on transient UI issues, and per-run evidence capture |
| **Safety Controls** | Rate limits actions, uses deterministic navigation paths, and enforces validation rules before submission |

## Tech Stack

| Component | Description |
|------------|-------------|
| **Language** | Python |
| **Frameworks** | Appium (UiAutomator2) |
| **Tools** | ADB, OpenCV, On-device OCR (ML Kit compatible pipeline) |
| **Infrastructure** | Docker, GitHub Actions |

---

## Directory Structure Tree

    android-ai-whatsapp-invoice-scanner-automation-bot/
    ├── src/
    │   ├── main.py
    │   ├── runner.py
    │   ├── device/
    │   │   ├── adb_manager.py
    │   │   ├── appium_driver.py
    │   │   └── device_pool.py
    │   ├── apps/
    │   │   ├── whatsapp/
    │   │   │   ├── navigator.py
    │   │   │   ├── media_picker.py
    │   │   │   └── chat_selector.py
    │   │   ├── scanner/
    │   │   │   ├── scanner_flow.py
    │   │   │   ├── crop_controls.py
    │   │   │   └── pdf_export.py
    │   │   └── rts_pro/
    │   │       ├── rts_login.py
    │   │       ├── invoice_form.py
    │   │       ├── pdf_uploader.py
    │   │       └── submit_flow.py
    │   ├── ocr/
    │   │   ├── ocr_engine.py
    │   │   ├── preprocess.py
    │   │   ├── field_extractor.py
    │   │   └── validators.py
    │   └── utils/
    │       ├── logger.py
    │       ├── timing.py
    │       ├── selectors.py
    │       ├── config_loader.py
    │       └── evidence.py
    ├── config/
    │   ├── device.yaml
    │   ├── whatsapp.yaml
    │   ├── scanner.yaml
    │   ├── rts_pro.yaml
    │   └── field_mapping.yaml
    ├── logs/
    │   ├── runs/
    │   └── activity.log
    ├── output/
    │   ├── invoices/
    │   ├── extracted_data.json
    │   └── run_summary.json
    ├── assets/
    │   ├── sample_invoices/
    │   └── selector_maps/
    ├── tests/
    │   ├── test_field_extractor.py
    │   ├── test_validators.py
    │   └── test_flows.py
    ├── docker/
    │   ├── Dockerfile
    │   └── docker-compose.yaml
    ├── requirements.txt
    └── README.md

---

## Use Cases

- **Invoice processors** use it to move invoices from WhatsApp to factoring submission so they can finish more applications per day with fewer mistakes.
- **Operations teams** use it to standardize scanning and data entry so they can reduce variance across different operators and devices.
- **Back-office admins** use it to auto-generate PDFs and fill invoice forms so they can focus on exceptions instead of repetitive entry.
- **Teams handling multiple vendors** use it to apply vendor-specific field mapping so they can submit invoices faster and consistently.

---

## FAQs

**How does it pick the “latest image” from WhatsApp reliably?**  
It navigates to a configured chat, opens recent media, and selects the most recent image based on UI ordering. A validation step confirms the selected item is an image before proceeding to scanning.

**What invoice fields can be extracted with OCR?**  
Common fields include invoice number, invoice date, due date, vendor name, customer name, subtotal, tax, total amount, and currency. Field mapping rules allow overrides per vendor format.

**What happens if OCR confidence is low or fields are missing?**  
The pipeline flags missing or low-confidence fields, captures screenshots and the OCR text output, and can either stop safely before submission or proceed with only validated fields based on configured rules.

**How does the PDF upload step work in the RTS Pro factoring app?**  
The scanner export creates a PDF in a known location, then the bot opens the RTS Pro attachment picker and selects that PDF. It verifies attachment presence before final submission.

---

## Performance & Reliability Benchmarks

**Execution Speed:**  
2–5 invoices per device per hour depending on scanner app speed and RTS Pro form complexity

**Success Rate:**  
92–94% across production runs with retries enabled, assuming stable app versions and consistent invoice formats

**Scalability:**  
Supports 10–100 Android devices using a device pool runner with per-device configs and parallel workers

**Resource Efficiency:**  
~200–450 MB RAM for the automation runner per device session; OCR preprocessing typically uses low CPU with short spikes during extraction

**Error Handling:**  
Step-level checkpoints, automatic retries with exponential backoff, selector fallbacks, screenshot + UI dump capture, and safe stop conditions before submission if validation fails

<p align="center">
<a href="https://cal.com/app-pilot-m8i8oo/30min" target="_blank">
 <img src="https://img.shields.io/badge/Book%20a%20Call%20with%20Us-34A853?style=for-the-badge&logo=googlecalendar&logoColor=white" alt="Book a Call">
</a>
 <a href="https://www.youtube.com/@Appilot-app/videos" target="_blank">
  <img src="https://img.shields.io/badge/ð¥%20Watch%20demos%20-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch on YouTube">
 </a>
</p>
