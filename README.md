# MANUS Voice Pro - AI Voice Bot

MANUS Voice Pro is a comprehensive, trainable AI voice bot designed to handle incoming phone calls, book appointments, and facilitate sales for any business. This system is built to be highly customizable, allowing businesses to tailor the bot's voice, knowledge base, and conversation flows to their specific needs.

## Features

*   **Instant Call Answering:** Answers calls on the first ring, ensuring no customer is left waiting.
*   **Natural Conversation:** Utilizes advanced Speech-to-Text, Natural Language Understanding (NLU), and Text-to-Speech (TTS) to create a natural and human-like conversational experience.
*   **Trainable for Any Business:** Can be trained with business-specific information, such as services, products, hours, and FAQs.
*   **Appointment Booking:** Capable of scheduling appointments and integrating with calendar systems (future enhancement).
*   **Sales Facilitation:** Can guide customers through sales processes and capture lead information.
*   **Customizable Voices:** Integrates with ElevenLabs to allow for the use of pre-made or custom-cloned voices that match the business's brand.
*   **Web-Based Management:** A comprehensive web dashboard for managing businesses, voices, and viewing call analytics.
*   **Scalable Architecture:** Built with a modular and scalable architecture that can handle a high volume of calls.

## System Architecture

The system is composed of several key components that work together to provide a seamless voice bot experience. For a detailed diagram and component breakdown, please refer to the `system_architecture.md` document.

## Setup and Installation

### Prerequisites

*   Python 3.11+
*   `pip` and `venv`
*   SignalWire account and phone number
*   ElevenLabs API key
*   Deepgram API key
*   OpenAI API key

### Installation Steps

1.  **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd voice_bot
    ```

2.  **Create and activate a virtual environment:**

    ```bash
    python3 -m venv venv
    source venv/bin/activate
    ```

3.  **Install the required dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up environment variables:**

    Create a `.env` file in the root of the project and add the following:

    ```
    ELEVENLABS_API_KEY="your_elevenlabs_api_key"
    DEEPGRAM_API_KEY="your_deepgram_api_key"
    OPENAI_API_KEY="your_openai_api_key"
    SIGNALWIRE_PROJECT_ID="your_signalwire_project_id"
    SIGNALWIRE_AUTH_TOKEN="your_signalwire_auth_token"
    SIGNALWIRE_SPACE_URL="your_signalwire_space_url"
    ```

## Configuration

1.  **SignalWire Configuration:**

    *   In your SignalWire dashboard, purchase a phone number.
    *   Configure the phone number to handle voice calls using a "LaML Webhook".
    *   Set the webhook URL to `https://your_public_domain/api/voice/incoming-call`.

2.  **Business Configuration:**

    *   Use the web interface to create and manage businesses. This includes setting the business name, phone number, services, hours, and custom greeting.

3.  **Voice Configuration:**

    *   Use the web interface to browse and select from available ElevenLabs voices or clone a custom voice.
    *   Assign a voice to each business.

## Running the Application

To start the Flask development server, run the following command:

```bash
python src/main.py
```

The application will be accessible at `http://localhost:5000`.

For production environments, it is recommended to use a production-grade WSGI server like Gunicorn or uWSGI.

## API Documentation

The application provides a RESTful API for managing businesses, voices, and call analytics. The API endpoints are defined in the following files:

*   `src/routes/business.py`: Endpoints for managing businesses and viewing analytics.
*   `src/routes/elevenlabs.py`: Endpoints for interacting with the ElevenLabs API.
*   `src/routes/voice.py`: Endpoints for handling incoming calls from SignalWire.

## Deployment

This application is designed to be deployed using Docker and Kubernetes for scalability and reliability.

1.  **Build the Docker image:**

    ```bash
    docker build -t voice-bot .
    ```

2.  **Run the Docker container:**

    ```bash
    docker run -p 5000:5000 -e ELEVENLABS_API_KEY=... -e DEEPGRAM_API_KEY=... -e OPENAI_API_KEY=... voice-bot
    ```

3.  **Kubernetes Deployment:**

    A sample Kubernetes deployment configuration is provided in the `k8s` directory (to be created). This will include deployments for the Flask application and a PostgreSQL database.

## Future Enhancements

*   **Calendar Integration:** Integrate with Google Calendar or other calendar systems to book appointments directly.
*   **CRM Integration:** Connect with CRM systems like Salesforce or HubSpot to create and update leads.
*   **Advanced Analytics:** Provide more detailed call analytics and sentiment analysis.
*   **Real-time Dashboard:** A real-time dashboard to monitor active calls.

