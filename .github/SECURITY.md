# Security Policy for FluentPDF-AI-Powered-Text-to-Speech-Processor

As an Apex Authority project, security is paramount and treated with the **Zero-Defect** philosophy. This repository adheres to the highest standards of defensive programming, especially concerning external service integrations (LLMs and TTS APIs).

## Supported Versions

We only actively support the latest stable release branch of Python (currently targeting 3.10+ as per our architectural guidelines) and the most current, versioned dependencies managed via `uv`.

## Reporting a Vulnerability

We highly value responsible disclosure. If you discover a security issue, please follow these strict protocols to ensure prompt, private remediation before public disclosure.

### 1. Private Disclosure

Please email the security team directly at `security@apex-architect.io` (Use a placeholder email address if no real contact is available, reflecting a professional security posture).

**In your report, please include:**

*   **Type of Vulnerability:** (e.g., Injection, SSRF, Dependency Confusion, Authentication Bypass).
*   **Affected Component:** Clearly identify the file or feature exhibiting the vulnerability.
*   **Proof of Concept (PoC):** Provide clear, non-destructive steps to reproduce the issue.
*   **Suggested Severity:** (Critical, High, Medium, Low).

### 2. Remediation Timeline

Upon receiving a valid report, the following timeline is strictly enforced:

1.  **Acknowledgement:** Within 24 hours.
2.  **Triage & Fix Development:** Up to 7 days for a fix to be developed, rigorously tested via **Pytest/Ruff** standards, and merged into a private branch.
3.  **Coordinated Disclosure:** Once the patch is ready for release, we coordinate with the reporter for public disclosure. If no coordination is possible after 30 days, the patch will be deployed.

## Security Considerations Specific to this Project

Given the nature of this project (`FluentPDF-AI-Powered-Text-to-Speech-Processor`), specific attention is paid to:

1.  **Input Sanitization:** All user-provided PDF content and configuration parameters must be rigorously sanitized before being processed by underlying TTS engines or passed to LLM prompts. **NEVER** trust input from external files directly.
2.  **API Key Management:** API keys for proprietary services (LLM/TTS) **MUST NOT** be committed to the repository. Developers must utilize secure environment variables loaded during runtime by the execution context (e.g., GitHub Actions secrets or local `.env` files managed outside of Git).
3.  **Dependency Scanning:** Automated security scanning is mandatory in the CI pipeline (`.github/workflows/ci.yml`) to detect vulnerable dependencies managed by `uv`.
4.  **Denial of Service (DoS):** Implement controls to limit the size or complexity of processed documents to prevent excessive API billing or resource exhaustion.

For more information on our development principles, please consult our contributing guidelines:

[CONTRIBUTING.md](../CONTRIBUTING.md)