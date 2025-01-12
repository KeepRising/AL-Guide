# Upgrading and Compounding

Improving your equipment is one of the main ways to strengthen your characters in Adventureland. Improving equipment increases the damage of weapons, the defensive values of armor and the amount of stats you get from said armor and accessories, which in turn will  improve your overall damage output (and survivability). You can look at all the levels of any item in the ingame guide or here: [online](https://adventure.land/docs/guide/all/items)

Generally, weapons and armor are upgraded, while accessories are compounded. Both processes are based on chance: You roll a number between 0 and 100 and the improvement succeeds if you roll a number smaller than the current upgrade chance in percent. A success increases the item's level by one, while a failure **permanently** destroys the item. <br>
You can upgrade your equipment at the red crafting table of the NPC `Cue` in town, right next the general shop. Similarly the blue crafting table is used for compounds, or you do it directly via code with the corresponding functions: [upgrade](https://adventure.land/docs/code/functions/upgrade) and [compound](https://adventure.land/docs/code/functions/compound)
For upgrading only a single item and an upgradescroll is needed, while compounding requires three items of the same type and the same level as well as a compoundscroll. Note that a successful compound will still only give you one item of the next higher level. Both upgrade and compoundscrolls can be bought at the NPC `Lukas` in town, close to the crafting tables themselves. Which scroll you need depends on the grade (tier) of the item you want to upgrade: Grades range from basic (no grade mentioned in tool tip) to `high`,`rare` and eventually `legendary`. To upgrade/compound an item you will need an upgrade-/compoundscroll of at least the same grade as the item you want to upgrade. Legendary scrolls can be bought at another NPC, but those are really expensive and only needed in the lategame.

## Giving Stats to your Armor
Lukas furthermore sells stat-scrolls for all 3 main attributes: Strength, Dexterity, Intelligence. Those can be used to upgrade armor and convert their stats to whatever you want. While the item is upgraded same way as a regular item would be, the success is guaranteed and will result it the stats of the armor changing to whatever scroll you used to upgrade. There is no limit on how often you can do this. The amount of stat-scrolls needed is defined by the rarity of the item: 1 for basic items, 10 for high, 100 for rare and 1000 for legendary. Giving stats to your armor is really important, as the damage each character is able to do scales with the main stat of its respective class.


## Upgradechances and how to improve them

The minimum upgradechance of an item is defined by the item level and its rarity at level 0, irregardless of it's rarity at the current level. Similarly, there is also a maximum upgradechance at each level (and level 0 rarity) which can not be exceeded. Generally the minimum upgradechance will always decrease with the item level, making high level equipment harder and harder to get. However, there are a few options to improve your chances.

### Using a higher tier scroll
Using a scroll of a higher tier than necessary for the current upgrade will improve the upgrade chance according to the following formula:

`upgrade_chance_increase = minimum_upgrade_chance * 0.2 + 0.01`

Note that all chances here are expressed as numbers, not percentages. The formula for compound is slightly different:

`compound_chance_increase = minimum_compound_chance * 1.1 + 0.001`

This increase depends only on the minimum chances on the current level of the item, **not** the current chance. So it is independent of all other factors and will be the same regardless of other methods used to increase the chance before or after. You just can't exceed the maximum chance. There is no further increase of the chance when using scrolls of 2 or more tiers higher, so it is always enough to just simply use the next higher tier of scroll. Note that due to the prices of compound scrolls and the smaller increase in the compound chance compared to the upgrades it is very rarely really worth gold-wise to use a next higher tier cscroll for compounds, apart from really expensive items. Of course it can still be used to reduce the total number of needed items by investing more gold.

### Using an Offering
There are currently three different offerings in the game: 
- Primling `offeringp` 
- Primodial Essence `offering`, prim for short
- Primodial X `offeringx`, primX for short

These can be used during an upgrade or compound to boost the upgradechance notably, but are permanently used up in the process. They are used by placing them into the open slot next to the scrolls when upgrading. Primlings cannot be bought from an NPC, but are dropped from different monsters in the world, most noteably Black Scorpions. They are the cheapest of the three, but also offer the smallest increase to the upgrade chances. Prims can be bought from `Garwyn` in town for 27.42m gold. PrimX are lategame items and need to be crafted and have a very expensive recipe.<br>
Offerings will always significantly increase the upgrade chances, but the bonus you get is not constant. Offerings enhance other chance increasing effects, for example an offering will give you more benefit when used on an item with some failstack compared to using it on an item without failstack.

### Failstacking
Whenever you fail an upgrade the next upgrade on the same level and one level below that gets a small bonus to its upgrade chance. This bonus is completly reset for that particular level after a successful upgrade. This works accross all item grades and the bonus itself is called a failstack. If you fail multiple times the boni will add up. There is a limit to how often you can increase your chance with this, but reaching that limit requires a lot of failstack, so much in fact, that you will reach the maximum upgrade chance at least with a prim. Failing higher level items (7+) gives passes down the failstack bonus to more than one level below and gives more failstack than failing an item on the lower level itself. Furthermore, there are two components to failstack: A general, server wide failstack and a personal one. The server wide failstack will be used up as soon as anyone on the server succeeds and upgrade on that level. So if you want to deliberately failstack for a certain item it is best to use cheap items of one higher level (even if you succeed one of those the failstack for the level below will not be used up) and make sure nobody else is doing upgrades at the same time. You can see this by how active the red crafting table at `Cue` is.<br>
For higher level items you may not see an improvement right away. That is because the minimum upgrade chance is actually not the base chance to which the bonus is applied. The actual base chance is lower, so you need to fail a few items before you can see any failstacking effect on a level 8 item for example. However, since the bonus is already applied internally offerings for example will already give you more benefit, before you are even able to notice any difference without an offering.

### Enhanced items
Items have a chance to have a naturally higher upgrade chance. This bonus exists in multiple strengths, the better the improvement the rarer it is. You cannot influence whether or not you get such an item, it is simply rolled at the item generation, but the bonus can be amplified with an offering.

### Using your Equipment
Using a piece of equipment on your characters very slowly gives the item a bonus to its upgrade/compoundchance. This process is very slow, but especially for compounds it can be used. For example it might be worth to check whether using your current +3 amulet gives you a higher compound chance than using 3 completely fresh ones right out of the bank. But again, the process is very slow.

### Feeding offerings to an item
It is possible to feed an offering into an item. To do so simply "upgrade" the item with an offering and without any scroll. The offering will be consumed and the upgradechance of that item will permanently go up slightly. However, due to the small increase and the high costs of offerings, this is not recommended. Failstacking the the way cheaper option.

### Increased Chance through Upgrade History
Using an offering or a higher tier scroll to upgrade or compound items will give those items a slight bonus to all future upgrade chances. This bonus is very small and it is basically never worth to use better scrolls or offerings for that particular reason, but it is a nice bonus to have, especially on compounds, where it is nearly impossible to properly failstack due to the amount of items required.
