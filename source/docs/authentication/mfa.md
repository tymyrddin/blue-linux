# Use multi-factor authentication (MFA)

Many sites and applications offer two-factor authentication (2FA), also named multi-factor authentication (MFA). 
With 2FA enabled, logging into a website or application requires both a password and a unique code that is texted to 
your phone number or delivered via an authenticator app. You have to input this code in order to gain access to your 
account. Even if someone else has your password, they will not be able to break into your accounts if they can not get 
the code.

When you use one of the authenticator apps included here, you bolster the password you know with the token, 
smartphone, or smartwatch that you have.

Setting up MFA usually involves scanning a QR code on the site with your phone's authenticator app. Note that you can 
scan the code to more than one phone, if you want a backup.

Authenticator apps generate time-based, one-time passcodes (TOTP or OTP), which are usually six digits that refresh 
every 30 seconds. Once you set up MFA, every time you want to log in to a site, you enter the code into the secured app 
or site's login page, and you’re in. The time limit means that if an adversary manages to get your one-time passcode, 
it won’t work for them after that 30 seconds.

Something to look for when choosing one of these apps is whether it backs up the account info (encrypted, of course) in 
case you no longer have the phone you set everything up on. These all do (Google Authenticator does not).

* [Authy](https://authy.com/)
* [Duo Mobile](https://duo.com/product/multi-factor-authentication-mfa/)
* [LastPass Authenticator](https://www.lastpass.com/solutions/authentication)
* [Microsoft Authenticator](https://www.microsoft.com/en-gb/security/mobile-authenticator-app)