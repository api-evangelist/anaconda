---
title: "[Help] Extremely Slow First-Time Import in New Conda Environments (torch / torchvision / cupy / PyMuPDF, etc.) with Almost Zero CPU/Disk Usage"
url: "https://forum.anaconda.com/t/help-extremely-slow-first-time-import-in-new-conda-environments-torch-torchvision-cupy-pymupdf-etc-with-almost-zero-cpu-disk-usage/107955#post_3"
date: "2026-07-06"
author: "@mrsimon07"
feed_url: "https://forum.anaconda.com/posts.rss"
---
Likely culprit: Windows Defender/SmartScreen doing on-access signature checks (cloud lookup) on each new DLL/PYD the first time it’s touched — that matches near-zero CPU/disk, multi-minute stalls, fast on immediate re-import (cached verdict), slow again after time (cache expires), and works fine on the other machine (different AV state/policy or already-trusted files). Quick things to check/try: Confirm it’s Defender , not just “disabled real-time protection” (that toggle doesn’t disable cloud/MAPS lookups or Smart App Control): Check if Smart App Control is ON (Settings → Privacy & Security) 
