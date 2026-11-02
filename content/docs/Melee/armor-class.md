---
title: Armor Class
description: How the Armor Class stat works in EverQuest
categories: [Melee]
tags: [melee, armor]
weight: 1
---

Armor Class in EverQuest is really two stats in one: an avoidance stat and a mitigation stat.  These are added together 
and represented to the player in a single value.  EverQuest was based on old DIKU MUDs and in those MUDs AC is also both
an avoidance and mitigation stat rolled into one, however EQ does not have a baseline THAC0 number and uses two distinct
mitigation and avoidance stats.  Sony/Verant may have combined these because gamers at the same were used to AC being a
single stat but that is speculation.

On January 18, 2017, Darkpaw [updated](https://bastiongame.com/library/patches/2017-01-18-1) the Live client to break 
apart the two AC stats in the UI.

On April 16, 2014, a then Sony developer by the name of Dzarn 
[outlined](https://forums.daybreakgames.com/eq/index.php?threads/ac-vs-acv2.210028/) how AC works in the game.
This post was key to understanding how melee combat worked in EverQuest and is the basis for this research.

Interestingly an 
[April 2002 thread](https://web.archive.org/web/20020625231456/http://pub14.ezboard.com/fthesteelwarriorthearena.showMessage?topicID=1462.topic) 
had the bulk of the AC logic in it.  It appears Magelo may have found some of the formulas in the binaries.

In the older UIs, the mitigation and avoidance stats are added together like so:

> SheetAC = INT(1000 * (MitigationAC + AvoidanceAC) / 847)

That essentially multiplies the result by about 1.18.  That is the final step before the value is displayed to the 
player.  _The server logic does not do this_ and the entire reason for this is seemingly to obfuscate how AC works.
That's EQ for you.  This weird multiplier is no longer done on Live's clients.  Server combat calculations use the
component mitigation and avoidance values separately.

For the rest of this document, assume all math is integer math, meaning remainders are deleted, unless an explicit
mention is made that a particular portion is done in floats.

## Mitigation AC

Mitigation AC increases the chance that the attacker will roll lower when a blow lands.  Mitigation AC is compared
against the attacker's Offense ATK.  Dzarn's post calls this "AC Sum" and the EQMac.exe binary calls it just "ac".
If you mouseover the stat in Live's new UI the tooltip calls it "Mitigation".  On this website it will be referred
to as Mitigation AC.  Even the word "mitigation" is somewhat misleading as mitigation AC does not actually reduce
the maximum possible damage hit but rather makes it less likely to occur; although at extreme Mitigation AC vs 
Offense ATK disparities the max possible hit becomes so rare as to be near impossible.

Mitigation can be broken down into several components: **worn AC, race+class bonuses, Defense skill, Agility, buffs**.

### Worn AC

Worn AC is the aggregate of the following: **armor AC (not ammo slot), shield AC, food/drink AC, tribute AC (in GoD)**.

Modern EQ has a few more things to add up.  See Dzarn's post if you are concerned about modern EQ.

Worn AC is then multiplied by 4 and divided by 3, which is an integer math way of multiplying it by 1.33333, but only
for non-magi classes. (i.e. classes that aren't the four pure Int casters)  Sony did this *4/3 thing in several places.
Why this is done is not known.  The pre-release February 1999 client has this in it so this is
valid for all eras of EQ.

EverQuest has anti-twink caps in various places to prevent twinks (low level characters with high level equipment) 
from being overly strong.  Worn AC is one of those places.  The anti-twink worn AC cap is **25 + (6 * player_level)** 
and is applied after the above multiplier for players under level 50.  This _doest not_ happen in the client AC 
calculations, so is invisible to the player.  This cap is found in the client decompiles however.  Sony's mitigation
AC function has a parameter to skip both AC caps in the result, so Sony intentionally hid this cap from players.  This
anti-twink cap is found in the February 1999 client, so it was in the game very early.

### Race and Class Bonuses and Monk Weight Penalty

This step is relevant if you are one or more of the following: a monk, a beastlord, a rogue, an Iksar.

#### Monks

Monks have a bonus or penalty applied depending on how much weight they are carrying.  It works by having a softcap
and a hardcap.  If the monk's weight is above the hardcap, the monk loses AC.  If the monk is carrying weight under or 
equal to the softcap, then the monk gets the entire AC bonus.  If the monk's weight is between both caps, then the AC bonus is scaled
to how much weight the monk is carrying.

In the October 2002 client and later, the penalty is applied to the worn AC and Iksar AC portions only, so if worn AC is zero
(the monk is naked) then the penalty is not applied.  In earlier clients this is allowed to go negative so seemingly
it would apply to other forms of AC.

These are the caps starting from April 17 2001: (the 62-65 ones were added with PoP)

| Level Range | Softcap | Hardcap |
| ----------- | ------- | ------- |
| 1-14        | 14      | 30      |
| 15-29       | 15      | 32      |
| 30-44       | 16      | 34      |
| 45-50       | 17      | 36      |
| 51-54       | 18      | 38      |
| 55-59       | 20      | 40      |
| 60-61       | 24      | 45      |
| 62-63       | 24      | 47      |
| 64          | 24      | 50      |
| 65          | 24      | 53      |

Sony changed the monk weight AC caps twice in the eras we are concerned with.
Prior to September 19 2000, the caps were 14 and 30 for all levels.  After that patch, levels 55 and 60
had cap raises to 18-38, and 22-45 respectively.

If the player's weight is < (hardcap - 1) and > softcap then a partial bonus is calculated like this:

```c
base_bonus = level + 5

reduction = (weight - softcap) * 6.66667
if (reduction <= 100.0) {
	reduction = 100.0 - reduction
}
else {
	reduction = 0.0
}
bonus = 0.0
reduction = (reduction / 100.0) * base_bonus
if (reduction >= 0.0) {
	bonus = reduction * 4.0
}
bonus = bonus / 3
```

If the player's weight is > (hardcap + 1) then the AC penalty is calculated like this:

```c
base_penalty = level + 5

mult = (weight - (hardcap - 10.0)) / 100.0;
if (mult > 1.0) {
	mult = 1.0;
}
penalty = 0 - (mult * ((base_penalty * 4.0) / 3.0));
```

If the player's weight is <= softcap, then the monk AC bonus is: **(level + 5) * 4 / 3**.

If the player's weight is equal to the hardcap or is +/-1 of it, then there is no AC modifier applied.

Older clients compute these the same way except for one difference: the penalty in older clients does a 
hardcap - 20.0 instead of a hardcap - 10.0.  When this change was made hasn't been narrowed down. (I had 
trouble getting the decompiler to work on it)

Note that Monk AC is one of the few places where floating point math is used.

#### Rogues

The rogue AC bonus was the same at launch in 1999 as it is mentioned in Dzarn's 2014 post.  I'll quote him:

```
LevelScaler = PlayerLevel - 26
If Agility < 80: ACBonus = (LevelScaler * 1) / 4
If Agility < 85: ACBonus = (LevelScaler * 2) / 4
If Agility < 90: ACBonus = (LevelScaler * 3) / 4
If Agility < 100: ACBonus = (LevelScaler * 4) / 4
If Agility >= 100: ACBonus = (LevelScaler * 5) / 4
If ACBonus > 12: = 12
```

#### Beastlords

The beastlord AC bonus explained by Dzarn is also the same as found in the 2001 Trilogy client and 
applies to beastlords above level 10:

```
LevelScaler = PlayerLevel - 6
If Agility < 80: ACBonus = (LevelScaler * 1) / 5
If Agility < 85: ACBonus = (LevelScaler * 2) / 5
If Agility < 90: ACBonus = (LevelScaler * 3) / 5
If Agility < 100: ACBonus = (LevelScaler * 4) / 5
If Agility >= 100: ACBonus = (LevelScaler * 5) / 5
If ACBonus > 16: = 16
```

#### Iksar Racial AC

The Iksar racial bonus is very simple:

If the player is above level 35, the bonus is 35  
if the player is under level 10, the bonus is 10  
if the player is level 10-34, the bonus is equal to the player's level  

### Defense Skill and Buff AC

Magi classes (the four Intelligence caster classes) actually gain more AC from buffs _and_ defense skill:

**MitigationAC = DefenseSkill / 2**  
**MitigationAC = BuffAC / 3**

For all other classes:

**MitigationAC = DefenseSkill / 3**  
**MitigationAC = BuffAC / 4**

BuffAC here is the sum of all the AC buffs on the character.

It's important to note that the AC numbers you see on some websites are incorrect.  If you visit
lucy.alkabor.com and look at the [Holy Armor](https://lucy.alkabor.com/spell_11.html) buff there, it shows
the buff's AC is 6.  This is wrong.  The real value for that spell is 15 to 20. (it scales some by level)
The reason why is some websites do a division on the actual values to try and mimic what Sony does so
when a player visits a website they get a better idea (but inaccurate) of how much AC it will add to 
their sheet AC number. [TAKP's Allaclone](https://www.takproject.net/allaclone/) will give you the real numbers.

### Mitigation Bonus from Agility

The bonus from agility is very simple and has never changed from launch until Dzarn's 2014 post:

If Agility > 70, MitigationAC = Agility / 20

### The Mitigation AC Cap

The final step for mitigation AC is the cap.  There is also an anti-twink cap which I explained above, but this section
will go over the more significant cap which applies to all players.  This cap is what min/maxing players will care about
most when it comes to AC and gives players a reason to calculate their mitigation AC so they know when to stop going
after AC in favor of hitpoints.  AC is EverQuest is capped fairly low so most players will hit it at some point.  Like
the anti-twink cap, this cap was deliberately hidden from players in the client.

The AC cap is a hardcap in the earliest eras but turned into a softcap in Luclin for melee classes.  The overcap returns 
were low in Luclin but became much more generous in PoP for certain classes.

**Players level 50 and under are always hardcapped at 350 for all classes** in _all the eras_ this website is concerned with.
This cap is found in the February 1999 client, so it's always existed.  In modern EQ this has changed.  In the Live client 
there is a file called ACMitigation.txt in the Resources folder which has all the modern caps in it which are more generous
than old EQ.

In Kunark the cap was still 350 for all classes even up to level 60, _except_ for warriors above level 50 which had a cap
of **405**.  This was found in the March 1999 client so was in at day 1 of Kunark.

The earliest client executable we have that shows a change to the Kunark caps is the **March 6 2001** client.  This patch was
three months post Velious launch.  This client showed significant cap changes:

For warriors above level 50, the hardcap is **430**  
For paladins, shadowknights, and bards, the hardcap is **403**  
For rangers, rogues, monks, the hardcap is **375**  
For everybody else, the cap is still 350

This change occurred after January 9 2001 and no later than March 6 2001.  We do not have clients between those dates, so
it could have been implemented prior to March 6.  No patch note hints at it.

The 2001 Trilogy client (August 22 2001) has beastlords added to the 375 classes.

The next client we have after 2001 Trilogy is the Gold UK client with a date of January 11 2002.  This is about five weeks
post Luclin launch.  As you would expect, it has the AAs in it.  The previously mentioned hardcaps were turned into softcaps
for the melee classes (i.e. not priests or magi/int casters) but were otherwise not changed.

Combat Stability AA adds 2%, 5%, or 10% more to the softcap for the appropriate ranks.  Physical Enhancement then does a 2%
multiplier on top of that.

The overcap returns in Luclin were **1/12th** for all melee classes.

The Gold US client is dated October 12 2002 and it does not show any changes.  Four days later however there was a patch with
two relative items in the notes:

>- Decreased Monks’ ability to mitigate damage
>- Improved the ability of Paladins, Shadowknights, Warriors and Bards to mitigate damage in some situations

The monk nerf is well-known.  Their AC cap was reduced to **315** which is a large decrease.  That second annotation might
indicate that the PoP era overcap returns were put in on that date.  We cannot be sure but it seems likely.  This October 16
patch was five days before PoP's launch.

The next client we have is the Al'Kabor client.  This client however could be described as being custom and a mix of future
client features because Hobart (EQMac's developer) was adding later PoP era features to it such as adding beastlords to the
Mass Group Buff AA.  It does however have the reduced monk cap in it which dates the mitigation routine to earlier than
April 8 2003.

The Al'Kabor client caps are the following:

Warrior: 430  
Paladin, SK, Cleric, Bard: 403  
Ranger, Shaman: 375  
Rogue, Druid, Beastlord, Necro, Magician, Wizard, Enchanter: 350  
Monk: 315

Monks were not the only class nerfed.  Sony nerfed beastlords and rogues as well, although to a smaller degree.  Clerics
on the other hand got a large buff by being moved to the 403 tier with knights.  They were previously down at 350.

In PoP the overcap returns completely changed.  Here are the overcap divisors in the Al'Kabor client: (plus berserkers for table completeness)

| Level | War | Clr | Pal | Rng | SK  | Dru | Mnk | Brd | Rog | Shm | Nec | Wiz | Mag | Enc | Bst | Ber |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 51-61 | 5   | 20  | 6   | 10  | 6   | 20  | 20  | 8   | 20  | 20  | 20  | 20  | 20  | 20  | 10  | 20  |
| 62    | 4   | 20  | 5   | 9   | 5   | 20  | 18  | 7   | 18  | 20  | 20  | 20  | 20  | 20  | 9   | 18  |
| 63    | 4   | 20  | 5   | 8   | 5   | 20  | 16  | 7   | 16  | 20  | 20  | 20  | 20  | 20  | 8   | 16  |
| 64    | 3   | 20  | 4   | 7   | 4   | 20  | 14  | 6   | 14  | 20  | 20  | 20  | 20  | 20  | 7   | 14  |
| 65    | 3   | 20  | 4   | 7   | 4   | 20  | 12  | 6   | 12  | 20  | 20  | 20  | 20  | 20  | 7   | 12  |

The mitigation AAs increased the softcap by the following amounts:

Combat Stability rank 1 = 2%  
Combat Stability rank 2 = 5%  
Combat Stability rank 3 = 10%  
Physical Enhancement = 2%  
Innate Defense = +3% for each rank (5 ranks total)

If you had them all, your softcap would be +27%.  A tiny change here from Luclin is that Physical Enhancement is no longer 
multiplicative.

A level 65 warrior with 1000 mitigation AC and all AAs would have a softcap of 546, overcap returns of 151, and a resulting
mitigation AC value of 697.

The April 8 2003 patch note says this:

> We have evaluated the mitigation abilities of cloth and leather
> classes, and have made changes as appropriate. For the most part, this
> change is a reasonable improvement to the ability of monks to absorb
> damage. At some point in the future we may re-examine the mitigation
> abilities of chain and plate classes. At this time, and with this final
> round of changes to cloth and leather classes, we believe that
> something very close to the appropriate balance is in place.

However the only change in the Evolution client (July 2003) regarding mitigation AC caps is the monk cap changing to 350.
None of the other softcaps changed, nor did any of the overcap divisors.  This is also the case in the Platinum client
(June 2004) which only added berserkers with a 375 softcap with rogue/monk overcap divisors.

## Avoidance AC

Avoidance AC increases the chance that the attacker will miss.  Avoidance AC is compared against the attacker's To-Hit.
Like mitigation AC, Sony's terminology for this is confusing.  Dzarn calls this "Computed Defense" and the EQMac.exe
binary refers to it as "defense".  Live's new UI calls it "Evasion".

Avoidance AC is much simpler than mitigation AC has only a few sources: Defense skill, Agility, Avoidance mod2, and 
drunkenness reduction.  Avoidance comes almost entirely from Defense skill.

### Defense Skill Avoidance

This is super simple:

**AvoidanceAC = DefenseSkill * 400 / 225**  

### Avoidance from Agility

This is the Agility bonus for the eras we are concerned with:

If the character has 1-39 Agility, the bonus is: **(Agility - 40) * 25 / 40**  
_(this is -25 to 0)_

If the character has 40-60 Agility, the bonus is **0**

If the character has 61-74 Agility, the bonus is: **(28 - (200 - Agility) / 5) * 2 / 3**  
_(this results in either 0 or 1, oddly.  seems unintentional)_

If the above doesn't apply, then variable x is assigned a value:

x = 35 if level 1-6  
x = 55 if level 7-19  
x = 70 if level 20-39  
x = 80 if level 40+  

If the character has 75-199 Agility, the bonus is: **(2 * (x - ((200 - Agility) / 5))) / 3**

If the character has 200+ Agility, the bonus is: **2 * x / 3**

For level 40+ players, the maximum bonus is 53.

The 75 Agility bonus is 6, 20, 30, or 36 depending on level.  That is a large step up from 1 bonus for all levels 
at 74 Agility.

Modern EQ changed this at some point after the Platinum client and it is different in Dzarn's post.

### Avoidance Mod2

Decompiles seem to show that +Avoidance on the old Mod2 items was just added to the sum without modifications in the same
line that calculated Avoidance AC from Defense skill (it is added after the *400/225 is done) but I have not verified this 
in a running client to be certain.

### Drunkenness

Drunk players have a drunkenness score which ranges from 0 to 200.  Sony uses this score to calculate a floating point 
multiplier which ranges from 0.1 to 0.9 then multiplies the Avoidance AC by this multiplier.

The formula is this: **ReductionMult = (110.0 - (DrunkennessScore / 2)) / 100.0**

This is not applied unless the player's drunkenness score is 40 or higher.

