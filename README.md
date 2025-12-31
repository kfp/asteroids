# Asteroids

An Asteroids clone in js/canvas from  `https://github.com/jsocol/asteroids`. Arrow keys turn and spacebar shoots.


## App Structure
The app is broken into three parts, HTML, CSS and Javascript(JS). Each part serves a different purpose.

### HTML
HTML is the main `structure`. It creates the overall playing field for our app and loads the other two elements.

### CSS
CSS is used to `style` our app. It manages things like colors, sizing, etc.

### Javascript
Javascript is used to `code` out app.  It's what has the game `engine` (what makes the game play, keep score, move, shoot, etc).  Javascript itself has a couple of different parts:

#### Variables 
Variables `hold information`.  They have a variable `name` and a `value`. The following are variables:
```
// Bullet settings
BULLET_SPEED = 200;
MAX_BULLETS = 300;
MAX_BULLET_AGE = 10000;
```
Variables have types as well. These variables are numbers. Variables can also be: 
- **strings** (that is text like `"this is my value")`
- **arrays** `[12, 345, 0]` (sets of values) 
- complex **objects** `{name: "bobby", age: 42}`
- **functions** (logical grouping of code which completes particular actions) `Asteroids.infoPane = function(game, home) { ... }` 
- other types

#### Statements
Statements `do stuff`.  Setting a variable is a statement, calling a `function` is a statement. In Javascript statements usually end in a `;` character. 

#### Functions
Functions are `groups of statements` organized logically around a particular task. You might have a funciton that sets up the initial game or draws the end game screen, moves the ship around or fires the bullets. This funciton is used to determine if the ship and asteroids have collided:

```
Asteroids.collision = function (a, b) {
    // if a.getPosition() inside b.getBounds?
    var a_pos = a.getPosition(),
        b_pos = b.getPosition();

    function sq (x) {
        return Math.pow(x, 2);
    }

    var distance = Math.sqrt(sq(a_pos[0] - b_pos[0]) +
                             sq(a_pos[1] - b_pos[1]));

    if (distance <= a.getRadius() + b.getRadius())
        return true;
    return false;
}
```
The function is defined by `funciton (a, b)` and includes all the statements between the `{` and `}` characters. a and b are arguments which are variables that are passed into the function. The function is called elsewhere with `Asteroids.collision(game.player, asteroids[i]))`. This checks if the player has collided with a particular asteroid. 

## Loading the Game in the Editor
...

## Challenges:
### Beginner
-  [ ] Unlike most programming languages, Javascript is VERY forgiving, if you leave off a `;` at the end of the line, or even have giberish on a line, it will try to keep going. See if you can make the game "crash" becomming unplayable. Put in some nonsense code, change lines, delete lines, etc. You can always go back to the original code by reloading the page
- [ ] Edit the CSS and change some colors around. he text is currently in `hexadecimal` which is a format of a `#` followed by 6 mostly numbers (but also the letters A-F) but you can also use common color names. (Replace `#000` with `red` or `salmon`)
- [ ] Edit the `FRAME_PERIOD` variable (this controls the frame `rate`), changing the number higher or lower. What affect does this have on the game?
- [ ] Edit one of the Javascript variables to give yourself more bullets.
- [ ] Edit one of the Javascript variables to increase the number of asteroids that spawn when an asteroid is destroyed
- [ ] Edit some variables to get the highest score you can
- [ ] Make yourself effectively invincible by changing some of the default variables
- [ ] Sometimes the code you write won't behave how you expect. `Logging` is a concept of aving your app write out information about what's happening. Right underneith your initial variables, add the following line `console.log("Look I'm logging")`. You will be able to see that line print out at the start of your game by clickign on the `console` tab at the bottom left of your game. 

### Hard
- [ ] Make the point of the game to die as quickly as possible with the lowest score. Change variables to make this more challenging/easier.
  - [ ] BONUS: the game keeps a record of highScores and prints them out at the end of the game in the order highest to lowest. Can you reverse the order it sorts them in reverse order so the lowest is at the top?
- [ ] Typically it's best practice to maintain your app `structure` in html and your app `styling` in CSS, but technically Javascript can do both in itself. In fact, the ship itself (the `player`) is drawn by a number of points defined by an `array`. See if you can read the code and find it, changing it to make the ship a different shape.
  - [ ] BONUS: The asteroids are sized/shaped/colored in the javascript. Change the asteroid colors/shapes.