# AI-Driven-Candidate-Assessment-System
The AI-Driven Candidate Assessment System is designed to streamline the hiring process by automating resume evaluation.


Project Overview

The AI-Driven Candidate Assessment System is designed to streamline the hiring process by automating resume evaluation. The system extracts skills from a candidate's resume, compares them to predefined job requirements, and generates a score. It is built using Node.js, Python, and PostgreSQL, integrating AI to provide accurate skill matching for HR departments.

Features:

    Automated Resume Parsing: Extracts key skills from uploaded resumes using spaCy NLP.
    Keyword Matching: Compares candidate skills with job requirements from a predefined keyword list.
    Candidate Scoring: Scores candidates based on matched skills.
    PDF Report Generation: Generates reports summarizing the evaluation.
    Database Storage: Saves resume data, responses, and matched skills to PostgreSQL.
    Frontend Form: A simple web form for candidates to submit their resumes and responses.
    HR-Friendly: Simplifies the recruitment process by automatically filtering candidates based on skills and qualifications.


How to Use the AI-Driven Candidate Assessment System
Prerequisites:

    Node.js v14+
    Python 3.7+
    PostgreSQL 12+
    spaCy with en_core_web_sm model installed

Step-by-Step Setup:

    Clone the Repository:

    bash

git clone https://github.com/your-repo/ai-driven-candidate-assessment.git
cd ai-driven-candidate-assessment

Install Dependencies:

    Node.js dependencies:

    bash

cd job-application-backend
npm install

Python dependencies:

bash

    pip install -r requirements.txt
    python -m spacy download en_core_web_sm

PostgreSQL Setup:

    Create a database:

    sql

CREATE DATABASE candidate_assessment;

Create the candidates table:

sql

    CREATE TABLE candidates (
      id SERIAL PRIMARY KEY,
      name VARCHAR(255),
      details TEXT,
      resume_path TEXT,
      responses TEXT[],
      submission_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
      extracted_skills TEXT
    );

Run the Server:

bash

node server.js

Access the Frontend: Open http://localhost:3000 in your browser to submit resumes and see the results.



Folder Structure and File Descriptions:

graphql

ai-driven-candidate-assessment/
│
├── job-application-backend/          # Backend folder (Node.js + Python)
│   ├── node_modules/                 # Node.js dependencies
│   ├── uploads/                      # Directory for uploaded resumes
│   ├── server.js                     # Main Node.js server file
│   ├── evaluate_assessment.py        # Python script for extracting and analyzing skills
│   ├── pdf_report_generator.py       # Script to generate PDF reports
│   ├── job_keywords.txt              # Contains job-related keywords
│   ├── package.json                  # Node.js project dependencies
│   ├── requirements.txt              # Python dependencies
│   └── package-lock.json             # Node.js package lock file
│
└── frontend/                         # Frontend folder
    ├── index.html                    # Main HTML file for user input form
    ├── styles.css                    # CSS file for styling
    ├── script.js                     # JavaScript file for form handling
    └── thank-you.html                # Confirmation page after form submission

Key Files:

    server.js: Manages the backend, file uploads, and database interaction.
    evaluate_assessment.py: Extracts and matches skills using NLP, and returns the result.
    job_keywords.txt: Contains the predefined keywords for job matching.
    index.html: The candidate's form submission interface.
    pdf_report_generator.py: Generates PDF reports for HR.



    ase Commands and Usage
Backend Commands:

    Install Dependencies:
        Node.js:

        bash

npm install

Python:

bash

    pip install -r requirements.txt
    python -m spacy download en_core_web_sm

Start the Backend Server:

bash

node server.js

    This starts the Node.js server, which listens for form submissions.

Run the Python Script Manually (for testing):

bash

    python3 evaluate_assessment.py <resume_path> <responses_json>

        Replace <resume_path> with the path to the PDF resume and <responses_json> with the candidate’s answers (as a JSON string).

PostgreSQL Commands:

    Create Database:

    sql

CREATE DATABASE candidate_assessment;

Create Table:

sql

CREATE TABLE candidates (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  details TEXT,
  resume_path TEXT,
  responses TEXT[],
  submission_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  extracted_skills TEXT
);

Query Data:

    Retrieve all records:

    sql

SELECT * FROM candidates;

Retrieve specific fields like extracted_skills:

sql

SELECT extracted_skills FROM candidates;




Code Documentation
1. server.js:

    Purpose: The main Node.js server file that handles file uploads, executes the Python script for resume analysis, and stores results in the PostgreSQL database.
    Key Functions:
        File Upload: Uses Multer to handle the resume upload and store it in the /uploads directory.
        Python Script Execution: Executes evaluate_assessment.py to extract skills and return matched results.
        Database Interaction: Inserts candidate details, responses, and matched skills into the PostgreSQL database.

2. evaluate_assessment.py:

    Purpose: A Python script that extracts skills from a resume, compares them to predefined job keywords, and calculates a score.
    Key Functions:
        extract_text_from_cv: Extracts text from the PDF resume using PyPDF2.
        extract_skills_and_experience_from_resume: Uses spaCy to identify relevant skills and experiences.
        score_candidate_skills: Compares extracted skills to job keywords and calculates the number of matched skills.
        main(): The main function that processes the resume, extracts skills, compares them with job requirements, and prints the result as JSON.

3. pdf_report_generator.py:

    Purpose: Generates a PDF report summarizing the extracted skills, score, and matched skills for HR purposes.
    Key Functions:
        generate_pdf_report(result, filename): Generates a PDF with the results of the evaluation, saving it as filename.

4. job_keywords.txt:

    Purpose: Contains the list of job-related keywords. These keywords are used to match against the candidate's skills extracted from their resume.

Frontend Files:

    index.html: A form for candidates to submit their resume and answers to the job application questions.
    styles.css: Styles for the frontend form.
    script.js: Manages form submission and sends the data to the backend.





    Project Report: AI-Driven Candidate Assessment System
1. Introduction:

The AI-Driven Candidate Assessment System is a recruitment tool designed to streamline the hiring process for HR departments by automating the evaluation of resumes and candidate responses. This system integrates NLP for resume parsing and AI-based skill matching with job requirements, providing a fast and accurate evaluation of candidates' qualifications.
2. Objectives:

    Automate candidate evaluation based on skill extraction.
    Improve recruitment efficiency by providing accurate candidate assessments.
    Generate detailed reports for HR use.

3. Methodology:

    Data Collection: The system accepts candidate resumes in PDF format and uses a predefined list of job-related keywords from job_keywords.txt.
    Skill Extraction: Using spaCy and basic AI models, the system extracts skills from the resume text.
    Matching Algorithm: Extracted skills are matched against job keywords to compute a match score, which is then stored in the PostgreSQL database.
    PDF Report Generation: A PDF report is generated with details about the extracted and matched skills.

4. Technology Stack:

    Frontend: HTML, CSS, JavaScript (for form submission).
    Backend: Node.js (for server-side processing and file uploads).
    NLP and AI: Python, spaCy (for resume parsing), PyPDF2 (for PDF extraction).
    Database: PostgreSQL (for storing candidate details and matched skills).

5. Features:

    Skill Extraction: Automatically parses resumes to extract relevant skills using NLP.
    Keyword Matching: Compares candidate skills with job requirements and computes a score.
    Candidate Scoring: Provides a match score based on the number of skills that align with the job's requirements.
    PDF Reports: Generates detailed reports for HR to evaluate candidate suitability.
    Database Storage: Saves candidate data, responses, and skill matches in a secure PostgreSQL database.

6. Results:

The system is capable of receiving resumes, extracting relevant skills, comparing them with job requirements, and generating reports. It reduces the manual effort involved in screening candidates, making the recruitment process faster and more efficient.



7. Limitations and Future Improvements:

    The current skill extraction is based on a simple rule-based approach. In future updates, the AI model will be improved using Named Entity Recognition (NER) or a specialized skill extraction model for more accurate results.
    Additional improvements to the job keyword list and custom skills dictionary could further enhance accuracy.



. Challenges Faced:

    Skill Extraction Accuracy: The basic rule-based approach (identifying nouns and proper nouns) sometimes misses relevant skills or extracts irrelevant terms.
    Parsing Diverse Resume Formats: Variability in how candidates format their resumes can impact text extraction accuracy.
    Keyword Matching: Ensuring that the extracted skills are relevant and adequately matched against the predefined job keywords.

2. Potential Use Cases:

    Recruitment Automation: HR departments can automatically screen and shortlist candidates based on skills.
    Skill Gap Analysis: Helps identify skill gaps between a candidate’s qualifications and job requirements.
    Job Fit Prediction: Predicts how well a candidate’s skills match the job requirements.

3. Security Considerations:

    Data Privacy: Candidate information must be stored securely, especially sensitive details like resumes and personal responses.
    Secure File Upload: Ensure file uploads are sanitized to prevent malicious files from being uploaded.
    Database Security: PostgreSQL should be configured with proper access controls, encryption, and regular security patches.

4. Detailed Example Scenario:

    Step 1: A candidate submits a resume and answers job-related questions through the frontend form.
    Step 2: The system processes the resume, extracting skills such as "Python," "SQL," and "Data Analysis."
    Step 3: The extracted skills are compared against the job keyword list. If 5 out of 10 required skills match, the candidate is scored accordingly.
    Step 4: A PDF report is generated with the evaluation results and stored in the database for HR to review.
