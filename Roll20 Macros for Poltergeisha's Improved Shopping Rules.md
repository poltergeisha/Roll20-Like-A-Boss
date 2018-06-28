You can find my rules here: https://docs.google.com/document/d/1fmjkjCjPFb0n6jLsVZ7xyEPHFL6r-VD9jwZMlRBr83s/edit?usp=sharing

To use these macros, it is best to make a character sheet called "Party Sheet" and give all the players access to it. Put these macros
in the sheet as Abilities (which are like sheet-specific macros.) When your players want to shop, they can just open up the Attributes tab
of the Party Sheet to access the macros, or start typing %shopping in chat to bring up the menu.

Copy EVERYTHING in the code boxes and name them EXACTLY as suggested.

# Shopping Menu

Name: Shopping

```
&{template:npcaction} {{rname=Shopping}} {{name=Be sure to select your token}} {{description= [Buy a Mundane Item](~Party Sheet|Buying-Mundane-Item) 
[Sell a Mundane Item](~Party Sheet|Selling-Mundane-Item)
[Buy a Magic Item](~Party Sheet|Buying-Magic-Item)
[Sell a Magic Item](~Party Sheet|Selling-Magic-Item)
}}
```

# Buying a Mundane Item

Name: Buying-Mundane-Item

```
&{template:npcaction} {{rname=Shopping for ?{Name of Item}}} {{name=[Click here for in depth rules](https://docs.google.com/document/d/1fmjkjCjPFb0n6jLsVZ7xyEPHFL6r-VD9jwZMlRBr83s/edit#bookmark=id.atwfsxh25vcp)}} {{description=**Availability:** ?{Settlement Size |
Thorpe,
Price Limit: 50 gp
Total Purchase Limit: 500 gp |
Hamlet,
Price Limit: 200 gp
Total Purchase Limit: 1000 gp |
Village,
Price Limit: 500 gp
Total Purchase Limit: 2500 gp |
Small Town,
Price Limit: 1000 gp
Total Purchase Limit: 5000 gp |
Large Town,
Price Limit: 2000 gp
Total Purchase Limit: 10.000 gp |
Small City,
Price Limit: 4000 gp
Total Purchase Limit: 25.000 gp |
Large City,
Price Limit: 8000 gp
Total Purchase Limit: 50.000 gp |
Metropolis,
Price limit: 16.000 gp
Total Purchase Limit: 100.000 gp}

**Price:** [[floor( ?{Item Type | 
Art Objects Gems Trade Goods, ?{Book Price in GP&#125; | 
Mundane items <= 25 gp, ?{Book Price in GP&#125; | 
Mundane items > 25 gp, ?{Book Price in GP&#125;*?{What economy modifier did the GM give you?&#124;
low price&#44;.5&#124;
normal price&#44;1&#124;
high price&#44;1.5&#125; |
Masterwork armor or weapon, (?{Book Price of non-masterwork version in GP&#125;+?{What kind of masterwork  item?&#124;
Light or Medium Armor&#44;100+5d20&#124;
Heavy Armor or Weapon&#44;250+5d20&#125;)*?{What economy modifier did the GM give you?&#124;
low price&#44;.75&#124;
normal price&#44;1&#124;
high price&#44;1.25&#125
} ) ]] gp
}}
```

# Selling a Mundane Item 

Name: Selling-Mundane-Item

```
&{template:npcaction} {{rname=Selling ?{Name of Item}}} {{name=[Click here for in depth rules](https://docs.google.com/document/d/1fmjkjCjPFb0n6jLsVZ7xyEPHFL6r-VD9jwZMlRBr83s/edit#bookmark=id.rg9ba432grqx)}} {{description=**Can you sell it here?** ?{Settlement Size |
Thorpe,
Value Limit: 50 gp
Total Sale Limit: 500 gp |
Hamlet,
Value Limit: 200 gp
Total Sale Limit: 1000 gp |
Village,
Value Limit: 500 gp
Total Sale Limit: 2500 gp |
Small Town,
Value Limit: 1000 gp
Total Sale Limit: 5000 gp |
Large Town,
Value Limit: 2000 gp
Total Sale Limit: 10.000 gp |
Small City,
Value Limit: 4000 gp
Total Sale Limit: 25.000 gp |
Large City,
Value Limit: 8000 gp
Total Sale Limit: 50.000 gp |
Metropolis,
Value limit: 16.000 gp
Total Sale Limit: 100.000 gp}

**Offered Price:** ?{Item Type | 
Art Objects Gems Trade Goods, [[ceil( (70 + 1d20)*0.01*?{Book Price in GP&#125; ) ]] gp | 
Mundane items <= 25 gp, [[ceil( (70 + 1d20)*0.01*?{Book Price in GP&#125; ) ]] gp | 
Mundane items > 25 gp, [[ceil( (70 + 1d20)*0.01*?{Book Price in GP&#125;*?{What economy modifier did the GM give you?&#124;
low price&#44;.5&#124;
normal price&#44;1&#124;
high price&#44;1.5&#125 ) ]] gp |
Masterwork armor or weapon, [[ ceil( ( (70+1d20)*0.01*(?{Book Price of non-masterwork version in GP&#125;+?{What kind of masterwork  item?&#124;
Light or Medium Armor&#44;100+5d20&#124;
Heavy Armor or Weapon&#44;250+5d20&#125;) )*?{What economy modifier did the GM give you?&#124;
low price&#44;.75&#124;
normal price&#44;1&#124;
high price&#44;1.25&#125 ) ]] gp}
}}
```

# Buying a Magic Item

Name: Buying-Magic-Item

```
<?--- Ordering of the Queries --->
!?{Name of Item} 

!?{How might your character know about the item?|I've heard hearsay and rumors about it,@{selected|charisma_mod}|I've read about it in books or learned about it from my mentor,@{selected|intelligence_mod}|Intuitively I'm pretty sure an item like it must exist,@{selected|wisdom_mod}} 

!?{Are you proficent in Arcana?|Yes,@{selected|pb}|No,0|Expertise,2*@{selected|pb}|Jack of All Trades,floor(@{selected|pb}/2) } 

!?{Do you want to use Investigation or Persuasion to find the item?|Investigation,@{selected|investigation_bonus}|Persuasion,@{selected|persuasion_bonus}} 

!?{Settlement Size | Thorpe, [[1d100cs<?{Rarity-&#124; Common&#44;49&#124; Minor Uncommon&#44;24&#125;cf>?{Rarity-&#124; Common&#44;49&#124; Minor Uncommon&#44;24&#125;]] | Hamlet, [[1d100cs<?{Rarity- &#124; Common&#44;74&#124; Minor Uncommon&#44;44&#124; Major Uncommon&#44;24&#125;cf>?{Rarity- &#124; Common&#44;74&#124; Minor Uncommon&#44;44&#124; Major Uncommon&#44;24&#125;]] | Village, [[1d100cs<?{Rarity- &#124; Common&#44;79&#124; Minor Uncommon&#44;54&#124; Major Uncommon&#44;44&#124; Minor Rare&#44;24&#125;cf>?{Rarity- &#124; Common&#44;79&#124; Minor Uncommon&#44;54&#124; Major Uncommon&#44;44&#124; Minor Rare&#44;24&#125;]] | Small Town, [[1d100cs<?{Rarity- &#124; Common&#44;84&#124; Minor Uncommon&#44;64&#124; Major Uncommon&#44;54&#124; Minor Rare&#44;34&#124; Major Rare&#44;24&#125;cf>?{Rarity- &#124; Common&#44;84&#124; Minor Uncommon&#44;64&#124; Major Uncommon&#44;54&#124; Minor Rare&#44;34&#124; Major Rare&#44;24&#125;]] | Large Town, [[1d100cs<?{Rarity- &#124; Common&#44;89&#124; Minor Uncommon&#44;74&#124; Major Uncommon&#44;64&#124; Minor Rare&#44;44&#124; Major Rare&#44;34&#124; Minor Very Rare&#44;24&#125;cf>?{Rarity- &#124; Common&#44;89&#124; Minor Uncommon&#44;74&#124; Major Uncommon&#44;64&#124; Minor Rare&#44;44&#124; Major Rare&#44;34&#124; Minor Very Rare&#44;24&#125;]] | Small City, [[1d100cs<?{Rarity- &#124; Common&#44;94&#124; Minor Uncommon&#44;84&#124; Major Uncommon&#44;74&#124; Minor Rare&#44;54&#124; Major Rare&#44;44&#124; Minor Very Rare&#44;34&#124; Major Very Rare&#44;24&#125;cf>{Rarity- &#124; Common&#44;94&#124; Minor Uncommon&#44;84&#124; Major Uncommon&#44;74&#124; Minor Rare&#44;54&#124; Major Rare&#44;44&#124; Minor Very Rare&#44;34&#124; Major Very Rare&#44;24&#125;]] | Large City, [[1d100cs<?{Rarity- &#124; Common&#44;94&#124; Minor Uncommon&#44;94&#124; Major Uncommon&#44;84&#124; Minor Rare&#44;64&#124; Major Rare&#44;54&#124; Minor Very Rare&#44;44&#124; Major Very Rare&#44;34&#124; Minor Legendary&#44;4&#125;cf>?{Rarity- &#124; Common&#44;94&#124; Minor Uncommon&#44;94&#124; Major Uncommon&#44;84&#124; Minor Rare&#44;64&#124; Major Rare&#44;54&#124; Minor Very Rare&#44;44&#124; Major Very Rare&#44;34&#124; Minor Legendary&#44;4&#125;]] | Metropolis, [[1d100cs<?{Rarity- &#124; Common&#44;100&#124; Minor Uncommon&#44;94&#124; Major Uncommon&#44;94&#124; Minor Rare&#44;74&#124; Major Rare&#44;64&#124; Minor Very Rare&#44;54&#124; Major Very Rare&#44;44&#124; Minor Legendary&#44;24&#124; Major Legendary&#44;5&#125;cf>?{Rarity- &#124; Common&#44;100&#124; Minor Uncommon&#44;94&#124; Major Uncommon&#44;94&#124; Minor Rare&#44;74&#124; Major Rare&#44;64&#124; Minor Very Rare&#44;54&#124; Major Very Rare&#44;44&#124; Minor Legendary&#44;24&#124; Major Legendary&#44;4&#125;]] }

!?{Rarity.| Common,5| Minor Uncommon,8| Major Uncommon,10| Minor Rare,12| Major Rare,15| Minor Very Rare,17| Major Very Rare,20| Minor Legendary,22| Major Legendary,25| Artifact,30} 

!?{Rarity,| Common,50+1d50[common]| Minor Uncommon,100+1d200[minor uncommon]| Major Uncommon,300+1d200[major uncommon]| Minor Rare,500+1d2250[minor rare]| Major Rare,2750+1d2250[major rare]| Minor Very Rare,5000+1d10000[minor very rare]| Major Very Rare,15000+1d10000[major very rare]| Minor Legendary,25000+1d12500[minor legendary]| Major Legendary,37500+1d12500[major legendary]} 

!?{Is this item consumeable?| Yes,.5[consumable]| No,1[not consumable]} 

!?{What economy modifier did the GM give you?| low price,.75[low price economy]| normal price,1[normal price economy]| high price,1.25[high price economy]} 

!?{Base Price of mundane version (if any) in GP|0}[mundane price]


<?--- The Actual Macro --->
&{template:npcaction} {{rname=Shopping for ?{Name of Item}}} {{name=[Click her for in depth rules](https://docs.google.com/document/d/1fmjkjCjPFb0n6jLsVZ7xyEPHFL6r-VD9jwZMlRBr83s/edit#bookmark=id.11ixkfarfntp)}} {{description=**Do you know about the item?** [[1d20+?{How might your character know about the item?|
I've heard hearsay and rumors about it,@{selected|charisma_mod}|
I've read about it in books or learned about it from my mentor,@{selected|intelligence_mod}|
Intuitively I'm pretty sure an item like it must exist,@{selected|wisdom_mod}}+?{Are you proficent in Arcana?|
Yes,@{selected|pb}|
No,0|
Expertise,2*@{selected|pb}|
Jack of All Trades,floor(@{selected|pb}/2) } ]]vs DC ?{Rarity.|
Common,5|
Minor Uncommon,8|
Major Uncommon,10|
Minor Rare,12|
Major Rare,15|
Minor Very Rare,17|
Major Very Rare,20|
Minor Legendary,22|
Major Legendary,25|
Artifact,30}

**Is it available?** ?{Settlement Size |

Thorpe, [[1d100cs<?{Rarity-&#124;
Common&#44;49&#124;
Minor Uncommon&#44;24&#125;cf>?{Rarity-&#124;
Common&#44;49&#124;
Minor Uncommon&#44;24&#125;]] |

Hamlet, [[1d100cs<?{Rarity- &#124; 
Common&#44;74&#124; 
Minor Uncommon&#44;44&#124; 
Major Uncommon&#44;24&#125;cf>?{Rarity- &#124; 
Common&#44;74&#124; 
Minor Uncommon&#44;44&#124; 
Major Uncommon&#44;24&#125;]] |

Village, [[1d100cs<?{Rarity- &#124;
Common&#44;79&#124; 
Minor Uncommon&#44;54&#124; 
Major Uncommon&#44;44&#124; 
Minor Rare&#44;24&#125;cf>?{Rarity- &#124;
Common&#44;79&#124; 
Minor Uncommon&#44;54&#124; 
Major Uncommon&#44;44&#124; 
Minor Rare&#44;24&#125;]] |

Small Town, [[1d100cs<?{Rarity- &#124;
Common&#44;84&#124; 
Minor Uncommon&#44;64&#124; 
Major Uncommon&#44;54&#124; 
Minor Rare&#44;34&#124;
Major Rare&#44;24&#125;cf>?{Rarity- &#124;
Common&#44;84&#124; 
Minor Uncommon&#44;64&#124; 
Major Uncommon&#44;54&#124; 
Minor Rare&#44;34&#124;
Major Rare&#44;24&#125;]] |

Large Town, [[1d100cs<?{Rarity- &#124;
Common&#44;89&#124; 
Minor Uncommon&#44;74&#124; 
Major Uncommon&#44;64&#124; 
Minor Rare&#44;44&#124;
Major Rare&#44;34&#124; 
Minor Very Rare&#44;24&#125;cf>?{Rarity- &#124;
Common&#44;89&#124; 
Minor Uncommon&#44;74&#124; 
Major Uncommon&#44;64&#124; 
Minor Rare&#44;44&#124;
Major Rare&#44;34&#124; 
Minor Very Rare&#44;24&#125;]] |

Small City, [[1d100cs<?{Rarity- &#124;
Common&#44;94&#124; 
Minor Uncommon&#44;84&#124; 
Major Uncommon&#44;74&#124; 
Minor Rare&#44;54&#124;
Major Rare&#44;44&#124; 
Minor Very Rare&#44;34&#124;
Major Very Rare&#44;24&#125;cf>{Rarity- &#124;
Common&#44;94&#124; 
Minor Uncommon&#44;84&#124; 
Major Uncommon&#44;74&#124; 
Minor Rare&#44;54&#124;
Major Rare&#44;44&#124; 
Minor Very Rare&#44;34&#124;
Major Very Rare&#44;24&#125;]] |

Large City, [[1d100cs<?{Rarity- &#124;
Common&#44;94&#124; 
Minor Uncommon&#44;94&#124; 
Major Uncommon&#44;84&#124; 
Minor Rare&#44;64&#124;
Major Rare&#44;54&#124; 
Minor Very Rare&#44;44&#124;
Major Very Rare&#44;34&#124; Minor Legendary&#44;4&#125;cf>?{Rarity- &#124;
Common&#44;94&#124; 
Minor Uncommon&#44;94&#124; 
Major Uncommon&#44;84&#124; 
Minor Rare&#44;64&#124;
Major Rare&#44;54&#124; 
Minor Very Rare&#44;44&#124;
Major Very Rare&#44;34&#124; Minor Legendary&#44;4&#125;]] |

Metropolis, [[1d100cs<?{Rarity- &#124;
Common&#44;100&#124; 
Minor Uncommon&#44;94&#124; 
Major Uncommon&#44;94&#124; 
Minor Rare&#44;74&#124;
Major Rare&#44;64&#124; 
Minor Very Rare&#44;54&#124;
Major Very Rare&#44;44&#124; 
Minor Legendary&#44;24&#124;
Major Legendary&#44;5&#125;cf>?{Rarity- &#124;
Common&#44;100&#124; 
Minor Uncommon&#44;94&#124; 
Major Uncommon&#44;94&#124; 
Minor Rare&#44;74&#124;
Major Rare&#44;64&#124; 
Minor Very Rare&#44;54&#124;
Major Very Rare&#44;44&#124; 
Minor Legendary&#44;24&#124;
Major Legendary&#44;4&#125;]]
} 
*Green is available, red is not.*

**Can you find it?**[[1d20+?{Do you want to use Investigation or Persuasion to find the item?|Investigation,@{selected|investigation_bonus}|Persuasion,@{selected|persuasion_bonus}}]]vs DC ?{Rarity.|
Common,5|
Minor Uncommon,8|
Major Uncommon,10|
Minor Rare,12|
Major Rare,15|
Minor Very Rare,17|
Major Very Rare,20|
Minor Legendary,22|
Major Legendary,25|
Artifact,30}

**Price:** [[ floor( (?{Base Price of mundane version (if any) in GP|0}[mundane price]+?{Rarity,|
Common,50+1d50[common]|
Minor Uncommon,100+1d200[minor uncommon]|
Major Uncommon,300+1d200[major uncommon]|
Minor Rare,500+1d2250[minor rare]|
Major Rare,2750+1d2250[major rare]|
Minor Very Rare,5000+1d10000[minor very rare]|
Major Very Rare,15000+1d10000[major very rare]|
Minor Legendary,25000+1d12500[minor legendary]|
Major Legendary,37500+1d12500[major legendary]})*?{Is this item consumeable?|
Yes,.5[consumable]|
No,1[not consumable]}*?{What economy modifier did the GM give you?|
low price,.75[low price economy]|
normal price,1[normal price economy]|
high price,1.25[high price economy]} ) ]] gp
}}
```

# Selling a Magic Item

Name: Selling-Magic-Item

```
<?--- Ordering of the Queries --->
!?{Name of Item} 

!?{Settlement Size | Thorpe,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;no&#124; Minor Rare&#44;no&#124; Major Rare&#44;no&#124; Minor Very Rare&#44;no&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Hamlet,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;no&#124; Major Rare&#44;no&#124; Minor Very Rare&#44;no&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Village,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;no&#124; Minor Very Rare&#44;no&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Village,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;no&#124; Minor Very Rare&#44;no&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Small Town,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;yes&#124; Minor Very Rare&#44;no&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Large Town,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;yes&#124; Minor Very Rare&#44;yes&#124; Major Very Rare&#44;no&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Small City,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;yes&#124; Minor Very Rare&#44;yes&#124; Major Very Rare&#44;yes&#124; Minor Legendary&#44;no&#124; Major Legendary&#44;no&#125; | Large City,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;yes&#124; Minor Very Rare&#44;yes&#124; Major Very Rare&#44;yes&#124; Minor Legendary&#44;yes&#124; Major Legendary&#44;no&#125; | Metropolis,?{Rarity. &#124; Common&#44;yes&#124; Minor Uncommon&#44;yes&#124; Major Uncommon&#44;yes&#124; Minor Rare&#44;yes&#124; Major Rare&#44;yes&#124; Minor Very Rare&#44;yes&#124; Major Very Rare&#44;yes&#124; Minor Legendary&#44;yes&#124; Major Legendary&#44;yes&#125;} 

!?{Rarity,| Common,50+1d50| Minor Uncommon,100+1d200| Major Uncommon,300+1d200| Minor Rare,500+1d2250| Major Rare,2750+1d2250| Minor Very Rare,5000+1d10000| Major Very Rare,15000+1d10000| Minor Legendary,25000+1d12500| Major Legendary,37500+1d12500} )

!?{Type|Potions scrolls and other consumables with all their uses intact, 0.5[consumable]*(55+1d20)[potion scroll etc]|Amulets rings rods wands staffs and other wondrous items, (65+1d20)[amulet ring rod etc]|Weapons and armor, (70+1d20)[weapons and armor]} 

!?{Base Price of mundane version (if any) in GP|0}

!?{What economy modifier did the GM give you?|low price,.75[low price economy]|normal price,1[normal price economy]|high price,1.25[high price economy]} )


<?--- The Actual Macro --->
&{template:npcaction} {{rname=Selling ?{Name of Item} }} {{name=[Click here for in depth rules](https://docs.google.com/document/d/1fmjkjCjPFb0n6jLsVZ7xyEPHFL6r-VD9jwZMlRBr83s/edit#bookmark=id.uo0z4896va49) }} {{description=**Can you sell it here?** ?{Settlement Size | 

Thorpe,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;no&#124; 
Minor Rare&#44;no&#124;
Major Rare&#44;no&#124; 
Minor Very Rare&#44;no&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Hamlet,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;no&#124;
Major Rare&#44;no&#124; 
Minor Very Rare&#44;no&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Village,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;no&#124; 
Minor Very Rare&#44;no&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Village,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;no&#124; 
Minor Very Rare&#44;no&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Small Town,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;yes&#124; 
Minor Very Rare&#44;no&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Large Town,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;yes&#124; 
Minor Very Rare&#44;yes&#124;
Major Very Rare&#44;no&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Small City,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;yes&#124; 
Minor Very Rare&#44;yes&#124;
Major Very Rare&#44;yes&#124; 
Minor Legendary&#44;no&#124;
Major Legendary&#44;no&#125; |

Large City,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;yes&#124; 
Minor Very Rare&#44;yes&#124;
Major Very Rare&#44;yes&#124; 
Minor Legendary&#44;yes&#124;
Major Legendary&#44;no&#125; |

Metropolis,?{Rarity. &#124;
Common&#44;yes&#124; 
Minor Uncommon&#44;yes&#124; 
Major Uncommon&#44;yes&#124; 
Minor Rare&#44;yes&#124;
Major Rare&#44;yes&#124; 
Minor Very Rare&#44;yes&#124;
Major Very Rare&#44;yes&#124; 
Minor Legendary&#44;yes&#124;
Major Legendary&#44;yes&#125;}

**Offer:** [[ ( (?{Base Price of mundane version (if any) in GP|0}[mundane price]+?{Rarity,|
Common,50+1d50[common]|
Minor Uncommon,100+1d200[minor uncommon]|
Major Uncommon,300+1d200[major uncommon]|
Minor Rare,500+1d2250[minor rare]|
Major Rare,2750+1d2250[major rare]|
Minor Very Rare,5000+1d10000[minor very rare]|
Major Very Rare,15000+1d10000[major very rare]|
Minor Legendary,25000+1d12500[minor legendary]|
Major Legendary,37500+1d12500[major legendary]})*?{What economy modifier did the GM give you?|
low price,.75[low price economy]|
normal price,1[normal price economy]|
high price,1.25[high price economy]} )*0.01[percent]*?{Type|
Potions scrolls and other consumables with all their uses intact, 0.5[consumable]*(55+1d20)[potion scroll etc]|
Amulets rings rods wands staffs and other wondrous items, (65+1d20)[amulet ring rod etc]|
Weapons and armor, (70+1d20)[weapons and armor]}]] gp
}}
```