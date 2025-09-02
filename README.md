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

- gpg with pass
    - generate a key pair with custom UID you be used with `pass init`
        - `gpg --full-generate-key` Then:
        - Key type: usually (1) RSA and RSA
        - Key size: 4096
        - Expiration: up to you (0 = never expires)
        - Real name: e.g. pass-key
        - Email address: you can leave this blank or put none@none
        - Comment: optional
        - If you leave email blank, GPG will still make a key but the UID will just show the name.
    - use `gpg --list-keys` to get the UID or the fingerprint 
    - Initialize pass with UID name or fingerprint
        - `pass init 1234ABCD5678EF901234567890ABCDEF12345678` or `pass init "some_name"`
        - add passwords
            - pass insert work/email
            - keep the same structure to be able to use it across multiple devices
        - list: pass list
        - show: pass work/email
            - add this in neomutt

## davmail
- the launch script set a size of 512M for the heap.
- need to change that to something lager, I used `-Xmx4096m` 4GB
- copied the script from `/usr/bin/davmail` and changed my version
- davmail.properties should be added to ~/.config/davmail because it store refresh token.

#  Contacts for abook if you want to use it instead of khard

# When looking for contacts, use this command
set query_command= "abook --mutt-query '%s'"
# Add current sender to address book
macro index,pager  a "<pipe-message>abook --add-email-quiet<return>" "Add this sender to Abook"
# Auto-complete email addresses by pushing tab
bind editor <Tab> complete-query


## notmuch 
- create a config
- to create one run, `notmuch setup`. This will create one in ~/.notmuch-config
    - will ask you for the location of the mail
- link the tagging script: `ln -s /home/safwan/.config/neomutt/.notmuch/hooks/post-new` in `/home/safwan/Documents/mail/.notmuch/hooks`
- run `notmuch new`

## khard
- clone the repo in github in .config

