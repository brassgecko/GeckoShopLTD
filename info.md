---
title: Info
layout: page
permalink: /info
---

{%- assign utils = true -%}
{%- assign lootboxes = true -%}
{%- assign puppeteer = false -%}
{%- for mod in site.data.modlist -%}
    {%- case mod.name -%}
        {%- when 'ToolkitUtils' %}
            {%- assign utils = true -%}
        {%- when 'ToolkitUtils - Testing' -%}
            {%- assign utils = true -%}
        {%- when 'Puppeteer' -%}
            {%- assign puppeteer = true -%}
        {%- when 'TwitchToolkit - Lootboxes' -%}
            {%- assign lootboxes = true -%}
    {%- endcase -%}
{%- endfor -%}


{%- assign bal = '!bal' -%}
{%- assign buy = '!buy' -%}
{%- for command in site.data.commands -%}
    {%- if command.data.isBal -%}
        {%- assign bal = command.usage -%}
        {%- continue -%}
    {%- endif -%}

    {%- if command.data.isBuy -%}
        {%- assign buy = command.usage -%}
        {%- continue -%}
    {%- endif -%}
{%- endfor -%}

# Welcome to the GeckoShop

These instructions go with my stream at twitch.tv/brassgecko and explain how to use [Twitch Toolkit](https://steamcommunity.com/sharedfiles/filedetails/?id=1718525787) in order to help or harm the colony. If anything's confusing, wrong, or broken please ask in the chat!


## What does Twitch Toolkit do?

Toolkit lets you directly interfere with the colony. [Commands]({{- "/commands" | relative_url -}}) are your tools
for interacting with the colony. The [store]({{- "/" | relative_url -}}) lets you purchase items or
events that will appear in-game. Buy a pawn to join the colony and outfit them with gear, change the weather, send resources
to help or raiders to try to burn everything..

Some useful shortcuts if you have purchased a colonist:
- To directly equip armor or clothing: $wear itemName
- To directly equip a weapon: $equip itemName
- To directly use food (might not work) or other consumables: $use itemName
- To put something in your colonist inventory: $backpack itemName

## What Are Coins?

Coins are the mod's currency. You can view your balance by using the `{{ bal }}` command. 
{% if utils == true %}
- 💰 represents the amount of coins you current have.
- ⚖ represents your current karma.
- 📈 represents the amount of coins you gain everytime the mod awards coins.
- 📉 represents the amount of coins you lose everytime to mod awards coins.

{% endif %}


{%- if lootboxes == true -%}
You'll also notice that you'll get a message from the bot about a lootbox. You can open this lootbox
by using the `!openlootbox` command, as well as check the number of lootboxes you have with `!lootboxes`.
You'll always get a new lootbox everyday.
{%- endif -%}


<br/>
## What is Karma?

Karma is a system that modifies the number of coins you earn. Beneficial events will raise your karma,
harmful events will lower it, and anything neutral -may- raise your karma, depending on how I have the
settings for the current scenario. BE WARNED! Your karma CAN go negative to the point that it begins
draining your coins away, at which point you rely on my mercy or the generosity of other vieweres for
a chance to recover. Plan your evils carefully!


{%- if puppeteer -%}
<br/>
## What is Puppeteer?

[Puppeteer](https://steamcommunity.com/sharedfiles/filedetails/?id=2057192142) is a mod by Brrainz that
allows viewers to directly control their pawns, and even view a number of information about your pawn in
a graphical way. It also redirects some of the responses from Twitch Toolkit to its website to clean up
chat a bit. So, if you're logged into Puppeeter and you're wondering why the bot isn't responding to you,
you should check the `TT` tab on the website first.
{%- endif -%}
