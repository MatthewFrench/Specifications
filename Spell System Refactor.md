#Specification : Spell System Refactor

##Objectives
* Any champion can cast any spell, spells can be swapped in-game easily(support of this feature allows many gamemodes)
* Spells can be customized to trigger other spells(or have full and complete logic for triggering any amount of projectiles/self buffs/toggles- think Doombots)
* There shouldn't be guesswork. When someone is making a spell script, they should have access to all the logic and information. It should be clear what a spell is doing and how it is doing it in the spell script. Minimal things should happen automatically outside of the spell script's control
* Less ambiguity, we shouldn't need to have functions if a spell doesn't need them. Leads to confusion

##Raw Thoughts
Right now spells are handled by the Champion class. 4 spells, 2 summoner spells and 1 recall spell. Each spell is instantiated at champion startup. Which sort of makes sense. We can't really have a spell create a spell temporarily(can we?). For example if a spell triggered another spell. The system doesn't support that. But separating projectiles from spells might be good enough. Or start off by adding spell onActive and onDeactivate. Maybe start the beginning of an event system. OnActivate and onDeactivate would handle passives. Buffs can have similar things.
When you cast a spell, it may only create new projectiles but the spell is still the same. So if multiple (of the same spell, think 0 cooldown) spells were cast, it would all be handled in the same spell instance.

Plan of action:

(1) Create onActivate and onDeactivate functions for spell scripts
(2) Create StatModifier class for being able to easily track and modify stat attributes from spells
(3) Create Buff list on Champion class, setup Buffs to behave the nearly the same as spells and allows spells to add Buffs to champions.(edited)

That should be enough to enable most spells and buffs.(edited)
Being able to swap spells and more customizable projectiles will have to be created later as they will require a bit more work.

##Class Diagrams
Below are the class diagrams for the system currently in place and the system being proposed.
####Current System
[Class Diagram Images]
####Proposed System
[Class Diagram Images]
##Use Cases
[Flow charts with description and example code for every use case]

(1) Ezreal

(2) Evelynn

(3) Nunu

(4) Katarina

(5) Singed
