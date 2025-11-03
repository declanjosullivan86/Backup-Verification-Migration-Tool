# 💾 Backup Verification & Migration Tool

## A Unified Solution for Personal Cloud Storage Integrity

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stack: React/Node](https://img.shields.io/badge/Stack-React%20%7C%20Node.js-blue)](https://react.dev/)
[![Status: Specification Complete](https://img.shields.io/badge/Status-Specification%20Complete-green)]()

---

## ✨ Overview

The **Backup Verification & Migration Tool** is a robust, browser-based Single-Page Application (SPA) designed to solve the critical problem of verifying data integrity between personal cloud storage and dedicated backup solutions.

Instead of manually checking file lists, this tool securely connects to cloud services, performs a rapid metadata comparison, and provides an **actionable, color-coded dashboard** of your backup health. It is the ultimate utility for ensuring your backups are complete, up-to-date, and truly migrated.

## 🎯 Core Features

| Feature | Description |
| :--- | :--- |
| **Unified Comparison** | Connect a **Source (S)** storage service (e.g., Google Drive) to a **Target (T)** backup bucket (Backblaze B2) for side-by-side analysis. |
| **Four State Analysis** | Instantly categorize files into four critical states: **Identical** (Success), **Missing in Target**, **Missing in Source**, and **Modified** (Out-of-Sync). |
| **Strong GUI** | Features a prominent **Split-Panel File Manager Interface** with intuitive color-coding for quick status identification. |
| **Actionable Results** | Execute immediate sync actions (e.g., **Upload**, **Download**, **Delete**) directly from the results table to reconcile discrepancies. |
| **Extensible Architecture** | Built to easily integrate additional Source services like **OneDrive** and **Dropbox** in future versions. |

---

## 🛠️ Technical Stack

This project is implemented as a modern SPA with a robust, secure backend microservice architecture.

### Frontend
* **Framework:** **React** (or Vue.js)
* **Purpose:** Dynamic, component-based user interface; handles OAuth flow initiation and displays comparison results.

### Backend
* **Technology:** **Node.js** / **Express** (or Python / FastAPI)
* **Purpose:** Securely manages API keys and secrets, orchestrates metadata retrieval from external APIs, and performs the core comparison logic.

### External Services
* **Source API:** Google Drive API (Initial release), designed for expansion to OneDrive/Dropbox APIs.
* **Target API:** Backblaze B2 API

---

## 💻 Getting Started

### Prerequisites

You will need the following installed locally:
* Node.js (LTS version)
* npm or Yarn
* Access to a **Google Drive** account and a **Backblaze B2** bucket.
* Required **API Credentials** (Client ID/Secret for Google OAuth, Application Key ID/Secret for B2).

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)[your-username]/backup-verification-tool.git
    cd backup-verification-tool
    ```

2.  **Install Dependencies:**
    ```bash
    # Install backend dependencies
    npm install
    
    # Install frontend dependencies (assuming a standard create-react-app structure)
    cd client
    npm install
    cd ..
    ```

3.  **Configure Environment Variables:**
    Create a `.env` file in the project root with your credentials:
    ```
    # Google Drive API
    GOOGLE_CLIENT_ID="..."
    GOOGLE_CLIENT_SECRET="..."
    
    # Backblaze B2 API
    B2_APPLICATION_KEY_ID="..."
    B2_APPLICATION_KEY="..."
    
    # Server configuration
    PORT=5000
    ```

4.  **Run the Application:**
    ```bash
    npm run dev # Or your specific script to run both server and client
    ```
    The application will typically be accessible at `http://localhost:3000`.

---

## 🗺️ High-Level Architecture

The architecture is designed for security and scalability, separating concerns between the presentation layer and the secure API handling layer.

1.  **Client (React):** Handles user input and displays results.
2.  **API Gateway (Node/Express):** Acts as a secure proxy. Receives user requests and holds all API secrets.
3.  **External Cloud APIs:** Google Drive and Backblaze B2 APIs are called *only* by the secure Backend service.
4.  **Comparison Logic:** The Backend retrieves metadata lists from both S and T, runs the comparison logic (Size, Timestamp check), and sends the structured four-state result back to the Client.

---
