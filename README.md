# neomutt

## Packages:
    - neomutt
    - khard
    - isync
    - msmtp
    - pass
    - lynx
    - notmuch
    - urlview

## Encryption
- using gpg
    - create a file with the passwords needed e.g., set imap_pass = "123456789", then encrypt it.
        - gpg --encrypt -r fingureprintID_or_email gmail.pw 
            - will generate gmail.pw.gpg file
        - add the file in neomutt config as: `source "gpg -dq /path/to/gmail.pw.gpg |"`
