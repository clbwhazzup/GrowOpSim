# GrowOpSim
#### Game Version 0.0.9.9
#### README Version 0.0.9.9
### Game Description
This is meant to be a fun game simulating growing and selling weed on the black market. Players will be able to experience the entire growing, harvesting, and selling processes while making money to upgrade their grow operation. Maybe there will be a story to follow
###### Written in Unreal Blueprints
###### Important distinction: Growth level is a float on a scale from 0-2000 and is accumalted per second based on nutrients. Growth stage is an integer on a scale from 0-4, which is based on growth level, and is used to determine nutrient decay multiplier and size of plant. Confusing but will probably stay

## State of the game
#### Pre-prototype. Main gameplay functions not complete

### Patch Notes (0.0.9.9)
* Not really sure what changed other than
  * Added a level
  * Fixed bugs

### Difference between current and next version
#### Current: 0.0.9.9
#### Next: 0.1
* Nutrients clear on harvest, should only occur when flushing
* Inventory system
  * Can only hold one item
  * Items are placed physically on table only
  * Inventory menu can only have items placed in it from store
* Saving and loading
  * Loading save happens when level opens, no choice on main menu or pause menu
  * New save is only in pause menu, should aslo be in main menu

### Version requirements
#### Version 0.1 (next)
##### Full gameplay cycle programmed with at least prototype models
##### Technically playable but not obvious what to do or how to do it
* **Saving**
  * Everything that can move in the world needs to be saved
  * Uses built in save game object, with mostly arrays of structures
  * Each master blueprint class has associated structure and functions to save and load dynamic variables
  * Player, for now at least, has functions that are called when the save button is clicked or when the level is loaded
  * Can load save and new save from main menu
  * Can save, load, and new save from pause menu
* Pause and main menu
  * Settings, saving, loading, new game, exit game
* Player
  * Has money
  * Has HUD
    * Crosshair
    * Money
  * Two key line trace contextual interaction
    * Primary key for main interactions
      * Picking up and placing or using any item
    * Secondary key for less used interactions
      * Moving pots
      * Moving harvest processing stations

* **Quality of final flower will depend on how well the player does during growing and post harvest processes**

* Pot
  * Place dirt
  * Plant seed
  * Nutrient Decay
    * Dependent on age
  * Add nutrients
    * Add mixed nutrients
  * Remove nutrients (flushing)
  * Can pick up whether planted or not
  
* Nutrient widget
  * Displays
    * All nutrients as progress bars
    * Growth level and growth time
    * Pot type and plant strain
  * Moves around the pot, always 90 degrees counterclockwise to player
  * Rotation changes to face player
  * Attached to pot

* Dirt
  * Can have nutrients pre-added
  * Has limited amount

* Nutrients
  * Can add to pot
  * Has limited amount

* Seeds of different strains have
    * Specific nutrient requirements
    * Pruning requirements
    * Dry and cure requirements
      * Tolerance for quality adjustment
    * Grace periods

* Plant
  * Receives many parameters from pot to determine
    * How fast to grow
    * What growth stage it's at for it's size
    * Whether it is in the harvesting stages
  * Can be pruned while holding specific held actor

* Harvesting
  * Cut down
    * ~~Requires specific held actor~~ Maybe not
    * Quality is first set here (function in pot bp) depending on
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
  * Can place plant inside computer for storage and selling
    * Plant has function to calculate quality and weight
      * Calculates weight based on formula W = (2.070114 * 1.001504 ^ L) - (0.008(T-L)), where W is the weight, L is the Growth Level, and T is the growth time
      * Calulates quality depending on how far off dry and cure were
        * Quality consideration for difference of growth time and growth level occurs in pot bp when harvested

* Inventory system
  * Scrollable hotbar based with inventory/storage ~~actor placed in world~~ menu inside computer

* Store
  * At least inside computer
  * Can buy all nutrients, seeds, tables, pots, stations
  * Cart total is displayed
  * Cart total updates on item added

#### Version 0.2
##### Fully playable game, without tutorials or direction, doesn't require proper materials or models
* Proper level to play entire game, whether or not it has proper materials or models
* Acidity management
* Mixed nutrients
  * Item type actor
  * Player can add single nutrients
  * Can be picked up
  * Can be used on pot to add multiple nutrients
    * Should be a way to add unequal parts of each
      * maybe just percentage

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
* Probably reorganize code