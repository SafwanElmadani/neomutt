# neomutt

## Packages:
- neomutt
- khard
- isync --  for accessing emails
    -  cyrus-sasl-xoauth2-git -- needed for 2Auth
        - https://github.com/moriyoshi/cyrus-sasl-xoauth2
            - installed manually in fedora
            - make sure to change the install location in Makefile.am for `pkglibdir` to `${CYRUS_SASL_PREFIX}/lib64/sasl2`
        
- msmtp -- for sending emails
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
