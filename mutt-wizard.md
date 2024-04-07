## mutt-wizard

### links
https://muttwizard.com/
https://github.com/LukeSmithxyz/mutt-wizard

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

---

[[/index|Get Back To Index]]
