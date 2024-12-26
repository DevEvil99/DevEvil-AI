# **DevEvil AI Server - Chat and Image Generation**

This repository enables you to host a powerful AI backend that supports chat and image generation using **xAI** for conversational AI and **FLUX** for advanced image generation. 

This guide will help you set up, configure, and use the server for your projects.

---

## **Features that are not in this Repository**
- Search
- Usage limit
- DevEvil API

---

## **Repository Structure**

- **`server.js`**  
  The main server file. Handles API endpoints for chat and image generation.
  
- **`.env.example`**  
  Template for environment variables. Rename this file to `.env` and fill in your credentials.

- **`package.json`**  
  Contains project metadata and dependencies for setting up the server.

---

## **Features**

1. **Chat API**  
   A conversational AI model powered by xAI to generate intelligent and context-aware responses.

2. **Image Generation API**  
   Generate images based on user prompts using the FLUX model.

3. **FTP Integration**  
   Images are securely stored on an FTP server and accessible via a URL.

---

## **Setup Guide**

### **1. Prerequisites**
- Node.js (v14 or higher)
- npm (Node Package Manager)
- An FTP server for image storage
- API keys for:
  - Hugging Face
  - xAI 

---

### **2. Installation**

1. Clone this repository:
   ```bash
   git clone https://github.com/DevEvil99/DevEvil-AI.git
   cd DevEvil-AI
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Rename `.env.example` to `.env`:
   ```bash
   mv .env.example .env
   ```

4. Fill in the `.env` file with your credentials:
   ```env
   XAI_API_KEY=your_xai_api_key
   HUGGING_FACE_API_KEY=your_hugging_face_api_key
   ```

---

### **3. Run the Server**

Start the server:
```bash
node server.js
```

You should see:
```
Server is running on http://localhost:5500
```

---

## **Usage**

### **Chat API**

**Endpoint:**  
`POST http://localhost:5500/chat`

**Headers:**
```json
{
  "Content-Type": "application/json"
}
```

**Body:**
```json
{
  "userMessage": "Hello, how are you?",
  "userId": "unique_user_id"
}
```

**Response:**
```json
{
  "botResponse": "I'm great! How can I assist you today?"
}
```

---

### **Image Generation API**

The `/chat` endpoint also supports image generation. To generate an image, include a command like **"Create an image of a sunset over mountains"** in the `userMessage`.

**Example Request:**
```json
{
  "userMessage": "Create an image of a futuristic city at night.",
  "userId": "unique_user_id"
}
```

**Response:**
```json
{
  "botResponse": "<img class=\"ai-image\" src=\"https://your_ftp_domain/unique_image_name.png\" alt=\"Generated Image\" />"
}
```

---

## **How to Integrate in Your Project**

1. **Include the API in Your Frontend**  
   Use `fetch` or any HTTP client (e.g., Axios) to send requests to the server.

   **Example (JavaScript):**
   ```javascript
   fetch('http://localhost:5500/chat', {
       method: 'POST',
       headers: {
           'Content-Type': 'application/json',
       },
       body: JSON.stringify({
           userMessage: "What's the weather like?",
           userId: "1"
       }),
   })
   .then(response => response.json())
   .then(data => console.log(data.botResponse))
   .catch(error => console.error('Error:', error));
   ```

2. **Host the Server Online**  
   Use a VPS or cloud platform like AWS, Google Cloud, or Heroku to deploy your server and make it publicly accessible.

---

## **Environment Variables**

| Variable              | Description                                      | Example Value               |
|-----------------------|--------------------------------------------------|-----------------------------|
| `XAI_API_KEY`         | API key for xAI            | `xai-abc123`                |
| `HUGGING_FACE_API_KEY`| API key for Hugging Face                         | `hf_abc123`                |


---

## **License**

This project is licensed under the MIT License. Feel free to use, modify, and distribute it.

---

## **Support**

For issues or questions, join our [Discord Community](https://dsc.gg/devevil) or open an issue in this repository.
