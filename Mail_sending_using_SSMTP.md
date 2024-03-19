# Mail sending using SSMTP.
## Preparation and settings.Preparation and settings.

### If You Have No email service, start by chosing one of it:
- mailganer,
- Sendsay,
- UniSender,
- mail Google Workspace,
- mail Microsoft Office 365.

#### Now, we have a mail service Provider and we have to know SMTP Server settings to use it in our settings file.Now, we have a mail service Provider and we have to know SMTP Server settings to use it in our settings file.
For Example:
If You still don't know SMTP Settings from your Google account, do the following:
1. Open your Google Account Security Settings page https://myaccount.google.com/security
2. Scroll down and click on the Application password section
3. Then, create a new Application password and copy it, to any secure place - (encrypted file, password manager e.t.c.) for use later.
> **NOTE:** You never can see this password again after the window closes.NOTE: You never can see this password again after the window closes.

### 1. Let`s install and prepare to use SSMTP on to the Server:
```bash
# apt update
# apt install ssmtp
```
### 2. Stettings in the ssmtp.conf
```bash
# nano /etc/ssmtp/ssmtp.conf
```
> If You have no the nono  editor in your system, you can add it using foloving:
```bash
# apt install nano
```

#### Gmail:
```bash
mailhub=smtp.gmail.com:587
hostname=smtp.gmail.com:587
root=your_account@gmail.com
AuthUser=your_account@gmail.com
AuthPass=your_account
UseSTARTTLS=YES
UseTLS=YES
FromLineOverride=YES
TLS_CA_File=/etc/pki/tls/certs/ca-bundle.crt
```
### 3. Settings the revaliases:
```bash
# nano /etc/ssmtp/revaliases
```
#### Gmail:
```bash
root:your_account@gmail.com:smtp.gmail.com:587
```
### 4. Chenge your mail sender to the SSMTP
```bash
# mv /usr/sbin/sendmail /usr/sbin/sendmail.orig
```

### 5. Create a symlink to the SSMTP instead of Sendmail
```bash
# ln -s /usr/sbin/ssmtp /usr/sbin/sendmail
```
### 6. Check your email sending
```bash
# $ echo test | mail -v -s "testing ssmtp" address@of-mail-reciever.net
```
### 7. If mails don't send, turn off captcha for new application logins

## Enjoy fully controlled your side mail sender

> [Online MarkDown Editor](http://https://pandao.github.io/editor.md/en.html "Online MarkDown Editor")

> [MarkDown Preview, Edit and Import/Export tool](https://dillinger.io/ "MarkDown Preview, Edit and Import/Export tool")
