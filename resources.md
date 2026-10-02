# Useful Resources

## CCADB Support

* For problems or questions when using the CCADB, please contact support [at] ccadb [dot] org.
* You can record enhancements, bugs, and API access requests in the 'Common CA Database' [component](https://bugzilla.mozilla.org/enter_bug.cgi?product=CA%20Program&component=Common%20CA%20Database) under the 'CA Program' [product](https://bugzilla.mozilla.org/describecomponents.cgi?product=CA%20Program) in Bugzilla.

## CCADB Data

The [CCADB Data Usage Terms](rootstores/usage#ccadb-data-usage-terms) applies to all data hosted in and by the CCADB.

### Root Store Information

The Root Store Operators participating in the CCADB are described below, along with resources and reports that may be helpful to members of the community.

**It is crucial to understand** that each of these root stores is carefully managed for specific use cases and user communities. While the availability of root store reports and associated certificate bundles may seem convenient for re-use, re-purposing custom-built root stores for applications that do not perfectly align with their intended products, communities, or policies can introduce significant risks to security and interoperability. Such misuse can undermine the very protections these root stores are designed to provide. 

In most cases, it's far more appropriate and secure to curate a purpose-built root store tailored to satisfy the specific risk-based determinations of your corresponding user community. To assist user communities in considering and establishing their own root stores, several additional reports are provided in the [Community Reports](#community-reports) section of this page. These can help you determine the set of roots most appropriate for your PKI use case and community goals, leading to a more secure and interoperable outcome compared to simply reusing a root store that you do not control.

#### Apple 

**Policy:** [Apple Root Certificate Program](https://www.apple.com/certificateauthority/ca_program.html) 

**Additional Resources:** 
     
**Contact:** certificate-authority-program [at] apple [dot] com 

**Root Store Reports:** 

| PKI Use Case              | Downloads         | Note       |
| ------------------------- | ----------------- | ---------- |
| TLS Server Authentication | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=AppleTLSServerAuthenticationCSV) |            |
| TLS Client Authentication | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=AppleTLSClientAuthenticationCSV) |            |
| S/MIME                    | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=AppleSMIMECSV) |            |
| Timestamping              | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=AppleTimestampingCSV) |            |

<br>

#### Cisco

**Policy:** [Cisco PKI: Trusted Root Stores](https://www.cisco.com/security/pki/trs/readme.html)

**Additional Resources:** 

- [Frequently Asked Questions](https://www.cisco.com/security/pki/trs/readme.html#frequently-asked-questions)
     
**Contact:**  trust-root-store [at] external [dot] cisco [dot] com

**Root Store Reports:** 

- See the [bundles](https://www.cisco.com/security/pki/trs/readme.html) offered by Cisco.

<br>

#### Google Chrome

**Policy:** [Chrome Root Program Policy](https://g.co/chrome/root-policy)

**Additional Resources:** 
- [Moving Forward, Together](https://googlechrome.github.io/chromerootprogram/moving-forward-together/)
- [Chrome Root Store & Certificate Verifier FAQ](https://chromium.googlesource.com/chromium/src/+/main/net/data/ssl/chrome_root_store/faq.md)
     
**Contact:** chrome-root-program [at] google [dot] com

**Root Store Reports:** 

| PKI Use Case              | Downloads         | Note       |
| ------------------------- | ----------------- | ---------- |
| TLS Server Authentication | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=ChromeTLSServerAuthenticationCSV) | This download includes certificates that are [constrained](https://chromium.googlesource.com/chromium/src/+/main/net/cert/root_store.proto#13) for various reasons. |

<br>

#### Microsoft

**Policy:** [Trusted Root Program Requirements](https://aka.ms/RootCert)

**Additional Resources:** 
- [Trusted Root Certificate Program Updates](https://aka.ms/rootupdates)
- [Trusted Root Audit Requirements](https://aka.ms/auditreqs)
     
**Contact:** msroots [at] microsoft [dot] com

**Root Store Reports:**  

| PKI Use Case                   | Downloads         | Note       |
| ------------------------------ | ----------------- | ---------- |
| TLS Server Authentication      | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftTLSServerAuthenticationCSV) |            |
| TLS Client Authentication      | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftTLSClientAuthenticationCSV) |            |
| S/MIME                         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftSMIMECSV) |            |
| Timestamping                   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftTimestampingCSV) |            |
| Code Signing                   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftCodeSigningCSV) |            |
| Document Signing               | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftDocumentSigningCSV) |            |
| Encrypting File System         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftEncryptingFileSystemCSV) |            |
| IP Security End System         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftIPSecurityEndSystemCSV) |            |
| IP Security IKE Intermediate   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftIPSecurityIKEIntermediateCSV) |            |
| IP Security Tunnel Termination | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftIPSecurityTunnelTerminationCSV) |            |
| IP Security User               | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MicrosoftIPSecurityUserCSV) |            |

<br>

#### Mozilla  

**Policy:** [Mozilla Root Store Policy](https://www.mozilla.org/en-US/about/governance/policies/security-group/certs/policy/)

**Additional Resources:** 
- [Root Program Documentation](https://wiki.mozilla.org/CA)
- [CA Communications](https://wiki.mozilla.org/CA/Communications)
- [CA Incident Dashboard](https://wiki.mozilla.org/CA/Incident_Dashboard)
- [dev-security-policy WebPKI Forum](https://groups.google.com/a/mozilla.org/g/dev-security-policy)
     
**Contact:** certificates [at] mozilla [dot] org

**Root Store Reports:**  

| PKI Use Case              | Downloads         | Note       |
| ------------------------- | ----------------- | ---------- |
| TLS Server Authentication | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MozillaTLSServerAuthenticationCSV) |            |
| S/MIME                    | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=MozillaSMIMECSV) |            |

<br>

### Community Reports

#### Use-case Specific Reports

The following reports contain any root Certification Authority (CA) certificate trusted for the given PKI use case by at least one CCADB Root Store Operator. The `Trust Bits for Root Cert` field is auto updated from a CCADB trigger that uses the collection of trust bits from all CCADB root stores. All "Apple Constrained", "Google Chrome Constrained", "Microsoft Constrained", "Mozilla Constrained" values will be boolean depending on if any constraint information exists for that root program on that root certificate.

| PKI Use Case                   | Downloads         | Note       |
| ------------------------------ | ----------------- | ---------- |
| TLS Server Authentication      | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=TLSServerAuthenticationCSV) | Trust Bits for Root Cert INCLUDES Server Authentication AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| TLS Client Authentication      | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=TLSClientAuthenticationCSV) | Trust Bits for Root Cert INCLUDES Client Authentication AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| S/MIME                         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=SMIMECSV) | Trust Bits for Root Cert INCLUDES Secure Email AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| Timestamping                   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=TimestampingCSV) | Trust Bits for Root Cert INCLUDES Time Stamping AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| Code Signing                   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=CodeSigningCSV) | Trust Bits for Root Cert INCLUDES Code Signing AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| Document Signing               | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=DocumentSigningCSV) | Trust Bits for Root Cert INCLUDES Document Signing AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| Encrypting File System         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=EncryptingFileSystemCSV) | Trust Bits for Root Cert INCLUDES Encrypting File System AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| IP Security End System         | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=IPSecurityEndSystemCSV) | Trust Bits for Root Cert INCLUDES IP Security End System AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| IP Security IKE Intermediate   | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=IPSecurityIKEIntermediateCSV) | Trust Bits for Root Cert INCLUDES IP Security IKE Intermediate AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| IP Security Tunnel Termination | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=IPSecurityTunnelTerminationCSV) | Trust Bits for Root Cert INCLUDES IP Security Tunnel Termination AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |
| IP Security User               | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/Report?Name=IPSecurityUserCSV) | Trust Bits for Root Cert INCLUDES IP Security User AND ((Apple Status != Not Included OR Removed) OR (Google Chrome Status != Not Included OR Removed) OR (Microsoft Status != Not Included OR Pending OR Removed) OR (Mozilla Status != Not Yet Included OR Removed OR Obsolete)) |

<br>

#### Additional Reports

| Description                    | Downloads         | Note       |
| ------------------------------ | ----------------- | ---------- |
| [AllCertificateRecords REST API](https://github.com/mozilla/CCADB-Tools/blob/master/API_AllCertificateRecords/README.md) | N/A | [Description](https://docs.google.com/document/d/1S3u0-_YACA7m-3LPpjE-t4WCh2cww_SQFh2C9DJeXHA/edit?usp=sharing) of report fields. This API intends to one day replace the All Certificate Information reports. |
| V5 All Certificate Information (root and intermediate) in the CCADB | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatV5) | [Description](https://docs.google.com/document/d/1S3u0-_YACA7m-3LPpjE-t4WCh2cww_SQFh2C9DJeXHA/edit?usp=sharing) of report fields. |
| V4 All Certificate Information (root and intermediate) in the CCADB | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatv4) | [V4a](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatV4a) (Records of CA certificates, excluding those that expired more than five years ago) [V4b](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormatV4b) (Records of CA certificates expired over five years ago). These two reports–V4a and V4b–are mutually exclusive partitions of the full dataset for V4 and can be combined to reconstruct the complete list. |
| All Included Root Certificate Trust Bit Settings | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllIncludedRootCertsCSV) | |
| List of CA problem reporting mechanisms (email, etc.) | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllProblemReportingMechanismsCSV) / [Custom](https://ccadb.my.salesforce-sites.com/ccadb/AllProblemReportingMechanismsReport) | Use this download to report a certificate problem directly to the CA. |
| List of CAA Identifiers | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCAAIdentifiersReportCSVV2) / [Custom](https://ccadb.my.salesforce-sites.com/ccadb/AllCAAIdentifiersReportV2) | Used to restrict issuance of certificates to specific CAs via a [DNS Certification Authority Authorization Resource Record](https://tools.ietf.org/html/rfc6844). |
| Disclosed Domain Control Validation Practices | [CSV](https://ccadb.my.salesforce-sites.com/googlechrome/TLSCertDomainValidationCSVFormat) | |
| Accepted Roots for Production Certificate Transparency Logs | [CSV](https://ccadb.my.salesforce-sites.com/ccadb/RootCACertificatesIncludedByRSReportCSV) | Includes CAs trusted by at least one of the CCADB root stores. |
| Accepted Roots for Test Certificate Transparency Logs| [CSV](https://ccadb.my.salesforce-sites.com/ccadb/RootCACertificatesInclusionReportCSV) | Includes CAs that have applied to at least one of the CCADB root stores. |
| All Certificate PEMs Year| [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificatePEMsCSVFormat?NotBeforeYear=1999) | Provides the certificate PEMs for which the CCADB record has a ‘Valid From (GMT)’ field that contains 1999. Change "1999" in the URL to a year of your choosing. |
| All Certificate PEMs Decade| [CSV](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificatePEMsCSVFormat?NotBeforeDecade=2010) | Provides the certificate PEMs for which the CCADB record has a ‘Valid From (GMT)’ field that contains 2010. Change "2010" in the URL to a decade of your choosing. |

<br>

### Additional Resources ###
- [crt.sh Certificate Search](https://crt.sh/)
- [Censys Certificate Search](https://censys.io/)
- [Certificate Explainer](https://tls-observatory.services.mozilla.com/static/certsplainer.html)
- [public@ccadb.org Forum](https://groups.google.com/a/ccadb.org/g/public)
- [Trust Service Provider Technical Best Practices](/documents/TSP_Technical_Best_Practices_eIDAS.pdf)
- [Qualified Website Authentication Certificates (QWACs) Interoperability](/documents/Qualified_Website_Authentication_Certificates_Interoperability.pdf)
