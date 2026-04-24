# DEMO PURPOSE ONLY
### Secure Application Development <br>
Assignment 4 Node Secrets  <br>
April 24, 2026   <br>

### This Demo Uses Fake Secrets





# Scenario 2 — Shared Secret in Repository

This repository demonstrates storing secrets in a **`.env` file that is
committed to the repository**. This is better than hard-coding secrets in
the source code, but it is still **bad practice** because everyone who
clones the repo automatically gets the secrets.

## The secrets

The app loads the following secrets from `.env`:

- `NODE_ENV` = `development`
- `API_KEY`  = `FAKE_SHARED_SECRET_IN_ENV_FILE`

The `.env` file is intentionally **not** listed in `.gitignore`, so it is
pushed to GitHub along with the rest of the source code.

## How to run

- Install 

        npm install


- Run the simple server

        node app.js


- TEST In the browser
    1.  http://127.0.0.1:3000   - The Host

    2.  http://localhost:3000/ - The Port



### Observations
1. Did the .env file get copied into the repo? 
    
    Yes.

2. Did GitHub complain about it? 

    No — GitHub does not block committing
    .env files. (It may run secret-scanning on well-known key formats,
    but a generic .env with custom variable names is pushed without
    warning.)


## Why this is still bad

Every developer who clones the repo receives every secret.
Secrets persist in git history forever.
Rotating a secret requires a new commit, and the old value remains
visible in history.
No access control, no auditing, no encryption at rest.
