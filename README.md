# API Security Risk Analysis — Future Interns Task 3

Read-only educational review of the public ReqRes demo API, prepared on 11 November 2026.

## Deliverables

- `API_Security_Risk_Analysis_Report.pdf` — Canva-designed assessment report.
- `evidence/postman-429-headers.png` — cropped Postman capture of the GET request and HTTP 429 response.
- `evidence/reqres-docs-live-sample.png` — cropped ReqRes documentation widget showing a separate HTTP 200 fixture response.

## Target and scope

- **Target:** ReqRes public demo API — <https://reqres.in>
- **Endpoint reviewed:** `GET https://reqres.in/api/users?page=2`
- **Scope:** One low-volume, read-only request; review of public API documentation and the response headers returned by Postman.
- **Excluded:** authenticated routes, other users' records, write methods, input fuzzing, bypass attempts, load testing, and private or production systems.

The Postman request returned **HTTP 429** because the anonymous daily IP quota was exhausted. Its response included `X-Ratelimit-Limit: 40` and `X-Ratelimit-Remaining: 0`. The ReqRes documentation's live sample separately displayed **HTTP 200** with fixed fixture records. These are separate observations, not the same request or response.

## Tools and method

- **Postman Online REST API Client:** sent the single GET request and inspected its response status and headers.
- **Web browser:** reviewed ReqRes public API documentation and its live sample.
- **Browser DevTools and Insomnia:** not used. DevTools are not claimed as a source of evidence; Insomnia is an alternative to Postman.

The review did not confirm an exploitable vulnerability. The report records the service-identification headers as a **Low / informational hardening observation** only. The 429 quota response is treated as evidence that rate limiting was enforced, not as a vulnerability. Public access and wildcard CORS are expected for this public fixture API and are not reported as findings by themselves.

## Study references

These repositories were used only to review API security concepts and report structure. Their text was not copied.

- [OWASP API Security project](https://github.com/OWASP/API-Security)
- [Shieldfy API Security Checklist](https://github.com/shieldfy/API-Security-Checklist)
- [Public APIs collection](https://github.com/public-apis/public-apis)
- [ReqRes API documentation](https://reqres.in/docs)
- [ReqRes free API overview](https://reqres.in/free-json-api)

## Limitations

This is a limited educational review of a demo service, not a production penetration test or comprehensive security audit. Authentication enforcement, object-level authorization, input validation, and abuse behavior were not tested. Findings should not be generalized to a production deployment.
