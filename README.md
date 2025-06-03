# Xeno CRM Assignment (ClientPulse)

**Project Live demo - https://xeno-crm-assignment-3ot4.onrender.com

It is a web application designed to help businesses manage customer relationships and marketing campaigns. It features customer data ingestion, audience segmentation, campaign creation, and AI-powered campaign optimization.

## Key Features

*   **Data Ingestion APIs:** Secure REST APIs to ingest customer and order data.
*   **Audience Segmentation:** Define customer segments using flexible rule logic.
*   **Campaign Creation & Management:** Design, schedule (conceptually), and manage email campaigns targeting specific segments.
*   **Campaign History:** View past campaigns with delivery statistics.
*   **AI Campaign Optimizer:** Get AI-driven suggestions for improving email content and optimal send times using Genkit and Google Gemini.
*   **User Authentication (Mock):** Basic user login/signup flow (client-side mock).

## Tech Stack

*   **Styling:** Tailwind CSS
*   **Forms:** React Hook Form & Zod (for validation)
*   **AI / Generative AI:**
    *   Google Gemini (via Genkit's Google AI plugin for campaign optimization)
*   **Language:** TypeScript
*   **Authentication:** Mock client-side authentication using React Context & localStorage.
*   **Deployment Platforms (Examples):**
    *   Render

## Architecture 

*   **User:** The person using the application.
*   **Client (React.js Frontend):** The user interface built with React and styled with Tailwind CSS.
*   **Google AI (Gemini Model):** The Large Language Model used for generating campaign suggestions.
*   **Postman/External System:** Tools or services used to interact with the ingestion APIs.

## Local Setup Instructions

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/KsM16/xeno-crm-assignment.git
    cd xeno-crm-assignment
    ```

2.  **Install Dependencies:**
    ```bash
    npm install
    ```
    or
    ```bash
    yarn install
    ```
    or
    ```bash
    pnpm install
    ```

3.  **Set Up Environment Variables:**
    *   Create a `.env` file in the root of your project by copying `.env.example` (if one exists) or creating it from scratch.
  
    *   Database URI, etc.
    *   **Google AI Credentials:** For local development, use Google-AI key


4.  **Run the Development Server:**
    ```bash
    npm run dev
    ```
    The application should now be running, typically at `http://localhost:9002` (as per your `package.json`).

5.  **Test APIs (Optional but Recommended):**
    *   Use a tool like Postman to test the data ingestion APIs:
        *   `POST http://localhost:9002/api/ingest/customers`
        *   `POST http://localhost:9002/api/ingest/orders`
    *   Refer to `src/lib/schemas.ts` for the expected JSON payload structure.

## API Endpoints

*   **`POST /api/ingest/customers`**
    *   **Description:** Ingests customer data. Validates against `CustomerIngestionSchema`. Saves to Firestore `customers` collection.
    *   **Request Body:** JSON object matching `CustomerIngestionPayload` from `src/lib/schemas.ts`.
*   **`POST /api/ingest/orders`**
    *   **Description:** Ingests order data. Validates against `OrderIngestionSchema`. Currently logs data to console.
    *   **Request Body:** JSON object matching `OrderIngestionPayload` from `src/lib/schemas.ts`.

## Known Limitations or Assumptions

*   **Authentication:** The current user authentication is a client-side mock. It does not provide real security and is for demonstration purposes only. Full Google OAuth 2.0 backend integration is pending.
*   **Campaign Delivery & Logging:** The backend logic for actual campaign delivery (sending emails/messages via a vendor API) and logging communication attempts (`communication_log`) is not yet implemented. The "Send/Schedule" button on the campaign form is a placeholder.
*   **Order Data Storage:** The `/api/ingest/orders` endpoint validates and logs order data but does not currently persist it to a database.
*   **Segment Rule Builder:** The segment criteria definition is text-based. A more dynamic, visual rule builder (e.g., drag-and-drop) is a potential future enhancement.
*   **Error Handling:** While basic error handling is in place, it can be further improved across the application for robustness.
*   **Firestore Security Rules:** The provided Firestore security rules are for development convenience and are **not secure for production**. They must be significantly hardened.
*   **AI Optimizer Input:** The effectiveness of the AI Campaign Optimizer heavily relies on the quality and relevance of the "historical campaign data" provided by the user.
*   **Scalability & Performance:** The application has not been extensively tested for performance under high load or for large-scale data processing.
*   **Data-AI-Hints:** Placeholder images use `data-ai-hint` attributes for potential future automated image sourcing, but this functionality is not implemented.

 
