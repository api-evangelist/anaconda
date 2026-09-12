---
title: "Unexpected reload of Chrome extension written with PyScript"
url: "https://forum.anaconda.com/t/unexpected-reload-of-chrome-extension-written-with-pyscript/46336#post_4"
date: "2026-08-12"
author: "@viktoriya viktoriya"
feed_url: "https://forum.anaconda.com/posts.rss"
---
viktoriya: The issue is your button is still type=“submit” inside a form, so it triggers form submission before the onsubmit=“return false” reliably kicks in within the extension context. Try changing the button website to type=“button”, that removes the default submit behavior entirely. PyScript doesn’t have a direct preventDefault, so avoiding the submit trigger altogether is the cleaner fix here.
