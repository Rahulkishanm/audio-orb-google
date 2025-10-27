# Audio Orb

Speak, and the orb responds. An interactive experience powered by the Live Audio API.

This project showcases a real-time voice conversation with the Gemini API, featuring an interactive 3D visualization that reacts to both the user's voice and the model's audio response.

## Features

-   **Real-time Conversation**: Engage in a natural, low-latency voice chat with the `gemini-2.5-flash-native-audio-preview-09-2025` model.
-   **Interactive 3D Visuals**: A dynamic 3D orb, built with Three.js, visualizes the audio from your microphone and the model's response.
-   **Web-based**: Runs directly in your browser, built with modern web technologies like Lit and TypeScript.

## How to Run This App Locally (macOS, Node.js 22)

This project is built using modern web technologies including TypeScript and requires a development server that can handle them on-the-fly. The instructions below guide you through setting up a local development environment using [Vite](https://vitejs.dev/), a fast and popular web development build tool.

### Prerequisites

1.  **Node.js v22**: Ensure you have Node.js version 22 or newer installed. You can download it from [nodejs.org](https://nodejs.org/).
2.  **Gemini API Key**: You'll need an API key from Google AI Studio to use the Gemini API. You can create one [here](https://aistudio.google.com/app/apikey).

### Step-by-Step Instructions

1.  **Project Setup**:
    Place all the project files (`index.html`, `index.tsx`, `analyser.ts`, etc.) into a single folder on your Mac.

2.  **Initialize Project with npm**:
    Open your Terminal application, navigate to the project folder you just created, and run the following command to create a `package.json` file:
    ```bash
    npm init -y
    ```

3.  **Install Dependencies**:
    The application relies on several libraries. Install them using npm:
    ```bash
    npm install lit three @google/genai
    ```

4.  **Install Development Tools**:
    Vite is used as the development server. It requires TypeScript as a peer dependency. Install them as development dependencies:
    ```bash
    npm install -D vite typescript
    ```

5.  **Configure API Key**:
    The application needs your Gemini API key to function. Vite uses `.env` files to manage environment variables.
    Create a file named `.env` in the root of your project folder and add your key like this:
    ```
    API_KEY=YOUR_API_KEY_HERE
    ```
    Replace `YOUR_API_KEY_HERE` with your actual Gemini API key.

6.  **Configure Vite**:
    To make the API key accessible in the browser code under `process.env.API_KEY`, you need to create a Vite configuration file.
    Create a file named `vite.config.js` in your project root and add the following content:
    ```javascript
    import { defineConfig, loadEnv } from 'vite';

    export default defineConfig(({ mode }) => {
      const env = loadEnv(mode, process.cwd(), '');
      return {
        define: {
          'process.env.API_KEY': JSON.stringify(env.API_KEY)
        },
      }
    })
    ```

7.  **Add Run Script**:
    For convenience, add a `dev` script to your `package.json` file. Open `package.json` and add the script to the `scripts` object:
    ```json
    "scripts": {
      "dev": "vite"
    },
    ```

8.  **Start the Development Server**:
    You are now ready to run the application! In your terminal, run:
    ```bash
    npm run dev
    ```
    Vite will start the server, and you'll see a message like `> Local: http://localhost:5173/`.

9.  **View The App**:
    Open the local URL (e.g., `http://localhost:5173`) in your web browser. The browser will ask for microphone permission; please allow it.
    Click the red circular button to start the conversation with the Audio Orb.
