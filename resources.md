# Useful Resources #

### CCADB Data ###
* [CCADB Data Usage Terms](rootstores/usage#ccadb-data-usage-terms) 
* Code Signing Root Certificates
  * [PEM of Root Certificates in Microsoft's Root Store with the Code Signing Trust Bit Enabled (TXT)](https://ccadb-public.secure.force.com/microsoft/IncludedRootsPEMTxtForMSFT?TrustBitsInclude=Code%20Signing)
  * [PEM of Root Certificates in Microsoft's Root Store with the Code Signing Trust Bit Enabled (CSV)](https://ccadb-public.secure.force.com/microsoft/IncludedRootsPEMCSVForMSFT?TrustBitsInclude=Code%20Signing)
* Email (S/MIME) Root Certificates
  * [PEM of Root Certificates in Mozilla's Root Store with the Email (S/MIME) Trust Bit Enabled (TXT)](https://ccadb-public.secure.force.com/mozilla/IncludedRootsPEMTxt?TrustBitsInclude=Email)
  * [PEM of Root Certificates in Mozilla's Root Store with the Email (S/MIME) Trust Bit Enabled (CSV)](https://ccadb-public.secure.force.com/mozilla/IncludedRootsPEMCSV?TrustBitsInclude=Email)
* Server Authentication (SSL/TLS) Root Certificates
  * [PEM of Root Certificates in Mozilla's Root Store with the Websites (TLS/SSL) Trust Bit Enabled (TXT)](https://ccadb-public.secure.force.com/mozilla/IncludedRootsPEMTxt?TrustBitsInclude=Websites)
  * [PEM of Root Certificates in Mozilla's Root Store with the Websites (TLS/SSL) Trust Bit Enabled (CSV)](https://ccadb-public.secure.force.com/mozilla/IncludedRootsPEMCSV?TrustBitsInclude=Websites)
* [All certs (root and intermediate) in CCADB](http://ccadb-public.secure.force.com/ccadb/AllCertificateRecordsCSVFormat) (CSV)
* [List of CA problem reporting mechanisms (email, etc.)](https://ccadb-public.secure.force.com/ccadb/AllProblemReportingMechanismsReport) (use this to report a certificate problem directly to the CA)
* [List of CAA Identifiers](https://ccadb-public.secure.force.com/ccadb/AllCAAIdentifiersReport) (used to restrict issuance of certificates to specific CAs via a [DNS Certification Authority Authorization Resource Record](https://tools.ietf.org/html/rfc6844))
    * [CSV List of CAA Identifiers](https://ccadb-public.secure.force.com/ccadb/AllCAAIdentifiersReportCSV) 

### Mozilla ###
* [Root Program Documentation](https://wiki.mozilla.org/CA)
* [Root Store Policy](https://www.mozilla.org/about/governance/policies/security-group/certs/policy/)
* [CA Communications](https://wiki.mozilla.org/CA/Communications)
* [CA Incident Dashboard](https://wiki.mozilla.org/CA/Incident_Dashboard)

### Microsoft ###
* [Trusted Root Program Requirements](https://aka.ms/RootCert)
* [Trusted Root Certificate Program Updates](https://aka.ms/rootupdates)
* [Trusted Root Audit Requirements](http://aka.ms/auditreqs)

### General ###
* [crt.sh Certificate Search](https://crt.sh/)
* [Censys Certificate Search](https://censys.io/)
* [Certificate Explainer](https://tls-observatory.services.mozilla.com/static/certsplainer.html)
* [dev-security-policy WebPKI Forum](https://www.mozilla.org/about/forums/#dev-security-policy)
* [Trust Service Provider Technical Best Practices](/documents/TSP_Technical_Best_Practices_eIDAS.pdf)
* [Qualified Website Authentication Certificates (QWACs) Interoperability](/documents/Qualified_Website_Authentication_Certificates_Interoperability.pdf)
