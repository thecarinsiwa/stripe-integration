# Stripe Integration Projects on GitHub

This document provides an overview of notable Stripe integration projects available on GitHub. These projects demonstrate various approaches to integrating Stripe's payment processing capabilities across different technology stacks and use cases.

## Overview Table

| **Project Name** | **Primary Technology** | **Core Features & Purpose** | **Key Integrations** |
|:---|:---|:---|:---|
| **Gateway Stripe Sandbox** | Django (Python) | A comprehensive Brazilian sandbox for testing **Cards, PIX, and Boletos**. Includes a full admin interface and webhook logging. | Stripe, ngrok |
| **stripe-Payment-integration** | Django (Python) | A demonstration repository for processing **one-time payments, subscriptions, and webhooks**. | Stripe |
| **Stripe_integration** | Kafka | A **two-way sync** project using Kafka to keep a customer catalog in sync with Stripe in near real-time. | Stripe, Kafka |
| **ms-stripe** | Python, Flask | A **production-style microservice** for handling customers, subscriptions, and webhooks with AWS SQS for reliable event polling. | Stripe, AWS (SQS, EKS) |
| **Simple Stripe Integration** | Node.js, React | A full-stack application (MERN) with a clean UI for seamless and secure payment processing, using UUIDs to prevent duplicate charges. | Stripe |
| **Technova (MERN Stripe Demo)** | MERN (MongoDB, Express, React, Node.js) | A full-stack project demonstrating **product payments** (one-time) and **service subscriptions** (recurring). | Stripe, React Router, Bootstrap |
| **stripe-integration (miniCal Extension)** | PHP, JavaScript | An extension for the miniCal platform to enable safe **payment, refund, and capture** with support for multiple currencies. | miniCal |
| **ignews** | Next.js (React) | A news site project where Stripe handles **payment for subscriptions**, integrated with a serverless database (FaunaDB) and a CMS (Prismic). | Stripe, FaunaDB, Prismic |

---

## 🧪 Detailed Spotlight: Gateway Stripe Sandbox (Django)

This project stands out as a complete, ready-to-run sandbox environment specifically tailored for the Brazilian market. It serves as an excellent learning tool for developers wanting to understand Stripe's API, webhooks, and payment flows within a full-stack web application context.

### 🚀 Key Features

- **Multiple Payment Methods:** Supports testing with:
  - **Credit cards** (including success, failure, and 3D Secure test cards)
  - **PIX** (noted as non-functional in the documentation)
  - **Bank slips (Boletos)**

- **Brazilian-Centric Validation:** Includes:
  - Automatic CPF/CNPJ masking
  - Brazilian address validation
  - Configurable expiration for Boletos

- **Comprehensive Admin Interface:** Offers a Django admin panel with:
  - Detailed transaction history
  - Color-coded payment statuses (Pending, Processing, Approved, Failed, etc.)
  - Webhook logs for debugging

- **Webhook Handling:** Configured to work with **ngrok** for local webhook testing, listening to key Stripe events like `payment_intent.succeeded` and `payment_intent.payment_failed`.

### 🛠️ Technology Stack

- **Backend:** Django 4.2.7 (Python)
- **Payment Gateway:** Stripe 7.8.0
- **Database:** SQLite (for development)
- **Utilities:** ngrok (for webhook tunneling)

### ⚙️ How It Works

1.  **Setup:** After cloning the repository, you configure your Stripe test API keys in a `.env` file and run Django migrations.

2.  **Catalog:** You can pre-populate a product catalog (e.g., "Python Course," "E-book") using the Django shell.

3.  **Checkout Flow:**
    - A user selects a product from the catalog and chooses a payment method (Card or Boleto).
    - For **cards**, they enter test card numbers (e.g., `4242 4242 4242 4242` for success, `4000 0000 0000 0002` for card declined).
    - For **Boletos**, they fill in Brazilian tax IDs (CPF for individuals, CNPJ for companies) and addresses with Brazilian formatting.
    - The system processes the payment through Stripe's API and shows a success or failure page with appropriate details.

4.  **Admin & Monitoring:**
    - All transactions are logged in the Django admin panel with full details.
    - Webhooks update the payment status in real-time as Stripe processes events.
    - You can view raw webhook event data in the admin interface for debugging purposes.
    - Payment statuses are color-coded for quick visual reference (green for success, red for failure, yellow for pending/processing).

This sandbox environment provides a practical, hands-on way to learn Stripe integration patterns while building a functional e-commerce payment system.
