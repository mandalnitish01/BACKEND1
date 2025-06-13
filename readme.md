### 🔐 MERN Stack Authentication System – Backend Description



## 1. User Registration (Signup)
# API Endpoint: POST /api/v1/user/register

- Accepts user details (name, email, password) from the frontend.

- Password is hashed using bcrypt before saving to MongoDB for security.

- Checks if the user already exists based on email to prevent duplicates.

- Optionally generates a verification token or sends a welcome email.

## 2. User verification (email)
# API Endpoint: GET /api/v1/user/verify/:token

- Verifies user details (name, email, password) from the frontend.

- Password is hashed using bcrypt before saving to MongoDB for security.

- Checks if the user already Verified based on email to prevent duplicates.

- After verification  User can login now.

## 3. User Login
# API Endpoint: POST /api/v1/user/login

- Accepts email and password.

- Uses bcrypt.compare() to validate hashed password.

- If valid, creates a JWT (JSON Web Token) signed with a secret key and returns it to the client.

- Token is used for authenticating protected routes.

## 4. Protected Routes (Authorization)
- Middleware like authMiddleware.js checks for a valid JWT token in headers.

- If valid, allows access to protected endpoints  (e.g., /api/v1/user/profile).


## 5. Token-Based Session Management
# JWT is stored in HTTP-only cookies or localStorage (less secure) on the frontend.

Expiry time can be set (e.g., 24 hour).

Optionally implements refresh tokens and access token for better session control.