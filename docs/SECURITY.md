# Security: Fintestix

## What is protected

Uploaded datasets and models, account credentials, and the integrity of results. A tampered result is worse than none, so receipts are sealed and append-only.

## Controls

| Area | Control |
|---|---|
| Passwords | Argon2id, minimum 12 characters, checked against a list of breached passwords |
| Sign-in | One generic error for every failure, constant-time checks for unknown emails, lockout after 10 failures with doubling duration, rate limits per IP and per account |
| Sign-up | A 6-digit code by email: 15-minute expiry, single use, 5 wrong tries end the code, stored as an HMAC bound to the user |
| Second factor | Optional authenticator app (TOTP), secret encrypted at rest |
| Sessions | 32 random bytes; only the hash is stored. HttpOnly, Secure and SameSite cookie. 30-minute idle and 12-hour absolute timeout. Users can see and revoke sessions |
| CSRF | Per-session token on every state-changing request, compared in constant time. A test walks every route |
| Access | Project membership checked on every query; outsiders get 404. Global admins have no implicit access to customer projects |
| Uploads | Extension and magic-byte checks, size limits, zip-bomb guard for XLSX, files stored by SHA-256 name outside any served path |
| Models and rules | No pickle, joblib or code execution. XGBoost JSON and ONNX only. Rule conditions are JSON interpreted by the app, never evaluated as code |
| Exports | Excel cells that start with formula characters are escaped |
| Browser | Strict Content Security Policy with no inline scripts, HSTS, frame-ancestors none, nosniff |
| Database | Least-privilege roles; append-only receipts and audit log enforced by grants and a trigger |
| Logs and errors | No passwords, tokens, emails or dataset values in logs; error reports scrubbed before sending |
| Supply chain | Lock files, pip-audit and npm audit, Bandit and Semgrep, gitleaks, a licence check that allows only open-source licences |
| Change control | Destructive database changes need a recorded human approval and a pull-request label, checked in CI |

## Reporting a vulnerability

Please do not open a public issue. Contact the author through their GitHub profile.

## Limits

Fintestix applies OWASP ASVS level 1 practices but has not been independently audited and makes no compliance claims.
