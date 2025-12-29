# PII Firewall Edge - API Examples

Official SDK examples for integrating PII Firewall Edge into your applications.

**Enterprise-grade PII detection. Zero AI. Zero Logs. 5ms latency.**

## Quick Links

| Resource | Link |
|----------|------|
| 🌐 **Website** | [pii-firewall-edge-web.vercel.app](https://pii-firewall-edge-web-1otq.vercel.app) |
| 📚 **API Docs** | [RapidAPI Documentation](https://rapidapi.com/image-zero-trust-security-labs/api/pii-firewall-edge) |

## SDK Repositories

| Language | Repository | Status |
|----------|------------|--------|
| ☕ **Java** | [pii-firewall-edge-api-java](https://github.com/myProjectsRavi/pii-firewall-edge-api-java) | Ready |
| 🟨 **JavaScript** | [pii-firewall-edge-api-js](https://github.com/myProjectsRavi/pii-firewall-edge-api-js) | Ready |
| 🐍 **Python** | [pii-firewall-edge-api-python](https://github.com/myProjectsRavi/pii-firewall-edge-api-python) | Ready |

## Get Started in 60 Seconds

### 1. Get Your Free API Key

Sign up at [RapidAPI](https://rapidapi.com/image-zero-trust-security-labs/api/pii-firewall-edge) (500 requests/month free).

### 2. Choose Your Language

#### JavaScript / Node.js

```javascript
const response = await fetch(
  'https://pii-firewall-edge.p.rapidapi.com/v1/redact/fast',
  {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-RapidAPI-Key': 'YOUR_API_KEY'
    },
    body: JSON.stringify({
      text: 'Contact john@company.com at 555-123-4567'
    })
  }
);

const { redacted, detections } = await response.json();
console.log(redacted);
// Output: Contact [EMAIL] at [PHONE_US]
```

#### Python

```python
import requests

response = requests.post(
    'https://pii-firewall-edge.p.rapidapi.com/v1/redact/fast',
    headers={
        'Content-Type': 'application/json',
        'X-RapidAPI-Key': 'YOUR_API_KEY'
    },
    json={
        'text': 'Contact john@company.com at 555-123-4567'
    }
)

data = response.json()
print(data['redacted'])
# Output: Contact [EMAIL] at [PHONE_US]
```

#### Java

```java
import java.net.http.*;
import java.net.URI;

HttpClient client = HttpClient.newHttpClient();
HttpRequest request = HttpRequest.newBuilder()
    .uri(URI.create("https://pii-firewall-edge.p.rapidapi.com/v1/redact/fast"))
    .header("Content-Type", "application/json")
    .header("X-RapidAPI-Key", "YOUR_API_KEY")
    .POST(HttpRequest.BodyPublishers.ofString(
        "{\"text\":\"Contact john@company.com at 555-123-4567\"}"
    ))
    .build();

HttpResponse<String> response = client.send(request, 
    HttpResponse.BodyHandlers.ofString());
System.out.println(response.body());
```

#### cURL

```bash
curl -X POST "https://pii-firewall-edge.p.rapidapi.com/v1/redact/fast" \
  -H "Content-Type: application/json" \
  -H "X-RapidAPI-Key: YOUR_API_KEY" \
  -d '{"text": "Contact john@company.com at 555-123-4567"}'
```

## API Endpoints

| Endpoint | Method | Latency | Description |
|----------|--------|---------|-------------|
| `/v1/redact/fast` | POST | 2-5ms | Structured PII (emails, phones, SSNs, cards) |
| `/v1/redact/deep` | POST | 5-15ms | All PII + human names + addresses |
| `/health` | GET | <1ms | API health check |

## Request Format

```json
{
  "text": "Your text containing potential PII",
  "mode": "label"  // or "mask" for asterisks
}
```

## Response Format

```json
{
  "redacted": "Your text with [PII_TYPE] labels",
  "detections": 3
}
```

## PII Types Detected (152 total)

| Category | Examples | Count |
|----------|----------|-------|
| Contact | Email, Phone (US/UK/IN/Intl) | 12 |
| Government | SSN, Passport, Driver's License | 40+ |
| Financial | Credit Card, IBAN, SWIFT, Crypto | 20+ |
| Healthcare | NPI, DEA, Medicare, MRN | 8 |
| Developer | AWS, GitHub, Stripe, OpenAI keys | 20+ |
| Global | China, Japan, Korea, Brazil, EU IDs | 50+ |

## Pricing

| Plan | Price | Requests/Month | Max Size |
|------|-------|----------------|----------|
| Basic | $0 | 500 | 20KB |
| Pro | $5 | 5,000 | 100KB |
| Ultra | $10 | 20,000 | 100KB |
| Mega | $25 | 75,000 | 100KB |

**97% less than AWS Comprehend or Google DLP.**

## Use Cases

### 1. LLM Data Protection

Sanitize user input before sending to ChatGPT/Claude:

```javascript
// Before sending to LLM
const { redacted } = await piiClient.redactFast(userMessage);
const aiResponse = await openai.chat({ content: redacted });
```

### 2. Log Sanitization

Remove PII from application logs:

```python
def log_safe(message):
    sanitized = pii_client.redact_fast(message)
    logger.info(sanitized.redacted)
```

### 3. Customer Support

Redact sensitive data in support tickets:

```java
String safeTicket = piiClient.redactFast(ticketContent).getRedactedText();
ticketSystem.store(safeTicket);
```

### 4. Data Export

Clean data before sharing with partners:

```python
for record in database.get_all():
    clean_record = pii_client.redact_deep(record['notes'])
    export_file.write(clean_record.redacted)
```

## Error Codes

| Code | Meaning | Solution |
|------|---------|----------|
| 400 | Invalid input | Check text is non-empty string |
| 401 | Invalid API key | Verify RapidAPI key |
| 413 | Payload too large | Split text or upgrade plan |
| 429 | Rate limit | Wait or upgrade plan |
| 500 | Server error | Retry request |

## Support

- **Documentation**: [RapidAPI Docs](https://rapidapi.com/image-zero-trust-security-labs/api/pii-firewall-edge)
- **SDK Examples**: [GitHub](https://github.com/myProjectsRavi/pii-firewall-edge-api-examples)
- **Email**: [Contact Support](mailto:piifirewalledge@gmail.com)

## License

MIT License - Use freely in your projects!

---

Made with security in mind. Zero AI. Zero Logs. Zero Compromise.
