# X to Nitter Redirect

A Chrome extension (Manifest V3) that opens every `x.com` link on
[nitter.cf](https://nitter.cf) instead. Links to `twitter.com`, `www.`, and
`mobile.` variants are redirected too.

The path and query string are kept, so
`https://x.com/jack/status/20?s=20` becomes
`https://nitter.cf/jack/status/20?s=20`.

## How it works

The redirect is a single static
[`declarativeNetRequest`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest)
rule in `rules.json`. Chrome applies it to top-level and frame navigations
before the request leaves the browser, so it covers clicked links, typed
URLs, bookmarks, and links opened from other apps. No content scripts run
and the extension cannot read your browsing data.

## Install

1. Open `chrome://extensions`.
2. Turn on **Developer mode** (top right).
3. Click **Load unpacked** and select this folder.

## Using a different Nitter instance

Edit `regexSubstitution` in `rules.json`, replacing `https://nitter.cf` with
the instance you want, then click the reload button on the extension's card
in `chrome://extensions`.
