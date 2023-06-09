---
layout: post
title: Jenkins - Vulnerabilities analysis part 1
tags: [Jenkins, Security, CI, CD]
description: "Jenkins - Vulnerabilities analysis part 1"
---

## Summary
I'm trying to learn what kind of vulnerabilities can be found on Jenkins. My analysis won't be 100% accurate, but I'm trying my best :)

To achieve this, I based all my research on their [*Security Advisory*](https://www.jenkins.io/security/advisories/).

I went through all of the web pages from **January 2021** to **March 2022**. On each page, I ran this piece of JavaScript to fastly get all the vulnerabilities name.

```js
var x =  document.querySelectorAll("h3");
for (let i = 0; i < x.length; i++) {
	console.log(x[i].innerText);
}
```

Which gave me those results. (Boring like this I know)

## Numbers
### 2021-01-13
- XSS vulnerability in notification bar 
- Stored XSS vulnerability in button labels 
- Reflected XSS vulnerability in markup formatter preview 
- Stored XSS vulnerability on new item page 
- Improper handling of REST API XML deserialization errors 
- Arbitrary file read vulnerability in workspace browsers 
- Path traversal vulnerability in agent names 
- Arbitrary file existence check in file fingerprints 
- Excessive memory allocation in graph URLs leads to denial of service 
- Missing permission check for paths with specific prefix 
- Credentials stored in plain text by TraceTronic ECU-TEST Plugin 
- XSS vulnerability in TICS Plugin 
- Credentials stored in plain text by Bumblebee HP ALM Plugin 

### 2021-01-26
- Arbitrary file read vulnerability in workspace browsers 

### 2021-02-19
- Privilege escalation vulnerability in bundled Spring Security library

### 2021-02-24
- Stored XSS vulnerability in Active Choices Plugin 
- CSRF vulnerability in Configuration Slicing Plugin 
- Stored XSS vulnerability in Repository Connector Plugin 
- XSS vulnerability in Claim Plugin 
- CSRF vulnerability in Claim Plugin 
- Support bundles can include user session IDs in Support Core Plugin 
- Stored XSS vulnerability in Artifact Repository Parameter Plugin 

### 2021-03-18
- Incorrect permission checks in Matrix Authorization Strategy Plugin may allow accessing some items 
- Incorrect permission checks in Role-based Authorization Strategy Plugin may allow accessing some items 
- Missing permission checks in CloudBees AWS Credentials Plugin allows enumerating credentials IDs 
- Missing permission checks in Warnings Next Generation Plugin allow listing workspace contents 
- CSRF vulnerability in Libvirt Agents Plugin 

### 2021-03-30
- Stored XSS vulnerability in Build With Parameters Plugin 
- CSRF vulnerability in Build With Parameters Plugin 
- Stored XSS vulnerability in Extra Columns Plugin 
- Missing permission check in Cloud Statistics Plugin 
- CSRF vulnerability and missing permission checks in OWASP Dependency-Track Plugin allow capturing credentials 
- Passwords stored in plain text by Jabber (XMPP) notifier and control Plugin 
- Stored XSS vulnerability in REST List Parameter Plugin 
- Missing permission check in Team Foundation Server Plugin allows enumerating credentials IDs 
- CSRF vulnerability and missing permission check in Team Foundation Server Plugin allow capturing credentials

### 2021-04-07
- Lack of type validation in agent related REST API 
- View name validation bypass 
- CSRF vulnerability in promoted builds Plugin 
- CSRF vulnerability and missing permission checks in Micro Focus Application Automation Tools Plugin 
- Reflected XSS vulnerability in Micro Focus Application Automation Tools Plugin 
- SSL/TLS certificate validation unconditionally disabled by Micro Focus Application Automation Tools Plugin 

### 2021-04-20
- Denial of service vulnerability in bundled Jetty

### 2021-04-21 
- XXE vulnerability in Config File Provider Plugin 
- Incorrect permission checks in Config File Provider Plugin allow enumerating credentials IDs 
- CSRF vulnerability in Config File Provider Plugin allows deleting configuration files 
- Missing permission checks in Config File Provider Plugin allow enumerating configuration file IDs 
- Remote code execution vulnerability in Templating Engine Plugin 
- Missing permission check in CloudBees CD Plugin allows scheduling builds

### 2021-05-11
- Reflected XSS vulnerability in Credentials Plugin 
- Stored XSS vulnerability in Dashboard View Plugin 
- Missing permission checks in S3 publisher Plugin allow obtaining metadata about artifacts 
- Missing permission check in S3 publisher Plugin 
- CSRF vulnerability in Xray - Test Management for Jira Plugin allows capturing credentials 
- Missing permission check in Xray - Test Management for Jira Plugin allows enumerating credentials IDs 
- CSRF vulnerability and missing permission checks in P4 Plugin 
- XXE vulnerability in Xcode integration Plugin 

### 2021-05-25
- XXE vulnerability in Filesystem Trigger Plugin 
- XXE vulnerability in Nuget Plugin 
- XXE vulnerability in URLTrigger Plugin 
- XSS vulnerability in Markdown Formatter Plugin 

### 2021-06-10
- Missing permission checks allow enumerating credentials IDs in Kubernetes CLI Plugin 
- Missing permission check in XebiaLabs XL Deploy Plugin allows enumerating credentials IDs 
- CSRF vulnerability and missing permission check in XebiaLabs XL Deploy Plugin allows capturing credentials 
- Reflected XSS vulnerability in Kiuwan Plugin 

### 2021-06-16
- Stored XSS vulnerability in Scriptler Plugin
- Stored XSS vulnerability in Scriptler Plugin 

### 2021-06-18
- XXE vulnerability in Generic Webhook Trigger Plugin

### 2021-06-30
- Improper permission checks allow canceling queue items and aborting builds 
- Session fixation vulnerability 
- XXE vulnerability in Selenium HTML report Plugin 
- Open redirect vulnerability in CAS Plugin 
- Missing permission check in requests-plugin Plugin allows viewing pending requests 
- CSRF vulnerabilities in requests-plugin Plugin 
- Missing permission check in requests-plugin Plugin allows sending emails 

### 2021-08-31
- RCE vulnerability in Code Coverage API Plugin 
- SAML Plugin allows bypassing CSRF protection for any URL 
- Azure AD Plugin allows bypassing CSRF protection for any URL 
- XXE vulnerability in Nested View Plugin 
- Password stored in plain text by Nomad Plugin 

### 2021-10-06 
- Improper handling of equivalent directory names on Windows 
- Jenkins core bundles vulnerable version of the commons-httpclient library 
- Path traversal vulnerability on Windows 
- Stored XSS vulnerability in Git Plugin 

### 2021-11-04
- Multiple vulnerabilities allow bypassing path filtering of agent-to-controller access control 
- Agent-to-controller access control allowed writing to sensitive directory used by Pipeline: Shared Groovy Libraries Plugin 
- Agent-to-controller access control allows reading/writing most content of build directories 
- Path traversal vulnerability in Subversion Plugin allows reading arbitrary files 

### 2021-11-12
- Stored XSS vulnerability in Active Choices Plugin 
- Stored XSS vulnerability in Scriptler Plugin 
- XXE vulnerability in Performance Plugin 
- XXE vulnerability in pom2config Plugin 
- XXE vulnerability in OWASP Dependency-Check Plugin 
- Arbitrary file write vulnerability in Squash TM Publisher (Squash4Jenkins) Plugin

### 2022-01-12 
- CSRF vulnerability in build triggers 
- CSRF vulnerability and missing permission checks in Mailer Plugin 
- Stored XSS vulnerability in Matrix Project Plugin 
- Missing permission check in Credentials Binding Plugin allows validating secret file credentials IDs 
- OS command execution vulnerability in Docker Commons Plugin 
- Missing permission checks in Bitbucket Branch Source Plugin allow enumerating credentials IDs 
- CSRF vulnerability in Bitbucket Branch Source Plugin allows capturing credentials 
- Missing permission checks in SSH Agent Plugin allow enumerating credentials IDs 
- Access key stored in plain text by Metrics Plugin 
- User passwords transmitted in plain text by Active Directory Plugin 
- Non-constant time token comparison in Configuration as Code Plugin 
- Path traversal vulnerability in Warnings Next Generation Plugin 
- Stored XSS vulnerability in Badge Plugin 
- Improper credentials masking in HashiCorp Vault Plugin 
- Stored XSS vulnerability in Publish Over SSH Plugin 
- CSRF vulnerability and missing permission checks in Publish Over SSH Plugin 
- Path traversal vulnerability in Publish Over SSH Plugin 
- Password stored in plain text by Publish Over SSH Plugin 
- CSRF vulnerability in batch task Plugin 
- Agent-to-controller security bypass in Conjur Secrets Plugin allows decrypting secrets 
- Agent-to-controller security bypass in Conjur Secrets Plugin allows retrieving all credentials 
- Agent-to-controller security bypass in Debian Package Builder Plugin

### 2022-02-09
- DoS vulnerability in bundled XStream library

### 2022-02-15
- OS command execution vulnerabilities in Pipeline-related plugins 
- Vulnerabilities in multiple Pipeline-related plugins allow reading arbitrary files on the controller 
- Sensitive information disclosure in Pipeline: Groovy Plugin 
- Sandbox bypass vulnerability in Pipeline: Shared Groovy Libraries Plugin 
- Sandbox bypass vulnerability in Pipeline: Shared Groovy Libraries Plugin 
- Sandbox bypass vulnerability in Pipeline: Shared Groovy Libraries Plugin 
- Password parameter default values exposed by Pipeline: Build Step Plugin 
- Stored XSS vulnerability in Generic Webhook Trigger Plugin 
- Agent-to-controller security bypass in HashiCorp Vault Plugin 
- Sensitive data stored in plain text by Support Core Plugin 
- Path traversal vulnerability in Fortify Plugin 
- Stored XSS vulnerability in Custom Checkbox Parameter Plugin 
- Missing permission check in Conjur Secrets Plugin allows enumerating credentials IDs 
- Stored XSS vulnerability in Agent Server Parameter Plugin 
- CSRF vulnerability and missing permission checks in Snow Commander Plugin allow capturing credentials 
- CSRF vulnerability and missing permission check in autonomiq Plugin 
- Open redirect vulnerability in GitLab Authentication Plugin 
- Path traversal vulnerability in HashiCorp Vault Plugin allows reading arbitrary files 
- CSRF vulnerability and missing permission check in SCP publisher Plugin 
- CSRF vulnerability and missing permission checks in Checkmarx Plugin allow capturing credentials 
- Stored XSS vulnerability in Promoted Builds (Simple) Plugin 
- Stored XSS vulnerability in Team Views Plugin 
- Agent-to-controller security bypass vulnerability in Doktor Plugin 
- CSRF vulnerability and missing permission checks in dbCharts Plugin 
- CSRF vulnerability and missing permission checks in Chef Sinatra Plugin allow XXE 
- Missing synchronization vulnerability in Convertigo Mobile Platform Plugin allow to capture passwords 
- CSRF vulnerability and missing permission check in SWAMP Plugin allows capturing credentials 

### 2022-03-15
- Sensitive parameter values captured in build metadata files by Parameterized Trigger Plugin 
- Stored XSS vulnerability in Favorite Plugin 
- Stored XSS vulnerability in Dashboard View Plugin 
- CSRF vulnerability and missing permission checks in CloudBees AWS Credentials Plugin 
- Stored XSS vulnerability in Folder-based Authorization Strategy Plugin 
- Agent-to-controller security bypass in Semantic Versioning Plugin 
- Stored XSS vulnerability in Extended Choice Parameter Plugin 
- Arbitrary JSON and property file read vulnerability in Extended Choice Parameter Plugin 
- CSRF vulnerability and missing permission checks in Extended Choice Parameter Plugin allow SSRF 
- Client Secret stored in plain text by GitLab Authentication Plugin 
- Stored XSS vulnerability in global-build-stats Plugin 
- Arbitrary file read vulnerability in Kubernetes Continuous Deploy Plugin 
- Missing permission checks in Kubernetes Continuous Deploy Plugin allow enumerating credentials IDs 
- CSRF vulnerability and missing permission checks in Kubernetes Continuous Deploy Plugin allow capturing credentials 
- Stored XSS vulnerability in List Git Branches Parameter Plugin 
- Stored XSS vulnerability in Environment Dashboard Plugin 
- CSRF vulnerability and missing permission checks in Release Helper Plugin 
- Passwords stored in plain text by dbCharts Plugin 
- Passwords stored in plain text by Vmware vRealize CodeStream Plugin 
- Personal tokens stored in plain text by incapptic connect uploader Plugin

## Next
Next part of this analysis, is to group vulnerability by "type", see [Jenkins - Vulnerability analysis part 2](https://liodeus.github.io/2022/03/19/Jenkins-Vulnerabilities-analysis-part-2.html).