---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

## What is PHX.SH?

PHX.SH is just a domain name for local web-app development.

It has DNS entries that point `*.phx.sh` to `127.0.0.1`

**This means that you can goto `https://your-app.phx.sh:4000` on your computer to access the app you're working on.**

<hr>

## Why?

HTTP/2 (H2) requires HTTPS (tls).

Phoenix has introduced a mix task to generate a self signed certificate for your project. It's a lot more manageable
if you generate a separate certificate for each project so that you can choose to trust (or not trust) them individually.

<hr>

## How do I Use it?

Run `mix phx.gen.cert` to generate a certificate to use with your app.

```
mix phx.gen.cert your-app.phx.sh
```

Then run

```
mix phx.server
```

And access your application at **https://your-app.phx.sh**

<hr>

## I need this to work offline.

For offline use you can add a DNS Entry to `/etc/hosts`

```
127.0.0.1               app-name.phx.sh
```

Or you can use something like dnsmasq.
