# Webhook Service Integration
**Kamphaeng Phet Community Municipal Hospital**
*LINE Official Account Platform*

---

## 1. System Overview

The Webhook Service Module serves as the primary integration interface between the LINE Messaging API and the hospital's internal backend systems. This service is designed to handle high-concurrency event processing, ensuring secure and reliable communication for the LINE Official Account.

| Attribute | Specification |
|:---|:---|
| **Module Name** | Webhook Service Integration |
| **Project** | Kamphaeng Phet Community Hospital LINE OA |
| **Primary Function** | Event Ingestion and Dispatching |
| **Operational Role** | Middleware Layer |

## 2. Interface Specifications

This section illustrates the Rich Menu interface deployed on the client side. The design facilitates user access to core hospital services including appointment scheduling and queue checking.

<p align="center">
  <img src="richmenu.png" alt="Rich Menu Interface" width="100%" style="border: 1px solid #ddd;">
</p>
<p align="center"><em>Figure 1: Rich Menu Interface Layout</em></p>

## 3. System Architecture

The module implements a synchronous event-driven architecture. The sequence diagram below details the transaction lifecycle from the user interaction to the final response delivery.

```mermaid
sequenceDiagram
    participant User as End User
    participant LINE as LINE Platform
    participant Webhook as Webhook Controller
    participant Service as Business Service
    participant Backend as Hospital Database

    User->>LINE: Triggers Action (Message/Postback)
    LINE->>Webhook: HTTPS POST /webhook
    Note right of LINE: Includes X-Line-Signature
    
    rect rgb(240, 240, 240)
        Note over Webhook: Security Validation
        Webhook->>Webhook: Validate HMAC-SHA256
    end

    alt Invalid Signature
        Webhook-->>LINE: 401 Unauthorized
    else Valid Signature
        Webhook->>Service: Dispatch Event
        Service->>Backend: Query Data / Execute Logic
        Backend-->>Service: Return Result
        Service->>LINE: Reply Message (ReplyToken)
        Webhook-->>LINE: 200 OK
    end
