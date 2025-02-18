# Nick Cannon

# V 0.8.0

## 2025.02.04 - 2025.02.18

##### Cannon event of the Jolly Nickholas

###### Look you want a description of this thing read the damn comments.

---

### Description

NICK CANNON - HTML
Created by Chance Hoard
2025.02.04 - 2025.02.18

A cheeseburger cannon that launces a projectile.
Custom physics engine
Custom animations
Replayability
Upgradable Projectile and Cannon
Everything is Cheeseburgers

---

---

# Classes

---

## Projectile:

### Variables

- Mass `Double`
- Aero(dynamicacy) `Double`
- ~~Bounce(s)~~ `Integer`
- ~~Bounce Num~~ `Integer`
- ~~Bounceness~~ `Double`
- Mass Cost `Double`
- Aero Cost `Double`
- Bounce Cost `Double`
- Bounceness Cost `Double`
- Velocity `int[2]`

---

### Methods

#### upgradeMass() -

> Determines if bank is sufficent enough to make purchase, then increases `this.mass` and takes away cost from bank.

#### upgradeAero() -

> Determines if bank is sufficent enough to make purchase, then increases `this.aero` and takes away cost from bank.

#### upgradeBounce() -

> Determines if bank is sufficent enough to make purchase, then increases `this.bounce` and takes away cost from bank.

#### upgradeBounceness() -

> Determines if bank is sufficent enough to make purchase, then increases `this.bounceness` and takes away cost from bank.

---

## Cannon:

### Variables

- Capacity (power) `Double`
- Efficiency `Double`
- American `Double`
- Capacity Cost `Double`
- Efficiency Cost `Double`
- American Cost `Double`

---

### Methods

#### updradeCapacity() -

> Determines if bank is sufficent enough to make purchase, then increases `this.capacity` and takes away cost from bank.

#### upgradeEfficiency() -

> Determines if bank is sufficent enough to make purchase, then increases `this.efficiency` and takes away cost from bank.

#### upgradeAmerican() -

> Determines if bank is sufficent enough to make purchase, then increases `this.american` and takes away cost from bank.

---

---

# Global Variables

---

#### Score (`Double`) -

> Current player score on this launch (directly proportional to Z distance of projectile)

#### Bank (`Double`) -

> Total player score through all launches, includes purchases. Used for shop.

#### Highscore (`Double`) -

> Highest single score the player has earned in 1 launch.

#### Launched (`Boolean`) -

> Has the projectile been launched?

#### Landed (`Boonlean`) -

> Has the projectile hit the ground?

#### Scene (`HTML DOM Element`) -

> Reference to `<a-entity id="scene"></a-scene>`

#### Cannon (`HTML DOM Element`) -

> Reference to the cannon entity `<a-entity id="cannon"></a-entity>`

#### Camera (`HTML DOM Element`) -

> Reference to the camera `<a-entity id="mainCam" camera></a-entity>`

#### Score Text EL (`HTML DOM Element`) -

> Reference to scoreText `<a-entity id="scoreText" text></a-entity>`

#### HighScore Text EL (`HTML DOM Element`) -

> Reference to highscireText `<a-entity id="highscoreText" text></a-entity>`

#### Tick Clock (`Integer`) -

> Int Timer to slow down the `tick:` method of `cannonaim`

---

---

# Components

---

## Cannon Aim:

### Handler for the events and translates physics in-game

#### `init:` -

> Defines `scene`, `cannon`, `camera`, `scoreTextEl`, `highscoreTextEl`
> Adds keyboard event listener that points to keyPressed() (see Functions)

#### `tick:` -

> Basically the main game loop. Handles all physics, calculations, component updates, of launching the projectile.

---

## User Interface:

### Handler for the UI elements

#### `init:` -

> Defines `UI_Main` and `UI_Shop` Along with all buttons attached to them.
> Adds event listeners for buttons: `mouseenter`, `mouseexit`, and `click`.

#### `tick:` -

> Sets all text values for UI Text components.

---

## Better Position Animation:

### Animation component for UI

#### `schema:` -

> To: Location where entity will move to (in AFRAME format:"0 0 0") `String`

> Speed: Units per frame the entity will traverse. `Integer`

> Delay: Delay in number of frames before the animation starts. `Integer`

> Ease: NOT CONFIGURED

> Direction: Direction the entity will travel (axis + dir) ex. "Y+" `String`

> Start Event: Event that will call the animation to play. `String`

#### `init:` -

> `this.animating = false;` animating is a toggle for the animation.
> `this.delayInterval` Counter timer for delaying the animation.

#### `update:` -

> Adds an event listener to self to play animation on `startEvent`

#### `tick:` -

> Updates animation for the entity.

#### `onAnimation:` -

> Called when `startEvent` is triggered. Sets `this.animating` true.

#### `multiple:` -

> Allows for an entity to have multiple instances of the same component.
> Since `UI_Main` has 2 animations (enter and exit), it needs 2 `betterposanimation` components.

---

---

# Functions

---

## Key Pressed (event) -

### Keyboard Input Handler

> Gets cannon X rotation and changes it if 'W' or 'S' are pressed accordingly.
> Clamps cannon rotation.
> Spawns a projectile element on space pressed.
> Sets `launched = true;`

---

## Cam move () -

### Moves and rotates the camera.

> Uses trigonometry concepts to move and rotate the camera so that the cannon and projectile are both visible from a profile view.
> Distance from projectile to cannon is leg A (opposite).
> Given leg A, move camera's X coordinate accordingly.
> Distance from camera to cannon is leg B (adjacent).
> `Math.atan(camera.getAttribute("position").x / 3) * (180 / Math.PI);` gives us the angle at which the camera should be facing.

---

## Relaunch () -

### Resets the game to its initial state but keeps user changes (highscore, upgrades, bank)

> This one's pretty straight forward it's just a reset.

---

## Shop Clicked () -

### Handles the 'click' event of `UI_BTN_Shop`

> Emits events to play `UI_Main` exit animation and `UI_Shop` enterance animation.
