# AI-Powered Warranty Claim Agent for Automotive Cloud

## Overview

Electra Cars, an automotive OEM managing over 300,000 vehicles, faced major operational bottlenecks in handling 1,000+ daily warranty claim requests from dealers through a manual email-based process. This project transforms that workflow into an AI-driven, automated claim management ecosystem using Salesforce Automotive Cloud, Agentforce, Apex, Flow, Slack, Web Chat, and WhatsApp integration.

The solution digitizes warranty claim intake, validates VINs, verifies warranty eligibility, creates structured warranty records, automates approval decisions, and empowers approvers with AI-assisted recommendations and Slack-based approval workflows.



## Business Problem

### Existing Challenges:

* Dealers submitted warranty claims manually through email
* Over 1,000+ daily claims overloaded approvers
* Only 3 approvers managed all requests manually
* Slow approval turnaround times
* Missing claim details caused delays
* High operational cost and inefficiency
* Poor dealer experience



## Solution Summary

We built a complete AI-powered warranty automation platform that:

### Dealer Side:

* Accepts warranty claims via Web Chat and WhatsApp
* Uses conversational AI to collect VIN, issue description, claim amount, and part details
* Validates VIN against Salesforce Vehicle records
* Checks manufacturer warranty eligibility
* Automatically creates Warranty Claim records
* Auto-approves valid low-value claims
* Auto-rejects expired warranties
* Escalates high-value claims for manual review

### Approver Side:

* Sends instant Slack notifications
* Uses AI to summarize warranty claims
* Recommends approval or rejection
* Enables direct Slack-based decision workflows
* Updates Salesforce records automatically



## Salesforce Products & Features Used

### Core Platforms:

* Salesforce Automotive Cloud
* Salesforce Agentforce
* Salesforce Flow
* Apex Invocable Actions
* Salesforce Slack Platform Connector
* Digital Engagement
* Embedded Service Deployment
* WhatsApp Integration



## Custom Object: Warranty Claim (Warranty_Claim__c)

### Key Fields:

* Claim Number (Auto Number)
* VIN
* Vehicle Lookup
* Dealer Lookup
* Contact Lookup
* Part Name
* Claim Amount
* Issue Description
* AI Recommendation
* AI Description
* AI Confidence
* Warranty Valid
* Submission Channel (Web/WhatsApp)
* Status

### Status Logic:

* Auto-Approved → Warranty valid + claim < 5000
* Pending Approval → Warranty valid + claim > 5000
* Auto-Rejected → Warranty expired


## Agentforce Agents Built

# Agent 1: Warranty Claim Agent (Dealer Submission Agent)

### Purpose:

Automates dealer warranty claim intake and validation.

### Capabilities:

* VIN validation
* Warranty check
* Claim data collection
* AI-generated warranty summaries
* Auto approval/rejection
* Warranty claim creation

### Subagent:

VIN Validation and Warranty Check

### Agent Actions:

* Check Warranty
* Create Warranty Claim



# Agent 2: Warranty Approver Agent

### Purpose:

Assists OEM claim approvers with decision-making.

### Capabilities:

* Retrieves warranty claim details
* Summarizes claims
* Suggests approval/rejection
* Supports Slack approval workflows

### Agent Action:

* Get Warranty Claim Details



## Apex Classes

### VehicleWarrantyService.cls

### Function:

* Validates VIN
* Checks vehicle existence
* Returns warranty status
* Provides Manufacturer Warranty End Date

### CreateWarrantyClaimInvocable.cls

### Function:

* Finds Vehicle by VIN
* Maps Vehicle to Asset
* Creates Warranty Claim record
* Maps Dealer and Contact
* Applies AI approval decision
* Stores AI descriptions



## Salesforce Flows

### 1. Check Warranty Flow

### Purpose:

* Collect VIN
* Invoke VehicleWarrantyService
* Return warranty validity



### 2. Create Warranty Claim Flow

### Purpose:

* Collect claim details
* Invoke CreateWarrantyClaimInvocable
* Create claim record



### 3. Slack Approval Notification Flow

### Purpose:

* Trigger when Warranty Claim is created
* Notify Slack approvers
* Escalate pending approvals
* Update Salesforce based on Slack response



## Slack Integration

### Features:

* Salesforce Slack Platform Connector
* Slack channel creation for approvals
* Record-triggered Slack notifications
* Approval/rejection workflows
* Real-time claim escalation

### Approval Process:

1. Claim submitted
2. Slack notification sent
3. Approver reviews
4. Approver approves/rejects
5. Salesforce status updated automatically



## Web Chat Integration

### Features:

* Embedded Service Deployment
* Trusted URLs + CORS setup
* Routing configuration
* Queue setup
* Website deployment script

### Result:

Dealers can submit claims directly from the company website.



## WhatsApp Integration

### Features:

* Salesforce Digital Engagement
* Conversational warranty submission
* Mobile-friendly dealer experience



## End-to-End Architecture


Dealer (Web/WhatsApp)
        ↓
Agentforce Dealer Agent
        ↓
VIN Validation (Apex + Flow)
        ↓
Warranty Check
        ↓
Create Warranty Claim
        ↓
Decision Engine
 ┌──────────────┬──────────────┬──────────────┐
 │ Auto Approve │ Pending       │ Auto Reject  │
 │              │ Approval      │              │
 └──────────────┴──────────────┴──────────────┘
                     ↓
              Slack Notification
                     ↓
           Agentforce Approver Agent
                     ↓
             Approve / Reject
                     ↓
          Salesforce Record Update


## Documentation Included in Repository

### This repository contains:

* Custom object schema and fields
* Agentforce setup documentation
* Apex classes
* Salesforce flow documentation
* Slack integration documentation
* Screenshots
* Demo steps
* Demo video link



## Demo Coverage

### Demonstrates:

* Dealer claim submission
* VIN validation
* Warranty eligibility
* AI claim creation
* Auto approval/rejection
* Slack notifications
* Approver AI assistance
* Final claim approval workflow



## Future Enhancements

If additional time were available:

* Data Cloud customer intelligence
* Fraud detection engine
* Image/document upload for damaged parts
* Predictive warranty analytics
* Multi-language support
* Voice-enabled dealer claims
* Mobile application
* Advanced dealer dashboards

---

## Business Impact

### Benefits:

* Reduces manual processing workload
* Improves claim turnaround speed
* Increases operational efficiency
* Enhances dealer satisfaction
* Improves claim accuracy
* Scales approval operations
* Demonstrates enterprise AI automation



## GitHub Repository Structure

* Documentation
* Apex Code
* Salesforce Flow Setup
* Slack Integration
* Agentforce Instructions
* Screenshots
* Demo Assets



## Team Submission

### Project:

AI-Powered Warranty Claim Agent for Electra Cars

### Built For:

Salesforce Automotive Cloud + Agentforce Hackathon


## Final Statement

This project successfully transforms Electra Cars’ outdated manual warranty approval system into a scalable, AI-powered, enterprise-grade automation platform using Salesforce technologies. By combining Automotive Cloud, Agentforce, Slack, Flow, and Apex, the solution significantly improves dealer experience, accelerates warranty approvals, and modernizes OEM warranty operations.
