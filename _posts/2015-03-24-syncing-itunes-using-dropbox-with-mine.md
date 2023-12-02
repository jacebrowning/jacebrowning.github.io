---
layout: post
title: Syncing iTunes using Dropbox with Mine
tags:
- mine
- dropbox
- itunes
- python
---

Many applications provide their own synchronization methods to enable usage on multiple computers, but what about those that don't? It turns out that lots of programs are perfectly happy to have their files stored inside Dropbox rather than their typical location.

## Storing iTunes in Dropbox

Many guides exist showing you how to do this with iTunes:

* [digiwonk.wonderhowto.com/how-to/sync-your-itunes-library-with-several-computers-using-dropbox](https://digiwonk.wonderhowto.com/how-to/sync-your-itunes-library-with-several-computers-using-dropbox-0155955)
* [macstories.net/tutorials/how-to-sync-your-entire-itunes-library-with-dropbox](https://www.macstories.net/tutorials/how-to-sync-your-entire-itunes-library-with-dropbox/)

Unfortunately, the shared caveat in all these guides is that only one instance of iTunes is to be running at any given time. That's where `mine` comes in.

## Installing and Configuring Mine

`mine` is a daemon and command-line [Python program]({{ site.author.github }}/mine) that starts and stops remote applications using a configuration file in Dropbox. After setting up iTunes and Dropbox using one of the above guides, install `mine`:

```
$ pip3 install --upgrade mine
```

If you don't have `pip3`, install `python3` with your system's package manager (on OSX with [Homebrew](https://brew.sh/): `$ brew install python3`).

Additional configuration instructions are found in the project's [README]({{ site.author.github }}/mine#setup).

## Using Mine to Manage Remote Applications

Once installed and configured, let it run in the background on each computer:

```
$ mine --daemon
```

Applications can be killed remotely and started on the current computer:

```
$ mine switch
```

To kill all local applications and start them on another computer:

```
$ mine switch <name>
```

where `<name>` is part of the name of another computer with `mine` running.

-----

See a typo? Help me [edit]({{ site.repo }}/edit/main/{{page.path}}) this post.

Find a problem with `mine`? Please submit an [issue]({{ site.author.github }}/mine/issues) or contribute!
