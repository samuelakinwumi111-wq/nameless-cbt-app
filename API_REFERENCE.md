# 🔗 API Reference

## Base URL
```
http://localhost:3000
```

## Authentication
- Admin endpoints require `adminLoggedIn` session
- Student endpoints require `studentLoggedIn` session
- Session maintained via cookies

---

## 🔐 Admin Endpoints

### Login
```http
POST /admin/login
```
**Request Body:**
```json
{
  "username": "Nameless",
  "password": "Niniola12@"
}
```

**Response (Success):**
```json
{
  "success": true,
  "message": "Login successful"
}
```

**Response (Error):**
```json
{
  "success": false,
  "error": "Invalid credentials"
}
```

---

### Logout
```http
POST /admin/logout
```

**Response:**
```json
{
  "success": true,
  "message": "Logout successful"
}
```

---

### Create Exam
```http
POST /admin/exam/create
```

**Request Body:**
```json
{
  "name": "Biology 101",
  "description": "Basic biology concepts",
  "timeLimit": 30
}
```

**Response:**
```json
{
  "success": true,
  "exam": {
    "id": "uuid-string",
    "name": "Biology 101",
    "description": "Basic biology concepts",
    "code": "ABC123",
    "timeLimit": 30,
    "createdAt": "2024-01-01T00:00:00Z",
    "questions": []
  }
}
```

---

### Get All Exams
```http
GET /admin/exams
```

**Response:**
```json
{
  "exams": [
    {
      "id": "uuid",
      "name": "Biology 101",
      "description": "...",
      "code": "ABC123",
      "timeLimit": 30,
      "createdAt": "2024-01-01T00:00:00Z",
      "questions": []
    }
  ]
}
```

---

### Get Exam Details
```http
GET /admin/exam/:id
```

**Parameters:**
- `id` (required) - Exam UUID

**Response:**
```json
{
  "exam": {
    "id": "uuid",
    "name": "Biology 101",
    "description": "...",
    "code": "ABC123",
    "timeLimit": 30,
    "questions": [
      {
        "id": "uuid",
        "question": "What is photosynthesis?",
        "options": ["Option A", "Option B", "Option C", "Option D"],
        "correctAnswer": 0
      }
    ]
  }
}
```

---

### Add Question to Exam
```http
POST /admin/exam/:id/question
```

**Parameters:**
- `id` (required) - Exam UUID

**Request Body:**
```json
{
  "question": "What is photosynthesis?",
  "options": [
    "Process of making food from sunlight",
    "Process of breaking down food",
    "Process of respiration",
    "Process of reproduction"
  ],
  "correctAnswer": 0
}
```

**Response:**
```json
{
  "success": true,
  "question": {
    "id": "uuid",
    "question": "What is photosynthesis?",
    "options": ["..."],
    "correctAnswer": 0
  }
}
```

---

### Edit Question
```http
PUT /admin/question/:questionId
```

**Parameters:**
- `questionId` (required) - Question UUID

**Request Body:**
```json
{
  "question": "Updated question text?",
  "options": ["New Option A", "New Option B", "New Option C", "New Option D"],
  "correctAnswer": 2
}
```

**Response:**
```json
{
  "success": true,
  "question": {
    "id": "uuid",
    "question": "Updated question text?",
    "options": ["..."],
    "correctAnswer": 2
  }
}
```

---

### Delete Question
```http
DELETE /admin/question/:questionId
```

**Parameters:**
- `questionId` (required) - Question UUID

**Response:**
```json
{
  "success": true,
  "message": "Question deleted"
}
```

---

### Delete Exam
```http
DELETE /admin/exam/:id
```

**Parameters:**
- `id` (required) - Exam UUID

**Response:**
```json
{
  "success": true,
  "message": "Exam deleted"
}
```

---

### Get All Results
```http
GET /admin/results
```

**Response:**
```json
{
  "results": [
    {
      "id": "uuid",
      "studentName": "John Doe",
      "examId": "exam-uuid",
      "examName": "Biology 101",
      "score": 8,
      "totalQuestions": 10,
      "percentage": "80.00",
      "submittedAt": "2024-01-01T00:00:00Z",
      "detailedResults": [
        {
          "questionId": "uuid",
          "question": "What is photosynthesis?",
          "studentAnswer": 0,
          "correctAnswer": 0,
          "isCorrect": true
        }
      ]
    }
  ]
}
```

---

### Get Results for Specific Exam
```http
GET /admin/exam/:id/results
```

**Parameters:**
- `id` (required) - Exam UUID

**Response:**
```json
{
  "results": [
    {
      "id": "uuid",
      "studentName": "John Doe",
      "examId": "exam-uuid",
      "examName": "Biology 101",
      "score": 8,
      "totalQuestions": 10,
      "percentage": "80.00",
      "submittedAt": "2024-01-01T00:00:00Z"
    }
  ]
}
```

---

## 👨‍🎓 Student Endpoints

### Login (Start Exam)
```http
POST /student/login
```

**Request Body:**
```json
{
  "name": "John Doe",
  "examCode": "ABC123"
}
```

**Response (Success):**
```json
{
  "success": true,
  "exam": {
    "id": "exam-uuid",
    "name": "Biology 101",
    "timeLimit": 30,
    "totalQuestions": 10
  }
}
```

**Response (Error):**
```json
{
  "error": "Invalid exam code"
}
```

---

### Get Exam Questions
```http
GET /student/exam/questions
```

**Response:**
```json
{
  "questions": [
    {
      "id": "uuid",
      "question": "What is photosynthesis?",
      "options": ["Option A", "Option B", "Option C", "Option D"]
    }
  ]
}
```

**Note:** Correct answers are NOT returned to students

---

### Submit Answer
```http
POST /student/submit-answer
```

**Request Body:**
```json
{
  "questionId": "uuid",
  "answer": 0
}
```

**Response:**
```json
{
  "success": true,
  "message": "Answer recorded"
}
```

---

### Submit Exam
```http
POST /student/submit-exam
```

**Response:**
```json
{
  "success": true,
  "result": {
    "score": 8,
    "totalQuestions": 10,
    "percentage": "80.00",
    "message": "You scored 8/10 (80.00%)",
    "detailedResults": [
      {
        "questionId": "uuid",
        "question": "What is photosynthesis?",
        "studentAnswer": 0,
        "correctAnswer": 0,
        "isCorrect": true
      }
    ]
  }
}
```

---

### Logout
```http
POST /student/logout
```

**Response:**
```json
{
  "success": true,
  "message": "Logged out"
}
```

---

## 🤖 AI Endpoints

### Generate Questions from File
```http
POST /api/generate-questions
```

**Headers:**
```
Content-Type: multipart/form-data
```

**Request (FormData):**
```
- file: File (TXT, PDF, or DOCX)
- examId: string (UUID of target exam)
- numberOfQuestions: number (default: 10)
```

**Response (Success):**
```json
{
  "success": true,
  "message": "10 questions generated and added to exam",
  "questions": [
    {
      "id": "uuid",
      "question": "Generated question?",
      "options": ["Option A", "Option B", "Option C", "Option D"],
      "correctAnswer": 0
    }
  ]
}
```

**Response (Error):**
```json
{
  "error": "Failed to generate questions: [error details]"
}
```

---

## Status Codes

| Code | Meaning |
|------|---------|
| 200 | Success |
| 400 | Bad Request (missing/invalid data) |
| 401 | Unauthorized (not logged in) |
| 404 | Not Found (resource doesn't exist) |
| 500 | Server Error |

---

## Error Examples

### Missing Required Field
```json
{
  "error": "Name and exam code are required"
}
```

### Unauthorized Access
```json
{
  "error": "Unauthorized"
}
```

### Resource Not Found
```json
{
  "error": "Exam not found"
}
```

---

## Rate Limiting
- No rate limiting implemented currently
- Will be added in production

## CORS
- CORS enabled for development
- Can be restricted in production via environment variables

## Session Details
- Session timeout: 24 hours
- Stored in memory (non-persistent)
- Use session database in production

---

## Examples

### Complete Flow: Admin Creating Exam

```bash
# 1. Login
curl -X POST http://localhost:3000/admin/login \
  -H "Content-Type: application/json" \
  -d '{"username":"Nameless","password":"Niniola12@"}'

# 2. Create exam
curl -X POST http://localhost:3000/admin/exam/create \
  -H "Content-Type: application/json" \
  -d '{
    "name":"Biology Test",
    "description":"Chapter 1-3",
    "timeLimit":45
  }'

# 3. Add question (use exam ID from response)
curl -X POST http://localhost:3000/admin/exam/EXAM_ID/question \
  -H "Content-Type: application/json" \
  -d '{
    "question":"What is photosynthesis?",
    "options":["A","B","C","D"],
    "correctAnswer":0
  }'

# 4. Get exam details
curl http://localhost:3000/admin/exam/EXAM_ID

# 5. Logout
curl -X POST http://localhost:3000/admin/logout
```

### Complete Flow: Student Taking Exam

```bash
# 1. Login with exam code
curl -X POST http://localhost:3000/student/login \
  -H "Content-Type: application/json" \
  -d '{
    "name":"John Doe",
    "examCode":"ABC123"
  }'

# 2. Get questions
curl http://localhost:3000/student/exam/questions

# 3. Submit answer
curl -X POST http://localhost:3000/student/submit-answer \
  -H "Content-Type: application/json" \
  -d '{
    "questionId":"QUESTION_ID",
    "answer":0
  }'

# 4. Submit exam
curl -X POST http://localhost:3000/student/submit-exam

# 5. Logout
curl -X POST http://localhost:3000/student/logout
```

---

**For more information, see README.md**
