# Better Auth is here

A simple authentication project using Next.js, Better Auth, MongoDB, HeroUI, Google OAuth, and Resend.

## Authentication Setup Process

### 1. Create Next.js Project

Create a new Next.js project.

    npx create-next-app@latest

---

### 2. Install Better Auth

    npm install better-auth

---

### 3. Install MongoDB

    npm install mongodb

---

### 4. Install Better Auth MongoDB Adapter

    npm install @better-auth/mongo-adapter

---

### 5. Configure MongoDB in `auth.ts`

Configure MongoDB in the Better Auth configuration file.

    lib/
    └── auth.ts

---

### 6. Create Sign Up Page

Create a sign-up page for user registration.

    /app/signup/page.tsx

---

### 7. Install HeroUI

Install HeroUI for designing the authentication pages.

    npm install @heroui/react

---

### 8. Add HeroUI Styles

Add HeroUI styles to the global CSS file.

    @import "@heroui/styles";

---

### 9. Design Sign Up Page

Design the sign-up page using HeroUI components.

The sign-up form contains:

- Name
- Email
- Password
- Sign Up button

---

### 10. Create Better Auth API Route

Create the Better Auth API route.

    /app/api/auth/[...all]/route.ts

This route handles Better Auth authentication requests.

---

### 11. Create `auth-client.ts`

Create the authentication client.

    /lib/auth-client.ts

This file is used to interact with Better Auth from the client side.

---

### 12. Sign Up

Handle sign-up using email and password.

    const { data: signUpData, error } = await signUp.email({
        name: data.name,
        email: data.email,
        password: data.password,
        callbackURL: "/",
    });

---

### 13. Sign In

Handle sign-in using email and password.

    const { data: signInData, error } = await signIn.email({
        email: data.email,
        password: data.password,
        callbackURL: "/",
    });

---

### 14. Session Management

Get the current user's session using:

    const { data: session } = authClient.useSession();

This is used to check the current authentication session.

---

### 15. Sign Out

Sign out the current user.

    await authClient.signOut({
        fetchOptions: {
            onSuccess: () => {
                router.push("/login");
            },
        },
    });

After successful sign-out, the user is redirected to the login page.

---

### 16. Create `proxy.js` for Private Routes

Create a `proxy.js` file to protect private routes.

    /proxy.js

Private routes can only be accessed by authenticated users.

---

### 17. Configure Google OAuth

Go to Google Console and create an OAuth Client ID.

Add the Google credentials to `.env`.

    BETTER_AUTH_GOOGLE_CLIENT_ID=your_google_client_id
    BETTER_AUTH_GOOGLE_CLIENT_SECRET=your_google_client_secret

---

### 18. Add Google OAuth to `auth.ts`

Add Google as a social provider.

    socialProviders: {
        google: {
            clientId: process.env.BETTER_AUTH_GOOGLE_CLIENT_ID,
            clientSecret: process.env.BETTER_AUTH_GOOGLE_CLIENT_SECRET,
        },
    },

Now users can authenticate using Google.

---

### 19. Email Verification

For email verification, use Resend.

#### a. Create Resend Account

Create an account on Resend.

#### b. Create API Key

Create an API key from the Resend dashboard.

#### c. Add API Key to `.env`

    RESEND_API_KEY=your_resend_api_key

The Resend API key is used to send verification emails.

---

## Authentication Features

- Email & Password Sign Up
- Email & Password Sign In
- Session Management
- Sign Out
- Private Route Protection
- Google OAuth
- Email Verification
- MongoDB Authentication Database
- HeroUI Authentication UI