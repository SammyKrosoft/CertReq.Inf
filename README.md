# CertReq
This repository is to create some guidance on how to create a certificate request.
I'll start with the information from my friend Rhoderick Milne from this blog post :
https://blogs.technet.microsoft.com/rmilne/2014/06/17/how-to-request-certificate-without-using-iis-or-exchange/

## CertReq initialization file
That is the "CertReq.inf" file on this repository, directly taken from Rhod's above article.
https://github.com/SammyKrosoft/CertReq.Inf/blob/master/CertReq.inf 

## CertReq command line
That one is :

```Batchfile
CertReq.exe -New CertReq.inf MyCertReq.req
```
And takes the information defined in the CertReq initialization file to create a Cert Request that you'll give to your Certification Authority.

Once you receive the response from the CA (Internal or External -Public- one), you must "mate" the "pending certificate request" with the signed CA response certificate using :

```Batchfile
CertReq -Accept CertReceivedFromCA.cer
```

IMPORTANT : the whole ```Batchfile CertReq -New and CertReq -Accept``` MUST be done on the same machine ... because when you create a CertRequest, a pair of keys are generated : one Public key, that is encoded with the .Req certificate request, and one Private key, that stays on the machine (encrypted, and under the Windows\Crypto\... subfolder)

## Other methods
Other well known methods to generate a certificate requests are through IIS and/or Exchange (using New-ExchangeCertificateRequest / Import-ExchangeCertificate / Enable-ExchangeCertificate), but I won't detail these about it, plenty of examples on the internet, including a DIGICERT Exchange PowerShell Certificate Request generator that work very well with any Exchange version - not only Exchange 2010)

IMPORTANT: just like the CertReq method, the Certificate Request and Acceptation/Import MUST be done from the same machine - with any methods, a pair of keys are created - one Public that is inside the request file and one Private that stays on the machine under Windows\Crypto\.... subfolder - and once imported the Private Key is attached (or "mated" like Rhoderick like to write it) with the received certificate from the Internal or External/Public CA.
