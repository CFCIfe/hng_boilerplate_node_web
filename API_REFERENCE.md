## [DB DIAGRAM]

![DB DIAGRAM](https://github.com/CFCIfe/hng_boilerplate_node_web/blob/36a100dfefd5c5b2acebddb231cbee8cb32b5079/HNG%20BACKEND%20-%20JOB%20POSTING%20SITE.png)

## Folder Structure

```
.
├── API_DOC_Techie_dev.json
├── API_DOC_tee.json
├── API_DOCUMENTATION.html
├── API_DOCUMENTATION.json
├── API_DOC_VICTOR.json
├── API_REFERENCE.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTORS_GUIDE.md
├── Endpoints.md
├── HNG BACKEND - JOB POSTING SITE.png
├── README.md
├── src
│   ├── controllers
│   ├── interfaces
│   ├── services
│   └── utils
└── tsconfig.json
```

# JobConnect API Documentation

API for JobConnect job portal

More information: [https://helloreverb.com](https://helloreverb.com)

Contact Info: [hello@helloreverb.com](hello@helloreverb.com)

Version: 1.0.0

BasePath:/v1

All rights reserved

http://apache.org/licenses/LICENSE-2.0.html

## Access

## Methods

\[ Jump to [Models](#__Models) \]

### Table of Contents

#### [Auth](#Auth)

- [`post /api/auth/login`](#apiAuthLoginPost)
- [`post /api/auth/logout`](#apiAuthLogoutPost)
- [`delete /api/auth/me`](#apiAuthMeDelete)
- [`get /api/auth/me`](#apiAuthMeGet)
- [`put /api/auth/me`](#apiAuthMePut)
- [`post /api/auth/register`](#apiAuthRegisterPost)

#### [Candidates](#Candidates)

- [`delete /api/candidates/{candidateId}`](#apiCandidatesCandidateIdDelete)
- [`get /api/candidates/{candidateId}`](#apiCandidatesCandidateIdGet)
- [`put /api/candidates/{candidateId}`](#apiCandidatesCandidateIdPut)
- [`get /api/candidates`](#apiCandidatesGet)
- [`post /api/candidates`](#apiCandidatesPost)

#### [Employers](#Employers)

- [`post /api/employers`](#createEmployer)
- [`delete /api/employers/{employerId}`](#deleteEmployer)
- [`get /api/employers/{employerId}`](#getEmployerById)
- [`get /api/employers`](#getEmployers)
- [`put /api/employers/{employerId}`](#updateEmployer)

#### [Frontend](#Frontend)

- [`post /contact_us`](#contactUsPost)
- [`get /profile-settings`](#profileSettingsGet)
- [`get /settings`](#settingsGet)

#### [Jobs](#Jobs)

- [`post /api/jobs`](#createJob)
- [`delete /api/jobs/{jobId}`](#deleteJob)
- [`get /api/jobs/{jobId}`](#getJobById)
- [`get /api/jobs`](#getJobs)
- [`put /api/jobs/{jobId}`](#updateJob)

#### [Search](#Search)

- [`get /api/search/candidates/{candidateId}`](#apiSearchCandidatesCandidateIdGet)
- [`get /api/search/recently-posted-jobs`](#apiSearchRecentlyPostedJobsGet)
- [`get /api/search/jobs/{jobId}`](#getJobById)
- [`get /api/search/candidates`](#searchCandidates)
- [`get /api/search/jobs`](#searchJobs)

# Auth

[Up](#__Methods)

```
post /api/auth/login
```

Login an existing user (apiAuthLoginPost)

Authenticate an existing user

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [auth_login_body](#auth_login_body) (required)

Body Parameter —

### Return type

[inline_response_200_2](#inline_response_200_2)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "token" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6Ik9saXZpYSBQb3BlIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
  },
  "message" : "User logged in successfully",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

User logged in successfully [inline_response_200_2](#inline_response_200_2)

#### 401

Invalid credentials[](#)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

[Up](#__Methods)

```
post /api/auth/logout
```

Logout the current user (apiAuthLogoutPost)

Logout the current user

### Responses

#### 200

User logged out successfully[](#)

---

[Up](#__Methods)

```
delete /api/auth/me
```

Delete the current user's profile (apiAuthMeDelete)

Delete the current user's profile

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 204

User profile deleted successfully[](#)

#### 400

Invalid input [inline_response_400](#inline_response_400)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

[Up](#__Methods)

```
get /api/auth/me
```

Get the current user's profile (apiAuthMeGet)

Retrieve the current user's profile information

### Return type

[inline_response_200_3](#inline_response_200_3)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "firstName" : "Olivia",
    "lastName" : "Pope",
    "user_id" : 1,
    "email" : "olivia.pope@example.com"
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

User profile retrieved successfully [inline_response_200_3](#inline_response_200_3)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

[Up](#__Methods)

```
put /api/auth/me
```

Update the current user's profile (apiAuthMePut)

Update the current user's profile information

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [UserResponse](#UserResponse) (required)

Body Parameter —

### Return type

[inline_response_200_4](#inline_response_200_4)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "firstName" : "Olivia",
    "lastName" : "Pope",
    "password" : "hashedpassword",
    "user_id" : 1,
    "email" : "olivia.pope@example.com"
  },
  "message" : "User profile updated successfully",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

User profile updated successfully [inline_response_200_4](#inline_response_200_4)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

[Up](#__Methods)

```
post /api/auth/register
```

Register a new user (apiAuthRegisterPost)

Create a new user account

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [User](#User) (required)

Body Parameter —

### Return type

[inline_response_201](#inline_response_201)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "firstName" : "Olivia",
    "lastName" : "Pope",
    "user_id" : 1,
    "email" : "olivia.pope@example.com"
  },
  "message" : "User created successfully",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 201

User created successfully [inline_response_201](#inline_response_201)

#### 409

User already exists [inline_response_409](#inline_response_409)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

# Candidates

[Up](#__Methods)

```
delete /api/candidates/{candidateId}
```

Delete a candidate (apiCandidatesCandidateIdDelete)

Delete a candidate by their ID

### Path parameters

candidateId (required)

Path Parameter — The ID of the candidate to delete format: int64

### Responses

#### 204

Candidate deleted successfully[](#)

#### 400

The specified candidate ID is invalid (not a number)[](#)

#### 404

A candidate with the specified ID was not found[](#)

#### default

Unexpected error[](#)

---

[Up](#__Methods)

```
get /api/candidates/{candidateId}
```

Get a candidate by ID (apiCandidatesCandidateIdGet)

Retrieve a candidate by their ID

### Path parameters

candidateId (required)

Path Parameter — The ID of the candidate to return format: int64

### Return type

[inline_response_200_6](#inline_response_200_6)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Candidate retrieved successfully [inline_response_200_6](#inline_response_200_6)

#### 400

The specified candidate ID is invalid (not a number)[](#)

#### 404

A candidate with the specified ID was not found[](#)

#### default

Unexpected error[](#)

---

[Up](#__Methods)

```
put /api/candidates/{candidateId}
```

Update a candidate (apiCandidatesCandidateIdPut)

Update a candidate's information

### Path parameters

candidateId (required)

Path Parameter — The ID of the candidate to update format: int64

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [Candidate](#Candidate) (required)

Body Parameter —

### Return type

[inline_response_200_6](#inline_response_200_6)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Candidate updated successfully [inline_response_200_6](#inline_response_200_6)

#### 400

The specified candidate ID is invalid (not a number)[](#)

#### 404

A candidate with the specified ID was not found[](#)

#### default

Unexpected error[](#)

---

[Up](#__Methods)

```
get /api/candidates
```

Get a list of all candidates (apiCandidatesGet)

Retrieve a list of all candidates

### Return type

[inline_response_200_5](#inline_response_200_5)

### Example data

Content-Type: application/json

```
{
  "data" : [ {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  }, {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  } ],
  "message" : "Candidates retrieved successfully",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

List of candidates retrieved successfully [inline_response_200_5](#inline_response_200_5)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

[Up](#__Methods)

```
post /api/candidates
```

Create a new candidate (apiCandidatesPost)

Register a new candidate

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [Candidate](#Candidate) (required)

Body Parameter —

### Return type

[inline_response_201_1](#inline_response_201_1)

### Example data

Content-Type: application/json

```
{
  "data" : [ {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  }, {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  } ],
  "message" : "Candidates updated successfully",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 201

Candidates updated successfully [inline_response_201_1](#inline_response_201_1)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

# Employers

[Up](#__Methods)

```
post /api/employers
```

Create a new employer (createEmployer)

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`

### Request body

body [New_Employer_RequestBody](#New_Employer_RequestBody) (required)

Body Parameter — Employer object that needs to be added

### Return type

[inline_response_201_2](#inline_response_201_2)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "company_name" : "Tech Corp",
    "employer_id" : "67890e5-12d3-a456-426614174000",
    "point_of_contact" : {
      "address" : "123 Tech Street, New York, NY",
      "name" : "John Doe",
      "contactNumber" : "555-1234",
      "email" : "contact@techcorp.com"
    }
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 201

Employer created successfully. [inline_response_201_2](#inline_response_201_2)

#### 400

Invalid input [inline_response_400](#inline_response_400)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

[Up](#__Methods)

```
delete /api/employers/{employerId}
```

Delete an employer (deleteEmployer)

### Path parameters

employerId (required)

Path Parameter — ID of the employer to delete

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 204

Employer deleted successfully.[](#)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

[Up](#__Methods)

```
get /api/employers/{employerId}
```

Get an employer by ID (getEmployerById)

### Path parameters

employerId (required)

Path Parameter — ID of the employer to retrieve

### Return type

[inline_response_201_2](#inline_response_201_2)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "company_name" : "Tech Corp",
    "employer_id" : "67890e5-12d3-a456-426614174000",
    "point_of_contact" : {
      "address" : "123 Tech Street, New York, NY",
      "name" : "John Doe",
      "contactNumber" : "555-1234",
      "email" : "contact@techcorp.com"
    }
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Employer updated successfully. [inline_response_201_2](#inline_response_201_2)

#### 404

Employer not found.[](#)

---

[Up](#__Methods)

```
get /api/employers
```

Get a list of all employers (getEmployers)

### Return type

[inline_response_200_9](#inline_response_200_9)

### Example data

Content-Type: application/json

```
{
  "data" : [ {
    "company_name" : "Tech Corp",
    "employer_id" : "67890e5-12d3-a456-426614174000",
    "point_of_contact" : {
      "address" : "123 Tech Street, New York, NY",
      "name" : "John Doe",
      "contactNumber" : "555-1234",
      "email" : "contact@techcorp.com"
    }
  }, {
    "company_name" : "Tech Corp",
    "employer_id" : "67890e5-12d3-a456-426614174000",
    "point_of_contact" : {
      "address" : "123 Tech Street, New York, NY",
      "name" : "John Doe",
      "contactNumber" : "555-1234",
      "email" : "contact@techcorp.com"
    }
  } ],
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

A list of employers. [inline_response_200_9](#inline_response_200_9)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

[Up](#__Methods)

```
put /api/employers/{employerId}
```

Update an employer (updateEmployer)

### Path parameters

employerId (required)

Path Parameter — ID of the employer to update

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`
- `application/x-www-form-urlencoded`

### Request body

body [Employer](#Employer) (required)

Body Parameter — Employer object with updated information

### Form parameters

employer_id (required)

Form Parameter —

company_name (required)

Form Parameter —

point_of_contact (required)

Form Parameter —

### Return type

[inline_response_201_2](#inline_response_201_2)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "company_name" : "Tech Corp",
    "employer_id" : "67890e5-12d3-a456-426614174000",
    "point_of_contact" : {
      "address" : "123 Tech Street, New York, NY",
      "name" : "John Doe",
      "contactNumber" : "555-1234",
      "email" : "contact@techcorp.com"
    }
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Employer updated successfully. [inline_response_201_2](#inline_response_201_2)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

# Frontend

[Up](#__Methods)

```
post /contact_us
```

Contact us (contactUsPost)

Send a message to the support team

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/pdf`

### Request body

body [Object](#Object) (required)

Body Parameter —

### Responses

---

[Up](#__Methods)

```
get /profile-settings
```

Get profile settings (profileSettingsGet)

Get profile settings for the user

### Return type

[inline_response_200_1](#inline_response_200_1)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "firstName" : "Olivia",
    "lastName" : "Pope",
    "profilePicture" : "https://example.com/olivia-pope.jpg",
    "theme" : "dark",
    "email" : "oliviapope@example.com"
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Profile settings retrieved successfully [inline_response_200_1](#inline_response_200_1)

---

[Up](#__Methods)

```
get /settings
```

Get settings (settingsGet)

Get settings for the user

### Return type

[inline_response_200](#inline_response_200)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "theme" : "dark",
    "notifications" : true
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Settings retrieved successfully [inline_response_200](#inline_response_200)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

# Jobs

[Up](#__Methods)

```
post /api/jobs
```

Create a new job (createJob)

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`
- `application/x-www-form-urlencoded`

### Request body

body [Job](#Job) (required)

Body Parameter — Job object that needs to be added

### Form parameters

job_id (required)

Form Parameter —

title (required)

Form Parameter —

description (required)

Form Parameter —

company (required)

Form Parameter —

location (required)

Form Parameter —

work_style (required)

Form Parameter —

min_salary (required)

Form Parameter — format: double

max_salary (required)

Form Parameter —

### Return type

[Job](#Job)

### Example data

Content-Type: application/json

```
{
  "max_salary" : 300000,
  "work_style" : "Remote",
  "job_id" : "12345",
  "description" : "Responsible for developing software solutions.",
  "min_salary" : 100000,
  "company" : "Tech Corp",
  "location" : "New York, NY",
  "title" : "Software Developer"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 201

Job created successfully. [Job](#Job)

#### 400

Invalid input [inline_response_400](#inline_response_400)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

[Up](#__Methods)

```
delete /api/jobs/{jobId}
```

Delete a job (deleteJob)

### Path parameters

jobId (required)

Path Parameter — ID of the job to delete

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 204

Job deleted successfully.[](#)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

[Up](#__Methods)

```
get /api/jobs/{jobId}
```

Get a job by ID (getJobById)

### Path parameters

jobId (required)

Path Parameter — ID of the job to retrieve

### Return type

[Unprotected_Job_Response](#Unprotected_Job_Response)

### Example data

Content-Type: application/json

```
{
  "description" : "Responsible for developing software solutions.",
  "company" : "Tech Corp",
  "location" : "New York, NY",
  "id" : "123e349-12d3-a456-426614174000",
  "title" : "Software Developer"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Job updated successfully. [Unprotected_Job_Response](#Unprotected_Job_Response)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

[Up](#__Methods)

```
get /api/jobs
```

Get a list of all jobs (getJobs)

### Return type

[inline_response_200_7](#inline_response_200_7)

### Example data

Content-Type: application/json

```
{
  "data" : [ {
    "max_salary" : 300000,
    "work_style" : "Remote",
    "job_id" : "12345",
    "description" : "Responsible for developing software solutions.",
    "min_salary" : 100000,
    "company" : "Tech Corp",
    "location" : "New York, NY",
    "title" : "Software Developer"
  }, {
    "max_salary" : 300000,
    "work_style" : "Remote",
    "job_id" : "12345",
    "description" : "Responsible for developing software solutions.",
    "min_salary" : 100000,
    "company" : "Tech Corp",
    "location" : "New York, NY",
    "title" : "Software Developer"
  } ],
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

A list of jobs. [inline_response_200_7](#inline_response_200_7)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

---

[Up](#__Methods)

```
put /api/jobs/{jobId}
```

Update a job (updateJob)

### Path parameters

jobId (required)

Path Parameter — ID of the job to update

### Consumes

This API call consumes the following media types via the Content-Type request header:

- `application/json`
- `application/x-www-form-urlencoded`

### Request body

body [Job](#Job) (required)

Body Parameter — Job object with updated information

### Form parameters

job_id (required)

Form Parameter —

title (required)

Form Parameter —

description (required)

Form Parameter —

company (required)

Form Parameter —

location (required)

Form Parameter —

work_style (required)

Form Parameter —

min_salary (required)

Form Parameter — format: double

max_salary (required)

Form Parameter —

### Return type

[inline_response_200_8](#inline_response_200_8)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "max_salary" : 300000,
    "work_style" : "Remote",
    "job_id" : "12345",
    "description" : "Responsible for developing software solutions.",
    "min_salary" : 100000,
    "company" : "Tech Corp",
    "location" : "New York, NY",
    "title" : "Software Developer"
  },
  "message" : "Job updated successfully.",
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Job updated successfully. [inline_response_200_8](#inline_response_200_8)

#### 400

Invalid input [inline_response_400](#inline_response_400)

#### 401

Unauthorized request [inline_response_401](#inline_response_401)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

#### 422

Validation Error [inline_response_422](#inline_response_422)

---

# Search

[Up](#__Methods)

```
get /api/search/candidates/{candidateId}
```

Retrieve a specific candidate by ID (apiSearchCandidatesCandidateIdGet)

Retrieve a specific candidate by ID

### Path parameters

candidateId (required)

Path Parameter —

### Return type

[inline_response_200_6](#inline_response_200_6)

### Example data

Content-Type: application/json

```
{
  "data" : {
    "candidate_id" : "123et4-12345-12345-12345",
    "resume" : "https://example.com/john-doe-resume.pdf",
    "last_name" : "Doe",
    "profile_picture" : "https://example.com/john-doe.jpg",
    "first_name" : "Doe",
    "email" : "john.doe@example.com"
  },
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Candidate retrieved successfully [inline_response_200_6](#inline_response_200_6)

#### 404

The specified resource was not found [inline_response_404](#inline_response_404)

---

[Up](#__Methods)

```
get /api/search/recently-posted-jobs
```

Retrieve a list of recently posted jobs (apiSearchRecentlyPostedJobsGet)

Retrieve a list of recently posted jobs

### Return type

[inline_response_200_10](#inline_response_200_10)

### Example data

Content-Type: application/json

```
{
  "data" : [ {
    "date_posted" : "2021-01-01",
    "job_id" : "12345d-12345-12345-12345",
    "description" : "description",
    "job_title" : "Software Developer",
    "employer_id" : "12e324-12345-12345-12345"
  }, {
    "date_posted" : "2021-01-01",
    "job_id" : "12345d-12345-12345-12345",
    "description" : "description",
    "job_title" : "Software Developer",
    "employer_id" : "12e324-12345-12345-12345"
  } ],
  "status" : "success"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

List of jobs retrieved successfully [inline_response_200_10](#inline_response_200_10)

---

[Up](#__Methods)

```
get /api/search/jobs/{jobId}
```

Retrieve a specific job by ID (getJobById)

Retrieve job details by job ID

### Path parameters

jobId (required)

Path Parameter — ID of the job to retrieve

### Return type

[Job](#Job)

### Example data

Content-Type: application/json

```
{
  "max_salary" : 300000,
  "work_style" : "Remote",
  "job_id" : "12345",
  "description" : "Responsible for developing software solutions.",
  "min_salary" : 100000,
  "company" : "Tech Corp",
  "location" : "New York, NY",
  "title" : "Software Developer"
}
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Successful operation [Job](#Job)

#### 400

Invalid job ID [JobIdError](#JobIdError)

#### 401

Unauthorized [UnauthorizedError](#UnauthorizedError)

#### 404

Job not found [JobNotFoundError](#JobNotFoundError)

---

[Up](#__Methods)

```
get /api/search/candidates
```

Search for candidates based on various criteria (searchCandidates)

Search for candidates using various criteria

### Query parameters

firstName (optional)

Query Parameter — First name of the candidate

lastName (optional)

Query Parameter — Last name of the candidate

email (optional)

Query Parameter — Email of the candidate

### Return type

array\[[Candidate](#Candidate)\]

### Example data

Content-Type: application/json

```
[ {
  "candidate_id" : "123et4-12345-12345-12345",
  "resume" : "https://example.com/john-doe-resume.pdf",
  "last_name" : "Doe",
  "profile_picture" : "https://example.com/john-doe.jpg",
  "first_name" : "Doe",
  "email" : "john.doe@example.com"
}, {
  "candidate_id" : "123et4-12345-12345-12345",
  "resume" : "https://example.com/john-doe-resume.pdf",
  "last_name" : "Doe",
  "profile_picture" : "https://example.com/john-doe.jpg",
  "first_name" : "Doe",
  "email" : "john.doe@example.com"
} ]
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Successful operation

#### 400

Invalid search criteria [CandidateSearchError](#CandidateSearchError)

#### 401

Unauthorized [UnauthorizedError](#UnauthorizedError)

#### 404

No candidates found matching the provided criteria [CandidateNotFoundError](#CandidateNotFoundError)

---

[Up](#__Methods)

```
get /api/search/jobs
```

Search for jobs based on various criteria (searchJobs)

Multiple status values can be provided with comma-separated strings

### Query parameters

status (optional)

Query Parameter — Status values to filter jobs by default: available

### Return type

array\[[Job](#Job)\]

### Example data

Content-Type: application/json

```
[ {
  "max_salary" : 300000,
  "work_style" : "Remote",
  "job_id" : "12345",
  "description" : "Responsible for developing software solutions.",
  "min_salary" : 100000,
  "company" : "Tech Corp",
  "location" : "New York, NY",
  "title" : "Software Developer"
}, {
  "max_salary" : 300000,
  "work_style" : "Remote",
  "job_id" : "12345",
  "description" : "Responsible for developing software solutions.",
  "min_salary" : 100000,
  "company" : "Tech Corp",
  "location" : "New York, NY",
  "title" : "Software Developer"
} ]
```

### Produces

This API call produces the following media types according to the Accept request header; the media type will be conveyed by the Content-Type response header.

- `application/json`

### Responses

#### 200

Successful operation

#### 400

Invalid status value [InvalidStatusError](#InvalidStatusError)

#### 401

Unauthorized [UnauthorizedError](#UnauthorizedError)

#### 404

No jobs found matching the provided criteria [JobNotFoundError](#JobNotFoundError)

---

## Models

\[ Jump to [Methods](#__Methods) \]

### Table of Contents

1.  [`Candidate`](#Candidate)
2.  [`CandidateNotFoundError`](#CandidateNotFoundError)
3.  [`CandidateSearchError`](#CandidateSearchError)
4.  [`Employer`](#Employer)
5.  [`Employer_point_of_contact`](#Employer_point_of_contact)
6.  [`InvalidStatusError`](#InvalidStatusError)
7.  [`Job`](#Job)
8.  [`JobIdError`](#JobIdError)
9.  [`JobList`](#JobList)
10. [`JobList_inner`](#JobList_inner)
11. [`JobNotFoundError`](#JobNotFoundError)
12. [`New_Employer_RequestBody`](#New_Employer_RequestBody)
13. [`New_Employer_RequestBody_point_of_contact`](#New_Employer_RequestBody_point_of_contact)
14. [`UnauthorizedError`](#UnauthorizedError)
15. [`Unprotected_Job_Response`](#Unprotected_Job_Response)
16. [`User`](#User)
17. [`UserResponse`](#UserResponse)
18. [`auth_login_body`](#auth_login_body)
19. [`inline_response_200`](#inline_response_200)
20. [`inline_response_200_1`](#inline_response_200_1)
21. [`inline_response_200_10`](#inline_response_200_10)
22. [`inline_response_200_1_data`](#inline_response_200_1_data)
23. [`inline_response_200_2`](#inline_response_200_2)
24. [`inline_response_200_2_data`](#inline_response_200_2_data)
25. [`inline_response_200_3`](#inline_response_200_3)
26. [`inline_response_200_4`](#inline_response_200_4)
27. [`inline_response_200_5`](#inline_response_200_5)
28. [`inline_response_200_6`](#inline_response_200_6)
29. [`inline_response_200_7`](#inline_response_200_7)
30. [`inline_response_200_8`](#inline_response_200_8)
31. [`inline_response_200_9`](#inline_response_200_9)
32. [`inline_response_200_data`](#inline_response_200_data)
33. [`inline_response_201`](#inline_response_201)
34. [`inline_response_201_1`](#inline_response_201_1)
35. [`inline_response_201_2`](#inline_response_201_2)
36. [`inline_response_400`](#inline_response_400)
37. [`inline_response_401`](#inline_response_401)
38. [`inline_response_404`](#inline_response_404)
39. [`inline_response_409`](#inline_response_409)
40. [`inline_response_422`](#inline_response_422)

### `Candidate` [Up](#__Models)

candidate_id (optional)

[String](#string)

example: 123et4-12345-12345-12345

first_name (optional)

[String](#string)

example: Doe

last_name (optional)

[String](#string)

example: Doe

email

[String](#string)

example: john.doe@example.com

profile_picture (optional)

[String](#string)

example: https://example.com/john-doe.jpg

resume

[String](#string)

example: https://example.com/john-doe-resume.pdf

### `CandidateNotFoundError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 404

message (optional)

[String](#string)

example: No candidates found matching the provided criteria

### `CandidateSearchError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 400

message (optional)

[String](#string)

example: Invalid search criteria

### `Employer` [Up](#__Models)

employer_id (optional)

[String](#string)

example: 67890e5-12d3-a456-426614174000

company_name (optional)

[String](#string)

example: Tech Corp

point_of_contact (optional)

[Employer_point_of_contact](#Employer_point_of_contact)

### `Employer_point_of_contact` [Up](#__Models)

name (optional)

[String](#string)

example: John Doe

address (optional)

[String](#string)

example: 123 Tech Street, New York, NY

contactNumber (optional)

[String](#string)

example: 555-1234

email (optional)

[String](#string)

example: contact@techcorp.com

### `InvalidStatusError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 400

message (optional)

[String](#string)

example: Invalid status value

### `Job` [Up](#__Models)

job_id (optional)

[String](#string)

example: 12345

title

[String](#string)

example: Software Developer

description

[String](#string)

example: Responsible for developing software solutions.

company

[String](#string)

example: Tech Corp

location

[String](#string)

example: New York, NY

work_style (optional)

[String](#string)

Enum:

Remote

Hybrid

Onsite

min_salary (optional)

[Double](#double) format: double

example: 100000

max_salary (optional)

[Integer](#integer)

example: 300000

### `JobIdError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 400

message (optional)

[String](#string)

example: Invalid job ID

### `JobList` [Up](#__Models)

### `JobList_inner` [Up](#__Models)

job_id (optional)

[String](#string)

example: 12345d-12345-12345-12345

job_title (optional)

[String](#string)

example: Software Developer

date_posted (optional)

[String](#string)

example: 2021-01-01

employer_id (optional)

[String](#string)

example: 12e324-12345-12345-12345

description (optional)

[String](#string) Job description

### `JobNotFoundError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 404

message (optional)

[String](#string)

example: No jobs found matching the provided criteria

### `New_Employer_RequestBody` [Up](#__Models)

employer_id (optional)

[String](#string)

example: 67890e5-12d3-a456-426614174000

company_name (optional)

[String](#string)

example: Tech Corp

point_of_contact (optional)

[New_Employer_RequestBody_point_of_contact](#New_Employer_RequestBody_point_of_contact)

### `New_Employer_RequestBody_point_of_contact` [Up](#__Models)

name (optional)

[String](#string)

example: John Doe

address (optional)

[String](#string)

example: 123 Tech Street, New York, NY

contactNumber (optional)

[String](#string)

example: 555-1234

email (optional)

[String](#string)

example: john@example.com

### `UnauthorizedError` [Up](#__Models)

code (optional)

[Integer](#integer) format: int32

example: 401

message (optional)

[String](#string)

example: Unauthorized access

### `Unprotected_Job_Response` [Up](#__Models)

id (optional)

[String](#string)

example: 123e349-12d3-a456-426614174000

title (optional)

[String](#string)

example: Software Developer

description (optional)

[String](#string)

example: Responsible for developing software solutions.

company (optional)

[String](#string)

example: Tech Corp

location (optional)

[String](#string)

example: New York, NY

### `User` [Up](#__Models)

user_id (optional)

[Long](#long) format: int64

example: 1

firstName

[String](#string)

example: Olivia

lastName

[String](#string)

example: Pope

email

[String](#string)

example: olivia.pope@example.com

password

[String](#string)

example: hashedpassword

### `UserResponse` [Up](#__Models)

user_id (optional)

[Long](#long) format: int64

example: 1

firstName (optional)

[String](#string)

example: Olivia

lastName (optional)

[String](#string)

example: Pope

email (optional)

[String](#string)

example: olivia.pope@example.com

### `auth_login_body` [Up](#__Models)

email

[String](#string)

password

[String](#string)

### `inline_response_200` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[inline_response_200_data](#inline_response_200_data)

### `inline_response_200_1` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[inline_response_200_1_data](#inline_response_200_1_data)

### `inline_response_200_10` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[JobList](#JobList)

### `inline_response_200_1_data` [Up](#__Models)

firstName (optional)

[String](#string)

example: Olivia

lastName (optional)

[String](#string)

example: Pope

email (optional)

[String](#string)

example: oliviapope@example.com

profilePicture (optional)

[String](#string)

example: https://example.com/olivia-pope.jpg

theme (optional)

[String](#string)

example: dark

### `inline_response_200_2` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: User logged in successfully

data (optional)

[inline_response_200_2_data](#inline_response_200_2_data)

### `inline_response_200_2_data` [Up](#__Models)

token (optional)

[String](#string)

example: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6Ik9saXZpYSBQb3BlIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

### `inline_response_200_3` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[UserResponse](#UserResponse)

### `inline_response_200_4` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: User profile updated successfully

data (optional)

[User](#User)

### `inline_response_200_5` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: Candidates retrieved successfully

data (optional)

[array\[Candidate\]](#Candidate)

### `inline_response_200_6` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[Candidate](#Candidate)

### `inline_response_200_7` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[array\[Job\]](#Job)

### `inline_response_200_8` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: Job updated successfully.

data (optional)

[Job](#Job)

### `inline_response_200_9` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[array\[Employer\]](#Employer)

### `inline_response_200_data` [Up](#__Models)

theme (optional)

[String](#string)

example: dark

notifications (optional)

[Boolean](#boolean)

example: true

### `inline_response_201` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: User created successfully

data (optional)

[UserResponse](#UserResponse)

### `inline_response_201_1` [Up](#__Models)

status (optional)

[String](#string)

example: success

message (optional)

[String](#string)

example: Candidates updated successfully

data (optional)

[array\[Candidate\]](#Candidate)

### `inline_response_201_2` [Up](#__Models)

status (optional)

[String](#string)

example: success

data (optional)

[Employer](#Employer)

### `inline_response_400` [Up](#__Models)

status (optional)

[String](#string)

example: Bad request

message (optional)

[String](#string)

example: Wrong ID

### `inline_response_401` [Up](#__Models)

status (optional)

[String](#string)

example: error

message (optional)

[String](#string)

example: Invalid token. Unauthorized

### `inline_response_404` [Up](#__Models)

status (optional)

[String](#string)

example: error

message (optional)

[String](#string)

example: Not found

### `inline_response_409` [Up](#__Models)

status (optional)

[String](#string)

example: error

message (optional)

[String](#string)

example: User already exists

### `inline_response_422` [Up](#__Models)

status (optional)

[String](#string)

example: Error

message (optional)

[String](#string)

example: Validation error

errors (optional)

[String](#string)

example: required properties missing
