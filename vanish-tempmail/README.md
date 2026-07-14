# Vanish — disposable email, one click

A static, no-backend disposable-inbox site. Generates a real address on a
domain you pick (or a random one), receives real mail, lets you delete a
message or the whole inbox whenever you want.

## How mail delivery works

The frontend talks directly to [mail.tm](https://mail.tm), a free public
API that issues real inboxes on real domains and lets the browser poll for
new messages. There's no backend of yours involved — your GitHub Pages
site is only the UI.

If you preview this inside a sandboxed tool (like an in-chat artifact
preview) and see `Failed to fetch`, that's the sandbox blocking outbound
network requests, not a bug — it works normally once hosted on GitHub
Pages or opened as a real page.

## About the domain picker

The dropdown is populated **live** from mail.tm's own `/domains` endpoint,
not a hardcoded list. This matters because an address only receives mail
if the domain is one the provider actually owns and has MX records for —
a made-up domain name looks fine in the UI but silently receives nothing.
So the picker always shows whatever real, working domains the provider
currently has active (their pool rotates over time), plus a "random"
option. If there aren't 10 live at once, that's the provider's real count,
not a limitation in this code.

## License

MIT — see `LICENSE`.
