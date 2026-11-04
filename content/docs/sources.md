---
title: Sources
description: Sources of old EverQuest data
weight: 50
---

## eqarchives.org

[EQ Archives](https://search.eqarchives.org/) is a search engine of old EverQuest websites pulled from Internet Archive's
[Wayback Machine](http://web.archive.org/), also Usenet.  It was created by Dolalin of the Project 1999 community, who 
deserves a medal for making this.  It has quickly become the primary research source/tool for this kind of work.  Wayback 
Machine was not practically searchable before Dolalin's site.  When you encounter a Wayback link on eqresearch.info, it's 
highly probable it was found via EQ Archives.

"The Internet is forever" is not an axiom, it's a misnomer.  The vast majority of the old EQ websites are now offline.
EQ Archives ensures that we will never lose access to Wayback Machine's archives because we can now have a local copy of it.
Dolalin made his entire [collection](https://github.com/dbsanfte/eq-archives) open and downloadable on Github.  You can
download the entirety of EQ Archives and search them locally using a tool like [dnGrep](https://dngrep.github.io/) so you
don't even require eqarchives.org to be up to search it.

As awesome as Wayback Machine and Internet Archive are, they did not capture the majority of the old web pages that existed.
Most of the old forum threads were lost forever.

## Usenet

Usenet was the Internet's discussion forums before Web 2.0 forums replaced it.  It's a fantastic source of information regarding
the earliest years of the game, particularly 1999 and 2000.

[Google Groups](https://groups.google.com/g/alt.games.everquest/) has good search functionality and posts going back to before
the original launch.  Unfortunately it was taken down for several months in 2026 because of the AI hysteria.  Websites are going
dark because of automated scraping to train AIs.  It's back up but may not stay up.

[Usenet Archives](https://usenetarchives.com/) is another Usenet repository that has very old posts. (pre 2000)  Wayback has
downloadable Usenet archives as well but their EverQuest group posts start at December 2000.

## Client Decompiles

The clients themselves are the most authoritative source we have.  This is actual game logic written by Sony/Verant 
themselves.  Although it's not bulletproof as there is no guarantee that the logic in the client is the same logic
on the server, but it's extremely likely to be.  The more likely issue is simply misinterpreting the decompile.  If 
something is found in multiple clients and it all matches with in-game observations then it's almost as good as reading
source code.

[Ghidra](https://github.com/nationalsecurityagency/ghidra) and [IDA](https://hex-rays.com/) are used to decompile the 
clients.

### Client Binaries

The known available client executables up through Gates of Discord are the following:

- Beta Phase 4 - January 26 1999
- February 15 1999 - Original Launch CD
- March 15 2000 - Kunark CD
- March 21 2000
- March 30 2000
- April 11 2000
- April 12 2000
- April 17 2000
- April 28 2000
- May 16 2000
- May 19 2000
- May 25 2000
- July 19 2000
- August 1 2000
- August 9 2000
- August 30 2000
- September 19 2000
- November 15 2000
- November 16 2000
- November 21 2000
- November 29 2000
- December 5 2000
- December 7 2000
- December 8 2000
- January 9 2001
- March 6 2001
- April 4 2001
- Trilogy - August 22 2001
- Gold UK - January 11 2002
- Trilogy SE - June 12 2002
- Gold US - October 12 2002
- Al'Kabor - circa November 2002 with customizations
- Evolution - July 11 2003
- Platinum - June 16 2004

The reason why we have so many client binaries centered around Kunark era is because Dolalin 
[found](https://www.project1999.com/forums/archive/index.php/t-355620.html) an old 
[Taiwanese website](https://web.archive.org/web/20010210003746/http://www.everquest.com.tw/patch_file.html) on Wayback
which had these old patch files.

Internet Archive also has several old EverQuest CDs for download, Trilogy included.  There were two Trilogy clients:
the first one released about 2/3rds into Velious, and the second Trilogy "Special Edition" released halfway into Luclin.
Internet Archive has the Velious era one.

One of the clients is special however: eqmac.exe from the Macintosh version of the game.  This executable has
debugging symbols which means Sony's function names are in it.  This makes finding things in it much easier and allows
us to know what Sony called certain things.

For obvious reasons the client binaries will not be hosted here.

## Live Servers

What about Live servers? is an obvious question.  Darkpaw's servers is a source that becomes less relevant with each 
passing year.  Darkpaw keeps making changes to the game.  At this point it's become somewhat of a last resort for
mechanics research, but sometimes is still the place to look.  Live is obviously a large source for NPC content related 
research but that data must also be scrutinized for possible changes.

There are some core designs that haven't changed from the game's original launch.  The D20 melee system for example.
Often Sony liked to just layer new systems on top of old ones, which allows one to peel the new stuff off and examine
the older systems.  At this point almost everything there still relevant to us has already been
looked at.  What we really need is for Darkpaw to put Al'Kabor back online or to make a true classic server like WoW did
so we can figure out the remaining issues, such as what /target range used to be.

Darkpaw has in some cases been exposing more of the game data to users however and this has been beneficial to us.
Much of Live's faction data has been exposed as is found in the modern client's Resources folder.

## Al'Kabor Data

The Al'Kabor server was the Macintosh server and it was stuck in the Planes of Power era for a decade.  It's very 
fortunate that Sony decided to abandon it because it became one of the primary sources of old EQ data.  The player logs
we've been given from this period amount to over seven gigabytes which is rather enormous.  Being stuck in the era
also meant that the players themselves were a good source of testimony about the game, much of which can be found
on the [The Al'Kabor Project](https://www.takproject.net/) forums.

Robregen, developer at The Al'Kabor Project, took zone snapshots of all but a few keyed zones to 
fill out TAKP's database.  This included all of the data the client received from the server, including things
like NPC size and what they were wielding.  This is how TAKP has precise spawn locations for most of the static spawns
in the game.  Rob also went around considering NPCs as an agnostic of each race and used an item data capture tool to
get accurate item data from the server, as well as merchant inventories.  TAKP has precise early PoP item data for about 
7k items.

Torven spent the last month of EQMac's life collecting max hp, attack rate, and damage NPC statistics from Al'Kabor.

## Patch Notes

There are multiple patch note collections out there, including in EQ Archives, but Torven's patch notes collection
might be the most extensive for the eras this site is concerned with and can be found
[here](https://drive.google.com/file/d/0B9w2lZ-BZM3lUWJUZGVZVXFzT1E/view?usp=drive_link&resourcekey=0-49yhGoYJjSJeYBBYfm3CEA).

## Logs

As mentioned previously, we have a large collection of Al'Kabor logs, but we also have a much smaller collection of logs
from other servers and eras.  Torven has hundreds of megabytes of personal logs from 2003 and early 2004 and a tiny number
of earlier era logs.

Pre-2002 logs are very rare and we have few of these, but the best source of these is from a public Github repo which I 
can link here.  The [tipa16384](https://github.com/tipa16384/harcourt_applets/tree/main/DSR) logs are an extremely 
valuable source of Velious and early Luclin logs.

Logs are searched with a Grep tool and also custom scripts written by Torven.  More information on this can be found in
the Parsing section. _(when it's written)_

## Magelo

Magelo is an obvious source of NPC locations and is the primary source for NPC drop tables.  They have blocked Wayback
from scraping them but measures have been taken to ensure the data does not become unavailable if the site were to go
offline.

## Item Data

EQ Emu [item data](https://sourceforge.net/projects/eqemu/files/EQEmulator%20Item%20DB/Latest%28December%207th%29/)
from December 2003 is still online and available.

## Torven's Web Archive

Torven has a little 
[web archive](https://drive.google.com/drive/folders/0B9w2lZ-BZM3lUklnT3llZTA3OXc?resourcekey=0-hcyMyzhKMVQ2wQXU21qSOw&usp=drive_link)
of saved web pages and miscellaneous files.  These saved pages contain highly relevant information regarding how the game
functions and how content has changed.  A lot of developer quotes are in there.
