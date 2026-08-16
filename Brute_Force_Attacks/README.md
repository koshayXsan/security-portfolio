# Non-Hashed Password Cracking: Overview & Defense

Coursework summary exploring why storing or transmitting passwords in plain text (rather than hashed) is a critical vulnerability, using three tool categories as case studies: brute-force attacks (Hydra), phishing/credential harvesting (SEToolkit), and web application brute-forcing (OWASP ZAP). Focus is on the underlying mechanics and, more importantly, how to defend against and detect these attack classes. Reproducible attack commands, target details, and captured credentials from the original coursework are intentionally left out here.

---

## Why Non-Hashed Passwords Are a Critical Risk

Modern systems are expected to hash passwords before storing them, converting a plain-text password into an irreversible string so that even a data breach doesn't expose usable credentials. When a system instead stores or transmits passwords in plain text, an attacker who intercepts that data gets the password directly, no cracking or decryption needed. This removes the single biggest obstacle standing between a breach and full account compromise, which is exactly why hashing (plus salting) is treated as non-negotiable in any real security posture.

---

## 1. Brute-Force Attacks (Hydra)

**Concept:** Automated tools attempt large numbers of username/password combinations against a login service (FTP, SSH, HTTP, etc.) until a valid pair is found. Tools like Hydra are built to do this quickly across many protocols in parallel.

**Why non-hashed passwords make it worse:** if the target service doesn't rate-limit or lock out failed attempts, and passwords are weak or reused, brute-forcing becomes a matter of time and thread count rather than sophistication.

**Defense:**
- Account lockout / exponential backoff after repeated failed logins
- Rate limiting and IP-based throttling at the network or application layer
- Enforce strong, unique password policies (length and complexity minimums, no default/service credentials like `admin/admin`)
- MFA so a correctly guessed password alone isn't sufficient
- Fail2ban or equivalent intrusion prevention tied to auth logs

---

## 2. Phishing / Credential Harvesting (SEToolkit)

**Concept:** Rather than attacking the system technically, the attacker clones a legitimate-looking login page and tricks the victim into entering credentials there, which are then captured directly in plain text.

**Why non-hashed passwords make it worse:** this attack doesn't touch hashing at all; it bypasses the concept entirely by capturing the password before it's ever hashed or transmitted to the real system. Reused passwords compound the damage across services.

**Defense:**
- MFA on all accounts (renders a harvested password alone insufficient)
- Password managers, which won't autofill credentials on a lookalike domain
- DNS filtering and browser isolation for known-bad or newly registered domains
- Regular phishing-simulation training so users recognize spoofed login pages
- Domain monitoring for lookalike/typosquatted domains targeting your organization

---

## 3. Web Application Brute-Forcing (OWASP ZAP)

**Concept:** A web app security scanner intercepts login requests and automates testing many password values against a login form, looking for a successful authentication response.

**Why non-hashed passwords make it worse:** if the backend stores or compares passwords in plain text (or over an insecure channel), a successful guess is immediately usable, and weak login implementations without lockout or CAPTCHA make this trivial to automate.

**Defense:**
- Server-side rate limiting and account lockout on login endpoints specifically (not just app-wide)
- CAPTCHA or equivalent challenge after a small number of failed attempts
- HTTPS enforced everywhere, with HSTS, so credentials are never transmitted in the clear
- Web application firewall (WAF) rules to detect and block automated fuzzing/brute-force patterns
- Regular security testing (the same class of tool used offensively here, used defensively as part of your own pentest cycle)

---

## Key Takeaway

All three approaches above converge on the same root problem: plain-text passwords remove the safety margin that hashing is supposed to provide. Hashing with a strong algorithm (e.g. bcrypt, Argon2) plus per-user salting, combined with MFA, rate limiting, and user education, closes off nearly every path described here. Technical controls and human awareness need to work together since brute-force and phishing exploit different weak points (system vs. person).

---

📄 [Full assignment writeup (PDF)](./hydra_zap.pdf)
