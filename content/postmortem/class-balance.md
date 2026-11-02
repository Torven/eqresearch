---
title: Class Balance
type: "docs"
weight: 40
menu:
  sidebar:
    weight: 40
---

This section will deal with class balance as it was from launch until Planes of Power, but also some specific abilities 
or spells that apply to multiple classes.

## Slows

Attack delay increasing spells (i.e. slows) were poorly designed, or at least the magnitude of the higher end spells
were too great.  EverQuest is a game where the player gets a more powerful version of their spells as they advance in
level, but this is very problematic for percent based (multiplicative) spells because unlike hitpoints which increase 
forever as a character raises in level, modifying a value with a multiplier essentially auto-scales the ability.  If 
you made a spell that healed a character for 50% (or 100%, i.e. Complete Heal) of their max hitpoints then the spell 
would also never need to be upgraded to maintain effectiveness. In fact these spells get _better_ over time simply 
because the mana cost becomes less taxing as the player increases their mana pool and regeneration.

But it gets worse for slows.  The difference between a 90% heal and a 100% heal is not that much.  But the difference 
between a 90% slow and a 100% slow is infinity.

The math for slows is this: new_attack_delay = 100 / (100 - slow_amount) \* old_attack_delay

Assuming the target's unslowed attack delay is one second between melee rounds:

| Slow % | Atk Dly  |      | Slow % | Atk Dly  |
| ------ | -------- | ---- | ------ | -------- |
| 10     | 1.11     |      | 60     | 2.50     |
| 15     | 1.18     |      | 65     | 2.86     |
| 20     | 1.25     |      | 70     | 3.33     |
| 25     | 1.33     |      | 75     | 4.00     |
| 30     | 1.43     |      | 80     | 5.00     |
| 35     | 1.54     |      | 85     | 6.67     |
| 40     | 1.67     |      | 90     | 10       |
| 45     | 1.82     |      | 95     | 20       |
| 50     | 2.00     |      | 100    | infinity |
| 55     | 2.22     |

The best slow is Turgur's Insects which is 75%.  A Turgur'ed mob outputs one quarter the amount of melee damage as it
would unslowed.  This is obviously a massive reduction and it caused a problem: anything that was slowable ended up
being trivialized by shamans casting a single debuff unless the mob had some sort of spell innate (i.e. an AoE) and the
majority of its damage was from that spell innate.  In Luclin Sony gave the slowable raid bosses a very low attack
delay because of this.  Aten has a 0.6 second attack delay which is the fastest I've seen.  In classic and Kunark
Sony simply made raid bosses magic immune.  In Velious they made a slow immunity flag so that bosses could be slow 
immune without being MR immune.  They also made some raid bosses slowable but set their MR at a level
which made them hard to land the spell.  Dagarn the Destroyer for example was given an MR just low enough that slow
will have a 7% chance to land after full debuffs are on it.  Vulak was left easy to slow and they intended him to have
a lower melee DPS output, however since AoEs were easily ducked he ended up being trivialized.

For Planes of Power Sony put in a slow mitigation mechanic, which was badly needed.  Setting MR at levels which made
slow hard to land is a poor solution because any new debuff added to the game suddenly makes them trivial to slow
overnight; also this makes fights more of a crap shoot instead of a skill check.

A consequence of Slow's design is that lower level slows don't do very much.  It was often not even worth the trouble to
use them.

Spells like lull and charm would have a similar problem if they weren't restricted by the target's level.  The level
limit on these spells provides a reason to upgrade them.  The same thing could have been done to slows so lower level
slows aren't so underpowered, and that would be one possible solution.  Also the highest level slow that was intended
for raid bosses might be weaker than the next highest ranked slow which would be intended for leveling or trash.

My idea to fix slows would be to simply raise the lower level slows and decrease the higher level slows.  I.e. make 
drowsy like 35% and Turgur's 50% with the rest in the middle.  Then in order to slow raid bosses, multiple slows
from several casters would need to be stacked to fully slow the mob.  Let's say the mob needs three slows to fully
slow it.  A single Turgur's would be a 16% slow; two landing from two casters would be 33%, and three would be 50%.
Four or more would refresh previous casts.  This provides a reason to have more than one slower on a raid.  The mana 
cost of the spell should also scale with the target's level.

Slows also entirely nullified any haste on a target, which in a design sense is debatable.  Although this does make
lower level slows worth using.

## Snares

I went over how poorly tuned snare was in the kiting section.  Snare -- Ensnare in particular -- is simply way too 
powerful.  In other games if you movement speed reduce something it'll last like 30 seconds.  In EQ it lasts 14
minutes, which is rather insane.  And it only costs 35 mana.  Snare is 15 mana for 4 minutes.

While Tugur's reduces an NPC's damage to one quarter, Ensnare will reduce it to zero if you have room to run around.
This is why druids were so good at soloing.  Snare is a large part of the reason why EverQuest has NPC summoning while
other games don't.

Necros and SKs had fear spells (druids could fear animals)
and the combination of snare + fear was extremely potent and resulted in a technique called 'reverse kiting'
because the NPC fled from you at slow speed while you chased it.  Necros were the most powerful class in classic 
era in part because they could do this.  Fear was so strong that Sony put a level cap of 52 on it very early on.
(before Kunark)

PvP in EQ was kind of a joke in large part because snare was ridiculous.  In most other games PvP works more naturally
because players don't have abilities that just completely shut down a person.  EQ's solution to this was to allow
players to become near immune to non-damage spells at a mere 100 MR but with a 1-2% chance to land, which is a poor
solution.  A better solution would be to reduce the potency of spells in PvP, by duration and/or effect.

## Pets

Pets in classic era were insane.  They would output more DPS than a melee class player.  I don't know what Sony was 
thinking but I surmise one reason is that they didn't consider the DPS increase from dual wielding.  Magician pets 
couldn't dual wield at all until late in classic.  Also prior to Luclin summoned pets had a 5 level random variance 
to them, so in order to get the best pet you had to put in effort.  This made pet zerging less effective.

Sony's solution to pets being OP was to simply not upgrade them very much in Kunark.  By the time of Luclin they
had to start buffing them again.

At some uncertain point in time, mid-Velious at the latest, Sony changed pet AI to refuse to engage a mob if four 
pets were already on it and a pet was tanking. (and maybe even if a player were tanking)  This was put in to stop
pet zergs, and was removed in late Luclin.

## Wizards

As for individual classes I'll start with wizards since this is the class I played.

Wizards had one big problem: they were an entirely burst damage class and had no manaless sustained DPS.  This 
resulted in an interesting outcome that would plague the class, which is that the class got worse the better your 
group played.  Why is this?  Because wizards needed downtime to recharge, and the better the group the less downtime
you had.  A wizard's damage contribution declines as uptime increases.  I used to argue all the time on the wizard
board about this, as some wizards thought they were great because they had bad groups who didn't pull enough.  Even
as late as PoP era, _warriors_ would outdamage wizards in competent exp groups.

The burst damage capacity of wizards was insufficient to compensate for the loss of not having a pet.  The value
of burst DPS is being able to quickly delete a NPC in a multi-pull, or to kill a caster NPC quickly.  The problems
were that a wizard's burst DPS just isn't that much higher than that of a magician + pet; swapping the wizard out for a
CC or slower class would work _much_ better; most pulls are just one or two mobs anyway; a wizard is not going to be 
able to do this without aggroing off a warrior tank; caster NPCs are easily neutralized with stuns.

Okay, so fix the problem by jacking up wizard spell damage and/or efficiency you say?  Well then you create the problems
of wizards being OP soloers, raid boss killers and PKers.  If you can delete a mob in group then you can delete it solo
and you won't need a group.  Although wizards weren't great on raids either for much of the game which I will get into 
in a minute.

Wizards needed solutions that improve their exp group value but not very much while soloing and raiding.  I don't have
an easy answer for this.  Giving them free nuke items doesn't work very well because you can't meditate while using
them, although it's better than nothing.  If you're chain casting your Velk robe then you're doing way less damage than
a monk or rogue who can output damage endlessly.  The real issue is that melee have no resource
which limits their output.  I think endurance was supposed to work like that in the early stages but they decided not to
go with it.  There are spells that increase player endurance that were useless.

One idea I had was to grant wizards a DD proc buff.  This would be near useless for soloing but increase group damage
if the group had a single melee character or pet in it.  I think it should have a cooldown such that only two people 
could have it on per wizard and it would need strict anti-twink limits.  Of course keeping a short duration buff on 
all the time like a damage shield is not the most engaging gameplay.  I suppose you could make it an aura of some sort 
instead.

In 1999 when dungeon crawling was a big thing, evacs were important.  I remember the days of evacing my group out of Guk
on a bad pull.  The older the game got however the less useful evacs became.  Wizards were never really compensated for 
this.  Ideally a new game would keep evacs being necessary by keeping dungeon crawling in the game however.

### Wizard Raid DPS

Wizards are considered good for raids on emulators but they really weren't, except during certain periods.  They were 
fairly good on Nag and Vox but garbage in Sky.  A lot of Sky mobs were completely immune to wizard damage pre-Kunark.
In Kunark they got lures which actually put wizards ahead of some of the other casters in some high resist situations
but on the hardest bosses melee disciplines crushed wizard lure DPS.  Lures could actually land but they had crippled
damage per cast time compared to normal nukes, meanwhile rogue backstabs were doing 1k+ under disciplines in an era
where killing a dragon took 60 seconds or less.

In Velious wizard banes were a _massive_ increase in power that made them the supreme DPS for the first time, but only
on bosses where banes were usable.  Of course they cost a bunch of platinum to use, because FU wizards.  Other than
banes, wizards were terrible in an era with high resists and hundreds of thousands of boss hitpoints.

Casters in general gained considerable power during Luclin.  Bosses 
had a ton of HP but also a ton of AC.  That AC made a large difference.  So much so that Sony reduced boss AC considerably 
in PoP.  Casters got more DPS from AAs than melee did, then focus items mid-era.  Casters not needing bane weapons meant 
they would not be in a situation of not doing damage, although pet classes could not use their pets.  That made wizards 
better relative to other casters and important for the Emperor fight which was the most important boss of the era.  Emp 
and Seru were also highly aggro sensitive which further favored wizards over other casters because wizards have an aggro 
reducing spell.  Late in the era the resist logic was changed which gave caster DPS a very large boost.

In PoP wizards roughly tied with well-geared rogues for the top DPS on raid bosses, but when rogues got LDoN augments 
they pulled ahead.  That a manaless DPS class can out-dps the mana restricted burst DPS class is not what I would call 
balanced but I would say that it was more rogues being OP.  Monks were well behind rogues.  Wizards required a high-aggro 
tank to perform well but melee DPS did not.  Although it was easier for a wizard to get SoS than a rogue a good poker.
For PoP bosses wizards generally didn't OOM, but for exp groups they did.
Melee DPS crushed wizards in exp groups, even in PoP.  A rogue would do _double_ a wizard's total damage in exp groups.

The wizard's raid performance illustrated the point that their burst damage was simply insignificant: if a rogue can
match wizard damage on a three minute raid boss, then this means wizard burst damage basically doesn't even exist, and 
therefore they are not compensated for their lack of sustainability. (although wizard damage is ranged but most boss 
AoEs hit everybody)  Wizards should generally 
be the top DPS on raid bosses where mana isn't a constraint unless resists or aggro come into play, or the 
designer intended for another class to be better than wizards on it with some gimmick.  Otherwise what's the point of the 
class?  Being easy to box doesn't count.  I do think Sony should have designed more bosses which favored other DPS 
classes to be the best on them but they didn't really do this except in some rare cases. (e.g. Fennin and rangers)

### Point-Blank AoE

PBAoE groups were the great equalizer for wizards.  This was the _one_ thing that they clearly did better than any other
class.  I tried to do this as much as possible.  The issue with AoE groups is that they're rare and the vast majority
of wizards never got to do them due to the strict requirements. (2 wizards, 2 enchanters, a competent puller, an open zone)
I wouldn't call the class balanced because of this.  Sony in fact nerfed this gameplay several times in various ways.
AoE groups died once the high level kill bonus went in anyway.  AoEing was some of the most fun I had in the game however 
and I  strongly think that games need high skill high reward options for players.

PBAoE spells are tricky to balance.  It's difficult to make them worth using but not overpowered.  You cannot simply set
a mana cost on the spell to do this.  Without a target limit on the spells, every zone in the game would need to be
designed to prevent pulling ridiculously large trains to AoE down.  A way to do this however is to place enough
caster NPCs in the zone such that pullers couldn't survive 20 wizard NPCs nuking them, which was PoP's flaw, a lack of caster NPCs.

Were I to design the spells I would probably do something like reduce the damage of each subsequent hit by 2% such that 
the spell's total damage were about 75% when hitting 25 targets, 50% on 50 targets then stopped hitting additional 
targets after 50 hits.  This preserves the damage of the spells for small to medium pulls but makes large pulls infeasible.

### Rains

I feel rains could have been a big part of the solution to wizards and were a missed opportunity.  Rains had an innate 
20% resist rate applied to them, as well as a guaranteed resist on targets under 10% HP which made them mostly unusable.
They hit a maximum of four times.  During Kunark, pets of group members would count toward the four hit limit.  Factoring 
in the 20%, Tears of Prexus was about 5% more efficient than Sunstrike with 3 hits, and 40% more than Sunstrike with four 
hits.  So it was usable if you could land it on two or more mobs and were careful not to use it on low HP targets or hit
yourself, but generally rains weren't worth the trouble.

Rains should not be the best spell to use on single targets, but they should massively increase the caster's DPS on two
or more.  EverQuest is a game that over-rewarded single pulling play, and rains jacking up your DPS and efficiency by a 
large amount if hitting multiple targets is a way to make groups with multiple tanks more competitive instead of 
enchanters being the kings of the group game all the time.  If rain damage on two or three targets were much higher than 
it makes wizards much more valuable in group play without making them OP in solo or raid play.

**Wizards should absolutely be the best DPS class in groups where there is no mezing going on and multiple targets are tanked 
simultaneously.**  It's unfortunate that they weren't outside of full-on PBAoE groups.

Rains could have easily done more than four hits and not been too strong.  I do think however that spreading the damage
over three spell waves should be preserved even on larger pulls by reducing the damage per hit so the limitation of
needing to keep the NPCs in one spot remains.

A simple way to improve rains would be to halve the damage per hit after every 4 hits up to a maximum of 12 hits.  If a
rain spell would do 90% efficiency of the top DD spell on a single target, then hitting two mobs would be 150%, three 
mobs 187%, and four mobs 210%.  Obviously the numbers here get subjective but I think rains and therefore wizards could 
be improved by granting them more damage on multiple targets somehow.

### Targeted AoEs

There were two kinds (excluding rains) of targeted AoEs: pillars and Al'Kabor spells.  The latter were perhaps the most 
useless damage spells in the game.  Pillars of course were used for quad kiting and that's about the only thing they 
were good for.

A problem these spells have is that rains need to be better than them because rain damage is done in waves, requiring
stationary targets.  So in groups there is no reason to use these.

I feel these could use a redesign.  One design implementation I think is a good idea is to scale the damage of
an AoE with the distance to the epicenter, as this just makes logical sense.  Raid boss AoEs could work this way as well.
For example, an AoE might do 100% within X distance then after which reduces down to zero at a final radius.

Other than scaling damage, another way to scale a spell might be to adjust the mana cost based on the number of targets 
it hit.  I think having an arbitrary limit of four, five, or whatever on an AoE spell makes no sense from a logical 
standpoint other than being a band-aid solution to prevent spells from being too powerful.  I prefer designs that are 
more analog and not all-or-nothing.

Mob AI could create a reason for these spells to exist.  For example, if certain mobs mostly ignored ranged spell damage
or tanks had good AoE taunt, and a raid needed to kill many of these simultaneously, and they output some kind of AoE 
damage or mana drain or their AI favored casters in melee range preventing the use of PBAoEs, then suddenly you have a 
great use for Al'Kabor spells.

### Quad Kiting

Quadding for a wizard was actually somewhat challenging because their snare lasts a much shorter amount of time compared
to druids, they don't get SoW and they cannot heal themselves.  However, I think kiting was bad for the game and should
have been made much less feasible in part by much shorter snare durations.
[Absor stated](https://web.archive.org/web/20010822064136/http://eqvault.ign.com/archive/arc27.shtml) publicly that he 
didn't like the tactic of quad kiting and made that known in tuning meetings.  Brad didn't like _any_ kiting, so if single 
kiting was unintended then quadding was certainly accidental/emergent.

The problem with nerfing kiting is that
wizards and druids were probably the worst grouping classes in the game and their soloing ability was a counterbalance
to their group undesirability.  If you remove kiting from them then you need to give them something strong in return,
although both classes can solo fairly well using roots.

If kiting is nerfed enough however then the four and five target limits could be relaxed considerably.

### Bolts

Bolts were much more significant when the game launched in 1999.  I remember using them as a young wizard.  You had to
aim with these spells by directly facing your target, and it had some sort of automatic Z adjusting if the target was
above/below like the game Doom if I recall but it's been many years.  Bolts also had the advantage of being longer 
range; 300 units instead of 200.

EverQuest had collision in that players could not run through other players or NPCs, which I liked.  Games not doing
this is anymore is the lazy way out of dealing with the issues of players potentially griefing by blocking areas.
That some spells could be blocked by players or objects is cool to me and makes the player actually think
about what they're doing more.  I think that the mana cost of a missed spell might be drastically reduced
however because whiffing a cast and eating the full cost is rather brutal.

## Warriors

Warrior was the second class I played extensively.  I two boxed almost everywhere from Velious to my GoD retirement, 
eventually becoming the main tank for my guild during the Plane of Time era and becoming the 
first Warrior to break 3000 AC so I'm also very familiar with this class.

In classic, pre-Kunark era, warriors were rather bad.  Warriors had virtually the same skill caps as hybrids back 
then and _all_ classes had the same AC cap.  In that earliest era, Sony was resigned to the fact that some classes 
would just be weaker, and these classes would level faster to compensate.  The warrior was one of these classes.
That is something not many people would consider acceptable today. (myself included)  Although hybrids were missing a
lot of stuff back then.  Shadowknights didn't even have lifetaps until seven months after launch and even after they
got them they had mana cost penalty.

Warriors got very large upgrades in Kunark.  Melee gained more DPS than casters did overall due to skill cap raises
and much better weapon ratios, also disciplines.  The warrior AC cap was raised to 405 in Kunark while knights were 
stuck at 350 which is a significant gap.

The best time to be a warrior was early Velious before the hate cap on procs-- a warrior could wield a Journeyman's 
Walking Stick which proced Tashani for massive aggro.

In Velious, hybrids and monks got large upgrades: a spell damage boost early in era and late in era they got a massive 
melee DPS boost in part from 2h damage being fixed.  This was part of a pattern of everybody except warriors getting
upgrades, which made warriors less powerful relative to other classes.  Knights also started getting 1-handers with 
damage similar to 2-handers in late Velious, allowing them to use a shield all the time with little penalty.  The AC 
cap gap also shrunk considerably in this era when warriors were raised to 430, knights 403 and monks 375.

What kept warriors afloat after these knight and monk upgrades was that defensive discipline became mandatory on raid 
bosses and proc weapons became much more available.

In Luclin uncapped Flowing Thought and the availability of FT gear meant that knights didn't need
to meditate to hold aggro forever.  Warriors didn't even get the Physical Enhancement AA until late into Luclin.
In PoP, shield AC started to not count toward the cap which allowed knights to 
mitigate as well as an undisced warrior.  NPC max hits at the time grew very large so ripostes made dual wield setups
take more damage which is something knights never had to worry about.  Warriors had the most generous overcap returns 
in PoP however and that was the one thing going for them other than hitpoints, however the cap on complete heal made 
the warrior HP advantage much less significant with Time gear allowing for 10k+ HP pools.  To top it off the 
Darkblade was worse than a Blade of War for hate generation until Anger III augments existed.

After the hybrid upgrades in Velious I think the gap between warriors and hybrids became so narrow that warriors became 
a one trick pony.  And that trick was Defensive Stance.  Defensive stance became the entire reason for the class.  Guilds
started using _monks_ as rampage tanks at this time instead of warriors because the mitigation advantage shrank so much
which led to a monk nerf.

Defensive Stance was too good and held the class back from getting any mitigation advantages or threat improvements.
Knights resented not getting to tank any bosses and warriors resented being so much worse than knights on everything 
else.  Although this was in part because knight aggro generation was too cheap which I will go into later.  Evasive 
stance was almost as OP and both should have been nerfed while buffing other things.

What really pushed Warriors over the edge was the introduction of Vie buffs.  In LDoN, Vie buffs were introduced which 
allowed knights to tank Time gods, so your raid didn't even need Defensive anymore.  This made warriors quite literally
organize a [protest](https://web.archive.org/web/20031209123117/http://www.thesteelwarrior.org/forum/showthread.php?s=&threadid=4109)
which Sony had to respond to.

Warrior DPS was actually fairly good.  If you had a glut of warriors in your guild they weren't dead weight because
their DPS was decent.

Warriors lacked 'snap aggro' and this was their Achilles heel.  Taunt was garbage for this.  In an exp group,
you want debuffs to land on targets ASAP and preferably without the mob getting off of the tank.  With a warrior tank
your shaman was going to eat hits for a while if he slowed immediately, but not with a knight.  If you pulled 3-4 mobs
then your cleric was going to eat hits with a warrior tank, but with a knight could get the attention of these mobs in
a much shorter amount of time.  A knight's hate generation advantage was simply much more significant than a warrior's 
mitigation advantage, on top of the rest of a knight's utility. (lulls, heals, snares, FD etc)

The problem with massively jacking up warrior hate generation is that you trivialize the game.  If wizards can just
nuke all day without worry and healers never aggro then the game is way too easy.  I would argue that the problem is
more that knights aggro too well than warriors too little.  In fact I think warrior hate generation got too high at
one point-- certainly after GoD AAs and unlinked discs and maybe after LDoN augments, at least on raid bosses with
raid gear, but not as much in group situations where a warrior needs hate immediately and doesn't have time to build 
it up.  It's the random nature of procs that makes warriors so poor in group scenarios.  I think the Taunt skill 
could probably be made to be more reliable on exp mobs, and perhaps could add hate even if the warrior is on top; 
also I don't see why Area Taunt couldn't have a much shorter cooldown.

It's worth mentioning that in the really old days (Velious and earlier), mob aggro was much more proximity based in
that they were much more inclined to attack closer players and mobs would need to be aggroed quite a bit to make them switch
off the tank.  This is why warriors could do their jobs without proc weapons and why proc weapons weren't really a high
priority for warriors until Velious.

## Knights

The big problem I see with knights is that their aggro generation is far too cheap.  A 10 mana spell should not
generate copious amounts of hate-- it should require significant amounts of mana to generate hate for tanking.  It
makes absolutely no sense for Disease Cloud to generate as much hate as Turgur's.  Knights should have to use their
higher level spells to keep up with hate generation.  This just makes logical sense and nobody would argue against this
if the game had been designed that way from the start.

In PoP, Sony implemented a shield aggro focus, Furious Bash, but it did virtually nothing for warriors while
giving knights a large boost, which was really dumb.  Furious Bash should have been a large flat +hate amount on landed bashes
instead of some spell hate multiplier.

I don't think making knight 1-handers with DPS levels similar to 2-handers was wise.  There needs to be a drawback to
using a shield.  This is partly why warriors became so far behind knights when defensive disc was off.  This wasn't so bad
before they made shield AC ignore the softcap and shields were kinda garbage but after that change it became an issue.

In the earliest eras before Velious, knights had some of the highest experience needed to level, and this was because
they were strong classes in the 1-50 game.  The class penalties definitely should have been removed in Kunark
when warriors and rogues both got massive upgrades and hybrids no longer had the same skill caps as warriors.
Kunark was the worst era for hybrids and they had legitimate complaints then.

Sony fixed many issues with hybrids in Velious: hybrid exp penalty removal, reduced cast times on 3+ second spells,
more spells granted from their parent classes, and spell casts no longer resetting the melee swing timer.  Knights had
their Defense skill caps raised to warrior level early in the era.  All Melee classes got AC cap raises in Velious.
But the biggest upgrade knights got was in the October 2001 melee revamp which greatly increased knight melee DPS.
After the Velious upgrades, warriors went from being part of the 'trinity' to being inferior group tanks again.  It
became apparent how worse warriors were in PoP when exp mobs started hitting for three times as much, making snap
aggro much more valuable.

Knights do have a serious issue however, and that is that they cannot meditate while doing their job. (tanking, pulling 
etc)  This is why clarity is so important for them.  If knights have to expend large amounts of mana to hold aggro then
they will need some way to regenerate mana while standing.  Flowing Thought mitigated this but that was in Luclin and required
high end raid drops.

## Druids

Druid is another class I've played a lot of starting with Project 1999 since I'm such a loner.

Druids were bit odd in that they could be very strong, even OP at times and underpowered at other times.  They are 
excellent soloers and the first 50s were druids who camped guards as snaring a mob and dotting it with SoW on is 
brainlessly easy and risk free.  Frankly soloing was far too easy for them and it flew in the face of EQ's core ethos
of being a group oriented game.

The issue with druids is that the tools they have that make them such strong soloers
are simply not nearly as valuable in a group.  Melee damage tended to outpace spell damage in groups in EverQuest,
which was the problem wizards had.  Druid DDs are even weaker.  DoTs won't last long enough to do full damage in groups.
Druids could heal however so they tended to do this in groups.  The problem with healing is that the gap between clerics
and the other healing classes is rather massive.  If only that gap were as large for spell damage classes, wizards would 
be elated.

Druids are supposed to be friendly to animals so it's ironic that the spell tools they get allow them to mass murder
animals.  A druid can snare an animal, fear it, then attack it with another dual wielding charmed animal with a massive 
haste and ATK buff on it.  Since the mob is feared your pet won't get injured.  There are few places in the game where 
this is possible but where it does work it makes enchanters envious.

Druids on raids were rather unremarkable until PoP.  They had a large kit so were never useless, but oftentimes were just not 
necessary.  In PoP however druids got significantly better with their CH-like heal which allowed them to substitute
clerics in CH rotations, and their FR and ATK debuffs were very strong.  People underestimate the druid ATK debuffs.  I
think druids were in a good place during PoP, even on raids.

Druids and wizards were the porting classes, and druids had the better teleports.  If you needed an evacer for a group,
you would prefer a druid generally.  Evacs became less relevant over time however.

Druids were generally considered the powerleveling kings, although after level 30 other means of powerleveling probably
won out like suiciding mage pets or monk FD.  Anyway druids were very good at this, and I feel should not have been 
allowed for reasons I went over.  People may not like that view and younger me wouldn't like it but show me another game 
that allows EQ's level of powerleveling.  Blizzard clamped down hard on it for a reason.  The harms outweigh the benefits.

OK, so say druid soloing gets made much less feasible and quadding is dead.  What should druids get?

I think druids 
should get much more powerful regen spells.  Shamans should not be in the lead on this, druids should be.  Imagine if
druid regen spells were five times more powerful and chloroplast did 50 HP a tick instead of 10.  This really just makes
sense from a lore perspective.  It narrows the gap between cleric and druid healing in a way that doesn't really trample
on the cleric's direct healing.  Smart groups would then endeavor to spread the damage around.  Although manastones
really could not exist along with this spell in the game.

Druids also should have gotten a single target HoT.  I think it should last longer than the cleric's HoT and be weaker 
per tick.

Druid ATK, AC and FR debuffs could be made cheaper and faster casting for exp group use.

More summoned mobs should be put in the game so druids can have places where they are as strong as clerics are in undead
zones, using anti-summoned creature nukes.

Snare should be more important in some dungeons.  Some dungeons should have mob AI that flees early requiring the use of
snares.

If the game has effective anti-cheats then druid tracking becomes quite valuable if you don't have a ranger along.
Dungeon design should have more randomized spawning in general which would make druids a more attractive option.

## Clerics

Almost the entire conversation about clerics is about Complete Heal.  Clerics were simply one of the most powerful classes
even without factoring in CH.  I don't see a lot wrong with them other than CH. (granted I've not played one seriously)

CH is a bad spell.  I went over this previously.  It's just crap gameplay to have to time your heal button in a way that
anticipates 10 seconds worth of damage, and do this for every single expansion forever.

CH exacerbated other issues in the game: the efficiency of the spell allowed groups to have no downtime which devalued
spell damage because melee could swing endlessly.  Tank mitigation ability matters less when healing power is infinitely
sustainable.

## Shamans

Slows were OP thus shamans were always good to great.  Lower ranked slows weren't as good so it took awhile for shamans
to reach OP status but by level 39 they were quite strong.  I think it's strange how large the shaman's kit was.  Why do
they get a pet?  Why do they get regen spells before druids?  Shamans get plenty of damage spells, including the
best DoTs.  Wizards were entirely a one trick pony but all caster classes got decent DDs including clerics and shamans.

If pets weren't so absurd in the 1-50 game I'd put shamans at #1 in the pecking order.  The first level 50 on my server
was an ogre shaman.  Necros were tops and mages slotted in #2 after they fixed pet dual wield for them which was somewhat
late in the era.  After that it was shamans.

I remember shamans lusting over the Sebilis nuke bracer.  Why did shamans get infinite nuke clickies before wizards?
Only Sony can tell us.

While shamans were strong I would say that they had some nontrivial issues however.

The shaman's biggest issue was that they were annoying to play.  To min-max a shaman, you have to time cannibalize casts
between mana regen ticks, which is terrible gameplay.  Keeping up so many buffs on the group is not fun either.  They
later merged buffs together which was a very good addition.  AA canni replaced spell canni.  This issue got better over time.

The buff limit was the necro's problem but it also affected shamans.  Shamans had more to do so they didn't need to DoT
raid bosses to be useful but shamans did have the best DoTs which were largely unusable on raids.  I really think DoT
classes should have been able to use them on raid bosses, and they should have gotten the spell damage in their logs.

Slows and debuffs don't really stack in raids unless the target is hard to slow or the boss dispelled itself (Sontalak).  So
raids generally didn't need more than one or two.

## Necromancers

Necros went from being the best class to being one of the worst.  At launch necros were totally insane.  Pets were
ridiculous and necros had the best pets.  For most of pre-Kunark classic era, you could give necro pets low delay weapons
and it would reduce their delay.  It was common to give necro pets daggers and they became buzz saws.  Mage pets 
couldn't dual wield until the patch giving necro pets daggers was nerfed, so necro pets were the clear winner for
10 months.  For whatever reason Sony gave the pet classes potent haste buffs with max level haste and other stats, so
they didn't even need an enchanter to buff them.

In 1999 one of my necro guildmates solo broke into the Plane of Fear by running to the north wall safe spot, 
FDing, relogging to clear aggro, then made a pet and reverse kited to kill mobs.  Necros could also solo the ghoul
lord room by charming.

Necros have the largest kit: pets, heals + lure DDs with lifetaps, non-lure DDs, potent anti-undead spells, FD, a mez, a 
resurrection spell, DoTs, fears, strong snares, a high mana regen rate with HP to mana conversion, even weak HoTs on other targets.
Necros are sort of like druids in the sense that their strong solo abilities didn't translate into group desirability
but the strength of pets made them beasts early on.

Necro power declined with the decline in pet power.  Pets obviously don't get stronger with gear like players do, (pet 
focus items aside) so by the time Luclin was current, Sony had to buff the top tier pets to keep Necros and Mages 
competitive.  Pets were also unusable on some fights due to AoEs or fears.  A necro's own fear spells were unusable
on targets above level 52 which meant they couldn't reverse kite much or at all after level 60.

Like shamans, the (de)buff limit and inability to stack the same DoT spell on a target by multiple players of the same 
class basically prevented necros from casting their DoTs; that plus not being able to see
the damage of them made players tend to not use them.  This really held back the class and turned them into weak wizards
with a pet in many cases.  In the late PoP era these limits were removed and necros suddenly got a major power boost 
which was long overdue.

Necros could transfer mana to another player, and this was often done to clerics doing a CH rotation.  Because the
CH rotation was the lynchpin of a guild's strategy to slay most raid bosses, if even a single cleric went OOM it could
cause the failure of the attempt, which for long battles put necros in the position of being mana batteries.  While
giving a class a mana transfer ability is situationally helpful I think this spell should have had a longer cooldown so
necros were not relegated to this undignified duty.  Of course you could also just remove CH from the game and the
problem mostly goes away.

## Magicians

Mages I think were rather underrated, although most everybody knows about how strong they are in the 1-50 game.  They
did start to fall off in Luclin, or earlier if they did not have their epic, but even in PoP their damage on raid bosses
was respectable.  PoP was the worst expansion for mages up to that time and arguably the best for wizards and yet mage
DPS could still equal that of a wizard assuming the raid boss had low AC & fire resist, pets were fully usable and the tank
generated plenty of hate.  Those four qualifiers are why mages were perhaps one of the weaker classes in PoP as often
pets were not usable and tanks couldn't maintain high levels of hate, but I feel that class balance in terms of damage 
output was very good in PoP, relative to previous eras, so no class was struggling.

Because much of a mage's damage comes from pet melee, mage damage doesn't crater when they run out of mana like a wizard's
DPS would.  This is the primary reason mages are far superior to wizards in (non-AoE) exp groups if evac isn't a concern.

In pre-Kunark classic, mage pets couldn't dual wield until January 28 2000.  So for 10 months, magicians were strong but
sane; but in the three months prior to Kunark magicians were quite _in_-sane and their pets were stronger than a level 50
warrior player.  Sony would balance this by making melee classes much stronger in Kunark while player pets did not get
much of an upgrade over the level 49 ones.

Call of the Hero and modulating rods ensured that mages always had a role in a guild.  Of course these duties were chores and
not terribly engaging.  In Luclin mages would just mass summon mod rods and drop them on the ground.  That went away
in PoP, thankfully.

I think what magicians needed were better pet focus items.  There were few in the game and they didn't do much.  The
pet focus drops from Vex Thal and Plane of Time should have been larger upgrades, and some weaker versions could have
existed for guilds not at the top end.  Pets simply don't scale much while everybody else does and this makes mages start 
to fall behind at the high end game.  Also mage AAs could be better.

I don't think it's a good idea to make mage pets so durable that raid boss attacks don't kill them.  I think generally
speaking it's OK if mages outdamage wizards by smallish margins under ideal conditions for them.  Some fights pets 
should just not work well or at all and other fights mages should top the DPS meters.

## Enchanters

Enchanters are ridiculous on the emulated servers, but that's because emulated servers didn't do a good job replicating
charm.  Unfortunately they've been OP so long on emus that people have started believing that they've always been this
way, which they haven't.  OG Sony was conservative in their designs and they didn't want spells being too strong.  That
Verant Sony would have allowed charm to be like it is on emus today but somehow players back then didn't bother to use it 
doesn't pass the sniff test.  Charm _was_ made overpowered just prior to PoP's launch but before then it was much weaker
because the break rates were over four times as frequent and charm pets could steal all the exp on kills until mid-Velious
requiring the use of mem blurs.

Lulls had the same story: they were near useless before a patch just prior to PoP's launch, then they become overpowered.
Servers emulating pre-PoP eras didn't realize this and failed to make their lulls accurate, making enchanters OP.  In the
old days enchanters were popular because of mez, clarity, haste and slow-- not charm and lull.  Even without charm and lull
enchanters were so strong that they were part of the so-called "trinity" of the time which was warrior cleric enchanter.

I do love the idea of this class in classic, at least the real version of it: just pure non-heal support and not a damage dealer.
Charming wasn't done very much in the old days and when it was it was probably to CC.  I do not like PoP's enchanter
where a single charm pet can outdamage two chain casting wizards and can be the entire basis of a group.  Sony made a 
huge error in 2002 when they massively buffed charm.  PoP charm trivialized the game and made other DPS classes feel 
terrible.  Charm trivialized the Rallos Zek encounter in Tactics which was a huge shame.

Enchanters did have periods where they were pretty bad.  In late Velious they were buff bitches in NToV.  If you can't mez, charm,
slow or lull then you're just a buff dispenser and the raid doesn't need more than one or two of you.

Color stuns were necessary for PBAoE groups, and because of this enchanters had first class tickets to the best exp in 
the game even before PoP's charm.

## Rogues

Rogues went from the worst class before Kunark to being the top damage dealing class.  Any guild with a clue wanted a
strong rogue contingent.  In EverQuest melee damage was just favored over spell damage for the most part and rogues
did the most melee damage, thus they were the top DPS class.  In Kunark melee classes all got large buffs because of
combat skill cap raises and weapon ratios improved sharply; meanwhile resists got harsher.  On top of this pure melee
classes got disciplines.  You would think that wizards would be the best DPS class on 32k hitpoint bosses after pet
nerfs but you'd be wrong.

In Velious things got even worse for casters as resists were still harsh but mobs now had an order of magnitude
more hitpoints.  Casters didn't generally OOM on bosses before but now they sure did.

The rogue epic was the easiest to complete and rogues got double backstab at level 55.  Backstab in particular is the
only melee skill that increased its base damage with gear, so while the other skills didn't scale over time backstab
did and this kept rogues in the lead.

I think it's fair to say that rogues as a class were overpowered.  Their damage output matched or exceeded spellcaster
damage and they never had to worry about overaggroing or running out of mana.  They were the undisputed DPS kings in 
non-AoE exp groups as casters would OOM.  In PoP however, AoE rampage became a thing
and this was the only real worry a rogue ever had, but only a handful of infrequented bosses had this and it was possible to avoid it
with very careful positioning.  It would otherwise have been rather harsh to not allow melee classes to do anything, but
there were several times where casters could do absolutely nothing due to resists. (e.g. Sky)  AoE rampage punished guilds
who stacked rogues and ignored ranged damage.

If casters were going to be severely limited by mana then I think endurance should have been designed into something
that limited melee damage output.

Shroud of Stealth was also OP and Brad would have never allowed it.  He stated himself that this level of impunity was
not appropriate for EverQuest.

I do like that lockpicking is required to access certain areas.  Throwing damage could probably be increased or made
more useful somehow.

## Monks

It's well known that monks tanked too well before their nerf in late Luclin.  Monks were pretty strong before that harsh
nerf then became weak.  Monks during their low AC period might be the worst PoP class, although the nerf was largely
reverted.  That nerf was far from the only reason why monks declined however.

The reason why monks tanked so well was because AC caps were 350 for _all_ classes originally which was already too high
for non-tank classes, then in Velious Sony raised the caps for all melee classes.  The monk cap was raised to
be the same as rangers, at 375, while warriors were 430 and knights 403.  Sony had also increased the monk's low weight
AC bonus in late Kunark, making reaching the cap easier.  Raising the cap to 375 was a mistake.

Monks get the block skill, which is by far the best avoidance skill.  A level 60 monk blocks 13% of the incoming
attacks against them, vs. 6% for warrior parry.  Monk dodge is also higher than a warrior's so they dodge 1% more often.
The combination of a generous AC cap with their avoidance skills made monks tank too well.  Feign Death and disciplines
along with their AC and avoidance skills made monks great rampage tanks.  Sony nerfed monks to a 315
cap then partially reverted it up to 350.

The need for a monk nerf declined with PoP's launch however.  The other classes got 
significant mitigation increases with softer caps.  Monks also lost relative power at this time for other reasons:
other classes started taking over pulling duties, and monk damage was falling behind from their skills not 
scaling with gear plus the major increase in caster damage from the resist changes.  In PoP, rangers
were doing monk level DPS with melee _and_ archery (much more using Trueshot) and even SKs were matching monk damage
on shorter raid boss fights, easily so using Harm Touch.

Monk specials not scaling with gear was a huge oversight.  Flying Kick should have been doing at least double the damage
it was in PoP with high end gear.

## Rangers

Rangers are another class I feel is underrated.  Just because a class is not the best DPS, healer or tank doesn't mean
they are useless.  In the 1-50 game rangers can tank very well, having a defense cap of 200 vs. 210 for a warrior.  In
fact you may even prefer a ranger to a warrior in this period for a group because of the hate generation, especially
before high end plate becomes available.  Rangers had the same offensive skill caps as a warrior in that period except 
for double attack which is a mere 5 points less.

In Kunark their defense cap isn't raised so their tankability falls behind, but in this era a lot of raid bosses are
immune to non-lure spell damage, so other classes were also having a bad time.  Kunark might be the worst era for
hybrids in terms of performance, _and_ they still had large experience penalties.  Rangers however get Greater Healing at 
57 which is quite usable and allows them to heal the AoE damage they take partially or in full while a rogue or monk 
would need a healer to keep them up.  Rangers start getting ATK buffs at this time ensuring that raids will want one ranger at 
least.  Keep in mind raid sizes back then were four or five groups.  Rangers also got jolt mid-Kunark which is quite nice.

Velious buffed hybrids considerably with higher skill caps, more spells, changes to make spell casts not cut into
melee damage as much, and the experience penalty removal.  Rangers had their weapon skills raised to match warriors early in era.
Rangers got their innate ATK bonus late in the era.  Their defense cap was raised to 220 at the same time, plus their AC 
softcap was raised to 375 mid-era.  With these upgrades rangers were made good enough for exp group tanking again, 
especially with a slower, while having better than warrior levels of DPS.  It's easy for chain classes to hit the AC 
cap in Velious gear.  After all the Velious upgrades Rangers became quite solid again.

Swiss army knife classes require the player to utilize all of their skills opportunistically.  Most rangers didn't do 
this and instead complained about the class sucking.  If you're a ranger in a group and you see un-full health bars 
during downtime, then cast heals to save your cleric mana.  That is better than a necro directly giving mana to the 
cleric.  Then meditate instead of stand around.

Play like a druid during downtime; play like
a knight when your group over-pulls and your tank can't immediately prevent all the mobs from attacking the cleric; CC 
with roots, snares and kiting; check tracking often and notify your group of rare mobs that spawn; utilize OP harmony to 
pull; dispel mobs when needed so your casters don't have to; keep buffs up on the group, including pets, and strength 
buffs if no better source of strength buff is available.

Rangers vs. summoned mobs should be the equivalent to paladins on undead and this was a missed opportunity.

### Archery

Everybody knows rangers got infinite archery in Luclin.  Archery didn't really become popular until Planes of Power
however because Luclin bosses were largely corner tanked plus had a lot of AC, also PoP made good bows easy to obtain.
Archery is more sensitive to AC because it has no damage bonus and PoP's bosses had much lower AC than Luclin's.
Archery also benefits from critical hit AAs more so than melee does so the extra PoP crits were not trivial.

Archery before Gates of Discord had a quirk/bug to it which was that if the target mob was touching a wall then the arrows
shot at it would poof and not hit, although in rare cases they might land if the archer was standing in some hidden
unknowable position that was close to a single wall the NPC was on.  If the mob was in a corner then archery never 
hit except in unusual cases where the NPC was well elevated above the player such as Mith Marr on a corner pedestal.

Archery in Luclin and PoP had trade-offs that made it acceptable even though it was a complete accident.  If archery could have
hit corner tanked or walled NPCs then it would obviously be super OP: without Trueshot, archery was manaless monk-level DPS 
(rangers and monks also had very similar melee DPS in PoP however) from 400 range with very little aggro using only a crafted bow.
With Trueshot, rangers were doing 2x monk DPS for 3 minutes.  If a guild was willing to fight a boss out in the open and 
not touching a wall, then rangers could do double their DPS for three minutes, on a 72 minute reuse.  Rangers would top
the meters in this situation, but that scenario was uncommon since the trade-off was significant: no guild wants to deal
with the melee push of uncornered or unwalled bosses.  The disc timer was long so guilds had to use it well into a fight
when it looked like it was going well, because they may not get another use of it again in that raiding session.  The long 
reuse timer prevented guilds from stacking too many rangers.

Providing options to guilds like this instead of every strategy being the same is a _good_ thing and it allowed rangers 
to be rockstars occasionally.  Once arrow poofing was fixed, archery needed to be nerfed hard.  I liked the reality that 
rangers couldn't just use archery on every single fight and had to use both melee and archery depending on the encounter.
Archery even in PoP should have done more hate however.

Rangers could shoot from over 400 units using certain bows and this was also a mistake.  This allowed them to avoid some boss
AoEs entirely and in some cases kill mobs for exp outside of their ignore radius, meaning they wouldn't chase the ranger.

While archery ended up in a semi-balanced state, I don't think it should have been designed that way on purpose.  Archery
doing nearly no hate is just dumb.  I believe that archery damage should fall off at longer ranges in terms of damage per hit
_and_ accuracy instead of doing full damage at 400 units for balance reasons but this is also realistic.  Trueshot needed 
a rework.  Maybe +50% damage instead of +100% with half the cooldown, and it also increased hate generation by as much
extra damage it did, requiring a tank who can hold the mob's attention or jolts.  With these changes I think you could 
fix arrow poofing.  Archery w/o disc should do slightly less than melee DPS so that meleeing doesn't become obsolete.

Sony at the time was well aware that archery would have been unacceptably powerful if the cornering/walling arrow poofing
were fixed, and they 
[said so publicly](https://web.archive.org/web/20030717154103/http://forums.interealms.com/ranger/showthread.php?threadid=24936).

In the original game, archery was kept weak intentionally because the designers really didn't like kiting.  I don't think
it's a coincidence that Luclin is when archery became relevant because several of the original team left during that
time.  But if designing a game from scratch, giving archery a cast time would mitigate the kiting issue.

## Bards

I'm not terribly familiar with the bard class and didn't play one very long.  I don't think I would get a lot of 
disagreement by saying that bards were the most annoying class to play because of song twisting.  Bard combat songs were
not very powerful on their own and to carry your weight as a bard required twisting four songs which was obnoxious.

Bards were actually pretty weak before Luclin.  Resist songs were far less helpful before the resist system revamp
and bards didn't get overhaste until Luclin.  Mana regeneration song was their most valuable contribution.  Bards did a
lot of things enchanters did but worse.

Sony was seemingly terrified of making bards too powerful.  Verant Sony was conservative in their designs, so they 
sometimes made spells or skills outright useless, like lulls.  At one point about five months after the original launch 
they put a secondary resist on bard mez songs because Sony was afraid of a mez that could be cast infinitely without 
user action, which made them rather unusable.

Sony wasn't entirely unjustified in their worries, as in PoP bards started doing AoE DoT swarms which awarded absurd
amounts of experience.  Sony tried to nerf this several times before ultimately making bard AoE DoTs do zero damage
on moving targets on Omen's launch.

I have mixed feelings about melody.  Twisting songs was too obnoxious to keep forcing players to do, yet melody
removed all interaction with the game and a bard could just AFK with it on.  I think perhaps I would prefer that songs were
simply strong enough that if bards couldn't have more than one song buff up at a time that it wouldn't cripple the 
class.

## Beastlords

Beastlords had one major problem and that was the class was and is unfinished.  They get all of their
good stuff at the highest levels, leaving beastlords under the level cap being mediocre or worse.  They do not get
a haste spell until level 60 for example, which is Alacrity.  They do not get Quickness _at all_ which makes no sense.
They are also stuck using Drowsy until level 60.  The first mana regen buff is at level 44.  They don't get their
strong ATK buff until 60 and it requires a peridot.  Their early level pets are also weak.  None of this makes sense.

The problem was even worse during Luclin.  Throughout the entire era Sony kept adding spells to the class because it 
was incomplete at launch.  Beastlord regen consisted a single spell, Spiritual Purity at level 59, and this spell was 
only +3 until Sony added the others near the end of Luclin.  They got disciplines mid-era as well.  Savagery and Sha's 
Advantage are key spells that prevent the class from being garbage but were rare raid drops and were not made vendor 
spells until three months into PoP.  Beastlords couldn't even summon a pet in Plane of Sky until the middle of PoP.

In PoP however the class is reasonably strong.  They get a 65% slow, plus Celerity which is a 50% haste.  They also aren't
the worst tanks for exp group scenarios.  If a group did not have an enchanter, shaman or bard in it then it would
greatly benefit from a beastlord.  Of course most groups did have one of those classes so if they're present then
you're just a monk without FD but with a mini-clarity.

Beastlords in PoP do monk-level damage if the pet is fully usable.  Since pets are often not fully usable on raids,
they do less damage than monks overall on raids.

The only reason to have beastlords around in raids is the mana regen and ATK buffs.  The original game's classes
already covered all the bases, so adding new classes just means trampling on another class' turf or making mana regen 
and/or ATK go up.  And that's the beastlord.

Beastlord spells have the word "spirit" in them way too frequently.
