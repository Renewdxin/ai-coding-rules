# Security Rules

## OWASP Top 10 Protection

### A01: Broken Access Control
- Implement role-based access control (RBAC)
- Use principle of least privilege
- Validate permissions on server-side
- Implement proper session management

### A02: Cryptographic Failures
- Use strong encryption algorithms (AES-256, RSA-2048+)
- Implement proper key management
- Use HTTPS for all communications
- Hash passwords with bcrypt/scrypt/Argon2

### A03: Injection Attacks
- Use parameterized queries for database operations
- Validate and sanitize all input data
- Implement Content Security Policy (CSP)
- Use prepared statements for SQL queries

## Authentication & Authorization Patterns
- **JWT Tokens**: Use for stateless authentication
- **OAuth 2.0**: For third-party authentication
- **Multi-Factor Authentication**: Implement for sensitive operations
- **Session Management**: Secure session handling with proper timeouts
- **Password Policies**: Enforce strong password requirements

## Input Validation & Sanitization
- **Whitelist Validation**: Allow only known good input
- **Data Type Validation**: Ensure correct data types
- **Length Validation**: Enforce maximum input lengths
- **Format Validation**: Use regex for format checking
- **Encoding**: Proper HTML/URL/SQL encoding

## Cryptography Standards
- **Symmetric Encryption**: AES-256-GCM for data encryption
- **Asymmetric Encryption**: RSA-2048 or ECC-256 for key exchange
- **Hashing**: SHA-256 for data integrity
- **Password Hashing**: bcrypt with salt rounds ≥ 12
- **Random Generation**: Use cryptographically secure random generators

## Vulnerability Assessment Process
- **Static Analysis**: Use tools like SonarQube, Checkmarx
- **Dynamic Analysis**: Implement DAST tools in CI/CD
- **Dependency Scanning**: Check for vulnerable dependencies
- **Penetration Testing**: Regular security assessments
- **Security Code Review**: Manual review of security-critical code

## Secure Configuration Management
- **Environment Variables**: Store secrets in environment variables
- **Secret Management**: Use HashiCorp Vault or AWS Secrets Manager
- **Configuration Validation**: Validate security configurations
- **Default Passwords**: Never use default credentials
- **Security Headers**: Implement proper HTTP security headers

## Data Protection
- **Data Classification**: Classify data by sensitivity level
- **Encryption at Rest**: Encrypt sensitive data in storage
- **Encryption in Transit**: Use TLS 1.3 for data transmission
- **Data Masking**: Mask sensitive data in non-production environments
- **Data Retention**: Implement proper data lifecycle management

## Logging & Monitoring
- **Security Events**: Log authentication and authorization events
- **Anomaly Detection**: Monitor for unusual access patterns
- **Audit Trails**: Maintain comprehensive audit logs
- **Log Protection**: Secure log files from tampering
- **Incident Response**: Have security incident response plan
