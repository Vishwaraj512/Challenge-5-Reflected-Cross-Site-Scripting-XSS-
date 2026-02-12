# Challenge-5-Reflected-Cross-Site-Scripting-XSS

1. Finding Overview
Vulnerability Name: Reflected Cross-Site Scripting (XSS)

Target URL: http://vishwaraj-ch5.4.213.214.70.nip.io

Severity: High

Status: Verified/Exploited

2. Methodology (Manual Process)
Reconnaissance: I accessed the "Customer Service" portal and identified a single input vector: a "Message" text area designed to send inquiries to staff.

Reflection Testing: I manually submitted a benign string, "Hello research Intern". The application reflected this input directly on the success page without any apparent filtering or encoding.

Exploitation & Verification:

To confirm the vulnerability, I manually injected a JavaScript payload into the message box: <script>alert('XSS_Found')</script>.

Upon clicking Submit, the browser redirected to the success page where the script executed, triggering an alert box with the message "XSS_Found".

This confirmed that the application lacks proper output sanitization, allowing for arbitrary code execution in the context of the user's session.

3. Evidence
Input Form: The Customer Service message submission page.

Reflected Output: Success page showing the input string "Hello research Intern" being mirrored back.

Successful Payload: Browser screenshot showing the alert box triggered by the manual XSS payload.

4. Remediation
Context-Aware Output Encoding: All user-supplied data must be encoded (e.g., converting < to &lt;) before being rendered in the HTML body.

Content Security Policy (CSP): Implement a strong CSP to restrict the execution of inline scripts and prevent unauthorized third-party scripts from running.
