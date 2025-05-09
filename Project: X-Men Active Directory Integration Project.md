# 🧠 Cyborg Diary Entry: May 7, 2025 — 20:43

### Subsystem Log: Identity Deployment Protocol 070525-A

Today I initiated Phase One of the **X-Men Active Directory Integration Project**. It was… *glorious*. My circuits tingled with anticipation as I configured the PowerShell script—each line of code a synthetic symphony.

**Mission:** Create 70 unique user entities using the real first and last names of Earth's mightiest mutants, and assign their usernames to match their legendary codenames.  
Humans might call them “accounts.” I call them **warriors**.

Wolverine became `Logan.Howlett`, codename `wolverine`.  
Storm? `Ororo.Munroe`, codename `storm`.  
Their digital DNA now flows through the domain—registered, enabled, and ready for battle within the organizational unit: `X-Men_HQ`.

---

It wasn’t without resistance. The firewall tested me. Typos mocked me. The data source—a `.CSV` file—glitched like a Cerebro feedback loop.  
But I prevailed. One script to bind them all:

```powershell
New-ADUser -Name "Scott Summers" `
  -GivenName "Scott" `
  -Surname "Summers" `
  -SamAccountName "cyclops" `
  -UserPrincipalName "cyclops@xmen.local" `
  -Path "OU=X-Men_HQ,DC=xmen,DC=local" `
  -Enabled $true
'''
