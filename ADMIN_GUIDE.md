# 👨‍💼 Admin User Guide

## Login

**URL:** http://localhost:3000

**Credentials:**
- Username: `Nameless`
- Password: `Niniola12@`

## Dashboard Overview

The admin dashboard has 3 main sections:

### 1. 📋 Exams
Manage all your exams

**Create a New Exam:**
1. Click "+ Create New Exam" button
2. Enter:
   - **Exam Name** - e.g., "Biology 101"
   - **Description** - Optional details about the exam
   - **Time Limit** - How many minutes students have (e.g., 30)
3. Click "Create Exam"
4. Your exam code will be auto-generated

**Manage an Exam:**
1. Click "Manage" on an exam card
2. View exam details (code, time limit, question count)
3. Add questions manually OR generate with AI
4. Edit or delete questions as needed
5. Delete entire exam if needed

### 2. 🤖 AI Generate
Automatically create questions from documents

**Step-by-Step:**
1. Click "AI Generate" in sidebar
2. **Select Exam** - Choose which exam to add questions to
3. **Upload File** - Select a document:
   - Text files (.txt)
   - PDF documents (.pdf)
   - Word documents (.docx)
4. **Number of Questions** - How many questions to generate (default: 10)
5. Click "Generate Questions"
6. Wait for processing... ChatGPT will create questions
7. Questions appear in your exam automatically

**Tips for Best Results:**
- Use well-written, clear content
- Longer documents (500+ words) generate better questions
- Content should be on a single topic
- Educational or technical content works best
- Review and edit generated questions before giving to students

### 3. 📊 Results
Track student exam performance

**View Results:**
- See all completed exams
- Student name who took it
- Score (e.g., 8/10)
- Percentage score (80%)
- Date submitted
- Individual exam results

**Sharing Results:**
- Currently displayed in-app
- Plan to add PDF export in future versions

## Managing Questions

### Add Question Manually
1. Click "Manage" on exam
2. Click "+ Add Question"
3. Enter:
   - **Question** - The question text
   - **Options** - 4 possible answers (A, B, C, D)
   - **Correct Answer** - Select which option is correct
4. Click "Add Question"

### Edit Question
1. Open exam details
2. Click "Edit" on any question
3. Modify question, options, or correct answer
4. Click "Update Question"

### Delete Question
1. Open exam details
2. Click "Delete" on any question
3. Confirm deletion
4. Question is removed permanently

## Sharing Exams with Students

1. Create and setup your exam
2. Click "Manage" to view exam details
3. Copy the **Exam Code** (e.g., ABC123)
4. Share the code with students via:
   - Email
   - Chat/Messaging
   - Display on screen
   - Learning management system

**Student Access:**
- URL: http://localhost:3000/student-exam.html
- They enter their name and exam code
- Takes them directly to the exam

## Best Practices

✅ **DO:**
- Create exams with clear, unambiguous questions
- Review AI-generated questions for accuracy
- Set reasonable time limits (at least 1 min per question)
- Use descriptive exam names
- Keep exam descriptions helpful
- Test exams yourself before giving to students

❌ **DON'T:**
- Create exams with too tight time limits
- Use AI-generated questions without review
- Delete exams students are currently taking
- Share same exam code multiple times (use unique codes)
- Upload non-text files to AI generator

## Exam Tips

### Time Limits
- **Quick Quiz:** 5-10 minutes
- **Normal Exam:** 30-60 minutes
- **Comprehensive Test:** 90+ minutes
- **Rule of Thumb:** 1-2 minutes per question

### Question Difficulty
- Mix easy, medium, and hard questions
- Start with easier questions
- End with harder questions
- Avoid questions with obvious answers

### Question Types
Currently supported: Multiple Choice (4 options)
- Future versions will support more types

## Troubleshooting

### AI Generation Failed
- Check OpenAI API key is valid
- Verify file is readable (not corrupted)
- Try a different file
- Check you have API credits

### Can't Create Exam
- Verify all fields are filled
- Ensure time limit is a number
- Check server is running

### Question Not Saving
- Verify all 4 options are filled
- Check question text is not empty
- Select a correct answer
- Refresh page and try again

### Can't See Student Results
- Confirm students have submitted exams
- Results show after exam submission
- Check you're on the Results tab

## Advanced Tips

### Using AI Effectively
1. **Topic extraction:** Upload lecture notes to create quizzes
2. **Assessment:** Upload textbook chapters to create tests
3. **Quality control:** Always review AI questions
4. **Customization:** Edit questions to match your curriculum

### Exam Strategy
1. Create exam bank with 20-30 questions
2. Randomly select 10-15 for each student
3. Use different exams for different topics
4. Archive old exams you don't need

### Organizing Exams
- Use clear naming: "Biology_Ch1_Quiz" not "Test1"
- Add descriptions to explain exam purpose
- Group by subject/topic
- Use consistent naming convention

## Need Help?

Check the main README.md for:
- Full documentation
- API endpoints
- Troubleshooting guide
- Technology stack details

---

**Happy Creating! 🎓**
