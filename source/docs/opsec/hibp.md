# ';--have i been pwned?

[';--have i been pwned? (HIBP)](https://haveibeenpwned.com/) is a database of several billion email addresses (and, separately, passwords) that have appeared in a publicly known past data breach. The service creates an SHA-1 hash of the submitted email address and passes the first six characters of that to HIBP's hash range query API. HIBP then returns a range of possible matches, if any, to the six character string, without ever handling the full email address.

Check if you have an account that has been compromised in a data breach, and if so, change your password and change it in any other place where you’ve used that password. Better yet, never use a password twice, and consider using a password manager.
