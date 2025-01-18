# GrowOpSim
#### Game Version 0.0.5
#### README Version 0.0.5
### Game Description
This is meant to be a fun game simulating growing and selling weed on the black market. Players will be able to experience the entire growing, harvesting, and selling processes while making money to upgrade your grow operation. Maybe there will be a story to follow
###### Written in Unreal Blueprints

### State of the game
Pre-prototype. Main gameplay functions not complete

### Difference between current and next version
#### Current: 0.0.5
#### Next: 0.1
* Only one key interaction
* Nutrients clear on harvest, should only occur when flushing
* Acidity management is non-existent and probably will be for a while
* Inventory system
  * Can only hold one item
  * Items are placed physically on table only
  * 
* Mixed nutrients don't exist yet
* Most of harvesting process doesn't exist
* Selling doesn't exist

### Version requirements
#### Version 0.1 (next)
##### Full gameplay cycle programmed with at least prototype models
##### Technically playable but not obvious what to do or how to do it
###### Important distinction: Growth level is a float on a scale from 0-2000 and is accumalted per second. Growth stage is an integer on a scale from 0-4, which is used for 
* Player interaction
  * Two key line trace contextual interaction
  * Primary key for main interactions
    * Picking up and placing or using any item
  * Secondary key for less used interactions
    * Moving pots
    * Moving harvest processing stations
* **Quality of final flower will depend on how well the player does during growing and post harvest**
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
    * What growth stage it's at for visual representation
* Harvesting
  * Here is when quality is adjusted for
    * Growth time and growth level difference
  * Cut down
    * Requires specific held actor
  * Trimming
    * Requires placing in actor
      * Then requires specific held
  * Drying
    * Requires placing in actor
    * Timing affects quality
  * Curing
    * Requires placing in actor
    * Timing affects quality
* Selling
  * Probably combo of
    * Customers come to you
    * You go to them
    * Internet based
  * Should be able to create a menu of available items for customers
    * Mixing multiple qualities of same strain
      * Player choice to do so
    * Set pricing based on market prices which are based on quality
* Inventory system
  * Scrollable hotbar based with inventory/storage actor placed in world
    * Storage actor interaction opens ***Invertory Menu***

#### Version 0.2
##### Fully playable game, without tutorials or direction, doesn't require proper materials or models
* Place to play entire game, whether or not it has proper materials or models

#### Version 0.3 (undecided)
##### Fully playable game, without tutorials or direction
* Models and materials for everything

#### Version 0.4 (undecided)
##### Fully playable
* Tutorial / Instruction Menu

#### Version 0.5 (undecided)
##### Polish
* Improved widgets
  * Uses images instead of border widgets
  * Progress bars use images(?)
  * Fonts
* Fleshed out interactions and animations
  * In-depth trimming
    * More than a single click in most cases
  * ???

#### Version 1.0 (undecided)
#####
* ?
