### Corrected Endpoints

Here are the corrected and logically structured endpoints:

1. **User Endpoints**:

   - POST /api/auth/register: Register a new user.
   - POST /api/auth/login: Login an existing user.
   - GET /api/auth/me: Get the current user's profile.
   - PUT /api/auth/me: Update the current user's profile.
   - POST /api/auth/logout: Logout the current user.

2. **Job Endpoints**:

   - GET /api/jobs: Get a list of all jobs.
   - GET /api/jobs/{jobId}: Get a job by ID.
   - POST /api/jobs: Create a new job.
   - PUT /api/jobs/{jobId}: Update a job.
   - DELETE /api/jobs/{jobId}: Delete a job.

3. **Candidate Endpoints**:

   - GET /api/candidates: Get a list of all candidates.
   - GET /api/candidates/{candidateId}: Get a candidate by ID.
   - POST /api/candidates: Create a new candidate.
   - PUT /api/candidates/{candidateId}: Update a candidate.
   - DELETE /api/candidates/{candidateId}: Delete a candidate.

4. **Employer Endpoints**:

   - GET /api/employers: Get a list of all employers.
   - GET /api/employers/{employerId}: Get an employer by ID.
   - POST /api/employers: Create a new employer.
   - PUT /api/employers/{employerId}: Update an employer.
   - DELETE /api/employers/{employerId}: Delete an employer.

5. **Search Endpoints for Jobs and Candidates**:
   - GET /api/search/jobs: Search for jobs based on various criteria.
   - GET /api/search/jobs/{jobId}: Retrieve a specific job by ID.
   - GET /api/search/candidates: Search for candidates based on various criteria.
   - GET /api/search/candidates/{candidateId}: Retrieve a specific candidate by ID.
   - GET /api/search/recently-posted-jobs: Retrieve a list of recently posted jobs.

### Sample Responses

#### User Endpoints

1. **POST /api/auth/register**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "User registered successfully.",
     "data": {
       "user_id": 1,
       "email": "user@example.com",
       "created_at": "2024-07-13T12:34:56Z"
     }
   }
   ```

   **Validation Error:**

   ```json
   {
     "status": "error",
     "message": "Validation error.",
     "errors": {
       "email": "Email is required.",
       "password": "Password must be at least 8 characters."
     }
   }
   ```

2. **POST /api/auth/login**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Login successful.",
     "data": {
       "token": "jwt-token-here"
     }
   }
   ```

   **Authentication Error:**

   ```json
   {
     "status": "error",
     "message": "Invalid email or password."
   }
   ```

3. **GET /api/auth/me**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "user_id": 1,
       "email": "user@example.com",
       "profile": {
         "first_name": "John",
         "last_name": "Doe",
         "profile_picture": "url-to-picture"
       }
     }
   }
   ```

   **Authentication Error:**

   ```json
   {
     "status": "error",
     "message": "Authentication required."
   }
   ```

4. **PUT /api/auth/me**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Profile updated successfully.",
     "data": {
       "user_id": 1,
       "email": "user@example.com",
       "profile": {
         "first_name": "John",
         "last_name": "Doe",
         "profile_picture": "url-to-updated-picture"
       }
     }
   }
   ```

   **Validation Error:**

   ```json
   {
     "status": "error",
     "message": "Validation error.",
     "errors": {
       "first_name": "First name is required."
     }
   }
   ```

5. **POST /api/auth/logout**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Logout successful."
   }
   ```

   **Authentication Error:**

   ```json
   {
     "status": "error",
     "message": "Authentication required."
   }
   ```

#### Job Endpoints

1. **GET /api/jobs**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "job_id": 1,
         "job_title": "Software Engineer",
         "date_posted": "2024-07-01",
         "employer_id": 1
       },
       {
         "job_id": 2,
         "job_title": "Data Analyst",
         "date_posted": "2024-07-05",
         "employer_id": 2
       }
     ]
   }
   ```

2. **GET /api/jobs/{jobId}**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "job_id": 1,
       "job_title": "Software Engineer",
       "date_posted": "2024-07-01",
       "employer_id": 1,
       "description": "Job description here..."
     }
   }
   ```

   **Error (Job Not Found):**

   ```json
   {
     "status": "error",
     "message": "Job not found."
   }
   ```

3. **POST /api/jobs**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Job created successfully.",
     "data": {
       "job_id": 1,
       "job_title": "Software Engineer",
       "date_posted": "2024-07-13",
       "employer_id": 1
     }
   }
   ```

   **Validation Error:**

   ```json
   {
     "status": "error",
     "message": "Validation error.",
     "errors": {
       "job_title": "Job title is required.",
       "date_posted": "Date posted is required."
     }
   }
   ```

4. **PUT /api/jobs/{jobId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Job updated successfully.",
     "data": {
       "job_id": 1,
       "job_title": "Senior Software Engineer",
       "date_posted": "2024-07-01",
       "employer_id": 1
     }
   }
   ```

   **Error (Job Not Found):**

   ```json
   {
     "status": "error",
     "message": "Job not found."
   }
   ```

5. **DELETE /api/jobs/{jobId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Job deleted successfully."
   }
   ```

   **Error (Job Not Found):**

   ```json
   {
     "status": "error",
     "message": "Job not found."
   }
   ```

#### Candidate Endpoints

1. **GET /api/candidates**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "candidate_id": 1,
         "first_name": "Jane",
         "last_name": "Doe",
         "profile_picture": "url-to-picture"
       },
       {
         "candidate_id": 2,
         "first_name": "John",
         "last_name": "Smith",
         "profile_picture": "url-to-picture"
       }
     ]
   }
   ```

2. **GET /api/candidates/{candidateId}**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "candidate_id": 1,
       "first_name": "Jane",
       "last_name": "Doe",
       "profile_picture": "url-to-picture",
       "resume": "url-to-resume"
     }
   }
   ```

   **Error (Candidate Not Found):**

   ```json
   {
     "status": "error",
     "message": "Candidate not found."
   }
   ```

3. **POST /api/candidates**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Candidate created successfully.",
     "data": {
       "candidate_id": 1,
       "first_name": "Jane",
       "last_name": "Doe",
       "profile_picture": "url-to-picture",
       "resume": "url-to-resume"
     }
   }
   ```

   **Validation Error:**

   ```json
   {
     "status": "error",
     "message": "Validation error.",
     "errors": {
       "first_name": "First name is required.",
       "resume": "Resume is required."
     }
   }
   ```

4. **PUT /api/candidates/{candidateId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Candidate updated successfully.",
     "data": {
       "candidate_id": 1,
       "first_name": "Jane",
       "last_name": "Doe",
       "profile_picture": "url-to-updated-picture",
       "resume": "url-to-updated-resume"
     }
   }
   ```

   **Error (Candidate Not Found):**

   ```json
   {
     "status": "error",
     "message": "Candidate not found."
   }
   ```

5. **DELETE /api/candidates/{candidateId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Candidate deleted successfully."
   }
   ```

   **Error (Candidate Not Found):**

   ```json
   {
     "status": "error",
     "message": "Candidate not found."
   }
   ```

#### Employer Endpoints

1. **GET /api/employers**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "employer_id": 1,
         "company_name": "Tech Innovations Inc.",
         "point_of_contact": "John Doe"
       },
       {
         "employer_id": 2,
         "company_name": "Data Solutions Ltd.",
         "point_of_contact": "Jane Smith"
       }
     ]
   }
   ```

2. **GET /api/employers/{employerId}**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "employer_id": 1,
       "company_name": "Tech Innovations Inc.",
       "point_of_contact": "John Doe"
     }
   }
   ```

   **Error (Employer Not Found):**

   ```json
   {
     "status": "error",
     "message": "Employer not found."
   }
   ```

3. **POST /api/employers**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Employer created successfully.",
     "data": {
       "employer_id": 1,
       "company_name": "Tech Innovations Inc.",
       "point_of_contact": "John Doe"
     }
   }
   ```

   **Validation Error:**

   ```json
   {
     "status": "error",
     "message": "Validation error.",
     "errors": {
       "company_name": "Company name is required.",
       "point_of_contact": "Point of contact is required."
     }
   }
   ```

4. **PUT /api/employers/{employerId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Employer updated successfully.",
     "data": {
       "employer_id": 1,
       "company_name": "Tech Innovations Inc.",
       "point_of_contact": "John Doe"
     }
   }
   ```

   **Error (Employer Not Found):**

   ```json
   {
     "status": "error",
     "message": "Employer not found."
   }
   ```

5. **DELETE /api/employers/{employerId}**

   **Success:**

   ```json
   {
     "status": "success",
     "message": "Employer deleted successfully."
   }
   ```

   **Error (Employer Not Found):**

   ```json
   {
     "status": "error",
     "message": "Employer not found."
   }
   ```

#### Search Endpoints

1. **GET /api/search/jobs**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "job_id": 1,
         "job_title": "Software Engineer",
         "date_posted": "2024-07-01",
         "employer_id": 1,
         "description": "Job description here..."
       },
       {
         "job_id": 2,
         "job_title": "Data Analyst",
         "date_posted": "2024-07-05",
         "employer_id": 2,
         "description": "Job description here..."
       }
     ]
   }
   ```

2. **GET /api/search/jobs/{jobId}**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "job_id": 1,
       "job_title": "Software Engineer",
       "date_posted": "2024-07-01",
       "employer_id": 1,
       "description": "Job description here..."
     }
   }
   ```

   **Error (Job Not Found):**

   ```json
   {
     "status": "error",
     "message": "Job not found."
   }
   ```

3. **GET /api/search/candidates**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "candidate_id": 1,
         "first_name": "Jane",
         "last_name": "Doe",
         "profile_picture": "url-to-picture",
         "resume": "url-to-resume"
       },
       {
         "candidate_id": 2,
         "first_name": "John",
         "last_name": "Smith",
         "profile_picture": "url-to-picture",
         "resume": "url-to-resume"
       }
     ]
   }
   ```

4. **GET /api/search/candidates/{candidateId}**

   **Success:**

   ```json
   {
     "status": "success",
     "data": {
       "candidate_id": 1,
       "first_name": "Jane",
       "last_name": "Doe",
       "profile_picture": "url-to-picture",
       "resume": "url-to-resume"
     }
   }
   ```

   **Error (Candidate Not Found):**

   ```json
   {
     "status": "error",
     "message": "Candidate not found."
   }
   ```

5. **GET /api/search/recently-posted-jobs**

   **Success:**

   ```json
   {
     "status": "success",
     "data": [
       {
         "job_id": 3,
         "job_title": "UI/UX Designer",
         "date_posted": "2024-07-10",
         "employer_id": 3,
         "description": "Job description here..."
       },
       {
         "job_id": 4,
         "job_title": "Product Manager",
         "date_posted": "2024-07-12",
         "employer_id": 4,
         "description": "Job description here..."
       }
     ]
   }
   ```
