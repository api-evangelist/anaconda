---
title: "Conda update fails due corrupt jupiterlab widgets archive"
url: "https://forum.anaconda.com/t/conda-update-fails-due-corrupt-jupiterlab-widgets-archive/108920#post_4"
date: "2026-08-12"
author: "@Robin3 Robin"
feed_url: "https://forum.anaconda.com/posts.rss"
---
It could be that some package is trying to update it to 3.0.16 which had issues due to long paths on Windows, see InvalidArchiveError with 3.0.16 · Issue #47 · conda-forge/jupyterlab_widgets-feedstock · GitHub .
