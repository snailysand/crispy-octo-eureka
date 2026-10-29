# X to Xitter Redirect

A Chrome extension that opens every `x.com` link on
[xitter.cf](https://xitter.cf) instead. Links to `twitter.com`, `www.`, and
`mobile.` variants are redirected too.

The path and query string are kept, so
`https://x.com/jack/status/20?s=20` becomes
`https://xitter.cf/jack/status/20?s=20`.

It works the same on Windows, macOS, Linux, and ChromeOS, and in other
Chromium browsers such as Microsoft Edge and Brave.

## Install

### Step 1: Download the extension

1. Open
   <https://github.com/snailysand/crispy-octo-eureka/tree/claude/chrome-nitter-redirect-zv07nn>.
2. Click the green **Code** button, then **Download ZIP**.

### Step 2: Unzip it

- **Windows:** right-click the ZIP file and choose **Extract All**, then
  **Extract**.
- **macOS:** double-click the ZIP file.

Move the unzipped folder somewhere you won't delete by accident, such as
your Documents folder. Chrome loads the extension from this folder every
time it starts, so the folder has to stay where it is.

### Step 3: Open the extensions page

Type `chrome://extensions` into Chrome's address bar and press Enter.
(In Edge, use `edge://extensions`.)

### Step 4: Turn on Developer mode

Click the **Developer mode** switch in the top-right corner of the page.
(In Edge, it is in the left sidebar.) New buttons appear at the top.

### Step 5: Load the extension

1. Click **Load unpacked**.
2. Select the folder you unzipped in Step 2 and click **Select Folder**
   (Windows) or **Select** (macOS).

Pick the folder that has `manifest.json` directly inside it. Unzipping
sometimes creates a folder inside a folder; if the folder you picked only
contains another folder, pick the inner one.

The **X to Xitter Redirect** card now appears on the extensions page.

### Step 6: Try it

Open <https://x.com/jack/status/20>. The address bar should change to
`https://xitter.cf/jack/status/20`.

## Updating from an older version

If you installed the earlier version that redirected to nitter.cf:

1. Download and unzip the new version (Steps 1 and 2).
2. On `chrome://extensions`, click **Remove** on the old card.
3. Load the new folder (Step 5).

If you replaced the files in the same folder instead, just click the
reload arrow on the extension's card.

## Troubleshooting

- **"Manifest file is missing or unreadable":** you picked the wrong
  folder. Pick the one with `manifest.json` directly inside it.
- **Developer mode or Load unpacked is greyed out:** the computer is
  managed by a school or company that blocks unpacked extensions. Ask its
  administrator.
- **Links redirect but the page doesn't load:** xitter.cf itself is down.
  You can switch to another site (see below).

## How it works

The redirect is a single static
[`declarativeNetRequest`](https://developer.chrome.com/docs/extensions/reference/api/declarativeNetRequest)
rule in `rules.json`. Chrome applies it to top-level and frame navigations
before the request leaves the browser, so it covers clicked links, typed
URLs, bookmarks, and links opened from other apps. No content scripts run
and the extension cannot read your browsing data.

## Redirecting to a different site

Edit `regexSubstitution` in `rules.json`, replacing `https://xitter.cf` with
the site you want, then click the reload arrow on the extension's card in
`chrome://extensions`.
