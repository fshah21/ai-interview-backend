# AI Interview Backend

This is the backend service for the AI Interview application. It handles resume parsing, interview question generation, and feedback generation using AI models.

## API Endpoints

### 1. Start Interview
```
POST /api/start-interview
```
Starts a new interview session by processing the resume and job description.

**Request:**
- Content-Type: multipart/form-data
- Body:
  - resume: PDF or DOCX file
  - jobDescription: PDF or DOCX file

**Response:**
```json
{
  "interviewId": "string",
  "current_question": "string"
}
```

### 2. Get Next Question
```
POST /api/get-next-question
```
Processes the user's response and returns the next interview question.

**Request:**
```json
{
  "response": "string",
  "interviewId": "string",
  "current_question_id": number
}
```

**Response:**
```json
{
  "question": "string",
  "current_question_id": number
}
```

### 3. End Interview
```
POST /api/end-interview
```
Ends the interview session and generates feedback.

**Request:**
```json
{
  "interviewId": "string"
}
```

**Response:**
```json
{
  "feedback": "string"
}
```

## Setup

1. Install dependencies:
```bash
npm install
```

2. Set up environment variables:
Create a `.env` file with the following variables:
```
PORT=3001
OPENROUTER_API_KEY=your_openrouter_api_key
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
```

3. Start the server:
```bash
npm start
```

## Database Schema

### interviews
- id: string (primary key)
- current_question_id: number
- questions: string[]
- responses: string[]
- feedback: string
- created_at: timestamp
- updated_at: timestamp

### interview_data
- id: string (primary key)
- resume_text: string
- job_description: string
