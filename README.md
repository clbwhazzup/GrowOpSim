# GrowOpSim
#### Game Version 0.0.6
#### README Version 0.0.6
### Game Description
This is meant to be a fun game simulating growing and selling weed on the black market. Players will be able to experience the entire growing, harvesting, and selling processes while making money to upgrade their grow operation. Maybe there will be a story to follow
###### Written in Unreal Blueprints

## State of the game
Pre-prototype. Main gameplay functions not complete

###### Important distinction: Growth level is a float on a scale from 0-2000 and is accumalted per second based on nutrients. Growth stage is an integer on a scale from 0-4, which is based on growth level, and is used to determine nutrient decay multiplier and size of plant. Confusing but will probably stay
### Patch Notes (0.0.6)
* Declared new version 0.0.6 because enough changes occured
* 0.1 version requirements changed
  * Requirements for selling possibly too complex, added points before to state following requirements are optional
* Inventory menu inside computer added (easiest way to connect to store)
  * Can take stuff out but only placed in by store
* Fixed store/inventory issue by initializing inventory list at start of game
  * List now always has all items whether or not player has bought them, but at 0 quantity
* Nutrient widget updated to have growth level and time
* Balancing
  * NuteDecayConst doubled to 0.04
  * Death quality reduction requirement increased to 2000 growth level or growth time, from 1500

### Difference between current and next version
#### Current: 0.0.6
#### Next: 0.1
* Only one key interaction
* Nutrients clear on harvest, should only occur when flushing
* Acidity management is non-existent and probably will be for a while
* Inventory system
  * Can only hold one item
  * Items are placed physically on table only
  * Inventory menu can only have items placed in it from store
* Mixed nutrients don't exist yet
* Most of harvesting process doesn't exist
* Selling doesn't exist
* Pruning not fully implemented

### Version requirements
#### Version 0.1 (next)
##### Full gameplay cycle programmed with at least prototype models
##### Technically playable but not obvious what to do or how to do it
* Player interaction
  * Two key line trace contextual interaction
  * Primary key for main interactions
    * Picking up and placing or using any item
  * Secondary key for less used interactions
    * Moving pots
    * Moving harvest processing stations
* **Quality of final flower will depend on how well the player does during growing and post harvest processes**
* Pot can have dirt, have seed planted and manages nutrients
  * Place dirt
    * Place dirt with nutrients pre-added
  * Plant seed
    * Seeds of different strains have
      * Specific nutrient requirements
      * Pruning requirements
  * Nutrient Decay
    * Dependent on age
  * Add nutrients
    * Add mixed nutrients
  * Remove nutrients (flushing)
  * Acidity management
* Plant
  * Receives many parameters from pot to determine
    * How fast to grow
    * What growth stage it's at for it's size
    * Whether it is in the harvesting stages
  * Can be pruned while holding specific held actor
* Harvesting
  * Cut down
    * Requires specific held actor
    * Quality is first set here depending on
      * Growth time and growth level difference
      * If it was pruned, if required
  * Trimming
    * Requires placing in actor
      * Then requires specific held
  * Drying
    * Requires placing in actor
    * Timing affects quality
  * Curing
    * Requires placing in actor
    * Timing affects quality
* Mixed nutrients
  * Item type actor
  * Player can add single nutrients
  * Can be picked up
  * Can be used on pot to add multiple nutrients
    * Should be a way to add unequal parts of each
      * maybe just percentage
* Selling
  * **Might be too hard to implement all consideration for pricing**
    * **Will probably only consider quality and amount which will be input for math function**
    * **Probably no customers exactly in this scenario, just a place to sell it in computer**
    * **Probably unmoving market prices**
  * At least internet based, but probably combo of
    * Customers come to you
    * You go to them
    * Internet based
  * Should be able to create a menu of available items for customers
    * Mixing multiple qualities of same strain
      * Player choice to do so
    * Set pricing based on market prices which are based on quality
* Computer
  * Has Store, Inventory, and Menu Creator
    * Store to buy stuff to grow with
    * Inventory to store stuff bought from store and fully cured plants
    * Menu Creator to set up the menu of available items
* Inventory system
  * Scrollable hotbar based with inventory/storage ~~actor placed in world~~ menu inside computer
* Store
  * At least inside computer
  * Can buy all nutrients and seeds(possibly level locked but probably just need money)

#### Version 0.2
##### Fully playable game, without tutorials or direction, doesn't require proper materials or models
* Proper level to play entire game, whether or not it has proper materials or models

#### Version 0.3 (undecided)
##### Fully playable game, without tutorials or direction
* Models and materials for everything

#### Version 0.4 (undecided)
##### Polish
* Improved widgets
  * Uses images instead of border widgets
  * Progress bars use images(?)
  * Fonts
* Fleshed out interactions and animations
  * In-depth trimming
    * More than a single click in most cases
  * ???
* Tutorial or instruction menu
* Line trace based retrieval of item info on HUD

#### Version 1.0 (undecided)
##### First release version
* Definitely tutorials
* Probably reputaion system
