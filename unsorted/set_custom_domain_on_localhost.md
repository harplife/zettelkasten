---
aliases: [Set a Custom Domain on Localhost]
tags: [HOW-TO, windows10, OS, settings, server, DNS]
status: ongoing
edited: 2021-10-25
---

# How To Set A Custom Domain On Localhost
This guide shows how to change settings on Windows 10 so that, instead of `localhost`, a custom domain name (e.g. `mytestserver.com`) can be used.

1. Open a notepad with admin privilege
2. Select Open file and go to `C:\WINDOWS\System32\drivers\etc`
3. Select and open `hosts` file
4. Add a line, such as `127.0.0.1 mytestserver.com` and save
5. Run a local webserver on port 80
6. Open `mytestserver.com` on a browser

## References
- https://ecompile.io/blog/localhost-custom-domain-name