---
layout: default
title: Frequently Asked Questions
nav_order: 8
---
# **Frequently Asked Questions (FAQ)**
{: .no_toc }

---

<details open markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

---

# Installing and launching Stash

The installation instructions are available from the [README.md](https://github.com/stashapp/stash).

## How do I get into Stash once installed?

#### Windows

- Run the executable (typically `stash-win.exe`). The app will start up in a terminal window, read in your configuration and then give you a URL to connect with in your browser.
- _Note for Windows users_: Running the app might present a security prompt since the binary isn't signed yet. Just click more info and then the `run anyway` button.
- Navigate to http://localhost:9999 to get started.

#### macOS

- Run `./stash-osx` from the terminal on macOS.
- _Note for Mac users_: If you have trouble, try running `chmod u+x stash-osx` to make the file executable.
- Navigate to http://localhost:9999 to get started.

#### Linux


- Run `./stash-linux` from the terminal on Linux.
- _Note for Linux users_: If you have trouble, try running `chmod u+x stash-linux` to make the file executable.
- Navigate to http://localhost:9999 to get started.

---

# Logging in

## How do I recover a forgotten username or password?

Stash saves login credentials in the `config.yml` file. You must reset both login and password if you have forgotten your password by doing the following:
- Close your Stash process;
- Open the `config.yml` file found in your Stash directory with a text editor;
- Delete the `login` and `password` lines from the file and save;
- Stash authentication should now be reset with no authentication credentials.

---

## How can I connect to my server from elsewhere within my network?

Find the local IP address of your Stash Server (guides for [Windows](https://support.microsoft.com/en-us/windows/find-your-ip-address-in-windows-f21a9bbc-c582-55cd-35e0-73431160a1b9), [MacOS](https://support.apple.com/guide/mac-help/find-your-computers-name-and-network-address-mchlp1177/11.0/mac/11.0), [Linux](https://wiki.archlinux.org/title/Network_configuration#IP_addresses)). Then, on another device on your local network, open a browser to http://SERVER.IP.ADDRESS.HERE:9999/

See [this article]({{ site.baseurl }}/docs/Authentication-Required-When-Accessing-Stash-From-the-Internet#alternative-and-safe-methods-to-access-your-stash) for ideas on accessing your stash from outside your network.

---

## How do I serve Stash over SSL/TLS (HTTPS)?
This is typically accomplished by putting Stash behind a reverse proxy, such as Nginx or Caddy. Stash can also serve SSL directly.
To use the built-in SSL:
First you must generate a SSL certificate and key combo.  Here is an example using openssl:

`openssl req -x509 -newkey rsa:4096 -sha256 -days 7300 -nodes -keyout stash.key -out stash.crt -extensions san -config <(echo "[req]"; echo distinguished_name=req; echo "[san]"; echo subjectAltName=DNS:stash.server,IP:127.0.0.1) -subj /CN=stash.server`

This command would need customizing for your environment.  [This link](https://stackoverflow.com/questions/10175812/how-to-create-a-self-signed-certificate-with-openssl) might be useful.

Once you have a certificate and key file name them `stash.crt` and `stash.key` and place them in the same directory as the `config.yml` file, or the `~/.stash` directory.  Stash detects these and starts up using HTTPS rather than HTTP.

---

## How do I serve Stash in a Subpath?

The basepath defaults to `/`. When running stash via a reverse proxy in a subpath, the basepath can be changed by having the reverse proxy pass `X-Forwarded-Prefix` (and optionally `X-Forwarded-Port`) headers. When detects these headers, it alters the basepath URL of the UI.

---

# Working with Content

## What's the best way to add metadata to Stash?

* Stash includes a single scraper, but you can add more via the [CommunityScrapers repo](https://github.com/stashapp/CommunityScrapers). See the README for installation and usage instructions.
* Pierre Delecto wrote [a Python script](https://github.com/ThePornDatabase/stash_theporndb_scraper) for scraping from ThePornDB. This is arguably the fastest way to mass create studios / performers and populate scene data.
* StashDB is a service that allows for crowdsourcing of porn metadata. Check the pinned messages in the #stashbox-invites channel in Discord to start using it.

---

## How do I rename or relocate a library folder?
**If you need to move or rename a folder**, you can remove the existing directory from your library and readd the new location. Stash will recognize the files on the next scan and re-link to the new location. **Do not run a Clean in between these steps, or you will lose the information from your relocated folders** (your files will not be affected).

> **⚠️ Note:** Don't forget to click `Save` after updating these directories!

---

## How do I add galleries?
For gallery-related issues check the relevant Documentation [section](https://github.com/stashapp/stash/blob/develop/ui/v2.5/src/docs/en/Galleries.md).

---

# Scraping

## Scrape behind paywall

A regular scraper can only scrape information from webpages that are open to the public access. If you want to scrape a webpage that requires login or behind a paywall, you need to use the "Visible CDP" technique. So far this technique was tested and passed under Windows 10 only. <p>
Normal CDP scraping will launch a headless chrome browser, which will not show up for any user interactions. "Visible CDP" turns the "headless chrome" into a "visible" instance.<p>
Steps: <p>
1. Prepare your scraper's .yml file and make sure it's valid and working. Your scraper should have the following setting inside:
```
driver:
  useCDP: true
```
2. Run a command console. Go to the Chrome's binary directory and run `chrome.exe --remote-debugging-port=9222`. This will launch a special Chrome instance that Stash Scrapers can control later on.
3. In Stash, make sure that the "Chrome CDP Path" setting is `http://localhost:9222/json/version`.
4. Use the special Chrome instance you launched earlier, go to the webpage you want to scrape, type in your user/pass or pass any other human tests, until you see the page with desired content.
5. Paste the webpage's URL in your Stash scene and start scraping. It should get the information correctly.

---

# Troubleshooting

## Known Issues
- Performer images uploaded in WebP format will not display on versions of Safari prior to version 13 or on anything earlier than MacOS Big Sur. This is a [limitation of Safari](https://caniuse.com/webp).  As a workaround, ensure you are uploading performer images in jpg or png format.

---

## Stash is showing a "FFMPEG Not Found" error
If Stash is unable to find or download FFMPEG, then download and install it yourself:

You can find links to pre-compiled binaries [here](https://github.com/stashapp/stash#pre-compiled-binaries).

The `ffmpeg(.exe)` and `ffprobe(.exe)` files should be placed in `~/.stash` on macOS / Linux or `C:\Users\YourUsername\.stash` on Windows.

---

# Other FAQs

## I have a question not answered here.
Join the Stash [Discord server](https://discord.gg/2TsNFKt).