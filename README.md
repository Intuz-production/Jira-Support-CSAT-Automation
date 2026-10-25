*Intuz — Your automation partner, one workflow at a time.*

<p align="center">
  <picture>
    <img alt="Banner Image" src="https://github.com/user-attachments/assets/210f97fc-0fce-404a-b647-7dfe1302cd37" />
  </picture>
</p>

[Intuz](https://www.intuz.com) helps organizations orchestrate AI, automation, and enterprise systems through scalable workflows. Our repository showcases proven implementations across healthcare, operations, customer support, document processing, sales, and back-office functions, enabling teams to accelerate automation initiatives without starting from scratch.

[N8N Creator](https://n8n.io/creators/intuz/) · [Workflow Automation](https://www.intuz.com/workflow-automation-services/) · [AI Consulting Company](https://www.intuz.com/company/) · [For Custom Workflow Automation](https://www.intuz.com/get-started/)

# Send Jira support auto-replies and CSAT surveys via WhatsApp, Gmail, and HubSpot

## Quick overview

This workflow closes the loop on Jira support tickets by sending an acknowledgement on ticket creation, requesting CSAT when an issue is marked Done, and saving CSAT results back to Jira with optional HubSpot notes, using Gmail and a WAHA WhatsApp API.

## How it works

1. Receives a ticket-created payload from another n8n workflow and loads the close-loop configuration.
2. Normalizes the payload, determines the customer channel (WhatsApp or Gmail), and checks whether the workflow has enough contact data to send an acknowledgement.
3. Sends the auto-reply to the customer via WAHA (WhatsApp) or Gmail, then adds a Jira comment and label to record that the auto-reply was sent.
4. Receives a Jira webhook when an issue changes status and validates the webhook token and that the issue is Done and not already CSAT-tagged.
5. Fetches the Jira issue, builds a CSAT form URL, sends the CSAT request via the same channel (WAHA or Gmail), and then comments and labels the Jira issue to mark CSAT as sent.
6. Receives the CSAT form submission, validates the ticket key, fetches the Jira issue to confirm it exists, and writes the CSAT score/comment back to Jira (including an optional custom field update).
7. If a HubSpot contact ID is present, creates and associates a HubSpot note for the auto-reply and/or CSAT submission, and then returns a confirmation page to the CSAT form submitter.

## Setup

1. Create Jira credentials (API token via HTTP Basic Auth) and configure a Jira automation/webhook to POST to the workflow’s Jira webhook endpoint with the correct token.
2. Add Gmail OAuth2 credentials for the account that sends customer emails.
3. Add WAHA HTTP Header Auth credentials and set your WAHA base URL and session ID in the workflow configuration.
4. Add HubSpot private app token (HTTP Header Auth) if you want CRM notes, and ensure your Jira issues store the HubSpot contact ID in the configured custom field.
5. Update the Jira base URL/project key, Done status name, labels, and Jira custom field IDs (channel, customer email/phone, CSAT score, WAHA session) in the configuration code nodes.
6. After importing the workflow, copy the CSAT Form Trigger path/webhook ID into the CSAT Form Path Config node so generated CSAT links point to the correct form URL.

## FAQ

**What channels does this workflow use to send auto-replies and CSAT surveys?**  
The workflow sends auto-replies and CSAT surveys via WhatsApp using WAHA API and Gmail.

**How does the workflow handle CSAT submissions?**  
It validates the ticket key, confirms the Jira issue exists, writes the CSAT score and comment back to Jira, and optionally creates HubSpot notes.

**What integrations are required to set up this workflow?**  
You need Jira credentials, Gmail OAuth2 credentials, WAHA HTTP Header Auth credentials, and optionally a HubSpot private app token.

## Related n8n templates from Intuz

- [Color Picker for iOS](https://github.com/Intuz-production/ColorPicker-iOS)
- [Google and Facebook sign in using firebase authentication](https://github.com/Intuz-production/Firebase-authenticaiton-android)
- [User auth api for nodejs](https://github.com/Intuz-production/user-auth-api-nodejs)

[See all of Intuz's free n8n templates](https://www.intuz.com/n8n-workflow-automation-templates/)

## Connect with us

Intuz is a USA-based AI & workflow automation company with 16+ years of experience building custom AI-enabled workflow automations for SMBs and Enterprises, specializing in agentic AI, LLM integrations, and CRM/ERP sync across Healthcare, FinTech, eCommerce, Manufacturing, and Real Estate.

* **Website:** [https://www.intuz.com](https://www.intuz.com)
* **Email:** [getstarted@intuz.com](mailto:getstarted@intuz.com)
* **LinkedIn:** https://www.linkedin.com/company/intuz/
* **Get Started:** https://n8n.partnerlinks.io/intuz

## For Custom Workflow Automation

[Click here - Get Started](https://www.intuz.com/get-started/)
