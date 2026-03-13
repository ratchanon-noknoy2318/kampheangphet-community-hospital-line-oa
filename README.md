# LINE Hospital Integration
**Enterprise-grade LINE Official Account gateway for automated patient workflows and clinical service orchestration.**

## Overview
The LINE Hospital Integration serves as a "Digital Front Door" for municipal healthcare environments. By leveraging the LINE Messaging API, this system automates patient interactions through structured interfaces, including 11 custom Flex Messages and 8 dynamic Rich Menus. The platform orchestrates essential clinical services—such as telemedicine, appointment scheduling, and medical roster queries—into a unified mobile experience, significantly reducing administrative load and improving patient accessibility.

## Architecture

| Component | Description |
| :--- | :--- |
| **Interface** | LINE Official Account (Rich Menu & Flex Messages) |
| **Logic Layer** | Node.js / JavaScript (Webhook Handling) |
| **Services** | Telemedicine Integration, FAQ Automation, Medical Roster API |
| **Data Flow** | [User] -> [LINE OA] -> [Webhook] -> [Service Handlers] |

## Tech Stack

| Category | Technology |
| :--- | :--- |
| **Language** | JavaScript (Node.js) |
| **API** | LINE Messaging API |
| **Messaging** | JSON-based Flex Messages |
| **Configuration** | Environment-based (.env) |

## Project Structure

| Directory / File | Description |
| :--- | :--- |
| `flex_message/` | JSON templates for structured clinical message payloads. |
| `push_message/` | Logic for outbound notification and alert systems. |
| `richmenu/` | Configuration and design assets for the 8-grid service menu. |
| `route.js` | Main entry point for webhook routing and request orchestration. |

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
