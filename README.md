# CertReq
This repository is to create some guidance on how to create a certificate request.
I'll start with the information from my friend Rhoderick Milne from this blog post :
https://blogs.technet.microsoft.com/rmilne/2014/06/17/how-to-request-certificate-without-using-iis-or-exchange/

## CertReq initialization file
Directly taken from Rhod's above article
## CertReq command line
That one is :

CertReq.exe -New CertReq.inf MyCertReq.req

And takes the information defined in the CertReq initialization file to create a Cert Request that you'll give to your Certification Authority.

## Other methods
Other well known methods to generate a certificate requests are through IIS and/or Exchange (using New-ExchangeCertificateRequest / Import-ExchangeCertificate / Enable-ExchangeCertificate), but I won't detail these about it, plenty of examples on the internet, including a DIGICERT Exchange PowerShell Certificate Request generator that work very well with any Exchange version - not only Exchange 2010)
