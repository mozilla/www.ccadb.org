# CCADB Usage Terms #

## CCADB Data Usage Terms ##

Redistribution and use of this data is permitted provided that neither the name 
and trademarks of Mozilla Corporation nor the names and trademarks of any 
Common CA Database contributor may be used to endorse or promote products 
derived from this data without specific prior written permission.

THIS DATA IS PROVIDED BY MOZILLA CORPORATION AND COMMON CA 
DATABASE CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES 
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE 
DISCLAIMED. IN NO EVENT SHALL MOZILLA CORPORATION AND COMMON 
CA DATABASE CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, 
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE 
GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS 
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE 
OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DATA, EVEN 
IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## CCADB Root Store Operator Usage Terms ##
As permitted by section 4 of the [Common CA Database
Agreement](mozilla-ccadb-agreement.pdf), and in addition to any other requirements set out
therein, Mozilla sets some usage terms and rules for Root Store Operators using
the CCADB, as follows.

### Meetings ###

Root Store Operators of the CCADB may meet by teleconference or
at face-to-face meetings for the purpose of discussing improvements or changes
to the operation of the CCADB. Such discussions should not include
competitively-sensitive information. Mozilla shall not be responsible for the
expenses of any such teleconferences or meetings.

### Customizing the CCADB ###

A Root Store Operator may make customization changes that only impact itself.
Before being applied to the production instance of the CCADB,
changes will be reviewed and tested by Mozilla (or its representative),
including to ensure that the changes will not negatively impact any of the
other Operators or the CCADB. Mozilla will either approve or decline
the proposed changes. If the changes are approved, then a Mozilla
representative will apply the changes to the production instance of the Common
CA Database. If the changes are denied, then the Mozilla representative will
provide an explanation, and the Operator organization may submit the
customizations again after addressing the feedback.

Root Store Operators may request customization changes that impact shared data
and interfaces. Mozilla (or its representative) will review, and approve or
deny such requests. If the request is approved, Mozilla will prioritize the
requested changes, and work with the Operators to design and test the changes in
a sandbox environment before applying them to the production instance of the
CCADB.

The customizations that Mozilla has applied to the CCADB are
available on [GitHub][CCADB-Github].

### Appropriate Data ###

Root Store Operators may store the following types of data in the Common CA
Database, as it pertains to the management of their Root Store Programs.
Aside from contact information, data uploaded to the Common CA Database is 
made generally available to the public:

* CA and subordinate CA certificate data;
* CA Owner information (CA name, company website, physical address, etc.);
* Contact information for CA Points of Contact (name, business email address, business phone number);
* Auditor information (Auditor name and location, auditor qualifications);
* Contact information for Auditors (name, business email address, business phone number);
* URLs to public-facing sites and documents;
* URLs to internal-facing sites and documents (provided the URLs are not
  confidential);
* Root-store-specific status and decisions regarding root inclusion/change
  requests;
* Dates and comments relating to root and intermediate certificates.

Root Store Operators shall **not** store the following types of data in the
CCADB:

* Confidential data
* Personal (as opposed to business) contact information for individuals

[CCADB-Github]:    https://github.com/CCADB
