# GrowOpSim
#### Game Version 0.1
#### README Version 0.1
### Game Description
This is meant to be a fun game simulating growing and selling weed on the black market. Players will be able to experience the entire growing, harvesting, and selling processes while making money to upgrade their grow operation. Maybe there will be a story to follow
###### Written in Unreal Blueprints
###### These requirements have been changed many times so that I enjoy development
###### Important distinction: Growth level is a float on a scale from 0-2000 and is accumalted per second based on nutrients. Growth stage is an integer on a scale from 0-4, which is based on growth level, and is used to determine nutrient decay multiplier and size of plant. Confusing but will probably stay

## State of the game
#### Prototype. Most main gameplay functions complete


#### Major Overhaul necessary
* Interaction
  * First, everything after each cast in player needs to be moved to the object that it's acting on
  * Then, interaction blueprint interface
    * Calls that code that was moved to the objects
    * Only one call to this in player, it will have to detect if the object has the interface
* Balancing
  * There should probably be a day night cycle
    * obviously plants can't take more than 14 in game days to grow
    * Can skip time, and plants will grow at the appropriate rate
    * Separate light cycles for veg and bloom
  * Plants are kind of too sensitive
    * Maybe they should be just as sensitive, but the nutrient levels move less
    * Maybe divide nute amounts by 10


### Patch Notes (0.1)
##### So much 
* Weed Storage actor
  * New spot for market
  * Place processed weed in it instead of computer
* Market
  * Sell button now spawns PackagedWeed actor, with player holding it
  * Can be placed on ground, or given to ready customer
* PackagedWeed actor
  * Holds variables to give to customer
  * Customer looks for actor in world to stop roaming and go to meetup spot
* Customer
  * Considers if they were scammed, and adjusts reputation
    * Uses math function (see 0.1 Customer)
* Meetup Spot
  * Pretty much just a vector, but actually an actor
  * Customer finds one and goes to it if they see that weed is available
* Hotbar exists, but non-functional
* No more exposure based lighting
* Probably bugs and stuff

### Difference between current and next version
#### Current: 0.1
#### Next: 0.2
* Nutrients clear on harvest, should only occur when flushing
* Inventory system
  * Can only hold one item (may stay that way)
  * Items are placed physically on table only
  * Inventory menu can only have items placed in it from store
* Saving and loading
  * Loading save happens when level opens, no choice on main menu or pause menu
  * New save is only in pause menu, should aslo be in main menu
* No settings 
* Acidity management
* Mixed nutrients
* Dirt
  * Needs limited amount
* Customer
  * Some should be "uneducated" on market prices
    * Less negative reputation when scammed
* Weed storage 
  * No menu creator
* Market price should go down for larger quantities
* Selling
  * Should be able to create a menu of available items for customers
    * Mixing multiple qualities of same strain
      * Player choice to do so

### Version requirements
#### Version 0.1
##### Full gameplay cycle programmed with at least prototype models
##### Technically playable but not obvious what to do or how to do it
* **Saving**
  * Everything that can move in the world needs to be saved
  * Uses built in save game object, with mostly arrays of structures
  * Each master blueprint class has associated structure and functions to save and load dynamic variables
  * Player, for now at least, has functions that are called when the save button is clicked or when the level is loaded
  * Can save, load, and new save
* Pause and main menu
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
      * Moving PackagedWeed

* **Quality of final flower will depend on how well the player does during growing and post harvest processes**

* Pot
  * Place dirt
  * Plant seed
  * Nutrient Decay
    * Dependent on age
  * Add nutrients
    * Add mixed nutrients
  * Can pick up whether planted or not
  
* Nutrient widget
  * Displays
    * All nutrients as progress bars
    * Growth level and growth time
    * Pot type and plant strain
  * Moves around the pot, always x degrees counterclockwise to player
  * Rotation changes to face player
  * Attached to pot

* Dirt
  * Can have nutrients pre-added

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
  * At least internet based, but probably combo of
    * Customers come to you
    * You go to them
    * Internet based
  * Set pricing based on market prices which are based on quality
  * Should be able to take weed from menu and give to customer
    * PackagedWeed actor holds variables that's passed to customer

* Customer
  * Player has reputations with customers
    * Changes based on sold price vs. market price
      * Uses Sigmoid function to simplify code
        * $R=\frac{M}{4+4(e^\frac{x-M}{M})}-\frac{M}{8}$, where R is reputation change, x is sold price, and M is market price
        * Other option would be many if statements

* Weed Storage
  * Can place plant inside for storage and selling
    * Plant has function to calculate quality and weight
      * Calculates weight based on formula $W = 2.070114 \cdot 1.001504^L - 0.008(T-L)$, where W is the weight, L is the Growth Level, and T is the growth time in seconds
      * Calulates quality depending on how far off dry and cure were
        * Quality consideration for difference of growth time and growth level occurs in pot bp when harvested
    * Market price is calculated based on quality Q, price per gram P, and weight W
      * $M = \frac{Q}{10} \cdot W \cdot P$

* Meetup Spots (possibly temporary)
  * Really just a location for customers to pathfind to

* Computer
  * Store to buy stuff to grow with
  * Inventory to store stuff bought from store

* Inventory system
  * Scrollable hotbar based with inventory/storage ~~actor placed in world~~ menu inside computer

* Store
  * At least inside computer
  * Can buy all nutrients, seeds, tables, pots, stations
  * Cart total is displayed
  * Cart total updates on item added

#### Version 0.2 (next)
##### Fully playable game, without tutorials or direction, doesn't require proper materials or models
###### This and further requirements are incomplete
* Proper level to play entire game, whether or not it has proper materials or models
* Acidity management
* Plant
  * Can be male or female
    * Male
      * Grows no flower
      * Produces pollen
        * Sprays after certain time
        * Affects nearby plants
* Mixed nutrients
  * Item type actor
  * Player can add single nutrients
  * Can be picked up
  * Can be used on pot to add multiple nutrients
    * Should be a way to add unequal parts of each
      * maybe just percentage
* Dirt
  * Has limited amount
* Pot or Dirt
  * Remove nutrients (flushing)
* Player can hold multiple items
* Customer
  * Can be "uneducated" on market prices
    * Less negative reputation when scammed
* Weed storage 
  * Should be able to create a menu of available items for customers
    * Mixing multiple qualities of same strain
      * Player choice to do so
* Market price should go down for larger quantities
* Pause and main menu
  * Settings, saving, loading, new game, exit game
* Wireless monitoring
  * Buyable upgrade
  * Enables widget
  * Checks plant stats anywhere
* Breeding
  * Plants can be bred
  * Plants can be male or female
  * Plants can be bred heterosexually only
  * Breeding 2 different strains can create
    * Predetermined strains, up to a certain point
      * Starting from the current 3 seeds, Bag Seed, Northern Lights, Super Silver Haze, a tree will be created of descending strains
    * Unnamed strains, if a predetermined one doesn't exist
      * Strain can be named
      * Will have "unique" stats
        * May be identical to another strain by chance
  * Bag Seed will always create an unnamed strain

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