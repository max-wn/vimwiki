## mutt-wizard

### links

1. https://muttwizard.com/
2. https://github.com/LukeSmithxyz/mutt-wizard

### Dependencies

[neomutt](neomutt.md) - the email client. (If you are using Gentoo GNU/Linux, you will need the sasl use flag to be enabled)
[curl](curl.md) - tests connections (required at install).
[isync](isync.md) - downloads and syncs the mail (required if storing IMAP mail locally).
[msmtp](msmtp.md) - sends the email.
[pass](pass.md) - safely encrypts passwords (required at insta

### Optional Dependencies

* pam-gnupg - Automatically logs you into your GPG key on login so you will
  never need to input your password once logged on to your system. Check the
  repo and directions out [here](https://github.com/cruegge/pam-gnupg).
* [lynx](lynx.md) - view HTML email in neomutt.
* [notmuch](notmuch.md) - index and search mail. Install it and run `notmuch
  setup`, tell it that your mail is in `~/.local/share/mail/` (although `mw`
  will do this automatically if you haven't set notmuch up before). You can
  run it in mutt with <kbd>ctrl-f</kbd>. Run `notmuch new` to process new
  mail.
* [abook](abook.md) - a terminal-based address book. Pressing tab while typing
  an address to send mail to will suggest contacts that are in your abook.
* [urlview](urlview.md) - outputs urls in mail to browser.
* cronie - (or any other major cronjob manager) to set up automatic mail
  syncing.
* mpop - If you want to use POP protocol instead of IMAP.

### Usage

```sh
mw

mw: mutt-wizard, auto-configure email accounts for mutt
including downloadable mail with `isync`.

Main actions:
  -a your@email.com     Add an email address
  -l                    List email addresses configured
  -d                    Remove an already added address
  -D your@email.com     Force remove account without confirmation
  -y your@email.com     Sync mail for account by name
  -Y                    Sync mail for all accounts
  -t number             Toggle automatic mailsync every  minutes
  -T                    Toggle automatic mailsync
  -r                    Reorder and set new default account

Options allowed with -a:
  -u    Account login name if not full address
  -n    "Real name" to be on the email account
  -i    IMAP/POP server address
  -I    IMAP/POP server port
  -s    SMTP server address
  -S    SMTP server port
  -x    Password for account (recommended to be in double quotes)
  -p    Add for a POP server instead of IMAP.
  -X    Delete an account's local email too when deleting.
  -o    Configure address, but keep mail online.
  -f    Assume typical English mailboxes without attempting log-on.
```

NOTE: Once at least one account is added, you can run
`mbsync -a` to begin downloading mail.
To change an account's password, run `pass edit your@email.com`.

### neomutt

`neomutt` configured by `mw` will have vim-like bindings. `o` downloads mail. `ctrl-f`
searches mail indexed by `notmuch`. `m` to write mail, `r` to reply to a mail, `y` to
send mail that is written.

See `man mw` for more information. You may also press `?` when within neomutt to get
a full list of key bindings.

---

[[/index|Get Back To Index]]
