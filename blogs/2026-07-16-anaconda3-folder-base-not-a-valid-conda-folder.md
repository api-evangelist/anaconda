---
title: "Anaconda3 folder / base not a valid Conda folder"
url: "https://forum.anaconda.com/t/anaconda3-folder-base-not-a-valid-conda-folder/108913#post_2"
date: "2026-07-16"
author: "@mrsimon07"
feed_url: "https://forum.anaconda.com/posts.rss"
---
From what you’ve described, your Conda base environment may be corrupted or its metadata is missing, which is why both VSCode and Conda can’t recognize it. Before reinstalling, check whether C:\Users\user\AppData\Local\anaconda3\conda-meta still exists and whether your PATH variables point to the correct installation. If conda-meta is missing or damaged, a clean reinstall after manually removing the broken installation is usually the most reliable fix.
