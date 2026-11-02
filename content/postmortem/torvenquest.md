---
title: TorvenQuest
type: "docs"
weight: 50
menu:
  sidebar:
    weight: 50
---

I am sometimes asked how I might make my own server, and making a custom content server is something I had wanted to, so 
I thought I would write a section on the subject.

I decided not to create a custom content emulated server for several reasons.  One is that cheats and hacks are so available now
and these ruin the game for me.  I don't want to spend potentially thousands of hours on making a server just to watch
people cheat on it with ShowEQ and client hacks.  Secondly I cannot monetize it, so instead making a game from scratch becomes
more appealing for that reason.  Thirdly I could not find people to help and the amount of labor involved is too massive
to do it alone.  Fourthly Darkpaw has become hostile to custom servers as of late.  Fifthly I lack the technical competence
to do client modifications.

Really what I would have liked to do is make two servers: an extremely accurate recreation server a la Project 1999 but 
with more accuracy and older clients, and a custom content server which would be classic EQ+ or EQ hard mode.  Were I to 
design a MMORPG from scratch the goals and mechanics would be different still.

## Accurate EQ

This may not surprise you, but my standards for what qualifies as "accurate" for an emulated server are very high.  
Frankly they are not being met to my full satisfaction, although that is not to say I don't think the emulated servers
aren't great places to play on and better than Darkpaw's servers, which they are.

Here's the deal about emulated servers: the older they get, the more they become their own 
thing and become resistant to change.  I know this from personal experience.  When I worked on TAKP, the older the server
got the more the community balked at changes I made to improve the accuracy if the changes made the game harder or more
annoying.  Eventually even my fellow developers started vetoing some of the 'akurate' changes I was making. (because they 
were players)  Some things just need to go in at server launch.  Project 1999 as a server is much older today than 
EverQuest _as a game_ was when Project 1999 launched.  Even TAKP is now older than EQMac was.

I can't blame emulated servers too much for refusing to add extremely unpopular changes that would cost them half their 
userbase.  Part of EQ is having a populated server and if nobody is on it then it's not EQ either.  But I wish they would
be more honest about it.  This entire website exists in large part because servers refuse to adopt my research.  I don't
mean to be disrespectful to P99 or TAKP-- I just want people to be aware of the inaccuracies of these servers.  Darkpaw's
TLPs are so much worse that I consider them to be unplayable by my standards and it never occurred to me to play on one,
but I'm very glad they're still in business.

Another problem with accurate recreations is that what is considered genuinely classic isn't always obvious.  There is
disagreement on this.  Theoretically if somebody discovered some exploit in an old client that allowed players to death
touch mobs that existed at the time but nobody discovered, would it be classic to include this?  My take on this is that
no, it's not accurate to include this.  That is of course an extreme hypothetical but it illustrates my point.  **If some 
exploit or cheese existed at the time which was not widely known or abused but would significantly change the experience of the game 
today then it should not be included.**  I get a lot of disagreement on this and TAKP devs and I have argued about this 
many times, but to their credit they let me have my way most of the time.

I also feel rather strongly that EQ should be played in first person view up through Kunark.  A client should be made
to revert the camera to first person view if the player moves, and mousewheel camera should not exist until PoP.  Third
person cameras change the feel of the game dramatically-- first person view is much more immersive.  Gamers at the time
were not familiar with third person cameras so they were all playing in first person view.  To replicate the feel of the
game,  first person view should be forced on the player.  One might even force the stone UI view on players for some
amount of time, although not nearly as long.

For this server, I would not be terribly concerned about online player counts and it would be a museum server.  Project 
1999 players _think_ they want classic, but they really don't.  They don't know what classic is.  If they were dropped
into it and you didn't tell them, they would scream bloody murder.  Everybody is so used to the Luclin and later changes
that they would balk at real classic.  I just want a museum server that is _truly_ the real thing that people who are
curious of what EQ was really like in 1999 could log in and see.  It's the server I would personally want to play on but
I realize that I'm in a small minority.

## EQ Hard Mode

There are many EQ servers which make the game easier than it was in 1999.  As far as I'm aware, all of them are.  There
is no place to play where somebody who wants a similar or greater challenge can find one.  I think this is sad.

The custom content server I had wanted to build was one with the same lore and similar mechanics of the original
game, but made more difficult by tougher NPCs, smarter AI, exploits/cheese fixed, and unspoiled content.  NPC placement
and itemization would be all-custom in dungeons and raids so nobody could look up what items were in the game and where
to get them.  Customizing the quests would have required a larger team so would have been unlikely, however that would
have been something I would want to do.  Certainly at least some quests would be added and rewards modified.

I really like the idea of players needing to unlock features of the game, and so things like boats and teleports would
not function at server launch.  Players would need to complete one-time mini-raids or events to permanently unlock these 
features.  A raging storm might prevent boat travel to Qeynos for example, and players on both sides might need to 
accomplish tasks (offerings to Karana or whatever) to quell the storm and allow the boat to function.  This would strand 
Erudites on Odus for some time, perhaps a few days or a week.  Odus however would get a makeover so players wouldn't be 
stuck in a content wasteland.

One idea I had that I really liked was to allow Iksars playable at launch, but with no travel to and from Kunark.  So
Iksars would be stuck over there with a level 50 cap and no clerics.  A GM event would pluck somebody on Antonica and 
put them over there a couple months before Kunark opened.  The outposts in FV and Overthere wouldn't exist yet.
(we'll just have to pretend FV's elf zone geometry doesn't exist)  I had wanted this kind of thing to be a surprise
but the server isn't going to get made.

At the high-end, some raids would be rare and require multiple guilds to complete.  Some raid bosses might spawn once
every month or two instead of once a week, and require a raid force of multiple guilds.  Some scripted events might
require guilds in different zones to coordinate.  Nobody will have anywhere near full BIS gear on this server, at least
not for a long time in the final expac.

Ideally I'd like to make player stats work a lot better, then change the itemization so prevent the items from being
too powerful.  Imagine if high agility actually made you avoid attacks by a meaningful amount, dexterity made you
channel spells better, intelligence increased spell damage, and wisdom increased mana pool for all classes instead of 
int.  I think no stat should be useless for any class and players should have to make hard choices in which stats to
stack.  This would be a significant deviation but I would like to experiment with it at least.

Deep dungeon delving would be the best exp on my server.  Period.  Risk vs. reward will be obeyed.  Killing mobs near
the zone line will not award as much as deeper in.

More higher level spells would require researching or from drops (including priest classes) instead of being found on 
vendors.  Getting higher end weight reduction bags would be more difficult, all would be lore and not localized to the 
earlier eras. (no more tink bags)

Factions would matter more.  Velious' faction system was fantastic and this should be expanded upon.  I think the
faction system should be modified such that avoiding hits becomes impossible if you participate in kills and perhaps
some faction choices should be permanent, requiring alts to participate in all content.

Some of the ideas I've outlined in earlier sections would be incorporated such as staggered level caps which are 
unlocked by server events.  The concept of the server having different states which can be switched by player activity 
is something I would really want to put in.  I.e. players picking a side in a NPC war to change the spawns in a zone 
for an extended period of time. (weeks)

The original planes of Fear and Hate were also fantastic, and I think they should serve as a model for more raid
zones.  Hostile zone entries would be much more commonplace on my server, and risk of permanent corpse loss in the 
most rewarding zones would be a possibility, although within reason.  Corpse expiry timers would be extended
for corpses with significant raid gear on them. (i.e. much longer than a week)

I think raid design (and AI in general, really) needs to be much less predictable.  You should never be able to 
predict with certainty that a raid boss will cast whatever spell after X amount of seconds or when the boss reaches Y%
hitpoints or the boss won't just get fed up hitting the same tank for five minutes and decide to attack somebody else.
Players should be forced to adept to circumstances they didn't entirely anticipate to some degree.  This
kind of design philosophy actually allows you to make a boss hit for far less damage and still be challenging.  Your raids 
stop being this fragile commonly employed strategy that falls apart quickly on mistakes because bosses hit so damned hard.

Modern games don't do that because the fights have to be entirely non-random for "fairness" or whatever word you like, but 
EverQuest in the old times didn't give a damn about "fairness".  In EQ you could zerg the crap out of a boss if you so chose.
Modern games on the other hand are tuned for exactly X number of participants, and he challenge level of every attempt must 
be exactly the same.  I reject this and would design encounters that might end up being too easy or hard one night due to RNG.

For PoP I had some wild ideas such as not including the original three planes in the 1-50 game and instead saving them
for PoP, then allowing players to switch deities through some server event every few months, and their deities determined
which planes were friendly and which were hostile.  Players would be agents of war for the deities to attack rival gods.
All planes would be level 65 raid zones and the flagging system wouldn't exist or be needed.  Friendly zones would grant 
quests similar to Plane of Growth (that zone would also be saved for later) and to get full BIS gear would require 
rotating deities many times, taking potentially multiple years.  Since this would be the final 'expansion', it would be 
large.  This would allow guilds to share content in a manner similar to Velious as guilds would coordinate to 
have different deities.  Most or all planes would have hostile entries.  Hole, Jaggedpine and Stonebrunt (which would be 
turned into level 50 zones, at least partially) would need to pick up the slack for missing content in earlier eras and 
outdoor raid bosses would need to be added. (I did say it was a wild idea)

## Not An Emu

Some of the things I criticize EverQuest for are not things I would nerf or remove on a custom content emulated server.
I would not nerf kiting or quadding on an emu for example. (at least not fully)  Changing the mechanics too much would 
turn off EQ veterans and those people are almost the entire audience, and frankly I'm one of them anyway.  I 
probably wouldn't be able to add in a bunch of new spells regardless.

Were I to design a MMORPG from scratch I would do things differently.  Kiting as it is on EQ wouldn't exist.  I would 
also omit long distance teleports entirely.  The world would be large and traveling across it would be 
dangerous even for mid-level players.

Anyway I haven't thought about a server from scratch that much and only bring it up to explain that there would be large
differences between my custom emu and a new game.
