---
title: "Python 3.14 env update bug? Illegal instruction"
url: "https://forum.anaconda.com/t/python-3-14-env-update-bug-illegal-instruction/110178#post_1"
date: "2026-09-03"
author: "@Bob8 Bob"
feed_url: "https://forum.anaconda.com/posts.rss"
---
I have a “py314” environment on Linux Mint 22.3 and it works well for several months, it is created previously using command: conda create --name py314 python=3.14 Recently I updated this environment, it is success. conda activate py314 conda update --all -y But this environment is not working anymore, the python command reports error: Illegal instruction (core dumped) I tried to recreated this environment, same error. Then reinstall with latest Anaconda installer from scratch and recreate the environment, same error again.
