## 2024-03-01 - Remote Code Execution via eval() in Loyalty API
**Vulnerability:** The ScoreCampaign module evaluated dynamic math formulas using `eval(placeholder)`, presenting a CRITICAL Command/Code Injection risk if `placeholder` isn't fully sanitized and controlled. An attacker who could control `placeholder` could execute arbitrary JavaScript code on the server.
**Learning:** It is dangerous to evaluate mathematical expressions with `eval()`. Without strict whitelist sanitization, any identifier (like `process`) or arbitrary method can execute.
**Prevention:** Always use safe-eval libraries (like `mathjs`) or use `new Function()` combined with extremely strict RegEx sanitization that only permits digits, simple math operators (`+-*/().`), and whitespace.
