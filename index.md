---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

## What is PHX.SH?

PHX.SH is just a domain name for local web-app development.

It has DNS entries that point `*.phx.sh` to `127.0.0.1`

**This means that you can goto `https://my-app.phx.sh:4000` on your computer to access the app you're working on.**

<hr>

## Why?

HTTP/2 (H2) requires HTTPS (tls). So you will need to use a certificate for local development.

Phoenix has introduced a mix task to generate a self signed certificate for your project. It's a lot more manageable
if you generate a separate certificate for each project so that you can choose to trust (or not trust) them individually.

<hr>

## How do I Use it?

Run `mix phx.gen.cert` to generate a certificate to use with your app.

```
mix phx.gen.cert my-app.phx.sh
```

You then need to update your `config/dev.exs` to include the certificate and turn on the strong cipher suite.

```elixir
config :my_app, MyApp.Endpoint,
       # ...
       https: [
         port: 4000,
         cipher_suite: :strong,
         keyfile: "priv/cert/selfsigned_key.pem",
         certfile: "priv/cert/selfsigned.pem"
       ]
```

Then run

```
mix phx.server
```

And access your application at **https://my-app.phx.sh:4000**

<hr>

## I need this to work offline.

For offline use you can add a DNS Entry to `/etc/hosts`

```
127.0.0.1               app-name.phx.sh
```

Or you can use something like dnsmasq. (See setup instructions here: https://gist.github.com/ogrrd/5831371)
