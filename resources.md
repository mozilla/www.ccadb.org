# Useful Resources #

### CCADB Data ###
* [CCADB Data Usage Terms](rootstores/usage#ccadb-data-usage-terms) 
* Code Signing Root Certificates
  * [PEM of Root Certificates in Microsoft's Root Store with Code Signing EKU (TXT)](https://ccadb.my.salesforce-sites.com/microsoft/IncludedRootsPEMTxtForMSFT?MicrosoftEKUs=Code%20Signing)
  * [PEM of Root Certificates in Microsoft's Root Store with Code Signing EKU (CSV)](https://ccadb.my.salesforce-sites.com/microsoft/IncludedRootsPEMCSVForMSFT?MicrosoftEKUs=Code%20Signing)
* Email (S/MIME) Root Certificates
  * [PEM of Root Certificates in Mozilla's Root Store with the Email (S/MIME) Trust Bit Enabled (TXT)](https://ccadb.my.salesforce-sites.com/mozilla/IncludedRootsPEMTxt?TrustBitsInclude=Email)
  * [PEM of Root Certificates in Mozilla's Root Store with the Email (S/MIME) Trust Bit Enabled (CSV)](https://ccadb.my.salesforce-sites.com/mozilla/IncludedRootsDistrustSMIMEPEMCSV?TrustBitsInclude=Email)
* Server Authentication (SSL/TLS) Root Certificates
  * [PEM of Root Certificates in Mozilla's Root Store with the Websites (TLS/SSL) Trust Bit Enabled (TXT)](https://ccadb.my.salesforce-sites.com/mozilla/IncludedRootsPEMTxt?TrustBitsInclude=Websites)
  * [PEM of Root Certificates in Mozilla's Root Store with the Websites (TLS/SSL) Trust Bit Enabled (CSV)](https://ccadb.my.salesforce-sites.com/mozilla/IncludedRootsDistrustTLSSSLPEMCSV?TrustBitsInclude=Websites)
* [All Certificate Information (root and intermediate) in CCADB](https://ccadb.my.salesforce-sites.com/ccadb/AllCertificateRecordsCSVFormat) (CSV)
* [All Included Root Certificate Trust Bit Settings](https://ccadb.my.salesforce-sites.com/ccadb/AllIncludedRootCertsCSV) (CSV)
* [List of CA problem reporting mechanisms (email, etc.)](https://ccadb.my.salesforce-sites.com/ccadb/AllProblemReportingMechanismsReport) (use this to report a certificate problem directly to the CA)
* [List of CAA Identifiers](https://ccadb.my.salesforce-sites.com/ccadb/AllCAAIdentifiersReport) (used to restrict issuance of certificates to specific CAs via a [DNS Certification Authority Authorization Resource Record](https://tools.ietf.org/html/rfc6844))
    * [CSV List of CAA Identifiers](https://ccadb.my.salesforce-sites.com/ccadb/AllCAAIdentifiersReportCSV) 
    
### All Certificate PEMs ###
The AllCertificatePEMsCSVFormat report accepts one of the following two parameters: NotBeforeYear or NotBeforeDecade.

Examples:
* https://ccadb.my.salesforce-sites.com/ccadb/AllCertificatePEMsCSVFormat?NotBeforeYear=1999
   * Provides the certificate PEMs for which the CCADB record has a ‘Valid From (GMT)’ field that contains 1999.
* https://ccadb.my.salesforce-sites.com/ccadb/AllCertificatePEMsCSVFormat?NotBeforeDecade=2010
   * Provides the certificate PEMs for which the CCADB record has a ‘Valid From (GMT)’ field that contains 201.

### Mozilla ###
* [Root Program Documentation](https://wiki.mozilla.org/CA)
* [Root Store Policy](https://www.mozilla.org/about/governance/policies/security-group/certs/policy/)
* [CA Communications](https://wiki.mozilla.org/CA/Communications)
* [CA Incident Dashboard](https://wiki.mozilla.org/CA/Incident_Dashboard)
* [dev-security-policy WebPKI Forum](https://groups.google.com/a/mozilla.org/g/dev-security-policy)

### Microsoft ###
* [Trusted Root Program Requirements](https://aka.ms/RootCert)
* [Trusted Root Certificate Program Updates](https://aka.ms/rootupdates)
* [Trusted Root Audit Requirements](https://aka.ms/auditreqs)

### Google Chrome ###
* [Chrome Root Program Policy](https://g.co/chrome/root-policy)
* [Chrome Root Store & Certificate Verifier FAQ](https://chromium.googlesource.com/chromium/src/+/main/net/data/ssl/chrome_root_store/faq.md)

### General ###
* [crt.sh Certificate Search](https://crt.sh/)
* [Censys Certificate Search](https://censys.io/)
* [Certificate Explainer](https://tls-observatory.services.mozilla.com/static/certsplainer.html)
* [public@ccadb.org WebPKI Forum](https://groups.google.com/a/ccadb.org/g/public)
* [Trust Service Provider Technical Best Practices](/documents/TSP_Technical_Best_Practices_eIDAS.pdf)
* [Qualified Website Authentication Certificates (QWACs) Interoperability](/documents/Qualified_Website_Authentication_Certificates_Interoperability.pdf)
