# Security Policy

## Responsible Use

PhishGuard AI is an educational security tool designed for legitimate phishing detection and awareness training. It must be used responsibly and ethically.

### Acceptable Use

✅ **Allowed**:
- Security research and education
- Internal security awareness training with consent
- Testing your own systems with authorization
- Analyzing suspicious emails and URLs
- Learning about phishing detection techniques

❌ **Prohibited**:
- Sending deceptive emails to real users without explicit consent
- Harvesting or collecting real credentials
- Attacking or testing systems without authorization
- Impersonating real organizations or individuals
- Using the platform for malicious purposes
- Distributing or executing malware

## Reporting Security Vulnerabilities

If you discover a security vulnerability in PhishGuard AI, please report it responsibly:

1. **Do not** open a public GitHub issue
2. Email the project maintainers with details
3. Allow reasonable time for a fix before public disclosure
4. Include steps to reproduce the vulnerability

## Security Measures Implemented

### Application Security

- **CSRF Protection**: All state-changing endpoints protected
- **Rate Limiting**: Prevents brute force and DoS attacks
- **Input Validation**: Server-side validation for all inputs
- **SQL Injection Prevention**: SQLAlchemy ORM with parameterized queries
- **XSS Prevention**: Output encoding and Content Security Policy
- **Secure Sessions**: HTTPOnly, Secure, and SameSite cookies

### Authentication & Authorization

(To be implemented with user accounts)
- Password hashing with Argon2id
- Secure session management
- Role-based access control

### Data Protection

- Sensitive data encrypted at rest
- Minimal data collection principle
- Secure credential storage in environment variables
- No logging of sensitive information

### Infrastructure Security

- Security headers (X-Frame-Options, X-Content-Type-Options, etc.)
- CORS properly configured
- File upload restrictions (size, type validation)
- No execution of submitted URLs or attachments

## Security Testing

### Automated Scanning

```bash
# Dependency vulnerability check
safety check

# Python security issues scan
bandit -r app/

# Code quality and security
ruff check app/
```

### Manual Testing

- Input validation testing
- Authentication bypass attempts
- Authorization checks
- Session management testing
- CSRF protection verification
- XSS payload testing
- SQL injection attempts

## Security Best Practices for Deployment

### Environment Configuration

1. Use strong, random `SECRET_KEY`
2. Enable `SESSION_COOKIE_SECURE` in production
3. Set appropriate CORS origins
4. Use environment variables for sensitive config
5. Enable HTTPS in production

### Database Security

1. Use strong database passwords
2. Restrict database network access
3. Regular database backups
4. Enable connection encryption
5. Use least-privilege database users

### Server Hardening

1. Keep all dependencies updated
2. Use a reverse proxy (nginx/Apache)
3. Enable firewall rules
4. Implement proper logging and monitoring
5. Regular security updates

## Known Limitations

### Current Limitations (Phase 1)

- Authentication not yet implemented
- No real-time threat intelligence integration
- Limited to local/on-premise deployment
- No encryption for data at rest yet
- Basic rate limiting (memory-based)

### Design Limitations

- **No URL Fetching**: By design, we do not visit submitted URLs to prevent:
  - SSRF (Server-Side Request Forgery) attacks
  - Malware execution on server
  - Privacy concerns from accessing arbitrary sites
  
- **No Email Attachment Execution**: Attachments are not executed or deeply analyzed to prevent:
  - Malware infection
  - System compromise
  - Resource exhaustion

## Compliance Considerations

PhishGuard AI is designed with security best practices in mind, but users are responsible for ensuring compliance with relevant regulations:

- **GDPR**: Minimize personal data collection, obtain consent
- **CCPA**: Provide data access and deletion mechanisms
- **Industry Standards**: Follow OWASP guidelines, NIST frameworks
- **Legal Requirements**: Obtain proper authorization before testing

## Security Roadmap

Future security enhancements planned:

- [ ] Full authentication and authorization system
- [ ] Two-factor authentication (2FA)
- [ ] API key authentication for integrations
- [ ] Advanced rate limiting with Redis
- [ ] Comprehensive audit logging
- [ ] Data encryption at rest
- [ ] Security event monitoring and alerting
- [ ] Regular penetration testing
- [ ] SOC 2 compliance documentation

## Security Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP API Security](https://owasp.org/www-project-api-security/)
- [Flask Security Best Practices](https://flask.palletsprojects.com/en/latest/security/)
- [React Security](https://reactjs.org/docs/dom-elements.html#dangerouslysetinnerhtml)

## Updates

This security policy is reviewed and updated regularly as the project evolves.

**Last Updated**: Phase 1 - Initial Development

---

**Remember**: Security is everyone's responsibility. If you see something, say something.
