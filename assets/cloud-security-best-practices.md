# Section 1: Identity and Access Management (IAM)

## 1.1 Introduction

Identity and Access Management (IAM) controls who can do what in your cloud environment. Getting IAM right helps you prevent unauthorized access, meet GDPR requirements (by limiting data exposure), and maintain a clear audit trail for U.S. privacy regulations.

## 1.2 Step-by-Step Tutorial

### Create a Dedicated Developers Group

Go to IAM → Groups → Create group in your cloud console. Name it "jrlvl-cloud-devs." Attach only the policies needed for common tasks (e.g., read-only access to storage buckets, permission to launch test servers).

### Apply the Principle of Least Privilege

Instead of giving "AdministratorAccess," grant only the actions each role needs. Example: for S3 file uploads, use a policy allowing s3:PutObject, s3:GetObject, but not s3:DeleteBucket.

### Enforce Multi-Factor Authentication (MFA)

Require MFA for the root account and all users in privileged groups. Go to IAM → Users → select user → Security credentials → Manage MFA.

### Use Roles for Service-to-Service Access

Create an IAM Role for any application or service (e.g., EC2 instance) that needs to access other resources. Assign minimal permissions and attach it to the instance—never hard-code credentials.

### Regularly Review and Remove Unused Access

Schedule a monthly check via IAM → Access advisor or by exporting a credential report. Remove inactive users and roles.

## 1.3 How to Test IAM Controls

### Group Tests:
- Log in as a test user in "jrlvl-cloud-devs."
- Attempt an allowed action (e.g., list buckets).
- Attempt a denied action (e.g., delete a bucket). You should see an "access denied" error.

### MFA Test:
- Log out and log in as a user with MFA enabled.
- Confirm the sign-in process prompts for your MFA code.

### Role Test:
- Launch an EC2 instance with your new role.
- From the instance, run aws s3 ls or another allowed command.
- Verify that actions outside the role's permissions are blocked.

## 1.5 Common Mistakes to Avoid

### Using the Root Account for Daily Tasks:
Root has unlimited power—use only for setup and emergencies.

### Wildcard Permissions ("*"):
Avoid granting "s3:*" or "ec2:*" unless strictly required.

### Ignoring Inactive Credentials:
Old access keys or unused users are liabilities. Remove them regularly.

## 1.4 Checklist
- [ ] Group "jrlvl-cloud-devs" created
- [ ] Policies scoped to least-privilege
- [ ] MFA enabled for all privileged accounts
- [ ] Service roles created and attached (no hard-coded credentials)
- [ ] Monthly IAM access review scheduled


# Section 2: Network Security

## 2.1 Introduction

Network security in the cloud focuses on limiting what resources can talk to each other — and under what conditions. You'll use things like security groups and firewalls to protect your applications and data from unwanted traffic. Both GDPR and U.S. privacy laws require that sensitive data be protected during transit and that exposure be minimized through proper segmentation.

## 2.2 Step-by-Step Tutorial

### Create a VPC (Virtual Private Cloud)

In your cloud provider's dashboard, go to Networking → VPC → Create VPC. Choose a CIDR range like 10.0.0.0/16. This becomes your isolated private network.

### Segment into Public and Private Subnets

Create at least two subnets:
- Public Subnet: for services that must talk to the internet (e.g., a public-facing web app)
- Private Subnet: for internal services like databases and application logic

### Configure Security Groups

Use security groups like mini firewalls. Create rules that allow only the required traffic:
- Port 22 (SSH): Allow only from your IP address
- Port 80/443 (HTTP/HTTPS): Only for public-facing resources
- Port 3306 (MySQL): Restrict to private subnets only

### Use Network ACLs for Additional Filtering

Network ACLs (Access Control Lists) give you stateless rules. Add a deny-all rule at the end and allow only the traffic you explicitly need between subnets.

### Enable VPC Flow Logs

These logs record accepted and rejected traffic. They help meet GDPR audit trail requirements and support incident analysis under U.S. breach laws. Enable via VPC → Flow Logs → Create.

## 2.3 How to Test Network Security Settings

### Port Scan Test:
Run nmap on your public IP. You should only see ports that were explicitly allowed (e.g., 80 or 443).

### SSH Test:
Try to SSH into a private instance from an unauthorized IP. It should be blocked.

### Subnet Isolation Test:
Deploy two instances: one in a public subnet and one in a private one. From the public instance, attempt to reach the private instance via ping or curl. If you've configured correctly, the connection should be denied.

## 2.4 Common Mistakes to Avoid

### Leaving All Ports Open (0.0.0.0/0):
Avoid this at all costs unless required for public access — and even then, combine it with throttling and monitoring.

### No Subnet Segmentation:
Everything in one subnet increases risk of lateral movement during an attack.

### Disabled Flow Logs:
Without flow logs, you can't see rejected connections or build incident reports when needed.

## 2.5 Network Security Checklist
- [ ] VPC created with appropriate CIDR
- [ ] Public and private subnets configured
- [ ] Security groups scoped to needed ports and IPs
- [ ] Network ACLs with deny-all fallback in place
- [ ] VPC Flow Logs enabled and writing to a secure storage bucket

# Section 3: Data Encryption (At Rest & In Transit)

## 3.1 Introduction

Encryption protects sensitive data from unauthorized access — whether it's being stored ("at rest") or sent between systems ("in transit"). To comply with GDPR and U.S. privacy regulations, encryption should be used by default for personal data and keys must be securely managed.

## 3.2 Step-by-Step Tutorial

### Enable Encryption for Storage Services (At Rest)

When creating cloud storage (e.g., AWS S3, Azure Blob, GCP Storage), check the box for server-side encryption.
Example: In AWS S3 → Enable SSE-S3 (AWS-managed) or SSE-KMS (your own key).

### Use Customer-Managed Keys (CMKs) for Sensitive Data

Generate keys using a Key Management Service (KMS). Assign usage permissions only to required users and roles.

### Enforce HTTPS and TLS for All Traffic (In Transit)

Ensure all services use https:// endpoints. Use TLS 1.2 or higher for APIs and application access.
Tip: For web apps, use an Application Load Balancer with an SSL certificate.

### Rotate Keys and Certificates Regularly

Set up automatic key rotation where possible (e.g., AWS KMS allows auto-rotation every 365 days). For TLS certificates, use managed services like AWS ACM or Let's Encrypt.

### Restrict Key Access

Use IAM policies to control who can encrypt, decrypt, or rotate keys. Never share keys in code or logs.

## 3.3 How to Test Encryption Settings

### Storage Encryption Test:
Upload a file to your cloud storage bucket. Then inspect the file's metadata or use CLI/API tools to verify encryption is enabled (e.g., aws s3api head-object).

### Network Encryption Test:
Access your site or API endpoint using HTTPS. Use browser tools or curl -v to confirm TLS is active and valid.

### Key Access Test:
Attempt to encrypt or decrypt data as a user who should not have permissions — the operation should fail with an access denied error.

## 3.4 Common Mistakes to Avoid

### Disabling Encryption for Non-Critical Buckets:
Even logs and staging files may contain sensitive data — encrypt everything.

### Using Default Cloud Keys Without Review:
If you must use default-managed keys, document where and why — regulators may ask.

### Leaving Expired Certificates Unrotated:
Expired TLS certificates will break apps and leave endpoints vulnerable.

## 3.5 Data Encryption Checklist
- [ ] All storage services have encryption enabled at rest
- [ ] HTTPS/TLS enforced for all endpoints and APIs
- [ ] Customer-managed KMS keys used for sensitive data
- [ ] Key and cert rotation policies in place
- [ ] IAM policies restrict access to key usage


# Section 4: Vulnerability Scanning

## 4.1 Introduction

Continuous monitoring and vulnerability scanning help you detect threats early and protect cloud resources.

## 4.2 Step-by-Step Tutorial

### Set Up a Vulnerability Scanner

Use a cloud-native or open-source scanner like:
- AWS: Amazon Inspector
- Azure: Microsoft Defender for Cloud
- GCP: Security Command Center
- Universal: OpenVAS or Nessus

Schedule regular scans of virtual machines, containers, and apps.

### Automate Alerts and Reports

Set up email or Slack alerts for critical findings. Generate regular reports for audits.

### Retain Logs for Compliance

Store logs securely in a tamper-proof bucket for 90-365 days. Ensure storage is encrypted and access is restricted.

### Common Mistakes to Avoid
- Skipping scans during rapid deployments.
- Not updating scanner definitions regularly.
- Allowing public access to scan reports.

### Mini Validation Test

Use your scanner's test feature or run a mock vulnerability (like EICAR for antivirus) and confirm alerts are triggered and logged.

### Checklist
- [ ] Vulnerability scanner installed and configured
- [ ] Scan schedule set up
- [ ] Reports delivered to key stakeholders
- [ ] Logs stored securely and encrypted

# Section 5: Data Encryption at Rest & In Transit

## 5.1 Introduction

Encryption protects sensitive data by converting it into unreadable code. It's essential for both compliance and cloud security.

## 5.2 Step-by-Step Tutorial

### Enable Encryption at Rest

Use managed key services or customer-managed keys in:
- AWS: KMS (Key Management Service)
- Azure: Azure Key Vault
- GCP: Cloud KMS

Ensure encryption is enabled for block storage, object storage, and databases.

### Encrypt Data in Transit

Enforce HTTPS/TLS for APIs, websites, and file transfers.

### Rotate Keys Regularly

Implement automatic key rotation policies where supported.

### Audit Key Access

Log and monitor all key usage. Limit key decryption access with IAM roles or policies.

### Common Mistakes to Avoid
- Using default keys without proper access controls.
- Forgetting to enforce TLS for internal services.
- Not rotating keys periodically.

### Mini Validation Test

Try uploading and downloading a file from cloud storage and inspect network traffic using a tool like Wireshark — the contents should be encrypted and transferred over HTTPS.

### Checklist
- [ ] Data encrypted at rest
- [ ] TLS enforced for all endpoints
- [ ] Key rotation policies applied
- [ ] Key access logs reviewed regularly

# Final Cloud Security Checklist

## Identity and Access Management
- [ ] IAM group created with least-privilege policies
- [ ] MFA enforced for root and privileged accounts
- [ ] Roles used for app-to-service access
- [ ] Monthly access reviews scheduled

## Network Security
- [ ] VPC with segmented subnets created
- [ ] Security groups and ACLs scoped by function
- [ ] Public-facing ports restricted
- [ ] Flow logs enabled for audit visibility

## Data Encryption
- [ ] Encryption enabled for all storage buckets and volumes
- [ ] TLS enforced for all APIs, apps, and websites
- [ ] Customer-managed keys used for sensitive data
- [ ] Key rotation and access logging in place

## Vulnerability Scanning & Monitoring
- [ ] Automated scanners deployed (native or third-party)
- [ ] Alerts and reports sent to security teams
- [ ] Logs stored in secure and encrypted location
- [ ] Scan schedule documented and followed